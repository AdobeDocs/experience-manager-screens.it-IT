---
title: Panoramica sull'architettura di Author e Publish
seo-title: Panoramica sull'architettura di Author e Publish
description: L'architettura di AEM Screens assomiglia a una tradizionale architettura di AEM Sites. Il contenuto viene creato su un’istanza di creazione AEM e quindi replicato in avanti in più istanze di pubblicazione. Per ulteriori informazioni su come creare e pubblicare una panoramica dell’architettura, consultate questa pagina.
seo-description: L'architettura di AEM Screens assomiglia a una tradizionale architettura di AEM Sites. Il contenuto viene creato su un’istanza di creazione AEM e quindi replicato in avanti in più istanze di pubblicazione. Per ulteriori informazioni su come creare e pubblicare una panoramica dell’architettura, consultate questa pagina.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Panoramica sull'architettura di Author e Publish {#author-and-publish-architectural-overview}

Questa pagina evidenzia i seguenti argomenti:

* **Introduzione ai server di pubblicazione**
* **Panoramica dell'architettura**
* **Processo di registrazione**

## Prerequisiti {#prerequisites}

Prima di iniziare a usare i server di creazione e pubblicazione, è necessario disporre di conoscenze precedenti su:

* **Topologia AEM**
* **Creazione e gestione di un progetto AEM Screens**
* **Processo di registrazione del dispositivo**

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.4 Screens Feature Pack 2. Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l'accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Introduzione {#introduction}

L'architettura di AEM Screens assomiglia a una tradizionale architettura di AEM Sites. Il contenuto viene creato su un’istanza di creazione AEM e quindi replicato in avanti in più istanze di pubblicazione. I dispositivi AEM Screens ora possono connettersi a una farm di pubblicazione AEM tramite il sistema di bilanciamento del carico. Potete aggiungere più istanze di pubblicazione AEM per continuare a ridimensionare la farm di pubblicazione.

*Ad esempio*, un autore di contenuti di AEM Screens invia un comando al sistema di authoring per un particolare dispositivo configurato per interagire con una farm di pubblicazione o con un autore di contenuti di AEM Screens che ottiene informazioni sui dispositivi configurati per interagire con le farm di pubblicazione.

Nel diagramma seguente sono illustrati gli ambienti di creazione e pubblicazione.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Progettazione architettonica {#architectural-design}

Sono disponibili cinque componenti architettonici che agevolano questa soluzione:

* ***Replica del contenuto*** dall’autore alla pubblicazione per la visualizzazione per dispositivi

* ***Inverti*** replica del contenuto binario dalla pubblicazione (ricevuto dai dispositivi) per l’authoring
* ***Invio*** di comandi dall’autore per la pubblicazione tramite specifiche API REST
* ***Messaggi*** tra le istanze di pubblicazione per sincronizzare gli aggiornamenti e i comandi delle informazioni sui dispositivi
* ***Sondaggio*** effettuato dall’autore delle istanze di pubblicazione per ottenere informazioni sui dispositivi tramite specifiche API REST

### Replica (avanti) di contenuti e configurazioni {#replication-forward-of-content-and-configurations}

Gli agenti di replica standard vengono utilizzati per replicare il contenuto dei canali di schermate, le configurazioni di posizione e le configurazioni dei dispositivi. Questo consente agli autori di aggiornare il contenuto di un canale ed eventualmente di passare attraverso un flusso di lavoro di approvazione prima di pubblicare gli aggiornamenti del canale. È necessario creare un agente di replica per ogni istanza di pubblicazione nella farm di pubblicazione.

Il diagramma seguente illustra il processo di replica:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>È necessario creare un agente di replica per ogni istanza di pubblicazione nella farm di pubblicazione.

### Agenti e comandi di replica dello schermo {#screens-replication-agents-and-commands}

Gli agenti di replica specifici per le schermate personalizzate vengono creati per inviare i comandi dall'istanza Author al dispositivo AEM Screens. Le istanze AEM Publish fungono da intermediario per inoltrare questi comandi al dispositivo.

Questo consente agli autori di continuare a gestire il dispositivo, ad esempio inviare aggiornamenti del dispositivo e acquisire screenshot dall'ambiente di authoring. Gli agenti di replica di AEM Screens dispongono di una configurazione di trasporto personalizzata, come gli agenti di replica standard.

### Messaggi tra istanze di pubblicazione {#messaging-between-publish-instances}

In molti casi, un comando può essere inviato a un dispositivo una sola volta. Tuttavia, in un’architettura di pubblicazione con bilanciamento del carico, non è noto a quale istanza di pubblicazione il dispositivo si sta connettendo.

Pertanto, l’istanza di creazione invia il messaggio a tutte le istanze di pubblicazione. Tuttavia, il dispositivo deve inviare un solo messaggio. Per garantire la corretta messaggistica, è necessario che tra le istanze di pubblicazione venga effettuata una comunicazione. Questo si ottiene utilizzando *Apache ActiveMQ Artemis. *Ogni istanza di pubblicazione viene inserita in una Toplogy con collegamento semplice utilizzando il servizio di individuazione Sling basato su Oak e ActiveMQ è configurato in modo che ogni istanza di pubblicazione possa comunicare e creare una singola coda di messaggi. Il dispositivo Screens esegue il polling della farm di pubblicazione tramite il sistema di bilanciamento del carico e recupera il comando dalla parte superiore della coda.

### Replica inversa {#reverse-replication}

In molti casi, seguendo un comando, è previsto un certo tipo di risposta dal dispositivo Screens da inoltrare all'istanza Author. Per ottenere questo risultato, viene utilizzata la replica ****** inversa di AEM.

* Create un agente di replica inversa per ogni istanza di pubblicazione, in modo analogo agli agenti di replica standard e agli agenti di replica delle schermate.
* Una configurazione di avvio del flusso di lavoro ascolta i nodi modificati nell'istanza di pubblicazione e, a sua volta, attiva un flusso di lavoro per inserire la risposta del dispositivo nella casella in uscita dell'istanza Pubblica.
* Una replica inversa in questo contesto viene utilizzata solo per i dati binari (come file di registro e screenshot) forniti dai dispositivi. I dati non binari vengono recuperati tramite polling.
* La replica inversa sottoposta a polling dall’istanza di creazione di AEM recupera la risposta e la salva nell’istanza di creazione.

### Polling di istanze di pubblicazione {#polling-of-publish-instances}

L’istanza di authoring deve essere in grado di eseguire il polling dei dispositivi per ottenere un heartbeat e conoscere lo stato di integrità di un dispositivo connesso.

I dispositivi eseguono il ping del sistema di bilanciamento del carico e vengono indirizzati a un'istanza di pubblicazione. Lo stato del dispositivo viene quindi esposto dall'istanza di pubblicazione tramite un'API Publish gestita @ **api/screens-dcc/devices/static** per tutti i dispositivi attivi e **api/screens-dcc/devices/&lt;device_id&gt;/status.json** per un singolo dispositivo.

L’istanza di autore esegue il polling di tutte le istanze di pubblicazione e unisce le risposte sullo stato del dispositivo in un unico stato. Il processo pianificato per il sondaggio sull’autore è `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` e può essere configurato in base a un’espressione cron.

## Registrazione {#registration}

La registrazione continua a essere avviata dall’istanza di creazione di AEM. AEM Screens Device (Dispositivo AEM Screens) punta all'istanza di creazione e la registrazione viene completata.

Dopo che un dispositivo è stato registrato nell’ambiente di authoring, la configurazione del dispositivo e le assegnazioni canale/pianificazione vengono replicate nelle istanze di pubblicazione di AEM. La configurazione del dispositivo AEM Screens viene quindi aggiornata per indicare il sistema di bilanciamento del carico davanti alla farm di pubblicazione AEM. Si tratta di una configurazione una tantum, una volta che il dispositivo Screens è collegato con successo all’ambiente di pubblicazione, può continuare a ricevere i comandi provenienti dall’ambiente di authoring e non dovrebbe essere necessario collegare mai il dispositivo Screens direttamente all’ambiente di authoring.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Passaggi successivi {#the-next-steps}

Una volta compreso il design architettonico dell’impostazione di creazione e pubblicazione in AEM Screens, consultate [Configurazione di Author e Publish per AEM Screens](author-and-publish.md) per ulteriori dettagli.