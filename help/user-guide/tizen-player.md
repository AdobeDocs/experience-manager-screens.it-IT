---
title: Tizen Player
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
translation-type: tm+mt
source-git-commit: dc2fedaa5726e1013e1b51f429ba19e4a709de28
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---


# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per  AEM Screens, effettuate le seguenti operazioni:

1. Andate alla pagina [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installate il file Tizen player *(.zip)* dal computer locale.

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
   ![immagine](/help/user-guide/assets/tizen/url-launcher.png)

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

1. Accedete a Indirizzo server e digitate nell’accesso all’URL MagicInfo, quindi premete Fine.

1. Imposta TLS da utilizzare o non utilizzare a seconda dei casi
   1. Vai alla porta e seleziona il numero della porta dal server.
   1. Premi Salva una volta che le opzioni sono pronte.

1. Passa alla scheda Dispositivo dopo aver effettuato l&#39;accesso a MIS
   1. Cercate il dispositivo che avete appena configurato guardando l&#39;indirizzo IP e/o il suo indirizzo Mac.
   1. Una volta trovato il dispositivo, fare clic sulla casella di controllo e selezionare Approva.

1. Dopo aver fatto clic sul pulsante Approvato, verrà visualizzato il seguente Pop Up
   1. Compilate le informazioni richieste
   1. selezionare un gruppo di dispositivi
   1. Fare clic su Pulsante Ok per completare il processo di approvazione.

1. Dopo l&#39;approvazione, il dispositivo deve essere visualizzato come segue nell&#39;elenco dei dispositivi.
   1. Fare clic sul pulsante Informazioni situato nella casella del dispositivo &quot;i&quot;

1. La finestra a comparsa Informazioni dispositivo verrà visualizzata come segue e fare clic sul pulsante Modifica.

1. Le opzioni Modifica dispositivo vengono visualizzate come segue e selezionate la scheda Configurazione.

1. Individuate la sezione URL Launcher e immettete l&#39;URL che ospita il wgt e `SSSP config file` per installare un&#39;applicazione SSSP.




