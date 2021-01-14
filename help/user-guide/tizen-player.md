---
title: Tizen Player
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
translation-type: tm+mt
source-git-commit: 4c005ace7b1da94ed527164d6cfa09666d746273
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%

---


# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per  AEM Screens, effettuate le seguenti operazioni:

1. Andate alla pagina [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installate il file Tizen player *(.zip)* dal computer locale.

## Esenzione degli agenti utente con l&#39;edizione del cookie Samesite {#exempting-user-agents}

>[!IMPORTANT]
>**Questa sezione si applica alle AEM da 6.5.5 a AEM 6.5.7**
>Alcuni motori del browser non sono compatibili con l&#39;attributo *SameSite=None* utilizzato nel token di login emesso da AEM 6.5 a AEM 6.7. Nella maggior parte dei casi, il problema può essere risolto aggiornando il browser all&#39;ultima versione disponibile. In alcuni casi tali aggiornamenti potrebbero non essere possibili, ad esempio con display intelligenti, set top box o altri dispositivi con motori di navigazione incorporati. Per esentare questi client incompatibili quando si utilizza SameSite=None, procedere come segue.

1. Scaricate la patch *file jar* da `https://artifactory.corp.adobe.com/artifactory/maven-aem-release-local/com/adobe/granite/crx-auth-token/2.6.10/`.

1. Andate a `/system/console/bundles` in AEM e fate clic sul pulsante `install/update`.

1. Installate il file `crx-auth-token` jar. Potrebbe essere necessario arrestare e riavviare AEM dopo l&#39;installazione di questo Jar perché è correlato all&#39;autenticazione.

1. Dopo AEM riavvio, andate a `/system/console/configMgr` e cercate **Gestore autenticazione token di granito di Adobe**. Impostare il valore per l&#39;impostazione SameSite su None.

1. Dovrebbe essere visualizzata una nuova opzione *Gli agenti utente che devono essere esentati dall&#39;attributo samesite*. Compilate questo con un regex corrispondente agli agenti utente che è(i) incompatibile con l&#39;attributo *SameSite=None*.
   >[!NOTE]
   >Vedere [SameSite=None: Client noti non compatibili](https://www.chromium.org/updates/same-site/incompatible-clients) per ulteriori dettagli.

1. Per il giocatore Tizen utilizzare il regex: `(.*)Tizen (4|5)(.*)` Registrare il lettore Tizen rispetto all&#39;istanza AEM 6.5.5 e superiore e registrare e mostrare il contenuto normalmente.


## Configurazione del server locale ed estrazione dei file ZIP {#setting-local-server}

Per configurare il server locale e copiare i file estratti, effettuate le seguenti operazioni:

1. Ottenere l&#39;indirizzo IP del computer locale.
   >[!NOTE]
   >Per informazioni su come abilitare il server locale sulla piattaforma, consulta la documentazione ufficiale.

1. Dal terminale, andate alla stessa directory della cartella del programma di installazione decompressa e verificate che il localhost funzioni.

1. Il lettore Tizen scaricherà il programma di installazione dal server locale.

1. Copiate i due file estratti come `AEMScreensPlayer.wgt` e `sssp_config.xml` nella directory principale del server Web Apache locale.

   >[!NOTE]
   >La `AEMScreensPlayer.wgt`è l&#39;applicazione Tizen Player effettiva e `sssp_config.xml` contiene informazioni su questa mappa che aiutano a installarla sul dispositivo Tizen.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Seguire i passaggi indicati di seguito sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens  sul dispositivo:

1. Accedete al dispositivo Samsung e attivatelo.

1. Fare clic sul pulsante **MENU** dal telecomando del dispositivo e scorrere verso il basso fino a **System** dalla barra di navigazione a sinistra.

1. Scorrete verso il basso e selezionate l&#39;opzione **Riproduci tramite URL Launcher**.
   ![immagine](/help/user-guide/assets/tizen/rms-2.png)

1. Premere il tasto **Home** dal telecomando.

1. Immettete l&#39;indirizzo IP del server localhost.

1. Selezionare **Remote** dalla **Modalità Sviluppatore**.

1. Fare clic sul pulsante **Home** dal telecomando del dispositivo e selezionare **URL Launcher**.

1.  AEM Screens Player dovrebbe ora installare e avviare automaticamente sul dispositivo Samsung.

## Provisioning di massa di Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Può essere un noioso sforzo per inserire manualmente l&#39;indirizzo del server AEM nell&#39;interfaccia utente di amministrazione di ciascun dispositivo per un gran numero di dispositivi. Si consiglia di utilizzare la soluzione Samsung Remote Management (RMS) per distribuire e gestire la soluzione. Per ulteriori informazioni, fare riferimento a [Iscrizione del dispositivo Tizen a Samsung Remote Management Service (RMS)](#enroll-tizen-device-rm).

Per eseguire il provisioning in massa dell’applicazione, eseguite i passaggi indicati di seguito per indirizzarla all’istanza di autore AEM all’avvio:

1. Scaricate e installate [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Aprire il file `wgt` utilizzando lo studio Tizen.
1. Aprite il file `firmware-platform.js` e cercate `DEFAULT_PREFERENCES`, modificate l&#39;URL del server nell&#39;URL dell&#39;autore AEM e salvate.
1. Create il nuovo file `wgt`.

   >[!NOTE]
   >Potrebbe essere necessario creare o impostare un certificato di firma.

1. Distribuire questo nuovo file RMS `wgt` e quando il lettore lo avvia, puntare automaticamente al server, in modo da non dover immettere manualmente il file per ogni dispositivo.

### Iscrizione del dispositivo Tizen a Samsung Remote Management Service(RMS) {#enroll-tizen-device-rms}

Seguite i passaggi riportati di seguito per iscrivere il dispositivo Tizen al servizio di gestione remota Samsung (RMS) e configurare in remoto il modulo di avvio URL:

>[!NOTE]
>Verificare le impostazioni di rete e il monitor.

1. Passare a **Menu** -> **Network** -> **Server Network Settings** e premere **Invio**.

   >[!NOTE]
   >Verificate che la schermata sia impostata su Riproduci tramite URL Launcher.
   >![immagine](/help/user-guide/assets/tizen/rms-2.png)

1. Accedete a Indirizzo server e digitate nell’accesso all’URL MagicInfo, quindi premete Fine.

1. Se necessario, imposta TLS. Andate alla porta e selezionate il numero di porta dal server. Fare clic su **Salva**.

1. Passate alla scheda Dispositivo e cercate il dispositivo appena configurato.

1. Una volta trovato il dispositivo, fare clic sulla casella di controllo e selezionare **Approva**.

1. Compilate le informazioni richieste e selezionate un gruppo di dispositivi. Fare clic su **Ok** per completare il processo di approvazione.

   >![immagine](/help/user-guide/assets/tizen/rms-7.png)

1. Una volta approvato, il dispositivo deve essere visualizzato nell&#39;elenco dei dispositivi. Fare clic sul pulsante *Informazioni* situato nella casella del dispositivo **i**.

   >![immagine](/help/user-guide/assets/tizen/rms-6.png)

1. Viene visualizzata la finestra di dialogo delle informazioni sul dispositivo. Selezionare la scheda **Informazioni dispositivo** e fare clic su **Modifica**.

1. Modificate le opzioni del dispositivo e selezionate la scheda **Configurazione**. Andate alla sezione **URL Launcher** e immettete l&#39;URL che ospita il wgt e `SSSP config file` per installare un&#39;applicazione `SSSP`, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/tizen/rms-9.png)

1. Fare clic su **Salva** per visualizzare le modifiche sullo schermo.




