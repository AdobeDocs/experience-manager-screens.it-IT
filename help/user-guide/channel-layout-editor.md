---
title: Editor layout canale
seo-title: Editor layout canale
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 81490abc-58cf-4daa-93d6-d697f7495232
contentOwner: jsyal
discoiquuid: 10beb13e-d8b2-440e-b2b0-d9fc2dafdc26
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Editor layout canale {#channel-layout-editor}

***L’editor del layout del canale*** consente di creare più aree contenuto e utilizzare varietà di risorse, quali video, immagini e testo che possono essere combinate in un unico schermo in modi contestuali. È possibile estrarre immagini, video e testi e combinarli per creare un'esperienza digitale intuitiva e interattiva. 

In base ai requisiti del progetto, talvolta è necessario disporre di più aree in un canale e modificarle come un’unica unità. Ad esempio, una sequenza del prodotto con il relativo feed social media in esecuzione in tre aree distinte su un singolo canale.

## Panoramica {#overview}

Durante la creazione di un canale, puoi utilizzare modelli diversi per creare le aree del canale. Puoi aggiungere un’immagine, un video o un canale incorporato per sfruttare i contenuti in base alle esigenze del progetto.

### Descrizione di un caso d’uso {#use-case-description}

Il seguente esempio di utilizzo descrive la creazione di più aree in un canale.

1. ***Creazione di un progetto Screens***

   1. Seleziona il collegamento all’Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
   1. Click **Create** to create a new Screens project.
   1. Select **Screens** from the **Create Screens Project** wizard and click **Next**.
   1. Enter the title as **Channel Layout Project** and click **Create**.
   ![ch1](assets/ch1.gif)

1. ***Creazione di un canale***

   1. Navigate to **Channel Layout Project**.
   1. Fai clic su **Crea** nella barra delle azioni. Si apre una procedura guidata.
   1. Choose the **1x2 Split Screen Channel** and click **Next**.
   1. Enter the **Title** as **Split horizontal** and click **Create**.
   ![cannella](assets/channelcreation.gif)

1. ***Aggiungere contenuti al canale***

   1. Navigate to the **Channel Layout Project** you created and select the channel (**Split Channel**).
   1. Click **Edit** from the action bar and the editor for the **Split Channel** opens.
   1. Fai clic sull’icona che apre o chiude il pannello laterale sinistro della barra delle azioni per aprire le risorse e i componenti. Trascina i componenti da aggiungere al canale.
   ![ch4](assets/ch4.gif)

   >[!NOTE]
   >
   >Ad esempio, le due immagini seguenti sono aggiunte al canale nell'editor.

   ![screen_shot_2018-02-08at123635pm](assets/screen_shot_2018-02-08at123635pm.png)

1. ***Creazione di una posizione***

   1. Navigate to the Locations folder where you want to create your display (**Channel Layout Project**--&gt; **Locations**).
   1. Fai clic su **Crea** nella barra delle azioni.
   1. Select **Location** from the **Create** wizard and click **Next**.
   1. Enter **Title** for your location as **San Jose**.
   1. Fai clic su **Crea**. 
   ![ch5](assets/ch5.gif)

1. ***Creazione di una nuova visualizzazione***

   1. Navigate to the location where you want to create your display (**Acme** --&gt; **Locations** --&gt; **San Jose**) and select **San Jose**.
   1. Fai clic su **Crea** nella barra delle azioni. Select **Display** from the **Create** wizard and click **Next**.
   1. Enter **Title** for your display location (enter the title as **Split Display)**.
   1. Under the **Display** tab, choose the details of the Layout. Choose the **Resolution** as **Full HD**. Choose the **Number of Devices Horizontally** as 1 and the **Number of Devices Vertically** as **1**.
   1. Fai clic su **Crea**. 
   ![ch6](assets/ch6.gif)

1. ***Assegnazione di un canale***

   1. Navigate to the display from **Channel Layout Project** --&gt; **Locations** --&gt; **San Jose** --&gt; **Split Display**.
   1. Select **Split Display** and tap/click **Assign Channel** from the action bar, Or,
   1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel. **Viene visualizzata la finestra di dialogo Assegnazione** canale.
   1. Enter the **Channel Role** as **Split**.
   1. Select **Reference Channel** by path. Select the channel folder path (**Channel Layout Project** --&gt; **Channels** --&gt; **Split horizontal**) in the Channel.
   1. Select the **Priority** for this channel as **1**.
   1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Fai clic su **Salva**.
   ![ch7](assets/ch7.gif)

1. ***Registrazione e assegnazione del dispositivo***

   1. Avvia una finestra separata del browser. Andate al lettore Screens utilizzando il browser Web o avviate l'app AEM Screens.
   1. Una volta aperto il dispositivo, vedrai che lo stato del dispositivo è non registrato. From the AEM dashboard, navigate to **Channel Layout Project** --&gt; **Devices**.
   1. Click **Device Manager** from the action bar.
   1. Click **Device Registration** and you will see the pending devices. Select the device you want to register and click **Register Device**.
   1. Dovrai convalidare il codice di verifica dal browser web o da AEM Screens Player. Click **Validate** to navigate to **Device Registration** screen.
   1. Enter Title as **NewD** and click **Register** and the device will be registered.
   1. Click **Assign Display** to move on to the next step where you assign the device to a display.
   1. Fate clic su Assegna dispositivo e selezionate il percorso di visualizzazione per il canale () come /content/screens/Test_Project/Locations/TestLocation/TestDisplay. Click **Assign**.
   1. Click **Finish** to complete the process, and now the device is assigned.
   ![ch8](assets/ch8.gif)

#### Visualizzazione del contenuto in AEM Screens Player {#viewing-content-in-aem-screens-player}

Carica AEM Screens Player oppure utilizza il browser web. Noterai il contenuto del canale visualizzato in Screens Player. Il contenuto viene visualizzato come modello del canale in modalità schermo diviso 1x2.

![](do-not-localize/screen_shot_2018-02-08at123648pm.png)

### Inferenza {#inference}

L’utilizzo dei modelli disponibili durante la creazione di un canale, consente di sfruttare e visualizzare il contenuto in aree diverse. L’esempio qui sopra mostra il caso d’utilizzo per il modello 2x2.

Le immagini seguenti mostrano il layout a cui è possibile accedere tramite i diversi modelli.
