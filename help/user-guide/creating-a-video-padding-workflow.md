---
title: Creazione di un flusso di lavoro di spaziatura video
seo-title: Creazione di un flusso di lavoro di spaziatura video
description: Per informazioni su come creare una spaziatura video nel flusso di lavoro per le risorse, seguite questa pagina.
seo-description: Per informazioni su come creare una spaziatura video nel flusso di lavoro per le risorse, seguite questa pagina.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Creazione di un flusso di lavoro di spaziatura video {#creating-a-video-padding-workflow}

Questa sezione illustra i seguenti argomenti:

* **Panoramica**
* **Prerequisiti**
* **Creazione di un flusso di lavoro di spaziatura video**
   * **Creazione di un flusso di lavoro**
   * **Utilizzo del flusso di lavoro in AEM Screens Project**

* **Convalida dell'output per il flusso di lavoro**

## Panoramica {#overview}

Il seguente caso d’uso prevede l’inserimento di un video (ad esempio: 1280 x 720) in un canale in cui il display è 1920 x 1080 e il video è collocato a 0x0 (in alto a sinistra). Il video non deve essere allungato o modificato in alcun modo e non utilizza la **copertina** nel componente video.

Il video verrà visualizzato come un oggetto da pixel 1 a pixel 1280 attraverso e da pixel 1 a pixel 720 verso il basso e il resto del canale sarà il colore predefinito.

## Prerequisiti {#prerequisites}

Prima di creare un flusso di lavoro per i video, completate i seguenti prerequisiti:

1. Caricare un video nella cartella **Risorse** nell’istanza di AEM
1. Create un progetto AEM Screens (ad esempio, **TestVideoRendition**) e un canale denominato (**VideoRendering**), come illustrato nella figura seguente:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Creazione di un flusso di lavoro di spaziatura video {#creating-a-video-padding-workflow-1}

Per creare un flusso di lavoro di spaziatura video, dovete creare un flusso di lavoro per il video e quindi usare lo stesso per il canale di progetto AEM Screens.

Per creare e utilizzare il flusso di lavoro, effettuate le operazioni seguenti:

1. Creazione di un flusso di lavoro
1. Utilizzo del flusso di lavoro in un progetto AEM Screens

### Creazione di un flusso di lavoro {#creating-a-workflow}

Per creare un flusso di lavoro per il video, effettuate le seguenti operazioni:

1. Andate all’istanza di AEM e fate clic sugli strumenti dalla barra laterale. Selezionare **Workflow** —&gt; **Modelli** per creare un nuovo modello.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Fare clic su **Modelli** —&gt; **Crea** —&gt; **Crea modello**. Immettete il **Titolo** (come **VideoRendition**) e il **Nome** nel modello **** Aggiungi flusso di lavoro. Fate clic su **Fine** per aggiungere il modello di workflow.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Dopo aver creato il modello di workflow, selezionate il modello (**VideoRendition**), quindi fate clic su **Modifica** nella barra delle azioni.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Trascinare il componente **Command Line **nel flusso di lavoro.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Selezionare il componente **Riga** di comando e aprire la finestra di dialogo delle proprietà.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Selezionare la scheda **Argomenti** per immettere i campi nella finestra di dialogo Riga di **comando - Proprietà** passaggio.

   Immettete il formato in Tipi **** mime (come ***video/mp4***) e il comando come (***/usr/local/Cellar/ffmpeg -i ${nomefile} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.fullhd p.mp4***) per avviare il flusso di lavoro nel campo **Comandi** .

   Fare riferimento ai dettagli su **Mime Types** and **Commands** nella nota seguente.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Selezionate il flusso di lavoro (**VideoRenditions**) e fate clic su **Avvia flusso di lavoro** dalla barra delle azioni per aprire la finestra di dialogo **Esegui flusso di lavoro** .

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Selezionate il percorso della risorsa nel **payload** (come ***/content/dam/huseinpeyda-crossways01_512kb 2.mp4***), immettete il **Title **(as ***RunVideo***) e fate clic su **Run**(Esegui).

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Utilizzo del flusso di lavoro in un progetto AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Per usare il flusso di lavoro nel progetto AEM Screens, procedi come segue:

1. Passa a un progetto AEM Screens (**TestVideoRendition** —&gt; **Canali** —&gt;**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. Trascinate e rilasciate il video inizialmente caricato nelle **risorse**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Dopo aver caricato il video, fate clic su **Anteprima** per visualizzare l’output.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Convalida dell'output per il flusso di lavoro {#validating-the-output-for-the-workflow}

Puoi convalidare l’output tramite:

* Controllare l'anteprima del video nel canale
* Andate a ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** in CRXDE Lite, come illustrato nella figura seguente:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

