---
title: Domande frequenti su AEM Screens
seo-title: AEM Screens FAQs
description: Segui questa pagina per ottenere le risposte alle domande frequenti relative a un progetto AEM Screens.
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: a3bed3baf7e825299a82ccf624c3cdf876830cd0
workflow-type: tm+mt
source-wordcount: '2119'
ht-degree: 1%

---

# Domande frequenti su AEM Screens {#aem-screens-faqs}

La sezione seguente fornisce le risposte ad alcune delle domande frequenti più frequenti relative a un progetto AEM Screens.

## Problema dello schermo vuoto {#blank-screen}

>[!NOTE]
>I controlli obbligatori elencati devono essere eseguiti dal supporto principale o dal supporto lato cliente prima di sollevare un problema.

### 1. Quali dovrebbero essere i passaggi per la risoluzione dei problemi di primo soccorso per qualsiasi cliente che si trova di fronte a uno schermo nero o a contenuti non riprodotti? {#troubleshooting-blank-screen}

* Controlla se l&#39;anteprima del canale funziona.
* Controlla se l&#39;anteprima della visualizzazione funziona
* Prova a registrare il lettore come estensione del browser sul tuo sistema allo stesso display e controlla se funziona.
* Con il lettore in esecuzione sul sistema, passa a `http://localhost:24502`. Controlla se tutto il contenuto viene scaricato correttamente.
* Controlla che le risorse vengano create le rappresentazioni appropriate e che venga riprodotto il rendering corretto.
* Controlla eventuali contenuti pianificati e se i tempi sono corretti. Controlla se l&#39;ora impostata nel lettore è corretta.
* Inspect registra la console del lettore e controlla eventuali errori. Fai clic con il pulsante destro del mouse e controlla per visualizzare i registri della console. Se si utilizza windows player, premere `CTRL + ALT +I` per visualizzare i registri nella console di sviluppo.

### 2. Come risolvere il problema dello schermo grigio in AEM Screens creando un canale o una pianificazione predefinita?

Per evitare le schermate vuote o grigie nel campo, crea un canale globale predefinito o una pianificazione, assegnata a ogni visualizzazione con la priorità minima 1. Nel caso in cui qualcosa non funzioni con gli aggiornamenti dei contenuti (a causa di rete, lettore, server o replica), poiché i lettori hanno già questo contenuto memorizzato nella cache del disco, che dovrebbe essere riprodotto correttamente ed evitare gli schermi grigi.

Tutti gli altri contenuti, come canali o pianificazioni, avranno priorità maggiore di 1, quindi l’altro contenuto ha priorità e il canale globale o il contenuto della pianificazione (con priorità 1) verrà riprodotto solo come opzione di fallback.

## Gestione dei canali {#channel-management}

### 1. Qual è la differenza tra un canale online e un canale offline? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***Canale online*** mostra il contenuto aggiornato in ambiente in tempo reale, mentre in ***Canale offline*** mostra il contenuto della cache.

### 2. Come faccio un canale online? {#how-do-i-make-a-channel-online}

Seleziona il canale e passa alle proprietà del canale dalla barra delle azioni. Controlla **Modalità Sviluppatore (forzare il canale ad essere online)** sotto **Canale** scheda per rendere il canale online.

### 3. Qual è l’utilizzo del campo Ruolo canale? {#what-is-the-use-of-the-channel-role-field}

Il Ruolo canale è l’astrazione del canale effettivo eseguito in modo che l’autore possa concentrarsi direttamente sull’esperienza generica. Puoi considerarlo come un tipo di tag che identifica in modo univoco il canale nel suo contesto (visualizzazione o pianificazione).

### 4. Come avviene la risoluzione effettiva del canale? {#how-does-actual-channel-resolution-happen}

Per *riferimenti statici*, la risoluzione segue il percorso specificato.

Per *riferimenti dinamici*, la risoluzione si verifica una volta che il canale viene assegnato alla visualizzazione (non alla pianificazione). Il percorso di visualizzazione diventa il contesto del canale e la risoluzione si verifica come segue (priorità da più alta a quella più bassa):

1. La visualizzazione ha un nodo figlio che corrisponde al nome del canale a cui si fa riferimento
1. La visualizzazione ha un nodo di pari livello che corrisponde al nome del canale a cui si fa riferimento
1. La posizione padre della visualizzazione ha un nodo figlio che corrisponde al nome del canale a cui si fa riferimento
1. La posizione principale della visualizzazione ha un nodo figlio che corrisponde al nome del canale di riferimento

E così via, fino a raggiungere la cartella delle posizioni e fermarsi lì al momento (in modo da non fare riferimento a un canale che sarebbe nella cartella dei canali, per esempio, solo i canali nella sottostruttura delle posizioni).

### 5. Come impostare la configurazione offline clientlib personalizzata nel canale AEM Screens?

Quando si utilizza un codice personalizzato incorporato lato client `clientlib` in un canale AEM Screens, sono necessari i seguenti passaggi per assicurarsi che il `clientlib` i file vengono caricati correttamente nel canale (`manifest.json`) e conterrà il percorso del `clientlib`.

Segui i passaggi riportati di seguito dall’editor di canali:

1. Seleziona un canale e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor canali.
1. Seleziona il componente in cui desideri aggiungere il `clientlib`.
1. Fai clic sul pulsante di configurazione (l’icona a forma di chiave inglese).
1. Passa a **Configurazione offline** e aggiungi il percorso alla clientlib personalizzata in **Librerie lato client**.

## Registrazione dispositivo {#device-registration}

### 1. Se scopro endpoint come richieste di onboarding e registrazione dei dispositivi, posso creare script su un gran numero di dispositivi e registrare questi dispositivi. Oltre a bloccare questo su un ramo Wi-Fi, è possibile proteggere queste richieste? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Attualmente la registrazione è possibile solo sull&#39;istanza dell&#39;autore. Anche se il servizio di registrazione non è autenticato, creerà solo un dispositivo in sospeso in AEM e non registrerà effettivamente il dispositivo o assegnerà alcun display.

Per registrare un dispositivo (il che significa creare un utente per il dispositivo in AEM), è comunque necessario eseguire l&#39;autenticazione per AEM e attualmente seguire manualmente la procedura guidata di registrazione per completare la registrazione. In teoria, un utente malintenzionato può creare diversi dispositivi in sospeso ma non può registrarne uno senza un accesso AEM.

### 2. Esiste un modo per trasformare le richieste HTTP GET in HTTP POST con una qualche forma di autenticazione? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La richiesta di registrazione è una richiesta di POST.

Si consiglia di ottenere l’ID dispositivo dalla sessione anziché come parametro. Questo eliminerebbe i registri del server, la cache del browser e così via. Attualmente non si tratta di un problema di sicurezza. Tieni presente che GET viene utilizzato semanticamente quando non vi sono modifiche di stato sul server e POST viene utilizzato quando si verifica una modifica di stato.

### 3. C&#39;è un modo per rifiutare una richiesta di registrazione del dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

Non è possibile rifiutare le richieste di registrazione. Al contrario, le richieste di registrazione dovrebbero scadere dopo un timeout configurato in `Adobe Experience Manager Web Console`. Per impostazione predefinita, questo valore è impostato su un giorno e viene memorizzato in una cache di memoria.

## Report di monitoraggio e integrità dei dispositivi {#device-monitoring-and-health-reports}

### 1. Come posso risolvere il problema, se il mio lettore AEM Screens mostra la schermata vuota? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Controlla le seguenti possibilità per risolvere il problema della schermata vuota:

* AEM non è in grado di inviare il contenuto offline
* Il canale non ha contenuto
* Nessuna delle risorse è pianificata per essere visualizzata al momento attuale

### 2. Cosa posso fare se AEM Screens Player non riesce a registrarsi e il suo stato viene visualizzato come Errore? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

È necessario abilitare l’opzione Consenti valori vuoti per il filtro di riferimento Apache Sling. Questo è necessario per il funzionamento ottimale del protocollo di controllo tra AEM Screens Player e il server AEM Screens.

1. Passa a **Configurazione della console Web di Adobe Experience Manager**
1. Controlla la **allow.empty** opzione .
1. Fai clic su **Salva**.

### 3. Come risolvere il problema se durante la registrazione di un lettore AEM Screens, il dispositivo mostra FAILURE e i registri della console mostrano l&#39;errore ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Questo problema può verificarsi se il lettore non è in grado di trovare il DNS del server AEM Screens. Puoi provare a utilizzare l&#39;indirizzo IP per la connessione. Per ottenere l’IP del server, utilizza: *arp &lt;server_dns_name>*.

### 4. AMS consiglia di implementare un Android Watchdog su tutti i dispositivi? Il plugin Watchdog (Cordova) è incluso come parte dell&#39;APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un cane da guardia Android multipiattaforma che utilizza API Android pure è già una parte dell&#39;apk. Non è necessario alcun software aggiuntivo, ma a seconda del dispositivo utilizzato, potrebbe essere necessario rassegnare l&#39;apk per ottenere i privilegi di sistema per un ciclo di alimentazione completo (API Powermanager). Se non viene rassegnato utilizzando i tasti del produttore, verrà chiuso e riavviato l&#39;applicazione ma non il ciclo di alimentazione.

Per ulteriori informazioni su come implementare Android Player, consulta [**Implementazione di Android Player**](implementing-android-player.md).

### 5. Quali strumenti di monitoraggio remoto e di avviso (software) di terze parti sono consigliati da Adobe/AMS per il monitoraggio di ciascun dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

A seconda delle esigenze di monitoraggio e avvisi, una nuova funzione del servizio Notifiche di AEM Screens ti avvisa se un dispositivo non è stato bloccato da qualche tempo. Gli strumenti di terze parti dipenderanno dal sistema operativo, dalle sue funzionalità e dalle esigenze specifiche del cliente.

Per ulteriori informazioni su dove è possibile monitorare l&#39;attività del dispositivo, consulta [**Servizio notifiche AEM Screens**](screens-notifications-service.md).

## Lettore AEM Screens {#aem-screens-player}

### 1. Come installare il lettore ChromeOS come plugin del browser Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS Player può essere installato come plugin del browser Chrome in modalità sviluppatore senza richiedere l&#39;effettivo dispositivo chrome player. Per l&#39;installazione, segui i passaggi seguenti:

1. Fai clic su [qui](https://download.macromedia.com/screens/) per scaricare il lettore Chrome più recente.
1. Decomprimere e salvarlo sul disco.
1. Apri il browser Chrome e seleziona **Estensioni** dal menu o direttamente passa a ***chrome://extensions***.
1. Accendere **Modalità Sviluppatore** dall&#39;angolo in alto a destra.
1. Fai clic su **Carica non imballato** dall&#39;angolo in alto a sinistra e carica il lettore Chrome decompresso.
1. Controlla **Lettore Chrome di AEM Screens** se disponibile nell’elenco delle estensioni.
1. Apri una nuova scheda e fai clic su **App** dall’angolo in alto a sinistra o direttamente passare a ***chrome://apps***.
1. Fai clic su **AEM Screens** Plug-in per avviare Chrome Player. Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Press **cese** per uscire dalla modalità a schermo intero.

### 2. Come risolvere il problema se Screens Player non è in grado di eseguire l&#39;autenticazione tramite l&#39;istanza di pubblicazione con un gestore di errori personalizzato? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

All&#39;avvio di AEM Screens Player, invia una richiesta a ***/content/screens/svc.ping.json***, quando il lettore riceve un errore 404. Il lettore avvia una richiesta di autenticazione da autenticare rispetto all&#39;istanza di pubblicazione. Se nell&#39;istanza di pubblicazione è presente un gestore di errori personalizzato, assicurati di restituire il codice di stato 404 per l&#39;utente anonimo su ***/content/screens/svc.ping.json***.

### 3. Come impostare lo schermo del dispositivo rimanere acceso in un lettore Android? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Segui i passaggi seguenti per attivare Stay Awake su qualsiasi lettore Android:

1. Passa alle impostazioni del lettore Android —> **Informazioni**
1. Tocca 7 volte il numero di build per abilitare **Opzioni per gli sviluppatori** in **Impostazioni**
1. Passa a **Opzioni per gli sviluppatori**
1. Abilita **Resta sveglia**

### 4. Come abilitare la modalità finestra per il lettore Windows?{#enable-player}

Non è disponibile una modalità finestra in Windows Player. È sempre in modalità a schermo intero.

### 5. Come risolvere i problemi se un lettore AEM Screens invia continuamente le richieste di accesso?{#requests-login}

Segui i passaggi seguenti per risolvere eventuali problemi relativi a un lettore AEM Screens che invia continuamente richieste a `/content/screens/svc.json` e `/libs/granite/core/content/login.validate/j_security_check`:

1. Quando AEM Screens Player si avvia, richiede a `/content/screens/svc.json`. Quando il lettore riceve un codice di stato 404 nella risposta, avvia una richiesta di autenticazione utilizzando `/libs/granite/core/content/login.validate/j_security_check` contro *pubblicare* istanza. Se è presente un gestore di errori personalizzato nel *pubblicare* istanza, assicurati di restituire il codice di stato 404 per l&#39;utente anonimo su `/content/screens/svc.json` o `/content/screens/svc.ping.json`.

1. Controlla se la configurazione del tuo dispatcher consente queste richieste nel `/filters`.

   Vedi [Configurazione dei filtri Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) per ulteriori dettagli.

1. Controlla se le regole di riscrittura del dispatcher stanno riscrivendo uno dei percorsi delle schermate in un percorso diverso.

1. Controlla se hai `/etc/map` le norme *autore* o *pubblicare* I percorsi delle istanze e delle schermate corrispondono a `sling:match` e reindirizzato internamente a un percorso diverso. Risoluzione dell&#39;url esatto in `/system/console/jcrresolver` aiuta a identificare se *pubblicare* istanza sta riscrivendo questi URL in qualsiasi altro percorso.

1. Controlla se la configurazione di Apache Sling Resource Resolver Factory sta causando riscritture interne.

### 6. Come ottenere i dettagli della visualizzazione e del dispositivo dall&#39;API del lettore?

È possibile ottenere i dettagli del display e del dispositivo tramite:

* **un’API JS interna**
* **un archivio ContextHub**: Tre archivi ContextHub definiti in `/libs/screens/clientlibs/contexthub` per esporre canali, dispositivi e informazioni di visualizzazione.

   Segui i passaggi seguenti per utilizzare i seguenti valori dell’archivio ContentHub:

   * Modifica le proprietà del canale e imposta il percorso ContextHub nella scheda personalizzazione sul valore (come indicato sopra)
   * Nel canale JS, puoi utilizzare:

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## Suggerimenti generali per la risoluzione dei problemi {#general-troubleshooting-tips}

### 1. Come disabilitare Livefyre per evitare l&#39;errore di A/P Screens? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Per disabilitare Livefyre per evitare errori di log :

1. ***Disattiva il bundle Livefyre:***

   * Accedi a `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Cerca il bundle Livefyre AEM: `com.adobe.cq.social.cq-social-livefyre`
   * Fai clic su **Interrompi**

1. ***Disattiva Livefyre poller:***

   * In CRXDE Lite, passa a `/etc/importers/polling/livefyre-poller/jcr:content`
   * Aggiungi una nuova proprietà *abilitato* type *Booleano*
   * Imposta **enabled, proprietà** a **false**

### 2. Come aggiungere informazioni sull&#39;indice Oak? {#add-oak-index-info}

AEM Screens crea definizioni di indice per le query utilizzate dal prodotto.
Se ce ne sono *Avvisi di attraversamento delle query* in `error.log`, crea un indice personalizzato per la query. Fai riferimento a [Configurazione degli indici](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) per ulteriori dettagli.

Puoi anche fare riferimento a una risorsa aggiuntiva su [Documentazione Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. Cosa è necessario per configurare i Manifest v3? {#configure-v3}

Per abilitare il manifesto v3, devi:

* Aggiorna Dispatcher.
Vedi [Configurazione di Dispatcher per la versione v3 del manifesto](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) per ulteriori dettagli.

* Aggiorna componente personalizzato.
Vedi [Modello per gestori personalizzati](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers) per ulteriori dettagli.

* Disattiva ContentSync in `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Abilita SmartSync in `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Modifica `channel/experience fragment/page components`.

* Passa a **Configurazione offline** scheda .

* Invio `clientlibs `e cartelle per i file statici che devono essere aggiunti al manifesto.

### 4. Cosa devi fare se, dopo l&#39;installazione dei pacchetti screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 e dei bundle di base degli schermi, sono installati ma non attivi?

È necessario installare una versione minima di AEM 6.5 Feature Pack 8 per il funzionamento del connettore AMS. Consulta la sezione [Disponibilità](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en#availability) per ottenere la versione minima del feature pack.