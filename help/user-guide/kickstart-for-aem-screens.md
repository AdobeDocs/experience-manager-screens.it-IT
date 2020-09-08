---
title: Guida di Kickstart
seo-title: Guida di Kickstart
description: Segui questa pagina per creare una dimostrazione  progetto AEM Screens. Consente di creare un'esperienza di digital signage a partire dall'installazione e dalla configurazione di un nuovo progetto per la visualizzazione dei contenuti  lettore AEM Screens.
translation-type: tm+mt
source-git-commit: 78aab8e8ad8ad9e3a3caf20fef044f507b5298a0
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 6%

---


# Guida di Kickstart {#kickstart-guide}

Questa sezione rappresenta un punto di partenza per  AEM Screens e illustra come impostare ed eseguire un progetto AEM Screens . Consente di configurare un&#39;esperienza di digital signage di base e di aggiungere contenuti quali risorse e/o video a ogni canale e di pubblicare ulteriormente i contenuti su un lettore AEM Screens .

>[!NOTE]
>Prima di iniziare a lavorare sui dettagli del progetto, accertatevi di aver installato il Feature Pack più recente. È possibile scaricare l&#39;ultimo pacchetto di funzioni per  versione di AEM Screens 6.5.5 dal portale [di distribuzione](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) software utilizzando l&#39;Adobe ID .

## Creazione di un&#39;esperienza di digital signage in 5 minuti {#creating-a-digital-signage-experience-in-minutes}

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


## Esercitazione {#tutorial}

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

1. Navigate to the *DemoProject* you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the *TestChannel* opens.

   ![immagine](assets/kickstart/demo-6.png)

1. Fai clic sull’icona che apre o chiude il pannello laterale sinistro della barra delle azioni per aprire le risorse e i componenti.

1. Trascina i componenti da aggiungere al canale.

   ![immagine](assets/kickstart/demo-7.png)

### Creazione di una posizione{#creating-location} 

Una volta installato il canale, è necessario creare una posizione.

>[!NOTE]
>***Le posizioni*** consentono di compartimentare le diverse esperienze di digital signage e contengono le configurazioni dei display in base a dove si trovano i vari schermi.

Per creare una nuova posizione per il progetto, effettuate le seguenti operazioni:

1. Navigate to the *DemoProject* you created and select the **Locations** folder.

1. Click **+ Create** from the action bar.

1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** for your location (enter the title as *TestLocation*) and click **Create**.

Il *TestLocation* viene creato e aggiunto alla cartella **Locations** .


### Creazione di un display per la posizione {#creating-display}

Dopo aver creato un percorso, è necessario creare una nuova visualizzazione per il percorso.

>[!NOTE]
>***I display*** rappresentano l&#39;esperienza digitale che viene eseguita su uno o più schermi.

1. Andate a **TestLocation** e selezionatelo.

1. Fai clic su **Crea** nella barra delle azioni.

1. Select **Display** from the **Create** wizard and click **Next**.

1. Inserite il **Titolo** (*LobbyDisplay*).

1. Fai clic su **Crea**.

Nella posizione in cui si trova, viene aggiunto un nuovo display (*TestDisplay*) **, come illustrato nella figura riportata di seguito.

### Assigning a Channel {#assigning-channel}

1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.

1. Select *TestDisplay* and tap/click **Assign Channel** from the action bar, *Or*,

1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **Viene visualizzata la finestra di dialogo Assegnazione** canale.

1. Select **Reference Channel** by **path**

1. Enter the **Channel Role** as *LiveStream*.

1. Selezionate il percorso **del** canale (*Test_Project* —> *Channels* —> *TestChannel* ) nel **canale**.

1. Select the **Priority** for this channel as *1*.

1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.

1. Immettere **Schedule** e selezionare le date in **attivo da** e **attivo fino**.

1. Fai clic su **Salva**.

Il canale viene creato e aggiunto al pannello.



### Registrazione di un dispositivo {#registering-device}

È necessario registrare il dispositivo utilizzando il dashboard di AEM.

>[!NOTE]
>È possibile aprire il lettore Screens utilizzando l&#39;app AEM Screens  scaricata o utilizzando il browser Web.



### Viewing the content in AEM Screens Player {#viewing-the-content-in-screens-player}

Una volta aggiunte le configurazioni di cui sopra, il lettore deve mostrare automaticamente il canale predefinito per il display sul dispositivo.



Per informazioni dettagliate su  lettore AEM Screens, vedere [AEM Screens Player](working-with-screens-player.md) .
