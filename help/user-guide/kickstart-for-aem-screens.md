---
title: Guida di Kickstart
seo-title: Guida di Kickstart
description: Segui questa pagina per creare una dimostrazione  progetto AEM Screens. Consente di creare un'esperienza di digital signage a partire dall'installazione e dalla configurazione di un nuovo progetto per la visualizzazione dei contenuti  lettore AEM Screens.
translation-type: tm+mt
source-git-commit: 77c81b84631b090333db0095986f634fa99c8223
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 5%

---


# Guida di Kickstart {#kickstart-guide}

Il kickstart to  AEM Screens illustra come impostare ed eseguire un progetto AEM Screens . Consente di configurare un&#39;esperienza di digital signage di base e di aggiungere contenuti quali risorse e/o video a ogni canale e di pubblicare ulteriormente i contenuti su un lettore AEM Screens .

>[!NOTE]
>Prima di iniziare a lavorare sui dettagli del progetto, accertatevi di aver installato l&#39;ultimo Feature Pack per  AEM Screens. È possibile scaricare l&#39;ultimo pacchetto di funzioni dal [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) utilizzando l&#39;Adobe ID .

## Prerequisiti {#prerequisites}

Seguite i passaggi riportati di seguito per creare un progetto di esempio per  AEM Screens e pubblicare ulteriormente il contenuto per il lettore Screens.

>[!NOTE]
>L&#39;esercitazione seguente mostra come riprodurre il contenuto del canale nel lettore Chrome OS.

>[!IMPORTANT]
>**Impostazioni di configurazione OSGi**
>È necessario abilitare il referente vuoto per consentire al dispositivo di inviare dati al server. Ad esempio, se la proprietà del referente vuoto è disabilitata, il dispositivo non può inviare una schermata indietro. Attualmente alcune di queste funzioni sono disponibili solo se Apache Sling Referrer Filter Allow Empty è abilitato nella configurazione OSGi. Il dashboard potrebbe visualizzare un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzioni.
>Seguite i passaggi riportati di seguito per attivare il filtro ***Apache Sling Referrer Filter Allow Empty***:


## Consenti richieste referente vuote {#allow-empty-referrer-requests}

1. Andate a **Configurazione della console Web Adobe Experience Manager** tramite AEM istanza —> icona del martello —> **Operazioni** —> **Console Web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Viene aperta la** configurazione della console Web di Adobe Experience Manager. Cerca referrer di fionda.

   Per eseguire la ricerca nella proprietà sling referrer, premere **Comando+F** per **Mac** e **Control+F** per **Windows**.

1. Selezionare l&#39;opzione **Consenti valori vuoti**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/empty-ref2.png)

1. Fate clic su **Salva** per abilitare l&#39;opzione Consenti valori nulli per il filtro di riferimento Apache Sling.

## Creazione di un&#39;esperienza di digital signage in 5 minuti {#creating-a-digital-signage-experience-in-minutes}

### Creazione di un progetto AEM Screens  {#creating-project}

Il primo passaggio consiste nel creare un progetto AEM Screens .

1. Andate all&#39;istanza Adobe Experience Manager (AEM) e fate clic su **Screens**. In alternativa, è possibile spostarsi direttamente da `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Fare clic su **Crea progetto Screens** per creare un nuovo progetto Screens. Immettete il titolo come **DemoScreens** e fate clic su **Save**.

   ![immagine](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Dopo aver creato il progetto, tornerai alla home page del progetto Screens. Ora puoi selezionare il progetto. In un progetto, sono presenti cinque cartelle diverse, denominate **Applicazioni**, **Canali**, **Dispositivi**, **Posizioni** e **Pianificazioni**.

### Creazione di un canale {#creating-channel}

Dopo aver creato il progetto AEM Screens , è necessario creare un nuovo canale in cui gestire il contenuto.

Per creare un nuovo canale per il progetto, effettuate le seguenti operazioni:

1. Dopo aver creato un progetto, selezionare il progetto **DemoScreens** e selezionare la cartella **Channels**, come illustrato nella figura seguente. Fare clic su **+ Crea** dalla barra delle azioni.

   ![immagine](assets/kickstart/demo-2.png)

1. Scegliere il **Canale sequenza** dalla procedura guidata e fare clic su **Avanti**.
   ![immagine](assets/kickstart/demo-3.png)

1. Immettete il **Titolo** come **TestChannel** e fate clic su **Crea**.

   ![immagine](assets/kickstart/demo-4.png)

   Il **TestChannel** viene ora aggiunto alla cartella dei canali, come illustrato nella figura riportata di seguito.

   ![immagine](assets/kickstart/demo-5.png)

### Aggiunta di contenuto a un canale {#adding-content}

Una volta installato il canale, è necessario aggiungere al canale il contenuto che  lettore AEM Screens visualizzerà.

Per aggiungere contenuto al canale (**TestChannel**) del progetto, effettuate le seguenti operazioni:

1. Andate alla **DemoProject** creata e selezionate la cartella **TestChannel** dalla cartella **Channels**.

1. Fare clic su **Modifica** dalla barra delle azioni (vedere la figura seguente). Viene aperto l&#39;editor per **TestChannel**.

   ![immagine](assets/kickstart/demo-6.png)

1. Fai clic sull’icona che apre o chiude il pannello laterale sinistro della barra delle azioni per aprire le risorse e i componenti.

1. Trascina i componenti da aggiungere al canale.

   ![immagine](assets/kickstart/demo-7.png)

### Creazione di una posizione{#creating-location} 

Una volta installato il canale, è necessario creare una posizione.

>[!NOTE]
>***Le posizioni*** consentono di compartimentare le diverse esperienze di digital signage e contengono le configurazioni dei display in base a dove si trovano i vari schermi.

Per creare una nuova posizione per il progetto, effettuate le seguenti operazioni:

1. Andate alla cartella **DemoProject** creata e selezionate la cartella **Locations**.

1. Fare clic su **+ Crea** dalla barra delle azioni.

1. Selezionare **Location** dalla procedura guidata e fare clic su **Next**.

1. Immettere il **Nome** della posizione (inserire il titolo come **TestLocation**) e fare clic su **Crea**.

La cartella **TestLocation** viene creata e aggiunta alla cartella **Locations**.


### Creazione di un display per la posizione {#creating-display}

Dopo aver creato un percorso, è necessario creare una nuova visualizzazione per il percorso.

>[!NOTE]
>***Display*** rappresenta l&#39;esperienza digitale che viene eseguita su uno o più schermi.

1. Accedete a **TestLocation** e selezionatelo.

1. Fai clic su **Crea** nella barra delle azioni.

   ![immagine](assets/kickstart/demo-disp1.png)

1. Selezionare **Display** dalla procedura guidata **Crea** e fare clic su **Next**.

   ![immagine](assets/kickstart/demo-disp2.png)

1. Immettete il **Titolo** come **VisualizzazioneLobby** e fate clic su **Crea**.

   ![immagine](assets/kickstart/demo-disp3.png)

   Nella posizione **TestDisplay** viene ora aggiunta una nuova visualizzazione denominata **TestDisplay**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/kickstart/demo-disp4.png)

### Assegnazione di un canale {#assigning-channel}

Una volta completata la configurazione del progetto, dovete assegnare il canale a uno schermo per visualizzare il contenuto.

1. Passare alla visualizzazione desiderata da **DemoScreens** —> **Locations** —> **TestLocation** —> **LobbyDisplay**.

1. Toccate/fate clic su **Assegna canale** dalla barra delle azioni.

   ![immagine](assets/kickstart/demo-assign1.png)

   Oppure,

   Toccate/fate clic su **Dashboard** nella barra delle azioni e fate clic su **+Assegna canale** nel pannello **CANALI ASSEGNATI &amp; PROGRAMMI**.

   ![immagine](assets/kickstart/demo-assign2.png)

1. Viene visualizzata la finestra di dialogo **Assegnazione canale**.

1. Dall&#39;opzione **Impostazioni**, scegliete il canale **per percorso** e **Eventi supportati** come **Carico iniziale** e **Schermo inattivo**.

   >[!NOTE]
   >
   >I **Ruolo canale**, **Priorità** e **Metodi di interruzione** sono tutti popolati per impostazione predefinita. Vedere la sezione [Proprietà canale](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) per ulteriori informazioni sulle proprietà di assegnazione dei canali.

   ![immagine](assets/kickstart/demo-assign3.png)

   Inoltre, è possibile selezionare la **finestra di attivazione** e la **programmazione ricorrenza**.

   >[!NOTE]
   >La *Pianificazione ricorrenza* consente di impostare una pianificazione periodica per il canale. Puoi impostare più pianificazioni di ricorrenza per un canale.
   >Per ulteriori informazioni, vedere [Programma di ricorrenza](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule).

1. Fare clic su **Salva** dopo aver configurato le preferenze.

### Registrazione di un dispositivo e assegnazione di un dispositivo a un display {#registering-device}

È necessario registrare il dispositivo utilizzando il dashboard di AEM.

>[!IMPORTANT]
>Il lettore Chrome OS può essere installato come il plugin Chrome Browser in modalità sviluppatore senza richiedere un dispositivo effettivamente chrome player. Per l’installazione, effettuate le seguenti operazioni:
>
>1. Fare clic [qui](https://download.macromedia.com/screens/) per scaricare il lettore Chrome più recente.
>1. Decomprimete il file e salvatelo su disco.
>1. Aprite il browser Chrome e selezionate **Estensioni** dal menu oppure andate direttamente a ***chrome://extensions***.
>1. Accendere la **Modalità Sviluppatore** dall&#39;angolo in alto a destra.
>1. Fare clic su **Carica non imballato** dall&#39;angolo in alto a sinistra e caricare il lettore Chrome decompresso.
>1. Controllare il plug-in **AEM Screens Chrome Player** se disponibile nell&#39;elenco delle estensioni.
>1. Aprite una nuova scheda e fate clic sull&#39;icona **App** dall&#39;angolo in alto a sinistra oppure andate direttamente a ***chrome://apps***.
>1. Fare clic su **AEM Screens** Plugin per avviare Chrome Player. Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premere **esc** per uscire dalla modalità a schermo intero.


Una volta che il lettore Chrome OS è attivato, seguire i passaggi seguenti per registrare un dispositivo Chrome.

1. Andate alla cartella **Devices** del progetto dall&#39;istanza AEM.

1. Toccate/fate clic su **Device Manager** dalla barra delle azioni.

   ![immagine](assets/kickstart/demo-register1.png)

1. Toccate/fate clic su **Registrazione dispositivo** in alto a destra.

1. Seleziona il dispositivo richiesto e tocca o fai clic su **Registra dispositivo**.

   ![immagine](assets/kickstart/demo-register2.png)

1. Attendete che il dispositivo invii il suo codice di registrazione e controllare simultaneamente il **Codice di registrazione** dal dispositivo Chrome.
   ![immagine](assets/kickstart/demo-register3.png)

1. Se il **Codice di registrazione** è lo stesso su entrambi i computer, toccare/fare clic su **Validate** in AEM.

1. Impostate il nome desiderato come **ChromeDevice forDemo** per il dispositivo, quindi fate clic su **Register**.

   ![immagine](assets/kickstart/demo-register4.png)

1. Fare clic su **Assegna visualizzazione** nella finestra di dialogo **Registrazione dispositivo completata**.

   ![immagine](assets/kickstart/demo-register5.png)

1. Selezionare il percorso del display come **DemoScreens** —> **Locations** —> **TestLocation** —> **LobbyDisplay** e fare clic su **Assign**.

   ![immagine](assets/kickstart/demo-device6.png)

1. Una volta che il dispositivo è stato assegnato correttamente, verrà visualizzata la seguente conferma.

   ![immagine](assets/kickstart/demo-register8.png)

1. Toccate/fate clic su **Fine** per completare il processo di registrazione. Dovrebbe essere possibile visualizzare il dispositivo registrato dal dashboard di visualizzazione.

   ![immagine](assets/kickstart/demo-register9.png)

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

Tutte le risorse del canale ora vengono riprodotte sul lettore Chrome OS.

Congratulazioni! State ora riproducendo il contenuto in un canale AEM Screens !

![immagine](assets/kickstart/demo-video-screens.gif)
