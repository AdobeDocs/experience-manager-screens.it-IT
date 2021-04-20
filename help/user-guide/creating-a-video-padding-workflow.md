---
title: Creazione di un flusso di lavoro di spaziatura video
seo-title: Creazione di un flusso di lavoro di spaziatura video
description: Segui questa pagina per scoprire come creare una spaziatura video nel flusso di lavoro per le risorse.
seo-description: Segui questa pagina per scoprire come creare una spaziatura video nel flusso di lavoro per le risorse.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# Creazione di un flusso di lavoro di spaziatura video {#creating-a-video-padding-workflow}

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Prerequisiti**
* **Creazione di un flusso di lavoro di spaziatura video**
   * **Creazione di un flusso di lavoro**
   * **Utilizzo del flusso di lavoro nel progetto AEM Screens**

* **Convalida dell’output per il flusso di lavoro**

## Panoramica {#overview}

Il seguente caso d’uso prevede il posizionamento di un video (ad esempio: 1280 x 720) in un canale in cui il display è 1920 x 1080 e il video deve essere posizionato a 0x0 (in alto a sinistra). Il video non deve essere esteso o modificato in alcun modo e non utilizzare **Copertura** nel componente video.

Il video verrà visualizzato come un oggetto da pixel 1 a pixel 1280 attraverso e da pixel 1 a pixel 720 verso il basso e il resto del canale sarà colore predefinito.

## Prerequisiti {#prerequisites}

Prima di creare un flusso di lavoro per i video, completa i seguenti prerequisiti:

1. Carica un video nella cartella **Risorse** nella tua istanza AEM
1. Crea un progetto AEM Screens (ad esempio, **TestVideoRendition**) e un canale denominato (**VideoRendering**), come illustrato nella figura seguente:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Creazione di un flusso di lavoro di spaziatura video {#creating-a-video-padding-workflow-1}

Per creare un flusso di lavoro di spaziatura video, devi creare un flusso di lavoro per il video e quindi utilizzarlo nello stesso modo nel canale di progetto AEM Screens.

Per creare e utilizzare il flusso di lavoro, effettua le seguenti operazioni:

1. Creazione di un flusso di lavoro
1. Utilizzo del flusso di lavoro in un progetto AEM Screens

### Creazione di un flusso di lavoro {#creating-a-workflow}

Per creare un flusso di lavoro per il video, effettua le seguenti operazioni:

1. Passa all’istanza AEM e fai clic su strumenti dalla barra laterale. Seleziona **Flusso di lavoro** —> **Modelli** per creare un nuovo modello.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Fai clic su **Modelli** —> **Crea** —> **Crea modello**. Inserisci i valori **Titolo** (come **VideoRendition**) e **Nome** in **Aggiungi modello flusso di lavoro**. Fai clic su **Fine** per aggiungere il modello di flusso di lavoro.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Una volta creato il modello di flusso di lavoro, seleziona il modello (**VideoRendition**) e fai clic su **Modifica** nella barra delle azioni.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Trascina il componente **Riga di comando** nel flusso di lavoro.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Seleziona il componente **Riga di comando** e apri la finestra di dialogo delle proprietà.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Selezionare la scheda **Argomenti** per immettere i campi nella finestra di dialogo **Riga di comando - Proprietà passaggio**.

   Inserisci il formato in **Tipi MIME** (come ***video/mp4***) e il comando come (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cf q5dam.video.fullhd-hp.mp4**) per avviare il flusso di lavoro nel campo **Comandi** .

   Fai riferimento ai dettagli su **Tipi di MIME** e **Comandi** nella nota seguente.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Seleziona il flusso di lavoro (**VideoRenditions**) e fai clic su **Avvia flusso di lavoro** nella barra delle azioni per aprire la finestra di dialogo **Esegui flusso di lavoro** .

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Seleziona il percorso della risorsa nel **Payload** (come ***/content/dam/huseinpeyda-crosspaths01_512kb 2.mp4***) e immetti il **Titolo** come ***EseguiVideo*** e fai clic su **Esegui&lt;a 9/>.**

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Utilizzo del flusso di lavoro in un progetto AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Per utilizzare il flusso di lavoro nel progetto AEM Screens, effettua le seguenti operazioni:

1. Passa a un progetto AEM Screens (**TestVideoRendition** —> **Canali** —>**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Fai clic su **Modifica** nella barra delle azioni. Trascina e rilascia il video inizialmente caricato in **Risorse**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Dopo aver caricato il video, fai clic su **Anteprima** per visualizzare l&#39;output.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Convalida dell&#39;output per il flusso di lavoro {#validating-the-output-for-the-workflow}

Puoi convalidare l’output tramite:

* Controlla l&#39;anteprima del video nel canale
* Passa a ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** in CRXDE Lite, come illustrato nella figura seguente:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

