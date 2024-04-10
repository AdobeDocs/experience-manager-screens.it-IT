---
title: Configurazione delle istanze di authoring e pubblicazione in AEM Screens
description: Scopri come configurare un’istanza Author e un’istanza Publish per AEM Screens.
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '1933'
ht-degree: 0%

---


# Configurazione delle istanze di authoring e pubblicazione in AEM Screens {#configuring-author-and-publish-in-aem-screens}

In questa pagina sono evidenziati i seguenti argomenti:

* **Configurazione delle istanze di authoring e pubblicazione**
* **Impostazione della topologia di pubblicazione**
* **Gestione della pubblicazione: distribuzione degli aggiornamenti dei contenuti dall’ambiente di authoring a quello di pubblicazione sul dispositivo**

## Prerequisiti {#prerequisites}

Prima di iniziare a utilizzare i server di authoring e pubblicazione, è necessario conoscere in precedenza:

* **Topologia AEM**
* **Creazione e gestione di un progetto AEM Screens**
* **Processo di registrazione del dispositivo**

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.4 Screens Feature Pack 2. Per accedere a questo Feature Pack, contatta il supporto Adobe e richiedi l’accesso. Dopo aver ricevuto l&#39;autorizzazione, puoi scaricarla da Condivisione pacchetti.

>[!IMPORTANT]
>
>Se desideri utilizzare più di un’istanza Publish con Dispatcher, devi aggiornare Dispatcher. Consulta [Abilitazione di sessioni permanenti](dispatcher-configurations-aem-screens.md#enable-sticky-session) per ulteriori dettagli.

## Configurazione delle istanze di authoring e pubblicazione {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Per ulteriori informazioni sulla panoramica dell’architettura Author e Publish e su come il contenuto viene creato su un’istanza AEM Author e poi replicato in avanti su più istanze Publish, consulta [Panoramica dell’architettura di authoring e pubblicazione](author-publish-architecture-overview.md).

La sezione seguente spiega come impostare gli agenti di replica sulla topologia Author e Publish.

Puoi impostare un semplice esempio, in cui ospiti un’istanza Author e due istanze Publish:

* Autore > localhost:4502
* Pubblicazione 1 (pub1) > localhost:4503
* Pubblicazione 2 (pub2) > localhost:4504

## Impostazione degli agenti di replica sull’autore {#setting-replication-agents}

Per creare gli agenti di replica, è necessario imparare a creare un agente di replica standard.

Per Screens sono necessari tre agenti di replica:

1. **Agente di replica predefinito ***(specificato come*** Agente di replica standard**)
1. **Agente di replica Screens**
1. **Agente replica inversa**

### Passaggio 1: creazione di un agente di replica predefinito {#step-creating-a-default-replication-agent}

Per creare un agente di replica predefinito, effettua le seguenti operazioni:

1. Passa all’istanza AEM > icona a forma di martello > **Operazioni** > **Configurazione**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Seleziona la **Replica** dalla struttura di navigazione a sinistra.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Seleziona la **Agenti per creazione** dal **Replica** cartella e seleziona **Nuovo** per creare un nuovo agente di replica standard.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Inserisci il **Titolo** e **Nome** in modo da poter creare l’agente di replica, quindi selezionare **Crea**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Fai clic con il pulsante destro del mouse sull’agente di replica e seleziona **Apri** per modificare le impostazioni.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Seleziona **Modifica**.

1. In **Impostazioni agente** immetti i dettagli.

   >[!NOTE]
   >
   >L’utente deve controllare **Abilitato** per abilitare l’agente di replica. Seleziona questa opzione per Predefinito, Schermi e Agenti di replica inversa.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Accedi a **Trasporto** e immetti il **URI**, **Utente**, e **Password**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >È inoltre possibile copiare e rinominare un agente di replica predefinito esistente.


#### Creazione di agenti di replica standard  {#creating-standard-replication-agents}

1. Crea un agente di replica standard per pub1 (l’agente predefinito deve già essere configurato). Ad esempio *`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`*
1. Crea un agente di replica standard per pub2. È possibile copiare come agente di replica per pub1 e aggiornare il trasporto da utilizzare per pub2 modificando la porta nella configurazione di trasporto. Esempio: *`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`*.

#### Creazione di agenti di replica Screens {#creating-screens-replication-agents}

1. Creazione di un agente di replica AEM Screens per pub1. Come funzione integrata, esiste un agente di replica Screens che punta alla porta 4503. Abilitala.
1. Creazione di un agente di replica AEM Screens per pub2. Copia l’agente di replica di Screens per pub1 e modifica la porta in modo che punti a 4504 per pub2.

   >[!NOTE]
   >Per informazioni su come configurare gli agenti di replica Screens, consulta [Configurazione dell’agente di replica di Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configure-screens-replication).

#### Creazione di Screens per agenti di replica inversa {#creating-screens-reverse-replication-agents}

1. Crea un agente di replica inversa per pub1.
1. Crea un agente di replica inversa per pub2. È possibile copiare l&#39;agente di replica inversa per pub1 e aggiornare il trasporto da utilizzare per pub2 modificando la porta nella configurazione di trasporto.

## Impostazione della topologia di pubblicazione {#setting-up-publish-topology}

### Passaggio 1: configurare l’individuazione basata su Oak di Apache Sling {#step-configure-apache-sling-oak-based-discovery}

Configurare Apache Sling Oak-Based Discovery per tutte le istanze Publish nella topologia

Per ogni istanza Publish:

1. Accedi a `https://<host>:<port>/system/console/configMgr`
1. Seleziona **Servizio di individuazione basato su Oak Apache Sling** Configurazione.
1. Aggiorna URL connettore topologia: aggiungi URL di tutte le istanze Publish che effettuano la raccolta e che sono:
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **Connettore topologia `Whitelist` Elenco**: adattati a IP o subnet che coprono tutte le istanze Publish. Assicurati di `whitelist` il nome IP/host di tutte le istanze Publish senza il numero di porta.

1. Abilita **Arresto automatico cicli locali**

La configurazione deve essere identica per ogni istanza Publish e il loop locale con arresto automatico impedisce un loop infinito.

#### Passaggio 2: verificare la topologia di pubblicazione {#step-verify-publish-topology}

Per una qualsiasi delle istanze Publish, passa a `https://:/system/console/topology`. Dovresti visualizzare ogni istanza Publish rappresentata nella topologia in **Connettori di topologia in uscita**.

#### Passaggio 3: configurare il cluster ActiveMQ Artemis {#step-setup-activemq-artemis-cluster}

Questo passaggio consente di creare una password crittografata per il cluster ActiveMQ Artemis.
L&#39;utente cluster e la password di tutte le istanze Publish nella topologia devono essere identici. La password della configurazione di ActiveMQ Artemis deve essere crittografata. Poiché ogni istanza dispone di una propria chiave di crittografia, è necessario utilizzare il Supporto crittografia per creare una stringa di password crittografata. Quindi, la password crittografata può essere utilizzata nella configurazione OSGi per ActiveMQ.

Per ogni istanza di pubblicazione:

1. Nella console OSGi, passa a **PRINCIPALE** > **Supporto crittografia** (`https://<host>:<port>/system/console/crypto`).
1. Digita la password di testo normale desiderata (stessa per tutte le istanze) in **Testo normale**
1. Seleziona **Protect**.
1. Copia il valore **Testo protetto** al blocco note o all’editor di testo. Questo valore può essere utilizzato nella configurazione OSGi per ActiveMQ.

Poiché ogni istanza Publish, per impostazione predefinita, dispone di chiavi di crittografia univoche, esegui questo passaggio su ogni istanza pub e salva la chiave univoca per la configurazione successiva.

>[!NOTE]
>
>La password deve iniziare e terminare con parentesi graffe. Ad esempio:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Passaggio 4: attivare il cluster ActiveMQ Artemis {#step-activate-activemq-artemis-cluster}

Su ogni istanza Publish:

1. Passa a Gestione configurazione OSGi `https://<host>:<port>/system/console/configMgr`
1. Seleziona **Provider Apache ActiveMQ Artemis JMS** Configurazione
1. Aggiorna quanto segue:

   * ***Password cluster***: utilizza un valore crittografato del passaggio precedente per la rispettiva istanza
   * ***Argomenti***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verifica cluster ActiveMQ Artemis {#verify-activemq-artemis-cluster}

Segui i passaggi seguenti per ogni istanza Publish:

1. Passa a Console OSGi > Principale > ActiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. Verificare e controllare per visualizzare le porte di altre istanze in Informazioni cluster > Topologia > nodi=2, membri=2.
1. Invia un messaggio di prova (nella parte superiore della schermata in Informazioni broker)
1. Immetti le seguenti modifiche nei campi:

   1. **Destinazione**: /com.adobe.cq.screens/devTestTopic
   1. **Testo**: Hello World
   1. Visualizza `error.log` di ogni istanza in modo da poter vedere che il messaggio è stato inviato e ricevuto nel cluster.

>[!NOTE]
>
>L’accesso alla console OSGi potrebbe richiedere alcuni secondi dopo il salvataggio della configurazione di cui al passaggio precedente. Puoi anche controllare il registro degli errori per ulteriori dettagli.

Ad esempio, l&#39;immagine seguente viene visualizzata in caso di configurazione corretta del server ActiveMQ Artemis.

Se non vedi la seguente configurazione da */system/console/mq*, quindi passa a */system/console/mq* e seleziona **Riavvia** per riavviare il broker.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Rimuovi requisito intestazione referente {#remove-referrer-header-requirement}

Segui i passaggi per ogni istanza Publish:

1. Accedi a **Console OSGi** > **Gestione configurazione**
1. Seleziona **Filtro referrer Apache Sling**
1. Aggiorna configurazione e **seleziona Consenti vuoto**

### Configurazione dell’istanza di authoring e pubblicazione {#configuring-author-and-publish-instance}

Dopo aver impostato la topologia di pubblicazione, configura le istanze Author e Publish per visualizzare i risultati pratici dell’implementazione:

>[!NOTE]
>
>**Prerequisiti**
>
>Per iniziare a utilizzare questo esempio, crea un progetto AEM Screens, quindi crea una posizione, una visualizzazione e un canale nel progetto. Aggiungi contenuto al tuo canale e assegna il canale a una visualizzazione.

#### Passaggio 1: avvio di un lettore AEM Screens (dispositivo)

1. Avvia una finestra del browser separata.
1. Passa a Screens player utilizzando *browser web*, ovvero`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` o avvia l&#39;app AEM Screens. Quando apri il dispositivo, noterai che lo stato del dispositivo non è registrato.

>[!NOTE]
>
>Puoi aprire un lettore AEM Screens utilizzando l’app AEM Screens che hai scaricato o il browser web.

#### Passaggio 2: registrazione di un dispositivo durante l’authoring {#step-registering-a-device-on-author}

1. Vai a `https://localhost:4502/screens.html/content/screens/we-retail` oppure seleziona il progetto e passa a Dispositivi > Gestione dispositivi.
1. Seleziona **Registra dispositivo**.
1. Seleziona **Registrazione dispositivo**.
1. Selezionare il dispositivo da registrare, quindi selezionare **Registra dispositivo**.
1. Verifica il codice di registrazione, quindi seleziona **Convalida**.
1. Inserisci un titolo per il dispositivo, quindi seleziona **Registrati**.

#### Passaggio 3: assegnazione del dispositivo alla visualizzazione {#step-assigning-the-device-to-display}

1. Seleziona **Assegna visualizzazione** dalla finestra di dialogo del passaggio precedente.
1. Seleziona il percorso di visualizzazione del canale dalla **Posizioni** cartella.
1. Seleziona **Assegna**.
1. Seleziona **Fine** per completare il processo, e ora il dispositivo viene assegnato.

Controlla il lettore e nota il contenuto aggiunto nel canale.

#### Passaggio 4: pubblicazione della configurazione del dispositivo nelle istanze di pubblicazione {#step-publishing-device-configuration-to-publish-instances}

**Verifica del dispositivo**

Per replicare l’utente del dispositivo, segui la procedura riportata di seguito:

1. Passa alla pagina dell’amministratore utenti. Esempio: `https://localhost:4502/useradmin`.
1. Cerca **`screens-devices-master`** gruppo.
1. Fare clic con il pulsante destro del mouse sul gruppo e selezionare **Attiva**.

>[!CAUTION]
>
>Non attivare author-publish-screens-service in quanto è un utente di sistema utilizzato dal processo di authoring.

È inoltre possibile attivare il dispositivo dalla console di gestione dei dispositivi. Effettua le seguenti operazioni:

1. Passa al progetto Schermi > **Dispositivi**.
1. Seleziona **Gestione dispositivi** dalla barra delle azioni.
1. Selezionare il dispositivo e selezionare **Attiva** dalla barra delle azioni, come illustrato nella figura riportata di seguito.

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>In alternativa, dopo aver attivato il dispositivo, puoi anche modificare o aggiornare l’URL del server. Seleziona **Modifica URL server** dalla barra delle azioni, come illustrato nella figura seguente, le modifiche vengono propagate al lettore AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Pubblicazione elenco di controllo {#publishing-check-list}

I punti seguenti riepilogano l&#39;elenco di controllo per la pubblicazione:

* *Utente dispositivo Screens* - Questo viene memorizzato come utente AEM e deve essere attivato da **Strumenti** > **Sicurezza** > **Utenti**. All’utente viene aggiunto il prefisso &quot;screens&quot; con una lunga stringa serializzata.

* *Progetto* - Il progetto AEM Screens.
* *Posizione* : posizione a cui è connesso il dispositivo.
* *Canali* - uno o più canali visualizzati nel percorso
* *Pianificazione* - se utilizzi una pianificazione, assicurati che sia pubblicata
* *Cartella posizioni, pianificazioni e canali* - se le risorse corrispondenti si trovano all’interno di una cartella.

Per verificare il comportamento di authoring e pubblicazione, segui i passaggi seguenti:

1. Aggiorna alcuni contenuti del canale nell’istanza di authoring.
1. Esegui **Gestisci pubblicazione** per pubblicare le nuove modifiche su tutte le istanze Publish.
1. Premi **Attiva** per attivare il dispositivo da **Gestione dispositivi**.
1. **Modifica URL** dall’URL dell’istanza di authoring a uno dell’URL delle istanze di pubblicazione.
1. Verifica che il contenuto del canale aggiornato venga visualizzato sul lettore AEM Screens.
1. Ripeti questi passaggi utilizzando un’istanza Publish diversa.


#### Passaggio 5: indirizzamento del dispositivo all’istanza Publish nel pannello di amministrazione {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visualizza l’interfaccia utente di amministrazione dal lettore Screens, premi a lungo l’angolo in alto a sinistra in modo da poter aprire il menu di amministrazione, sul lettore AEM Screens touch o utilizzando un mouse.
1. Seleziona la **Configurazione** dal pannello laterale.
1. Cambia l’istanza di authoring in Istanza di pubblicazione in **Server**.

Visualizza le modifiche nel lettore AEM Screens.

In alternativa, puoi anche aggiornare/modificare l’URL del server dalla console di gestione del dispositivo seguendo la procedura riportata di seguito:

1. Passa al progetto AEM Screens e seleziona la **Dispositivi** cartella.
1. Seleziona **Gestione dispositivi** dalla barra delle azioni.
1. Selezionare il dispositivo e selezionare **Modifica URL server** dalla barra delle azioni, come illustrato nella figura seguente, e le modifiche vengono propagate al lettore AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

Il **Gestisci pubblicazione** Questa funzione consente di fornire aggiornamenti di contenuto da Authoring a Pubblicazione sul dispositivo. Puoi pubblicare/annullare la pubblicazione dei contenuti per l’intero progetto AEM Screens o solo per uno dei tuoi canali, posizione, dispositivo, applicazione o pianificazione. Per ulteriori informazioni su questa funzione, consulta [Aggiornamento dei contenuti on-demand](on-demand-content.md).

## Suggerimenti per la risoluzione dei problemi {#troubleshoot-tips}

Leggi la sezione seguente per ottenere risposte alle domande frequenti relative alla configurazione di authoring/pubblicazione.

### Come si aggiunge un reindirizzamento da https a http dopo la registrazione e l’assegnazione iniziali? {#add-redirect}

**Soluzione**
Imposta attivazione `Proxy/Load Balancer Connection in the Jetty configuration` a `true`.

### Come aggiornare i contenuti offline e scaricare i problemi del lettore con le risorse esterne `/content/dam/projects/<project>`? {#update-offline-content}

**Soluzione**
Concedi autorizzazioni di lettura per utenti di servizi bulk-offline-update-screens e `screens-devices-master` gruppo per tutti `/content/dam` o le risorse specifiche che desideri utilizzare, se desideri essere più restrittivo.

### Come si risolvono gli errori dell’agente di replica di Screens? {#replication-agent}

**Soluzione**
Assicurati di non aver selezionato l’opzione Usa per replica inversa nella configurazione dell’agente. L’agente di replica di Screens non può essere utilizzato come agente di replica inversa e l’ambito di questa funzione è quello di inoltrare i comandi del dispositivo dall’istanza di authoring a quella di pubblicazione.