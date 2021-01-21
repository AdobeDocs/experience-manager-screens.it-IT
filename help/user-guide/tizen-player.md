---
title: Tizen Player
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
translation-type: tm+mt
source-git-commit: 2ace2f926900304377afcd6187462545a60784d3
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 1%

---


# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per  AEM Screens, effettuate le seguenti operazioni:

1. Andate alla pagina [ Download di AEM Screens Player](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installate il file Tizen player *(.zip)* dal computer locale.

## Configurazione del server locale ed estrazione dei file ZIP {#setting-local-server}

>[!NOTE]
> Estrarre il file zip e rendere disponibile il lettore Tizen tramite un `http server`. (Il server `http server` non deve essere locale o Apache).

Effettua le seguenti operazioni:

1. Copiate i due file estratti come `AEMScreensPlayer.wgt` e `sssp_config.xml` nella directory principale del server Web Apache locale.

   >[!NOTE]
   >La `AEMScreensPlayer.wgt`è l&#39;applicazione Tizen Player effettiva e `sssp_config.xml` contiene informazioni su questa mappa che aiutano a installarla sul dispositivo Tizen.

1. Ottenete l’IP o l’URL del server HTTP locale (e il percorso della cartella contenente i file estratti nel passaggio 2 se estratti in una sottocartella e non in una cartella principale)

1. Il lettore Tizen scaricherà il programma di installazione dal server locale.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Seguire i passaggi indicati di seguito sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens  sul dispositivo:

1. Accedete al dispositivo Samsung e attivatelo.

1. Fare clic sul pulsante **MENU** dal telecomando del dispositivo e scorrere verso il basso fino a **System** dalla barra di navigazione a sinistra.

1. Scorrete verso il basso e selezionate l&#39;opzione **Riproduci tramite**, quindi cambiatela in **URL Launcher**.
   ![immagine](/help/user-guide/assets/tizen/rms-2.png)

1. Una volta impostato l&#39;URL Launcher, premere il tasto **Home** dal telecomando.

1. Andate alle **Impostazioni di avvio URL** e immettete l&#39;indirizzo IP del server localhost, quindi fate clic su **Fine**.
   >[!NOTE]
   >Il lettore Tizen deve essere in grado di connettersi al server http.

1.  AEM Screens Player dovrebbe ora installare e avviare automaticamente sul dispositivo Samsung.

   >[!NOTE]
   >Sia il dispositivo Tizen che il server `http` devono essere in grado di connettersi tra loro, ovvero il server deve essere raggiungibile dal lettore Tizen.


## Esenzione degli agenti utente con l&#39;edizione del cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Questa sezione si applica ad Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Alcuni motori del browser non sono compatibili con l&#39;attributo *SameSite=None* utilizzato nel token di login emesso da AEM 6.5 a AEM 6.7. Nella maggior parte dei casi, il problema può essere risolto aggiornando il browser all&#39;ultima versione disponibile. In alcuni casi tali aggiornamenti potrebbero non essere possibili, ad esempio con display intelligenti, set top box o altri dispositivi con motori di navigazione incorporati.

Seguite i passaggi riportati di seguito per esentare questi client incompatibili quando utilizzate *SameSite=None*:

1. Aggiornamento ad Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Dopo AEM riavvio, andate a `/system/console/configMgr` e cercate **Gestore autenticazione token di granito di Adobe**. Impostare il valore per il valore **SameSite** su **None**.

1. Dovrebbe essere visualizzata una nuova opzione *Gli agenti utente che devono essere esentati dall&#39;attributo samesite*. Compilate questo con un regex corrispondente agli agenti utente che è(i) incompatibile con l&#39;attributo *SameSite=None*.
   >[!NOTE]
   >Vedere [SameSite=None: Client noti non compatibili](https://www.chromium.org/updates/same-site/incompatible-clients) per ulteriori dettagli. Per il giocatore Tizen utilizzare il regex: `(.*)Tizen(.*)`.

1. Registrare il lettore Tizen rispetto all&#39;istanza AEM 6.5.5 e superiore e registrare e mostrare il contenuto normalmente.

## Provisioning di massa di Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Può essere un noioso sforzo per inserire manualmente l&#39;indirizzo del server AEM nell&#39;interfaccia utente di amministrazione di ciascun dispositivo per un gran numero di dispositivi. Si consiglia di utilizzare la soluzione Samsung Remote Management (RMS) per l&#39;implementazione e la gestione di soluzioni più grandi. Per ulteriori informazioni, fare riferimento a [Iscrizione del dispositivo Tizen a Samsung Remote Management Service (RMS)](#enroll-tizen-device-rm).

Per eseguire il provisioning in massa dell’applicazione, eseguite i passaggi indicati di seguito per indirizzarla all’istanza di autore AEM all’avvio:

1. Scaricate e installate [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Aprire il file `wgt` utilizzando lo studio Tizen.
1. Aprite il file `firmware-platform.js` e cercate `DEFAULT_PREFERENCES`, modificate l&#39;URL del server nell&#39;URL dell&#39;autore AEM e salvate.
1. Create il nuovo file `wgt`.

   >[!NOTE]
   >Potrebbe essere necessario creare o impostare un certificato di firma.

1. Distribuite questo nuovo file `wgt` utilizzando RMS o URL Launcher e quando il lettore viene avviato, il file deve essere indirizzato automaticamente al server, in modo che non sia necessario immetterlo manualmente per ogni dispositivo.

### Iscrizione del dispositivo Tizen al servizio di gestione remota Samsung (RMS) {#enroll-tizen-device-rms}

Seguite i passaggi riportati di seguito per iscrivere il dispositivo Tizen al servizio di gestione remota Samsung (RMS) e configurare in remoto il modulo di avvio URL:

>[!NOTE]
>Verificare le impostazioni di rete e il monitor.

1. Passare a **Menu** -> **Network** -> **Server Network Settings** e premere **Invio**.

1. Andate all&#39;indirizzo Server e digitate nell&#39;accesso all&#39;URL MagicInfo, quindi premete **Done**.

1. Se necessario, imposta TLS. Andate alla porta e selezionate il numero di porta dal server, quindi fate clic su **Salva**.

1. Andate alla scheda **Dispositivo** e verificate il dispositivo appena configurato. Una volta trovato il dispositivo, fare clic sulla casella di controllo e selezionare **Approva**.

   >![immagine](/help/user-guide/assets/tizen/rms-3.png)

1. Compilate le informazioni richieste e selezionate un gruppo di dispositivi. Fare clic su **OK** per completare il processo di approvazione.

   >![immagine](/help/user-guide/assets/tizen/rms-7.png)

1. Una volta approvato, il dispositivo deve essere visualizzato nell&#39;elenco dei dispositivi. Fare clic sul pulsante *Information* situato nella casella del dispositivo, ovvero **i**, come illustrato nella figura riportata di seguito.

   >![immagine](/help/user-guide/assets/tizen/rms-6.png)

1. Viene visualizzata la finestra di dialogo delle informazioni sul dispositivo. Selezionare la scheda **Informazioni dispositivo** e fare clic su **Modifica**.

   >![immagine](/help/user-guide/assets/tizen/rms-5.png)

1. Modificate le opzioni del dispositivo e selezionate la scheda **Configurazione**. Andate alla sezione **URL Launcher** e immettete l&#39;URL che ospita il wgt e `SSSP config file` per installare un&#39;applicazione `SSSP`, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/tizen/rms-9.png)

1. Fare clic su **Salva** per visualizzare le modifiche sullo schermo.

