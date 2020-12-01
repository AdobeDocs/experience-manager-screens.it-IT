---
title: Durata riproduzione immagine a livello di progetto
seo-title: Durata riproduzione immagine a livello di progetto
description: 'Questa funzionalità consente di definire la durata di riproduzione delle immagini a livello di progetto. '
seo-description: 'Questa funzionalità consente di definire la durata di riproduzione delle immagini a livello di progetto. '
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# Durata riproduzione immagine a livello di progetto {#project-level-image-playback}

## Panoramica {#overview}

Questa funzione consente di definire la durata di riproduzione delle immagini a livello di progetto. Per impostazione predefinita, tutte le immagini ereditano questa durata di riproduzione. Se non viene definita alcuna durata a livello di progetto, la riproduzione predefinita di 8 secondi continuerà.

### Prerequisiti {#prerequisites}

Prima di utilizzare questa funzione, accertatevi di configurare un progetto come prerequisito per iniziare ad implementare questa funzionalità. Esempio,

1. Creare un progetto AEM Screens  (in questo esempio, **ProjectLevelPlayback**)

1. Creare un canale di sequenza come **PlayBackChannel** nella cartella **Channels**

1. Aggiungere contenuto a **PlayBackChannel**

   ![assets](assets/image_playback1.png)

   Ad esempio, l&#39;immagine seguente mostra le immagini aggiunte all&#39;editor **PlayBackChannel**:

   ![assets](assets/image_playback2.png)

## Modifica dell&#39;assegnazione della durata di riproduzione dell&#39;immagine a livello di progetto {#editing-project-level-image-playback-duration-assignment}

La sezione seguente spiega come modificare la durata di riproduzione del contenuto in un progetto AEM Screens .

### Aggiornamento della durata di riproduzione per le immagini a livello di progetto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Per aggiornare la durata di riproduzione a livello di immagine o canale, fare riferimento a [Durata di riproduzione a livello di canale](channel-level-image-playback.md).

Per informazioni su come aggiornare la durata di riproduzione delle immagini a livello di progetto, effettuate le seguenti operazioni:

1. Andate al progetto **ProjectLevelPlayback** e fate clic su **Properties** dalla barra delle azioni.
   ![assets](assets/image_playback3.png)

1. Selezionate tutte le immagini del canale e fate clic sull’icona chiave inglese in alto a sinistra (come illustrato nella figura riportata di seguito) per aprire la finestra di dialogo Configura a livello di canale.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Viene visualizzata la finestra di dialogo** Pagefinestra di dialogo.

   >[!NOTE]
   >
   >Per impostazione predefinita, le immagini in un canale sono impostate su una durata di riproduzione di 8 secondi e i video vengono riprodotti alla durata predefinita.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modificate la **Durata** da 8000 (ms) a 3000 (ms), ossia 3 secondi. Fare clic sul segno di spunta in alto a destra della finestra di dialogo **Pagina** per salvare le modifiche.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualizzazione del risultato {#viewing-the-result}

Dopo aver aggiornato la durata di riproduzione del canale (in questo esempio, tutte e tre le immagini), noterete che le immagini verranno riprodotte per 3 secondi anziché 8 (valore predefinito).

![channel_preview](assets/channel_preview.gif)

