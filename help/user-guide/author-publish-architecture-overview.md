---
title: Panoramica dell’architettura di authoring e pubblicazione
seo-title: Panoramica dell’architettura di authoring e pubblicazione
description: L’architettura di AEM Screens assomiglia a un’architettura AEM Sites tradizionale. Il contenuto viene creato su un’istanza di authoring AEM e quindi replicato in avanti in più istanze di pubblicazione. Segui questa pagina per ulteriori informazioni sull’authoring e la pubblicazione di una panoramica dell’architettura.
seo-description: L’architettura di AEM Screens assomiglia a un’architettura AEM Sites tradizionale. Il contenuto viene creato su un’istanza di authoring AEM e quindi replicato in avanti in più istanze di pubblicazione. Segui questa pagina per ulteriori informazioni sull’authoring e la pubblicazione di una panoramica dell’architettura.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Amministrazione di schermi
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 3%

---


# Panoramica dell’architettura di authoring e pubblicazione {#author-and-publish-architectural-overview}

Questa pagina evidenzia i seguenti argomenti:

* **Introduzione ai server di pubblicazione**
* **Panoramica dell&#39;architettura**
* **Processo di registrazione**

## Prerequisiti {#prerequisites}

Prima di iniziare a utilizzare i server di authoring e pubblicazione, è necessario disporre di conoscenze precedenti su:

* **Topologia AEM**
* **Creazione e gestione di un progetto AEM Screens**
* **Processo di registrazione dei dispositivi**

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se hai installato AEM Feature Pack 2 di 6.4 Screens. Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Introduzione {#introduction}

L’architettura di AEM Screens assomiglia a un’architettura AEM Sites tradizionale. Il contenuto viene creato su un’istanza di authoring AEM e quindi replicato in avanti in più istanze di pubblicazione. I dispositivi AEM Screens ora possono connettersi a una farm di pubblicazione AEM tramite load balancer. È possibile aggiungere più istanze di pubblicazione AEM per continuare a ridimensionare la farm di pubblicazione.

*Ad esempio*, un autore di contenuti AEM Screens invia un comando al sistema di authoring per un particolare dispositivo configurato per interagire con una farm di pubblicazione o un autore di contenuti AEM Screens che ottiene informazioni sui dispositivi configurati per interagire con farm di pubblicazione.

Il diagramma seguente illustra gli ambienti di authoring e pubblicazione.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Progettazione architettonica {#architectural-design}

Sono disponibili cinque componenti architettonici che facilitano questa soluzione:

* ***Replicazione del*** contenuto dall&#39;autore alla pubblicazione per la visualizzazione da parte dei dispositivi

* ****** Ripristino del contenuto binario dalla pubblicazione (ricevuto dai dispositivi) all’authoring
* ****** Invio di comandi dall’autore per la pubblicazione tramite API REST specifiche
* ****** Messaggistica tra istanze di pubblicazione per sincronizzare gli aggiornamenti e i comandi delle informazioni sul dispositivo
* ****** Inchiostro da parte dell’autore delle istanze di pubblicazione per ottenere informazioni sul dispositivo tramite API REST specifiche

### Replica (avanti) dei contenuti e delle configurazioni {#replication-forward-of-content-and-configurations}

Gli agenti di replica standard vengono utilizzati per replicare il contenuto del canale delle schermate, le configurazioni della posizione e le configurazioni del dispositivo. Questo consente agli autori di aggiornare il contenuto di un canale ed eventualmente di passare attraverso un flusso di lavoro di approvazione prima di pubblicare gli aggiornamenti del canale. È necessario creare un agente di replica per ogni istanza di pubblicazione nella farm di pubblicazione.

Il diagramma seguente illustra il processo di replica:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>È necessario creare un agente di replica per ogni istanza di pubblicazione nella farm di pubblicazione.

### Comandi e agenti di replica Screens {#screens-replication-agents-and-commands}

Vengono creati agenti di replica specifici per gli schermi personalizzati per inviare i comandi dall&#39;istanza Author al dispositivo AEM Screens. Le istanze di AEM Publish fungono da intermediario per inoltrare questi comandi al dispositivo.

Questo consente agli autori di continuare a gestire il dispositivo, ad esempio inviare aggiornamenti del dispositivo e scattare schermate dall’ambiente di authoring. Gli agenti di replica AEM Screens dispongono di una configurazione di trasporto personalizzata, come gli agenti di replica standard.

### Messaggistica tra istanze di pubblicazione {#messaging-between-publish-instances}

In molti casi, un comando deve essere inviato a un dispositivo una sola volta. Tuttavia, in un&#39;architettura di pubblicazione con bilanciamento del carico, non è noto a quale istanza di pubblicazione il dispositivo si sta connettendo.

Pertanto, l’istanza di authoring invia il messaggio a tutte le istanze Publish. Tuttavia, solo un messaggio deve essere inviato al dispositivo. Per garantire la corretta messaggistica, è necessario che vi sia una comunicazione tra le istanze di pubblicazione. Questo si ottiene utilizzando *Apache ActiveMQ Artemis*. Ogni istanza di pubblicazione viene inserita in una topologia agganciata liberamente utilizzando il servizio di individuazione Sling basato su Oak e ActiveMQ è configurato in modo che ogni istanza di pubblicazione possa comunicare e creare una singola coda di messaggio. Il dispositivo Screens esegue il polling della farm di pubblicazione tramite il load balancer e rileva il comando dalla parte superiore della coda.

### Replica inversa {#reverse-replication}

In molti casi, seguendo un comando, è previsto un qualche tipo di risposta dal dispositivo Screens da inoltrare all&#39;istanza Author. Per ottenere questo AEM viene utilizzata ***Replica inversa***.

* Crea un agente di replica inversa per ogni istanza di pubblicazione, simile agli agenti di replica standard e agli agenti di replica dello schermo.
* Una configurazione del modulo di avvio del flusso di lavoro ascolta i nodi modificati nell’istanza di pubblicazione e a sua volta attiva un flusso di lavoro per inserire la risposta del dispositivo nella casella in uscita dell’istanza di pubblicazione.
* Una replica inversa in questo contesto viene utilizzata solo per i dati binari (come file di registro e schermate) forniti dai dispositivi. I dati non binari vengono recuperati dal polling.
* La replica inversa estratta dall&#39;istanza di authoring AEM recupera la risposta e la salva nell&#39;istanza di authoring.

### Polling delle istanze di pubblicazione {#polling-of-publish-instances}

L’istanza autore deve essere in grado di eseguire il polling dei dispositivi per ottenere un heartbeat e conoscere lo stato di integrità di un dispositivo connesso.

I dispositivi eseguono il ping del load balancer e vengono indirizzati a un&#39;istanza di pubblicazione. Lo stato del dispositivo viene quindi esposto dall&#39;istanza di pubblicazione tramite un&#39;API Publish fornita @ **api/screens-dcc/devices/static** per tutti i dispositivi attivi e **api/screens-dcc/devices/&lt;device_id>/status.json** per un singolo dispositivo.

L’istanza di authoring controlla tutte le istanze di pubblicazione e unisce le risposte sullo stato del dispositivo in un unico stato. Il processo pianificato che esegue il polling sull’autore è `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` e può essere configurato in base a un’espressione cron.

## Registrazione {#registration}

La registrazione continua ad avere origine nell’istanza di authoring AEM. Il dispositivo AEM Screens viene puntato all’istanza di authoring e la registrazione viene completata.

Una volta che un dispositivo è stato registrato nell’ambiente di authoring, la configurazione del dispositivo e le assegnazioni di canale/pianificazione vengono replicate nelle istanze di pubblicazione AEM. La configurazione del dispositivo AEM Screens viene quindi aggiornata per puntare al load balancer davanti alla farm di pubblicazione AEM. Questa è una configurazione unica, una volta che il dispositivo Screens è connesso correttamente all’ambiente di pubblicazione può continuare a ricevere i comandi provenienti dall’ambiente di authoring e non dovrebbe essere necessario collegare direttamente il dispositivo Screens all’ambiente di authoring.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Passaggi successivi {#the-next-steps}

Una volta compreso il design architettonico dell&#39;impostazione di authoring e pubblicazione in AEM Screens, consulta [Configurazione di authoring e pubblicazione per AEM Screens](author-and-publish.md) per ulteriori dettagli.
