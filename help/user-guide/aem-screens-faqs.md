---
title: Domande frequenti su AEM Screens
description: Risposte alle domande frequenti relative a un progetto AEM Screens.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# Domande frequenti su AEM Screens {#aem-screens-faqs}

Questo argomento fornisce le risposte alle domande frequenti più frequenti relative a un progetto AEM Screens.

## Problema schermo vuoto {#blank-screen}

>[!NOTE]
>I controlli obbligatori elencati che devono essere eseguiti dal supporto principale o dal supporto lato cliente prima di segnalare un problema.

### 1. Quali dovrebbero essere i passaggi per la risoluzione dei problemi di primo soccorso per qualsiasi cliente che si trova di fronte a una schermata nera o contenuti non riprodotti? {#troubleshooting-blank-screen}

* Verifica se l’anteprima del canale funziona.
* Verifica se l’anteprima del display funziona
* Prova a registrare il lettore come estensione del browser sul sistema per lo stesso schermo e verifica se funziona.
* Con il lettore in esecuzione sul sistema, vai a `http://localhost:24502`. Verifica se tutto il contenuto è scaricato correttamente.
* Controlla le risorse in modo da poter creare le rappresentazioni appropriate e riprodurre quella corretta.
* Controlla la presenza di eventuali contenuti pianificati e se gli orari sono corretti. Verificare che l&#39;ora impostata nel lettore sia corretta.
* Inspect registra la console del lettore e verifica la presenza di errori. Fai clic con il pulsante destro del mouse e controlla per visualizzare i registri della console. Se si utilizza Windows Player, premere `CTRL + ALT +I` per visualizzare dev console e i relativi registri.

### 2. Come risolvere il problema della schermata grigia in AEM Screens creando un canale o una pianificazione predefiniti?

Per evitare le schermate vuote o grigie nel campo, crea un canale o una pianificazione globale predefinita, assegnata a ogni visualizzazione con la priorità minima di 1. In caso di problemi con gli aggiornamenti dei contenuti (a causa di rete, lettore, server o replica), poiché i lettori hanno già tali contenuti memorizzati nella cache del disco che dovrebbero essere riprodotti correttamente ed evitare le schermate grigie.

Tutti gli altri contenuti, ad esempio i canali o le pianificazioni, hanno priorità maggiore di 1, quindi gli altri contenuti hanno priorità e i contenuti globali dei canali o delle pianificazioni (con priorità 1) vengono riprodotti solo come opzione di fallback.

## Gestione dei canali {#channel-management}

### 1. Qual è la differenza tra un canale online e uno offline? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***Canale online*** mostra il contenuto aggiornato nell’ambiente in tempo reale, mentre un’ ***Canale offline*** mostra il contenuto della cache.

### 2. Come si crea un canale online? {#how-do-i-make-a-channel-online}

Fai clic sul canale e accedi alle proprietà del canale dalla barra delle azioni. Verifica **Modalità sviluppatore (forza canale online)** in **Canale** per rendere il canale online.

### 3. Qual è l’utilizzo del campo Ruolo canale? {#what-is-the-use-of-the-channel-role-field}

Il Ruolo canale è l’astrazione del canale effettivo eseguito in modo che l’autore possa concentrarsi direttamente sull’esperienza generica. Puoi considerarlo come una sorta di tag che identifica in modo univoco il canale nel suo contesto (visualizzazione o pianificazione).

### 4. Come avviene la risoluzione effettiva del canale? {#how-does-actual-channel-resolution-happen}

Per *riferimenti statici*, la risoluzione segue semplicemente il percorso specificato.

Per *riferimenti dinamici*, la risoluzione si verifica una volta che il canale è assegnato alla visualizzazione (non alla pianificazione). Il percorso di visualizzazione diventa il contesto per il canale e la risoluzione avviene come segue (priorità dalla più alta alla più bassa):

1. La visualizzazione ha un nodo figlio che corrisponde al nome del canale a cui si fa riferimento
1. La visualizzazione ha un nodo di pari livello che corrisponde al nome del canale di riferimento
1. La posizione padre della visualizzazione ha un nodo figlio che corrisponde al nome del canale di riferimento
1. La posizione padre principale della visualizzazione ha un nodo figlio che corrisponde al nome del canale di riferimento

E così via, finché non raggiungi la cartella posizioni e ci fermi in questo momento (quindi non puoi fare riferimento a un canale che si troverebbe nella cartella canali, ad esempio, solo i canali nella sottostruttura posizioni ).

### 5. Come impostare la configurazione offline personalizzata clientlib nel canale AEM Screens?

Quando si utilizza un codice lato client personalizzato generato `clientlib` in un canale AEM Screens, sono necessari i seguenti passaggi per garantire che il `clientlib` i file sono stati caricati correttamente nel canale (`manifest.json`) e contiene il percorso del `clientlib`.

Segui i passaggi seguenti dall’editor canali:

1. Fai clic su un canale, quindi fai clic su **Modifica** dalla barra delle azioni.
1. Fai clic sul componente in cui desideri aggiungere il componente personalizzato `clientlib`.
1. Fai clic sul pulsante Configura (icona a forma di chiave inglese).
1. Accedi a **Configurazione offline** e aggiungere il percorso alla libreria client personalizzata in **Librerie lato client**.

## Registrazione dispositivo {#device-registration}

### 1. Se rilevo endpoint quali richieste di onboarding e registrazione dei dispositivi, posso inserire nello script molti dispositivi e registrarli. Oltre a bloccarlo su una filiale Wi-Fi, è possibile proteggere queste richieste? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Attualmente la registrazione è possibile solo sull’istanza di authoring. Sebbene il servizio di registrazione non sia autenticato, crea solo un dispositivo in sospeso nell’AEM e non registra effettivamente il dispositivo né assegna alcun display.

Per registrare un dispositivo (creando un utente per il dispositivo in AEM), eseguire l&#39;autenticazione in AEM e attualmente seguire manualmente la registrazione guidata per completare la registrazione. In teoria, un utente malintenzionato può creare diversi dispositivi in sospeso, ma non può registrarne nessuno senza un accesso AEM.

### 2. Esiste un modo per trasformare le richieste HTTP GET in HTTP POST con una qualche forma di autenticazione? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La richiesta di registrazione è una richiesta POST.

Si consiglia di ottenere l’ID dispositivo dalla sessione anziché passare come parametro. In questo modo verrebbero eliminati i registri del server, la cache del browser e così via. Non è un problema di sicurezza. Semanticamente. GET viene utilizzato quando non vi è alcuna modifica di stato sul server e POST viene utilizzato quando si è verificata una modifica di stato.

### 3. Esiste un modo per rifiutare una richiesta di registrazione del dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

Impossibile rifiutare le richieste di registrazione. Le richieste di registrazione dovrebbero invece scadere dopo un timeout configurato in `Adobe Experience Manager Web Console`. Per impostazione predefinita, questo valore è impostato su un giorno e viene memorizzato in una cache di memoria.

## Monitoraggio dei dispositivi e rapporti sullo stato {#device-monitoring-and-health-reports}

### 1. Come posso risolvere i problemi se il lettore AEM Screens mostra una schermata vuota?

Cerca le seguenti possibilità per risolvere il problema della schermata vuota:

* AEM non è in grado di inviare contenuti offline in push
* Il canale non ha alcun contenuto
* Nessuna delle risorse è programmata per essere visualizzata al momento

### 2. Cosa posso fare se il lettore AEM Screens non riesce a registrarsi e il suo stato viene visualizzato come Errore?

Abilita il filtro Apache Sling Referrer Allow Empty. Ciò è necessario per il funzionamento ottimale del protocollo di controllo tra AEM Screens Player e il server AEM Screens.

1. Accedi a **Configurazione console Web Adobe Experience Manager**
1. Controlla la **allow.empty** opzione.
1. Fai clic su **Salva**.

### 3. Come risolvere il problema se durante la registrazione di un lettore AEM Screens, il dispositivo mostra l’errore FAILURE e i registri della console mostrano l’errore ENAME_NOT_FOUND?

Questo problema può verificarsi se il lettore non è in grado di trovare il DNS di AEM Screens Server. Prova a utilizzare l’indirizzo IP per la connessione. Per ottenere l&#39;IP del server, utilizzare: *arp &lt;server_dns_name>*.

### 4. AMS consiglia di implementare un watchdog Android™ su tutti i dispositivi? Il plug-in Watchdog (Cordova) è incluso nell’APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un watchdog Android™ multipiattaforma che utilizza API Android™ pure fa già parte dell’apk. Non sono necessari software aggiuntivi. Tuttavia, a seconda del dispositivo utilizzato, è possibile rassegnare l&#39;apk per ottenere i privilegi di sistema per un ciclo di alimentazione completo (`Powermanager` api), se necessario. Se non viene rassegnato utilizzando i tasti del produttore, l&#39;applicazione viene chiusa e riavviata, ma non viene eseguita l&#39;accensione.

Per ulteriori informazioni su come implementare Android™ Player, consulta [**Implementazione di Android™ Player**](implementing-android-player.md).

### 5. Quali strumenti di monitoraggio e avviso remoti (software) di terze parti consiglia Adobe/AMS per il monitoraggio di ciascun dispositivo? {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

A seconda delle esigenze di monitoraggio e degli avvisi, una nuova funzione del servizio AEM Screens Notifications notifica all’utente se un dispositivo non effettua il ping da un po’. Gli strumenti di terze parti dipendono dal sistema operativo in uso, dalle sue funzionalità e dalle esigenze specifiche del cliente.

Per ulteriori informazioni su dove è possibile monitorare l&#39;attività dei dispositivi, vedere [**Servizio di notifica di Scree NS per AEM**](screens-notifications-service.md).

## Lettore AEM Screens

### 1. Come installare il lettore ChromeOS come plug-in del browser Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Il lettore ChromeOS può essere installato come plug-in del browser Chrome in modalità sviluppatore senza richiedere il dispositivo effettivo del lettore Chrome. Per l&#39;installazione, procedere come segue:

1. Clic [qui](https://download.macromedia.com/screens/) per scaricare il lettore Chrome più recente.
1. Decomprimi e salva su disco.
1. Apri il browser Chrome e fai clic su **Estensioni** dal menu o passa direttamente a ***chrome://extensions***.
1. Accendere il **Modalità sviluppatore** dall&#39;angolo superiore destro.
1. Clic **Carica decompresso** dall’angolo in alto a sinistra e carica Chrome Player decompresso.
1. Se disponibile nell’elenco delle estensioni, seleziona **AEM Screens Chrome Player** plugin.
1. Apri una nuova scheda e fai clic su **App** dall&#39;angolo in alto a sinistra, oppure passare direttamente a ***chrome://apps***.
1. Fai clic su **AEM Screens** Plugin. Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premi **Esc** per uscire dalla modalità a tutto schermo.

### 2. Come risolvere i problemi se Screens Player non è in grado di eseguire l’autenticazione tramite l’istanza di pubblicazione con un gestore degli errori personalizzato?

All’avvio di AEM Screens Player, viene inviata una richiesta a ***/content/screens/svc.ping.json***, quando il lettore riceve un errore 404. Il lettore avvia una richiesta di autenticazione per eseguire l’autenticazione nell’istanza di pubblicazione. Se nell’istanza di pubblicazione è presente un gestore degli errori personalizzato, assicurati di restituire il codice di stato 404 per l’utente anonimo il ***/content/screens/svc.ping.json***.

### 3. Come impostare lo schermo del dispositivo rimanere su in un lettore Android™? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Segui i passaggi seguenti per attivare Stay Awake in su qualsiasi lettore Android™:

1. Passa a Impostazioni lettore Android™ > **Informazioni su**.
1. Tocca sette volte il numero di build per abilitare **Opzioni sviluppatore** in **Impostazioni**.
1. Accedi a **Opzioni sviluppatore**.
1. Abilita **Rimani sveglio**.

### 4. Come abilitare la modalità finestra per il lettore Windows?{#enable-player}

Nessuna modalità finestra in Windows Player. È sempre in modalità a schermo intero.

### 5. Come risolvere i problemi se un lettore AEM Screens invia continuamente richieste di accesso?

Segui i passaggi seguenti per risolvere i problemi relativi a un lettore AEM Screens che invia continuamente richieste a `/content/screens/svc.json` e `/libs/granite/core/content/login.validate/j_security_check`:

1. All’avvio di AEM Screens Player, questo richiede di: `/content/screens/svc.json`. Quando il lettore ottiene un codice di stato 404 nella risposta, avvia una richiesta di autenticazione utilizzando `/libs/granite/core/content/login.validate/j_security_check` contro *pubblicare* dell&#39;istanza. Se è presente un gestore degli errori personalizzato in *pubblicare* , assicurati di restituire il codice di stato 404 per l’utente anonimo il `/content/screens/svc.json` o `/content/screens/svc.ping.json`.

1. Verifica se la configurazione del Dispatcher consente tali richieste nel `/filters`.

   Consulta [Configurazione dei filtri di Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters) per ulteriori dettagli.

1. Verifica se le regole di riscrittura del Dispatcher stanno riscrivendo uno qualsiasi dei percorsi dello schermo in un percorso diverso.

1. Controlla se hai `/etc/map` le regole relative alla *autore* o *pubblicare* i percorsi dell’istanza e degli schermi corrispondono a `sling:match` e reindirizzato internamente a un percorso diverso. Risoluzione dell’URL esatto in `/system/console/jcrresolver` aiuta a identificare se *pubblicare* L’istanza sta riscrivendo questi URL in qualsiasi altro percorso.

1. Verifica se la configurazione di Apache Sling Resource Resolver Factory sta causando riscritture interne.

### 6. Come ottenere i dettagli della visualizzazione e del dispositivo dall’API del lettore?

È possibile ottenere i dettagli del display e del dispositivo tramite:

* **un’API JS interna**
* **un archivio ContextHub**: in sono definiti tre store ContextHub `/libs/screens/clientlibs/contexthub` per esporre canali, dispositivi e, visualizza informazioni.

  Per utilizzare questi valori dell’archivio ContentHub, segui i passaggi seguenti:

   * Modifica le proprietà del canale e imposta il percorso ContextHub nella scheda di personalizzazione sul valore (come indicato sopra)
   * In JS per il canale, puoi utilizzare:

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## Suggerimenti generali per la risoluzione dei problemi {#general-troubleshooting-tips}

### 1. Come disabilitare Livefyre per evitare errori di schermate A/P?

Disattiva Livefyre per evitare errori di registro, effettuando le seguenti operazioni.

1. ***Disabilita bundle Livefyre:***

   * Accedi a `https://<host>:<port>/system/console/bundles`.
   * Cerca il bundle AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`.
   * Clic **Interrompi**.

1. ***Disabilita poller Livefyre:***

   * In CRXDE Liti, passa a `/etc/importers/polling/livefyre-poller/jcr:content`.
   * Aggiungi una proprietà *abilitato* tipo *Booleano*.
   * Imposta **proprietà enabled** a **false**.

### 2. Come aggiungere le informazioni dell’indice Oak? {#add-oak-index-info}

AEM Screens crea definizioni di indice per le query utilizzate dal prodotto.
Se sono presenti *Avvisi di attraversamento query* nel `error.log`, crea un indice personalizzato per la query. Consulta [Configurazione degli indici](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes) per ulteriori dettagli.

È inoltre possibile visualizzare una risorsa aggiuntiva in [Documentazione di Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. Cosa è necessario per configurare i manifesti v3? {#configure-v3}

Per abilitare il manifesto v3, effettuare le seguenti operazioni:

* Aggiorna Dispatcher.
Consulta [Configurazione di Dispatcher per la versione v3 del manifesto](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) per ulteriori dettagli.

* Aggiorna componente personalizzato.
Consulta [Modello per gestori personalizzati](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers) per ulteriori dettagli.

* Disattiva ContentSync in `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Abilita SmartSync in `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Modifica `channel/experience fragment/page components`.

* Accedi a **Configurazione offline** scheda.

* Invio `clientlibs `cartelle e per i file statici che devono essere aggiunti al manifesto.

### 4. Cosa devi fare se, dopo il pacchetto screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 e i bundle di base screens sono installati ma non attivi?

Installa una versione minima del Feature Pack 8 di AEM 6.5 affinché il connettore AMS funzioni. Consulta [Disponibilità](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) in modo da ottenere la versione minima del feature pack di AEM Screens.

### 5. Come configurare il servizio CQ Link Externalizer in Screens?

Il servizio viene utilizzato per definire il nome host pubblico per le istanze di authoring e pubblicazione e i valori vengono quindi utilizzati per aggiornare gli URL del server dispositivo e anche per il targeting ContextHub.

Il servizio CQ Link Externalizer in Screens può essere configurato tramite:

1. Accedi a `http://localhost:4502/system/console/configMgr`
1. Day CQ Link Externalizer
1. Modifica il nome host per `author/publish` voci in base alle esigenze