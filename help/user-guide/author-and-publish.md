---
title: Configurazione di Author e Publish in AEM Screens
seo-title: Configurazione di Author e Publish in AEM Screens
description: L’architettura di AEM Screens assomiglia a un’architettura AEM Sites tradizionale. Il contenuto viene creato su un’istanza di authoring AEM e quindi replicato in avanti in più istanze di pubblicazione. Segui questa pagina per scoprire come configurare l’authoring e la pubblicazione per AEM Screens.
seo-description: L’architettura di AEM Screens assomiglia a un’architettura AEM Sites tradizionale. Il contenuto viene creato su un’istanza di authoring AEM e quindi replicato in avanti in più istanze di pubblicazione. Segui questa pagina per scoprire come configurare l’authoring e la pubblicazione per AEM Screens.
feature: Amministrazione di schermi
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 2%

---


# Configurazione di Author e Publish in AEM Screens {#configuring-author-and-publish-in-aem-screens}

Questa pagina evidenzia i seguenti argomenti:

* **Configurazione delle istanze di authoring e pubblicazione**
* **Impostazione della topologia di pubblicazione**
* **Gestione della pubblicazione: Distribuzione di aggiornamenti di contenuto da Author a Publish to Device**

## Prerequisiti {#prerequisites}

Prima di iniziare a utilizzare i server di authoring e pubblicazione, è necessario disporre di conoscenze precedenti su:

* **Topologia AEM**
* **Creazione e gestione di un progetto AEM Screens**
* **Processo di registrazione dei dispositivi**

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se hai installato AEM Feature Pack 2 di 6.4 Screens. Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

>[!IMPORTANT]
>
>Se desideri utilizzare più istanze di pubblicazione con il dispatcher, devi aggiornare il file dispatcher.any nel dispatcher. Per ulteriori informazioni, consulta [Abilitazione di sessioni permanenti](dispatcher-configurations-aem-screens.md#enable-sticky-session) .

## Configurazione delle istanze Author e Publish {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Per ulteriori informazioni sull’authoring e la pubblicazione della panoramica dell’architettura e su come viene creato il contenuto in un’istanza di authoring AEM e quindi replicato in avanti in più istanze di pubblicazione, consulta [Panoramica dell’architettura di authoring e pubblicazione](author-publish-architecture-overview.md).

La sezione seguente spiega come impostare gli agenti di replica sulla topologia di authoring e pubblicazione.

Potete impostare un semplice esempio, in cui ospitate un autore e due istanze di pubblicazione:

* Autore —> localhost:4502
* Publish 1 (pub1) —> localhost:4503
* Publish 2 (pub2) —> localhost:4504

## Impostazione degli agenti di replica sull&#39;autore {#setting-replication-agents}

Per creare agenti di replica, devi imparare a creare un agente di replica standard.

Sono necessari 3 agenti di replica per Screens:

1. **Agente di replica predefinito  ***(specificato*** come agente** di replica standard)
1. **Agente di replica Screens**
1. **Agente replica inversa**

### Passaggio 1: Creazione di un agente di replica predefinito {#step-creating-a-default-replication-agent}

Per creare un agente di replica predefinito, effettua le seguenti operazioni:

1. Passa all&#39;istanza AEM —> icona a forma di martello —> **Operazioni** —> **Configurazione**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Seleziona **Replica** dalla struttura di navigazione a sinistra.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Seleziona gli **Agenti sull&#39;autore** dalla cartella **Replica** e fai clic su **Nuovo** per creare un nuovo agente di replica standard.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Immetti i valori **Titolo** e **Nome** per creare l&#39;agente di replica e fai clic su **Crea**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Fai clic con il pulsante destro del mouse sull&#39;agente di replica e fai clic su **Apri** per modificare le impostazioni.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Fare clic su **Modifica** per aprire la finestra di dialogo **Impostazioni agente** per immettere i dettagli.

   >[!NOTE]
   >
   >L&#39;utente deve controllare **Enabled** per abilitare l&#39;agente di replica. È necessario selezionare questa opzione su Default, Screens e Reverse Replication Agent.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Passa alla scheda **Trasporto** e immetti l’ **URI**, **Utente** e **Password**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >È inoltre possibile copiare e rinominare un agente di replica predefinito esistente.


#### Creazione di agenti di replica standard {#creating-standard-replication-agents}

1. Crea un agente di replica standard per pub1 (è già necessario configurare l&#39;agente predefinito preconfigurato) (ad esempio, *https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. Crea un agente di replica standard per pub2. È possibile copiare l&#39;agente rep per pub1 e aggiornare il trasporto da utilizzare per pub2 modificando la porta nella configurazione di trasporto. (ad esempio, *https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### Creazione di agenti di replica Screens {#creating-screens-replication-agents}

1. Crea un agente di replica AEM Screens per pub1. Preconfigurato, un agente di replica Screens che punta alla porta 4503. È necessario attivarlo.
1. Crea un agente di replica AEM Screens per pub2. Copia l&#39;agente di replica Screens per pub1 e cambia la porta in punto a 4504 per pub2.

#### Creazione di agenti di replica inversa Screens {#creating-screens-reverse-replication-agents}

1. Crea un agente di replica inversa standard per pub1.
1. Crea un agente di replica inversa standard per pub2. È possibile copiare l&#39;agente di rep inversa per pub1 e aggiornare il trasporto da utilizzare per pub2 modificando la porta nella configurazione di trasporto.

## Impostazione della topologia di pubblicazione {#setting-up-publish-topology}

### Passaggio 1: Configurare la scoperta basata su Oak Apache Sling {#step-configure-apache-sling-oak-based-discovery}

Configurare Apache Sling Oak-Based Discovery per tutte le istanze Publish nella topologia

Per ogni istanza di pubblicazione:

1. Accedi a `https://<host>:<port>/system/console/configMgr`
1. Seleziona Configurazione **Apache Sling Oak-Based Discovery Service** .
1. Aggiorna gli URL del connettore topologia: aggiungi gli URL di tutte le istanze di pubblicazione partizionate che sono:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **Elenco** whitelist del connettore topologia: adattarsi agli IP o alle subnet che coprono le istanze di pubblicazione parziali
1. Abilita **Arresto automatico loop locali**

La configurazione deve essere identica per ogni istanza di pubblicazione e il ciclo locale di arresto automatico impedisce un ciclo infinito.

#### Passaggio 2: Verificare la topologia di pubblicazione {#step-verify-publish-topology}

Per una qualsiasi delle istanze di pubblicazione, passa a `https://:/system/console/topology`. Dovresti vedere ogni istanza di pubblicazione rappresentata nella topologia in **Connettori topologia in uscita**.

#### Passaggio 3: Imposta cluster di array ActiveMQ {#step-setup-activemq-artemis-cluster}

Questo passaggio ti consente di creare una password crittografata per il cluster ActiveMQ Artemis.
L&#39;utente del cluster e la password di tutte le istanze di pubblicazione nella topologia devono essere identici. La password della configurazione di ActiveMQ Artemis deve essere crittografata. Poiché ogni istanza ha la propria chiave di crittografia, è necessario utilizzare Crypto Support per creare una stringa di password crittografata. Quindi la password crittografata verrà utilizzata nella configurazione OSGi per ActiveMQ.

In ogni istanza di pubblicazione:

1. Nella console OSGi passa a **MAIN** —> **Supporto di Crypto** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`).
1. Digita la password di testo normale desiderata (stessa per tutte le istanze) in **Testo normale**
1. Fare clic su **Protect**.
1. Copia il valore **Testo protetto** nel blocco note o nell&#39;editor di testo. Questo valore verrà utilizzato nella configurazione OSGi per ActiveMQ.

Poiché ogni istanza di pubblicazione per impostazione predefinita dispone di chiavi di crittografia univoche, devi eseguire questo passaggio su ogni istanza di pub e salvare la chiave univoca per la configurazione successiva.

>[!NOTE]
>
>La password deve iniziare e terminare con parentesi graffe. Esempio:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Passaggio 4: Attiva cluster di array ActiveMQ {#step-activate-activemq-artemis-cluster}

Su ogni istanza di pubblicazione:

1. Passa al gestore di configurazione OSGi `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. Seleziona **Configurazione di Apache ActiveMQ Artemis JMS Provider**
1. Aggiorna quanto segue:

   * ***Password*** cluster: utilizza il valore crittografato del passaggio precedente per ogni singola istanza
   * ***Argomenti***:  `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verifica cluster ActiveMQ Artemis {#verify-activemq-artemis-cluster}

Segui i passaggi seguenti su ogni istanza di Publish:

1. Passa alla console OSGi -> Principale > Artemide ActiveMQ `https://localhost:4505/system/console/mq`.
1. Verifica e controlla per visualizzare le porte di altre istanze in Informazioni cluster > Topologia > nodi=2, membri=2.
1. Invia un messaggio di test (nella parte superiore dello schermo in Informazioni broker)
1. Immetti le seguenti modifiche nei campi:

   1. **Destinazione**: /com.adobe.cq.screens/devTestTopic
   1. **Testo**: Hello World
   1. Visualizza il file error.log di ogni istanza per vedere che il messaggio è stato inviato e ricevuto nel cluster

>[!NOTE]
>
>Per passare alla console OSGi, potrebbero essere necessari alcuni secondi dopo il salvataggio della configurazione nel passaggio precedente. Puoi anche controllare error.log per ulteriori dettagli.

Ad esempio, l&#39;immagine seguente viene visualizzata in caso di configurazione corretta di ActiveMQ Artemis Server.

Se non vedi la seguente configurazione da */system/console/mq*, vai a */system/console/mq* e fai clic su **Restart** per riavviare il broker.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Rimuovi il requisito dell&#39;intestazione del referente {#remove-referrer-header-requirement}

Segui i passaggi per ogni istanza di Publish:

1. Passa alla **console OSGi** > **Configuration Manager**
1. Seleziona **Filtro di riferimento Sling Apache**
1. Aggiorna la configurazione e **controlla Allow Empty**

### Configurazione dell&#39;istanza di authoring e pubblicazione {#configuring-author-and-publish-instance}

Una volta impostata la topologia di pubblicazione, è necessario configurare le istanze di authoring e pubblicazione per visualizzare i risultati pratici dell’implementazione:

>[!NOTE]
>
>**Prerequisiti**
>
>Per iniziare a utilizzare questo esempio, crea un nuovo progetto AEM Screens seguito dalla creazione di una posizione, una visualizzazione e un canale nel progetto. Aggiungi il contenuto al tuo canale e assegna il canale a una visualizzazione.

#### Passaggio 1: Avvio di un lettore AEM Screens (dispositivo) {#step-starting-an-aem-screens-player-device}

1. Avvia una finestra separata del browser.
1. Passa a Screens Player utilizzando il *browser Web*, ovvero`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` o avvia l&#39;app AEM Screens. Una volta aperto il dispositivo, vedrai che lo stato del dispositivo è non registrato.

>[!NOTE]
>
>Puoi aprire un lettore AEM Screens utilizzando l’app AEM Screens che hai scaricato o il browser Web.

#### Passaggio 2: Registrazione di un dispositivo sull&#39;autore {#step-registering-a-device-on-author}

1. Vai a `https://localhost:4502/screens.html/content/screens/we-retail` o seleziona il progetto e vai a Dispositivi > Gestione dispositivi.
1. Selezionare **Registra dispositivo**.
1. Fai clic su **Registrazione dispositivo** per visualizzare il dispositivo.
1. Seleziona il dispositivo da registrare e fai clic su **Registra dispositivo**.
1. Verifica il codice di registrazione e fai clic su **Convalida**.
1. Inserisci un titolo per il dispositivo e fai clic su **Registra**.

#### Passaggio 3: Assegnazione del dispositivo da visualizzare {#step-assigning-the-device-to-display}

1. Fare clic su **Assegna visualizzazione** nella finestra di dialogo del passaggio precedente.
1. Seleziona il percorso di visualizzazione del canale dalla cartella **Posizioni** .
1. Fare clic su **Assegna**.
1. Fare clic su **Fine** per completare il processo e ora il dispositivo viene assegnato.

Controlla il tuo lettore e vedrai il contenuto aggiunto nel tuo canale.

#### Passaggio 4: Pubblicazione della configurazione del dispositivo per pubblicare le istanze {#step-publishing-device-configuration-to-publish-instances}

**Verifica del dispositivo**

Prima di eseguire i passaggi seguenti, assicurati di verificare l&#39;ID dispositivo. Per verificare, cerca l&#39;ID dispositivo in CRXDE Lite, con il percorso */home/users/screens/we-retail/devices*.

Segui i passaggi riportati di seguito per replicare l’utente del dispositivo:

1. Passa alla pagina di amministrazione dell’utente (ad esempio: `https://localhost:4502/useradmin`
1. Cerca il gruppo **screens-devices-master**
1. Fai clic con il pulsante destro del mouse sul gruppo e fai clic su **Attiva**

>[!CAUTION]
>
>Non attivare author-publish-screens-service in quanto è un utente di sistema, utilizzato dal processo di authoring.

Puoi anche attivare il dispositivo dalla console di gestione dei dispositivi. Effettua le seguenti operazioni:

1. Passa al progetto Screens —> **Dispositivi**.
1. Fai clic su **Gestione dispositivi** nella barra delle azioni.
1. Seleziona il dispositivo e fai clic su **Attiva** nella barra delle azioni, come mostrato nella figura seguente.

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>In alternativa, una volta attivato il dispositivo è anche possibile modificare o aggiornare l&#39;URL del server facendo clic su **Modifica URL server** nella barra delle azioni, come mostrato nella figura seguente, e le modifiche verranno propagate al lettore AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Pubblicazione dell&#39;elenco di controllo {#publishing-check-list}

I punti seguenti riepilogano l’elenco Controllo pubblicazione:

* *Utente dispositivo Screens* : viene memorizzato come utente AEM e può essere attivato da  **Strumenti**  >  **Protezione**  >  **Utenti**. L’utente avrà il prefisso &quot;screens&quot; con una lunga stringa serializzata.

* *Progetto*  - Il progetto AEM Screens.
* *Posizione* : posizione a cui è connesso il dispositivo.
* *Canali* : uno o più canali visualizzati nella posizione
* *Pianificazione* : se utilizzi una pianificazione, assicurati che venga pubblicata
* *Posizione, pianificazioni e Cartella canali*  - se le risorse corrispondenti si trovano all’interno di una cartella.

Per verificare il comportamento di authoring/pubblicazione, effettua le seguenti operazioni:

1. Aggiorna alcuni contenuti del canale sull&#39;istanza dell&#39;autore
1. Esegui **Gestisci pubblicazione** per pubblicare nuove modifiche in tutte le istanze di pubblicazione
1. Premere **Attiva** per attivare il dispositivo da **Gestione dispositivi**
1. **Modifica** URL dall’URL dell’istanza di authoring a uno degli URL delle istanze di pubblicazione
1. Verifica che il contenuto del canale aggiornato sia visualizzato sul lettore AEM Screens
1. Ripeti questi passaggi utilizzando un’altra istanza di pubblicazione


#### Passaggio 5: Selezione del dispositivo per la pubblicazione dell’istanza nel pannello di amministrazione {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visualizza l&#39;interfaccia utente amministratore da Screens Player, premi a lungo nell&#39;angolo in alto a sinistra per aprire il menu Admin, sul tuo lettore AEM Screens abilitato al tocco o utilizzando un mouse.
1. Fai clic sull&#39;opzione **Configurazione** nel pannello laterale.
1. Cambia l&#39;istanza dell&#39;autore per pubblicare l&#39;istanza in **Server**.

Visualizza le modifiche nel lettore AEM Screens.

In alternativa, puoi anche aggiornare/modificare l’URL del server dalla console di gestione dispositivi seguendo i seguenti passaggi:

1. Passa al progetto AEM Screens e seleziona la cartella **Dispositivi** .
1. Fai clic su **Gestione dispositivi** nella barra delle azioni.
1. Seleziona il dispositivo e fai clic su **Modifica URL server** nella barra delle azioni, come mostrato nella figura seguente, e le modifiche verranno propagate al lettore AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

La funzione **Gestisci pubblicazione** consente di distribuire aggiornamenti dei contenuti dall&#39;autore al dispositivo di pubblicazione. Puoi pubblicare/annullare la pubblicazione dei contenuti per l’intero progetto AEM Screens o solo per uno dei canali, la posizione, il dispositivo, l’applicazione o una pianificazione. Per ulteriori informazioni su questa funzione, consulta [Aggiornamento dei contenuti on-demand](on-demand-content.md).


