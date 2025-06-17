---
title: Creazione di un flusso di lavoro di spaziatura video
description: Ulteriori informazioni sulla creazione di una spaziatura video nel flusso di lavoro per le risorse.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Creazione di un flusso di lavoro di spaziatura video {#creating-a-video-padding-workflow}

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Prerequisiti**
* **Creazione di un flusso di lavoro di spaziatura video**
   * **Creazione di un flusso di lavoro**
   * **Utilizzo del flusso di lavoro in AEM Screens Project**

* **Convalida dell&#39;output per il flusso di lavoro**

## Panoramica {#overview}

Il seguente caso d’uso prevede il posizionamento di un video (ad esempio: 1280 x 720) in un canale in cui il display è 1920 x 1080 e il posizionamento del video su 0x0 (in alto a sinistra). Il video non deve essere allungato o modificato in alcun modo e non utilizzare **Copertina** nel componente video.

Il video viene visualizzato come un oggetto da pixel 1 a pixel 1280 in e da pixel 1 a pixel 720 in giù. Il resto del canale è il colore predefinito.

## Prerequisiti {#prerequisites}

Prima di creare un flusso di lavoro per i video, completa i seguenti prerequisiti:

1. Carica un video nella cartella **Assets** nella tua istanza di AEM
1. Crea un progetto AEM Screens (ad esempio, **TestVideoRendition**) e un canale denominato (**VideoRendering**), come illustrato nella figura seguente:

![schermata_shot_2018-10-17alle85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Creazione di un flusso di lavoro di spaziatura video {#creating-a-video-padding-workflow-1}

Per creare un flusso di lavoro per la spaziatura video, crea un flusso di lavoro per il video e quindi utilizza lo stesso nel canale del progetto AEM Screens.

Per creare e utilizzare il flusso di lavoro, segui i passaggi seguenti:

1. Creazione di un flusso di lavoro
1. Utilizzo del flusso di lavoro in un progetto AEM Screens

### Creazione di un flusso di lavoro {#creating-a-workflow}

Per creare un flusso di lavoro per il video, effettua le seguenti operazioni:

1. Passa all’istanza di AEM.
1. Fate clic sugli strumenti nella barra laterale.
1. Fai clic su **Flusso di lavoro** > **Modelli** per creare un modello.

   ![schermata_shot_2018-10-17alle90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Fai clic su **Modelli** > **Crea** > **Crea modello**. Immetti il **Titolo** (ad esempio **VideoRendition**) e il **Nome** nel **Aggiungi modello flusso di lavoro**. Fai clic su **Fine** per aggiungere il modello di flusso di lavoro.

   ![schermata_shot_2018-10-17alle90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Dopo aver creato il modello di flusso di lavoro, fare clic sul modello (**VideoRendition**) e quindi su **Modifica** nella barra delle azioni.

   ![schermata_shot_2018-10-17alle91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Trascina il componente **`Command Line`** nel flusso di lavoro.

   ![schermata_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Fare clic sul componente **`Command Line`** e aprire la finestra di dialogo delle proprietà.

   ![schermata_shot_2018-10-17alle95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Fare clic sulla scheda **Argomenti**.
1. Nella finestra di dialogo **Riga di comando - Proprietà passaggio**, immettere il formato in **Tipi Mime** (come ***video/mp4***) e il comando come (***`/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.fullhd-hp.mp4`***). Questo comando avvia il flusso di lavoro nel campo **Comandi**.

   Vedi i dettagli su **Tipi Mime** e **Comandi** nella nota seguente.

   ![schermata_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Fai clic sul flusso di lavoro (**VideoRenditions**).
1. Fare clic su **Avvia flusso di lavoro** nella barra delle azioni.

   ![schermata_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Nella finestra di dialogo **Esegui flusso di lavoro**, fai clic sul percorso della risorsa nel **Payload** (come ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***) e immetti il **Titolo** come ***EseguiVideo*** e fai clic su **Esegui**.

   ![schermata_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Utilizzo del flusso di lavoro in un progetto AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Per utilizzare il flusso di lavoro nel progetto AEM Screens, segui i passaggi seguenti:

1. Passa a un progetto AEM Screens (**TestVideoRendition** > **Canali** >**VideoRendition**).

   ![schermata_shot_2018-10-17alle100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Fai clic su **Modifica** nella barra delle azioni. Trascina e rilascia il video caricato inizialmente in **Assets**.

   ![schermata_shot_2018-10-17alle102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Dopo aver caricato il video, fai clic su **Anteprima** per visualizzare l&#39;output.

   ![schermata_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Convalida dell’output per il flusso di lavoro {#validating-the-output-for-the-workflow}

Per convalidare l’output:

* Controlla un&#39;anteprima del video nel canale
* Passa a ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** in CRXDE Lite, come illustrato nella figura seguente:

![schermata_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
