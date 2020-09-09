---
title: Guida di Kickstart
seo-title: Guida di Kickstart
description: Segui questa pagina per creare una dimostrazione  progetto AEM Screens. Consente di creare un'esperienza di digital signage a partire dall'installazione e dalla configurazione di un nuovo progetto per la visualizzazione dei contenuti  lettore AEM Screens.
translation-type: tm+mt
source-git-commit: d49ceecab42762425d779d50a31291091088ee19
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 5%

---


# Guida di Kickstart {#kickstart-guide}

Questa sezione rappresenta un punto di partenza per  AEM Screens e illustra come impostare ed eseguire un progetto AEM Screens . Consente di configurare un&#39;esperienza di digital signage di base e di aggiungere contenuti quali risorse e/o video a ogni canale e di pubblicare ulteriormente i contenuti su un lettore AEM Screens .

>[!NOTE]
>Prima di iniziare a lavorare sui dettagli del progetto, accertatevi di aver installato il Feature Pack più recente. È possibile scaricare l&#39;ultimo pacchetto di funzioni per  versione di AEM Screens 6.5.5 dal portale [di distribuzione](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) software utilizzando l&#39;Adobe ID .

## Prerequisiti {#prerequisites}

Seguite i passaggi riportati di seguito per creare un progetto di esempio per  AEM Screens e pubblicare ulteriormente il contenuto per il lettore Screens.

>[!NOTE]
>L&#39;esercitazione seguente mostra come riprodurre il contenuto del canale nel lettore Chrome OS.

>[!IMPORTANT]
>**Impostazioni di configurazione OSGi**
>È necessario abilitare il referente vuoto per consentire al dispositivo di inviare dati al server. Ad esempio, se la proprietà del referente vuoto è disabilitata, il dispositivo non può inviare una schermata indietro. Attualmente alcune di queste funzioni sono disponibili solo se Apache Sling Referrer Filter Allow Empty è abilitato nella configurazione OSGi. Il dashboard potrebbe visualizzare un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzioni.
>Per attivare il filtro ***Apache Sling Referrer Filter Allow Empty***, effettuate le seguenti operazioni:


## Consenti richieste referente vuote {#allow-empty-referrer-requests}

1. Passa a Configurazione **console Web** Adobe Experience Manager tramite AEM&#39;istanza —> icona a forma di martello —> **Operazioni** —> Console **** Web.

   ![immagine](assets/config/empty-ref1.png)

1. **Viene visualizzata la configurazione** della console Web di Adobe Experience Manager. Cerca referrer di fionda.

   Per cercare la proprietà sling referrer, premere **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

1. Selezionare l&#39;opzione **Consenti valori nulli** , come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/empty-ref2.png)

1. Fate clic su **Salva** per attivare l&#39;opzione Consenti valori nulli per il filtro Apache Sling Referrer.


## Creazione di un&#39;esperienza di digital signage in 5 minuti {#creating-a-digital-signage-experience-in-minutes}

### Creating an AEM Screens Project {#creating-project}

Il primo passaggio consiste nella creazione di un nuovo progetto AEM Screens .

1. Passate all&#39;istanza Adobe Experience Manager (AEM) e fate clic su **Screens**. In alternativa, potete navigare direttamente da `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![immagine](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Dopo aver creato il progetto, tornerai alla home page del progetto Screens. Ora puoi selezionare il progetto. In un progetto, esistono cinque diverse cartelle denominate **Applicazioni**, **Canali**, **Dispositivi**, **Posizioni** e **Pianificazioni**.


### Creazione di un canale {#creating-channel}

Una volta installato il progetto, è necessario creare un nuovo canale in cui gestire il contenuto.

Per creare un nuovo canale per il progetto, effettuate le seguenti operazioni:

1. Dopo aver creato un progetto, selezionate il progetto **DemoScreens** e selezionate la cartella **** Canali, come illustrato nella figura riportata di seguito. Click **+ Create** from the action bar.

   ![immagine](assets/kickstart/demo-2.png)

1. Scegliete il canale **** della sequenza dalla procedura guidata e fate clic su **Avanti**.
   ![immagine](assets/kickstart/demo-3.png)

1. Enter the **Title** as *TestChannel* and click **Create**.

   ![immagine](assets/kickstart/demo-4.png)

   Il *TestChannel* viene creato e aggiunto alla cartella dei canali, come illustrato nella figura riportata di seguito.

   ![immagine](assets/kickstart/demo-5.png)

### Adding Content to a Channel {#adding-content}

Una volta installato il canale, è necessario aggiungere al canale il contenuto che verrà visualizzato dal lettore Screens.

Per aggiungere contenuti al canale (*TestChannel*) del progetto, effettuate le seguenti operazioni:

1. Navigate to the **DemoProject** you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the **TestChannel** opens.

   ![immagine](assets/kickstart/demo-6.png)

1. Fai clic sull’icona che apre o chiude il pannello laterale sinistro della barra delle azioni per aprire le risorse e i componenti.

1. Trascina i componenti da aggiungere al canale.

   ![immagine](assets/kickstart/demo-7.png)

### Creazione di una posizione{#creating-location} 

Una volta installato il canale, è necessario creare una posizione.

>[!NOTE]
>***Le posizioni*** consentono di compartimentare le diverse esperienze di digital signage e contengono le configurazioni dei display in base a dove si trovano i vari schermi.

Per creare una nuova posizione per il progetto, effettuate le seguenti operazioni:

1. Navigate to the **DemoProject** you created and select the **Locations** folder.

1. Click **+ Create** from the action bar.

1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** for your location (enter the title as *TestLocation*) and click **Create**.

Il **TestLocation** viene creato e aggiunto alla cartella **Locations** .


### Creazione di un display per la posizione {#creating-display}

Dopo aver creato un percorso, è necessario creare una nuova visualizzazione per il percorso.

>[!NOTE]
>***I display*** rappresentano l&#39;esperienza digitale che viene eseguita su uno o più schermi.

1. Andate a **TestLocation** e selezionatelo.

1. Fai clic su **Crea** nella barra delle azioni.

   ![immagine](assets/kickstart/demo-disp1.png)

1. Select **Display** from the **Create** wizard and click **Next**.

   ![immagine](assets/kickstart/demo-disp2.png)

1. Enter the **Title** as **LobbyDisplay** and click **Create**.

   ![immagine](assets/kickstart/demo-disp3.png)

   Una nuova visualizzazione con titolo **TestDisplay** ora viene aggiunta alla posizione **TestLocation**, come illustrato nella figura seguente.

   ![immagine](assets/kickstart/demo-disp4.png)

### Assigning a Channel {#assigning-channel}

Una volta completata la configurazione del progetto, dovete assegnare il canale a uno schermo per visualizzare il contenuto.

1. Passare alla visualizzazione desiderata da **DemoScreens** —> **Locations** —> **TestLocation** —> **LobbyDisplay**.

1. Tap/click **Assign Channel** from the action bar.

   ![immagine](assets/kickstart/demo-assign1.png)

   Oppure,

   Toccate/fate clic su **Dashboard** nella barra delle azioni e fate clic su **+Assegna canale** dal pannello CANALI **ASSEGNATI e PIANIFICAZIONI** .

   ![immagine](assets/kickstart/demo-assign2.png)

1. The **Channel Assignment** dialog box opens.

1. Dall’opzione **Impostazioni** , scegliete il canale **per percorso** e gli eventi **** supportati come caricamento **** iniziale e **schermata** inattiva.

   >[!NOTE]
   >
   >Il ruolo **del** canale, la **priorità** e i metodi **di** interruzione sono tutti popolati per impostazione predefinita. Consulta la sezione Proprietà [](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) canale per ulteriori informazioni sulle proprietà di assegnazione dei canali.

   ![immagine](assets/kickstart/demo-assign3.png)

   Inoltre, puoi selezionare la finestra **** Attivazione e la programmazione **** ricorrenza.

   >[!NOTE]
   >La programmazione ** ricorrenza consente di impostare una pianificazione periodica per il canale. Puoi impostare più pianificazioni di ricorrenza per un canale.
   >Per ulteriori dettagli, consulta [Pianificazione](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) ricorrenza.

1. Dopo aver configurato le preferenze, fate clic su **Salva** .

### Registrazione di un dispositivo e assegnazione di un dispositivo a uno schermo {#registering-device}

È necessario registrare il dispositivo utilizzando il dashboard di AEM.

>[!IMPORTANT]
>Il lettore Chrome OS può essere installato come il plugin Chrome Browser in modalità sviluppatore senza richiedere un dispositivo effettivamente chrome player. Per l’installazione, effettuate le seguenti operazioni:
>
>1. Clicca [qui](https://download.macromedia.com/screens/) per scaricare la versione più recente di Chrome Player.
>1. Decomprimete il file e salvatelo su disco.
>1. Aprite il browser Chrome e selezionate **Estensioni** dal menu oppure passate direttamente a ***chrome://extensions***.
>1. Attivate la modalità **** Sviluppatore dall&#39;angolo in alto a destra.
>1. Fare clic su **Carica non imballato** dall&#39;angolo in alto a sinistra e caricare Chrome Player decompresso.
>1. Controllare **plugin AEM Screens Chrome Player** se è disponibile nell&#39;elenco delle estensioni.
>1. Aprite una nuova scheda e fate clic sull&#39;icona **App** dall&#39;angolo in alto a sinistra oppure passate direttamente a ***chrome://apps***.
>1. Fate clic su **AEM Screens** Plugin per avviare Chrome Player. Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premere **esc** per uscire dalla modalità a schermo intero.


Una volta che il lettore Chrome OS è attivato, seguire i passaggi seguenti per registrare un dispositivo Chrome.

1. Andate alla cartella **Devices** del progetto dall&#39;istanza AEM.

1. Tap/click the **Device Manager** from the action bar.

   ![immagine](assets/kickstart/demo-register1.png)

1. Toccate/fate clic su Registrazione **** dispositivo in alto a destra.

1. Seleziona il dispositivo richiesto e tocca o fai clic su **Registra dispositivo**.

   ![immagine](assets/kickstart/demo-register2.png)

1. Attendi che il dispositivo invii il suo codice di registrazione e contemporaneamente, controlla il Codice **di** registrazione dal tuo dispositivo Chrome.
   ![immagine](assets/kickstart/demo-register3.png)

1. Se il codice **di** registrazione è lo stesso su entrambi i computer, toccate o fate clic su **Convalida** in AEM.

1. Impostate il nome desiderato come **ChromeDevice forDemo** per il dispositivo, quindi fate clic su **Register (Registra)**.

   ![immagine](assets/kickstart/demo-register4.png)

1. Fare clic su **Assegna visualizzazione** dalla finestra di dialogo Registrazione **dispositivo completata** .

   ![immagine](assets/kickstart/demo-register5.png)

1. Selezionare il percorso del display come **DemoScreens** —> **Locations** —> **TestLocation** —> **LobbyDisplay** e fare clic su **Assign**.

   ![immagine](assets/kickstart/demo-device6.png)

1. Una volta che il dispositivo è stato assegnato correttamente, verrà visualizzata la seguente conferma.

   ![immagine](assets/kickstart/demo-register8.png)

1. Tap/click **Finish** to complete the registration process.

1. Dovrebbe essere possibile visualizzare il dispositivo registrato dal dashboard di visualizzazione.

   ![immagine](assets/kickstart/demo-register9.png)

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

Tutte le risorse del canale ora vengono riprodotte sul lettore Chrome OS.

Congratulazioni! State ora riproducendo il contenuto in un canale AEM Screens !

![immagine](assets/kickstart/demo-video-screens.gif)






