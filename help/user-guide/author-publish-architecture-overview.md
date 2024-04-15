---
title: Panoramica dell’architettura di authoring e pubblicazione
description: L’architettura di AEM Screens è simile a un’architettura tradizionale di AEM Sites. Il contenuto viene creato su un’istanza dell’autore AEM e quindi replicato in avanti su più istanze di pubblicazione.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# Panoramica dell’architettura di authoring e pubblicazione {#author-and-publish-architectural-overview}

In questa pagina sono evidenziati i seguenti argomenti:

* **Introduzione ai server di pubblicazione**
* **Panoramica dell’architettura**
* **Processo di registrazione**

## Prerequisiti {#prerequisites}

Prima di iniziare a utilizzare i server di authoring e di pubblicazione, è necessario conoscere in precedenza:

* **Topologia AEM**
* **Creazione e gestione di un progetto AEM Screens**
* **Processo di registrazione del dispositivo**

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.4 Screens Feature Pack 2. Per accedere a questo Feature Pack, contatta il supporto Adobe e richiedi l’accesso. Dopo aver ricevuto l&#39;autorizzazione, scaricala da Condivisione pacchetti.

## Introduzione {#introduction}

L’architettura di AEM Screens è simile a un’architettura tradizionale di AEM Sites. Il contenuto viene creato su un’istanza dell’autore AEM e quindi replicato in avanti su più istanze di pubblicazione. I dispositivi su AEM Screens ora possono connettersi a una farm di pubblicazione AEM tramite il load balancer. È possibile aggiungere più istanze di pubblicazione AEM per continuare a scalare la farm di pubblicazione.

*Ad esempio*, un autore di contenuti AEM Screens esegue un comando sul sistema di authoring di un determinato dispositivo. Il dispositivo è configurato per interagire con una farm di pubblicazione o con un autore di contenuti AEM Screens che ottiene informazioni sui dispositivi configurati per interagire con le farm di pubblicazione.

Il diagramma seguente illustra sia l’ambiente di authoring che quello di pubblicazione.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Progettazione architettonica {#architectural-design}

Questa soluzione è facilitata da cinque componenti architettonici:

* ***Replica dei contenuti*** dall’authoring alla pubblicazione per la visualizzazione per dispositivi

* ***Inverso*** replica di contenuti binari dall&#39;ambiente di pubblicazione (ricevuti dai dispositivi) all&#39;ambiente di authoring.
* ***Invio*** comandi dall’ambiente di authoring a quello di pubblicazione tramite API REST specifiche.
* ***Messaggistica*** tra le istanze di pubblicazione per sincronizzare gli aggiornamenti e i comandi relativi alle informazioni sul dispositivo.
* ***Polling*** dall’autore delle istanze di pubblicazione per ottenere informazioni sul dispositivo tramite API REST specifiche.

### Replica (inoltro) di contenuti e configurazioni  {#replication-forward-of-content-and-configurations}

Gli agenti di replica standard vengono utilizzati per replicare il contenuto del canale AEM Screens, le configurazioni di posizione e le configurazioni dei dispositivi. Questo consente agli autori di aggiornare il contenuto di un canale e, facoltativamente, di passare attraverso una sorta di flusso di lavoro di approvazione prima di pubblicare gli aggiornamenti del canale. È necessario creare un agente di replica per ogni istanza di pubblicazione nella farm di pubblicazione.

Il diagramma seguente illustra il processo di replica:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>È necessario creare un agente di replica per ogni istanza di pubblicazione nella farm di pubblicazione.

### Agenti e comandi di replica Screens  {#screens-replication-agents-and-commands}

Gli agenti di replica specifici per schermi personalizzati vengono creati per inviare comandi dall’istanza Autore al dispositivo AEM Screens. Le istanze Pubblicazione AEM fungono da intermediario per inoltrare questi comandi al dispositivo.

Questo consente agli autori di continuare a gestire il dispositivo come, inviare aggiornamenti del dispositivo e acquisire schermate dall’ambiente di authoring. Gli agenti di replica di AEM Screens dispongono di una configurazione di trasporto personalizzata, come gli agenti di replica standard.

### Messaggistica tra istanze di pubblicazione  {#messaging-between-publish-instances}

Spesso un comando deve essere inviato a un dispositivo una sola volta. Tuttavia, in un’architettura di pubblicazione con carico bilanciato, non è noto a quale istanza di pubblicazione il dispositivo si connette.

Pertanto, l’istanza di authoring invia il messaggio a tutte le istanze Publish. Tuttavia, solo un singolo messaggio deve quindi essere inoltrato al dispositivo. Per garantire la corretta messaggistica, la comunicazione deve aver luogo tra le istanze di pubblicazione. Ciò si ottiene utilizzando *Apache ActiveMQ Artemis*. Ogni istanza di pubblicazione viene inserita in una topologia liberamente associata utilizzando il servizio di individuazione Sling basato su Oak e ActiveMQ è configurato in modo che ogni istanza di pubblicazione possa comunicare e creare una singola coda di messaggi. Il dispositivo AEM Screens esegue il polling della farm di pubblicazione dell’AEM tramite il load balancer e seleziona il comando dalla parte superiore della coda.

### Replica inversa {#reverse-replication}

Spesso, a seguito di un comando, è previsto che il dispositivo Screens invii una risposta all’istanza di authoring. Per ottenere questo AEM ***Replica inversa*** viene utilizzato.

* Crea un agente di replica inversa per ogni istanza di pubblicazione, simile agli agenti di replica standard e agli agenti di replica di AEM Screens.
* Una configurazione del modulo di avvio del flusso di lavoro ascolta i nodi modificati nell’istanza di pubblicazione dell’AEM e a sua volta attiva un flusso di lavoro per inserire la risposta del dispositivo nella casella in uscita dell’istanza di pubblicazione dell’AEM.
* In questo contesto, la replica inversa viene utilizzata solo per i dati binari (ad esempio, file di registro e schermate) forniti dai dispositivi. I dati non binari vengono recuperati tramite polling.
* Il polling di replica inversa dall’istanza di authoring AEM recupera la risposta e la salva nell’istanza di authoring.

### Polling delle istanze di pubblicazione  {#polling-of-publish-instances}

L’istanza di authoring deve essere in grado di eseguire il polling dei dispositivi per ottenere un heartbeat e conoscere lo stato di integrità di un dispositivo connesso.

I dispositivi eseguono il ping del load balancer e vengono indirizzati a un’istanza Publish. Lo stato del dispositivo viene quindi esposto dall’istanza AEM Publish tramite un’API Publish distribuita il **api/screens-dcc/devices/static** per tutti i dispositivi attivi e **api/screens-dcc/devices/&lt;device_id>/status.json** per un singolo dispositivo.

L’istanza di authoring esegue il polling di tutte le istanze di pubblicazione e unisce le risposte sullo stato del dispositivo in un singolo stato. Il processo pianificato che esegue il polling sull’autore è `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` e possono essere configurati in base a un’espressione cron.

## Registrazione {#registration}

La registrazione continua a provenire dall’istanza di authoring AEM. Il dispositivo AEM Screens punta all’istanza di authoring e la registrazione è completa.

Dopo che un dispositivo è stato registrato nell’ambiente di authoring dell’AEM, la configurazione del dispositivo e le assegnazioni di canale/pianificazione vengono replicate nelle istanze di pubblicazione dell’AEM. La configurazione del dispositivo AEM Screens viene quindi aggiornata per puntare al load balancer davanti alla farm di pubblicazione dell’AEM. Questa è una configurazione una tantum. Una volta connesso correttamente all’ambiente di pubblicazione, il dispositivo Screens può continuare a ricevere comandi provenienti dall’ambiente di authoring. Non dovrebbe essere mai necessario collegare direttamente il dispositivo AEM Screens all’ambiente di authoring dell’AEM.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Passaggi successivi {#the-next-steps}

Quando conosci il design architetturale della configurazione di authoring e pubblicazione in AEM Screens, consulta [Configurazione di Author e Publish per AEM Screens](author-and-publish.md) per ulteriori dettagli.
