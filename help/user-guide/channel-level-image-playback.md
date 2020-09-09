---
title: Durata della riproduzione di massa immagini a livello di canale
seo-title: Durata della riproduzione di massa immagini a livello di canale
description: Questa pagina descrive come modificare la durata di riproduzione di un componente immagine specifico.
seo-description: Questa pagina descrive come modificare la durata di riproduzione di un componente immagine specifico.
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 3%

---


# Durata della riproduzione di massa immagini a livello di canale {#channel-level-bulk-image-playback-duration}

## Panoramica {#overview}

Dopo aver creato un canale di sequenza e aggiunto le immagini, per impostazione predefinita tutte le immagini assumeranno la durata di riproduzione definita nella configurazione a livello di canale. Ogni singola immagine può comunque ignorare l’impostazione predefinita e avere una durata di riproduzione diversa, a tal fine è possibile modificare la durata di riproduzione del componente immagine specifico.

### Prerequisiti {#prerequisites}

Prima di iniziare ad implementare questa funzionalità, accertatevi di aver configurato un progetto come prerequisito per iniziare ad implementare questa funzionalità. Esempio,

1. Create un esempio di progetto AEM Screens , **ChannelLevelPlayback**.

1. Crea un canale di sequenza come **PlaybackChannel** nella cartella **Channels (Canali** ).

1. Aggiungere contenuto a **PlaybackChannel**.

## Modifica dell&#39;assegnazione durata riproduzione immagine a livello di canale {#editing-channel-level-image-playback-duration-assignment}

La sezione seguente spiega come modificare la durata di riproduzione del contenuto in un canale AEM Screens .

### Aggiornamento della durata di riproduzione per le immagini di un canale {#updating-the-playback-duration-for-images-in-a-channel}

Per informazioni su come aggiornare l’assegnazione durata di riproduzione delle immagini a livello di canale, effettuate le seguenti operazioni:

1. Passare al canale della sequenza **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Aggiungete due o più immagini nell’editor canale, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Selezionate tutte le immagini del canale e fate clic sull’icona chiave inglese in alto a sinistra (come illustrato nella figura riportata di seguito) per aprire la finestra di dialogo Configura a livello di canale.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Viene visualizzata la finestra di dialogo Pagina** .

   >[!NOTE]
   >Per impostazione predefinita, le immagini in un canale sono impostate su una durata di riproduzione di 8 secondi.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modificate la **durata** da 8000 (ms) a 3000 (ms), ossia 3 secondi. Fate clic sul segno di spunta in alto a destra della finestra di dialogo **Pagina** per salvare le modifiche.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualizzazione del risultato {#viewing-the-result}

Dopo aver aggiornato la durata di riproduzione del canale (in questo esempio, tutte e tre le immagini), noterete che le immagini verranno riprodotte per 3 secondi anziché 8 (valore predefinito).

![channel_preview](assets/channel_preview.gif)

