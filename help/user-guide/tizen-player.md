---
title: Giocatore Tizen
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
feature: Administering Screens, Players
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 1%

---


# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per AEM Screens, effettua le seguenti operazioni:

1. Passa alla pagina [Download di AEM Screens Player](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installa il file Tizen player *(.zip)* dal computer locale.

## Configurazione del server locale ed estrazione dei file ZIP {#setting-local-server}

>[!NOTE]
> Estrai il file zip e rendi disponibile il Tizen player tramite un `http server`. (Il `http server` non deve essere un server locale o Apache).

Effettua le seguenti operazioni:

1. Copia i due file estratti, ad esempio `AEMScreensPlayer.wgt` e `sssp_config.xml` nella directory principale del server Web Apache locale.

   >[!NOTE]
   >L&#39; `AEMScreensPlayer.wgt`è l&#39;applicazione Tizen Player effettiva e `sssp_config.xml` contiene informazioni su questa mappa che ti aiutano a installarla sul dispositivo Tizen.

1. Ottieni l’IP o l’URL del server HTTP locale (e il percorso della cartella contenente i file estratti nel passaggio 2 se estratti in una sottocartella e non in una cartella principale)

1. Il Tizen Player scaricherà il programma di installazione dal server locale.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Segui i passaggi seguenti sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens sul dispositivo:

1. Passa al tuo dispositivo Samsung e accendi.

1. Fai clic sul pulsante **MENU** dal telecomando del dispositivo e scorri verso il basso fino a **Sistema** dalla barra di navigazione a sinistra.

1. Scorri verso il basso e seleziona l&#39;opzione **Riproduci tramite** e modificala in **URL Launcher** .
   ![immagine](/help/user-guide/assets/tizen/rms-2.png)

1. Una volta impostato l&#39;URL Launcher, premere il pulsante **Home** dal telecomando.

1. Passa a **Impostazioni di avvio URL** e immetti l&#39;indirizzo IP del server localhost e fai clic su **Fine**.
   >[!NOTE]
   >Il lettore Tizen deve essere in grado di connettersi al server http.

1. AEM Screens Player dovrebbe ora installare e avviare automaticamente sul tuo dispositivo Samsung.

   >[!NOTE]
   >Sia il dispositivo Tizen che il server `http` devono essere in grado di connettersi tra loro, ovvero il server deve essere raggiungibile con il lettore Tizen.


## Esenzione degli agenti utente con problema cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Questa sezione si applica a Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Alcuni motori del browser sono incompatibili con l&#39;attributo *SameSite=None* utilizzato nel token di accesso rilasciato da AEM 6.5 a AEM 6.7. Nella maggior parte dei casi il problema può essere risolto aggiornando il browser all&#39;ultima versione disponibile. In alcuni casi tali aggiornamenti potrebbero non essere possibili, ad esempio con display intelligenti, decoder o altri dispositivi con motori di navigazione incorporati.

Segui i passaggi seguenti per esentare questi client incompatibili quando utilizzi *SameSite=None*:

1. Aggiornamento a Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Dopo AEM riavvio, vai a `/system/console/configMgr` e cerca **Gestore di autenticazione dei token di Adobe**. Imposta il valore per il valore **SameSite** su **None**.

1. Dovresti vedere una nuova opzione *Agenti utente da esentare dall&#39;attributo samesite*. Compila questo con un regex corrispondente agli agenti utente che sono incompatibili con l&#39;attributo *SameSite=None* .
   >[!NOTE]
   >Vedere [SameSite=None: Client noti incompatibili](https://www.chromium.org/updates/same-site/incompatible-clients) per ulteriori dettagli. Per il giocatore Tizen usare il regex: `(.*)Tizen(.*)`.

1. Registra il Tizen player rispetto alla tua istanza AEM 6.5.5 e successive e dovrebbe registrare e mostrare il contenuto normalmente.

## Provisioning in blocco di Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Può essere un noioso sforzo per inserire manualmente l&#39;indirizzo del server AEM nell&#39;interfaccia utente amministratore di ogni dispositivo per un numero elevato di dispositivi. Si consiglia di utilizzare la soluzione di gestione remota (RMS) Samsung per l&#39;implementazione e la gestione di soluzioni più grandi. Per ulteriori informazioni, consulta [Registrazione del dispositivo Tizen al servizio di gestione remota Samsung (RMS)](#enroll-tizen-device-rm) .

Segui i passaggi seguenti per eseguire il provisioning in serie dell’applicazione per puntare all’istanza di authoring AEM all’avvio:

1. Scarica e installa [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Apri il file `wgt` utilizzando Tizen studio.
1. Apri il file `firmware-platform.js` e cerca `DEFAULT_PREFERENCES`, modifica l&#39;URL del server nell&#39;URL dell&#39;autore AEM e salva.
1. Crea il nuovo file `wgt`.

   >[!NOTE]
   >Potrebbe essere necessario creare o impostare un certificato di firma.

1. Distribuisci questo nuovo file `wgt` utilizzando RMS o URL Launcher e quando il lettore viene avviato deve puntare automaticamente al server in modo da non doverlo immettere manualmente per ogni dispositivo.

### Registrazione del dispositivo Tizen al servizio di gestione remota Samsung (RMS) {#enroll-tizen-device-rms}

Segui i passaggi seguenti per registrare il dispositivo Tizen al servizio di gestione remota Samsung (RMS) e configurare in remoto l&#39;URL Launcher:

>[!NOTE]
>Verificare le impostazioni di rete e il monitor.

1. Passa a **Menu** -> **Rete** -> **Impostazioni di rete del server** e premi **Invio**.

1. Accedi all&#39;indirizzo Server e digita l&#39;accesso all&#39;URL MagicInfo e premi **Fine**.

1. Imposta TLS, se necessario. Passa alla porta e seleziona il numero di porta dal server e fai clic su **Salva**.

1. Passa alla scheda **Dispositivo** e controlla il dispositivo appena configurato. Una volta trovato un dispositivo, fai clic sulla casella di controllo e seleziona **Approva**.

   >![immagine](/help/user-guide/assets/tizen/rms-3.png)

1. Compila le informazioni richieste e seleziona un gruppo di dispositivi. Fai clic su **OK** per completare il processo di approvazione.

   >![immagine](/help/user-guide/assets/tizen/rms-7.png)

1. Una volta approvato, il dispositivo dovrebbe essere visualizzato nell&#39;elenco dei dispositivi. Fai clic sul pulsante *Informazioni* situato nella casella del dispositivo, ovvero **i**, come illustrato nella figura riportata di seguito.

   >![immagine](/help/user-guide/assets/tizen/rms-6.png)

1. Viene visualizzata la finestra di dialogo delle informazioni sul dispositivo. Seleziona la scheda **Informazioni sul dispositivo** e fai clic su **Modifica**.

   >![immagine](/help/user-guide/assets/tizen/rms-5.png)

1. Modifica le opzioni del dispositivo e seleziona la scheda **Configurazione** . Passa alla sezione **URL Launcher** e immetti l’URL che ospita il wgt e `SSSP config file` per installare un’applicazione `SSSP`, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/tizen/rms-9.png)

1. Fai clic su **Salva** per visualizzare le modifiche nella schermata di visualizzazione.

