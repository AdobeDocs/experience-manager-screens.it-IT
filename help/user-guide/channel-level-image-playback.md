---
title: Durata riproduzione immagine in blocco a livello di canale
description: Scopri come modificare la durata di riproduzione di un componente immagine specifico in AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
source-git-commit: 8a914d4b0237c327b7954c936c84a2c1aa719603
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# Durata riproduzione immagine in blocco a livello di canale {#channel-level-bulk-image-playback-duration}

## Panoramica {#overview}

Quando create un canale di sequenza e aggiungete immagini ad esso, per impostazione predefinita, tutte le immagini assumono la durata di riproduzione definita nella configurazione a livello di canale. Qualsiasi singola immagine può comunque ignorare l’impostazione predefinita e avere una durata di riproduzione diversa. Questa funzionalità viene eseguita modificando la durata di riproduzione del componente immagine specifico.

### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, assicurati di aver impostato un progetto come prerequisito per iniziare a implementarla. Ad esempio:

1. Crea un esempio di progetto AEM Screens, **ChannelLevelPlayback**.

1. Crea un canale di sequenza come **PlaybackChannel** nella cartella **Channels**.

1. Aggiungi contenuto a **PlaybackChannel**.

## Modifica dell&#39;assegnazione della durata di riproduzione immagine a livello di canale {#editing-channel-level-image-playback-duration-assignment}

La sezione seguente spiega come modificare la durata di riproduzione dei contenuti in un canale AEM Screens.

### Aggiornamento della durata di riproduzione per le immagini in un canale {#updating-the-playback-duration-for-images-in-a-channel}

Segui i passaggi seguenti per scoprire come aggiornare l’assegnazione della durata di riproduzione dell’immagine a livello di canale:

1. Passare al canale di sequenza **PlaybackChannel**.

   ![schermata_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Fai clic su **Modifica** nella barra delle azioni.

   ![schermata_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Aggiungi due o più immagini nell’editor canali, come illustrato nella figura riportata di seguito.

   ![schermata_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Fare clic su tutte le immagini del canale e fare clic sull&#39;icona chiave inglese in alto a sinistra (come illustrato nella figura riportata di seguito) per aprire la finestra di dialogo Configurazione a livello di canale.

   ![schermata_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. Viene visualizzata la finestra di dialogo **Pagina**.

   >[!NOTE]
   >Per impostazione predefinita, le immagini in un canale sono impostate su una durata di riproduzione di 8 secondi.

   ![schermata_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modifica la **Durata** da 8000 (millisecondi) a 3000 (millisecondi), ovvero 3 secondi. Fai clic sul segno di spunta in alto a destra nella finestra di dialogo **Pagina** per salvare le modifiche.

   ![schermata_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualizzazione del risultato {#viewing-the-result}

Dopo aver aggiornato la durata di riproduzione del canale (in questo esempio, tutte e tre le immagini), le immagini vengono ora riprodotte per 3 secondi anziché 8 secondi (valore predefinito).

![channel_preview](assets/channel_preview.gif)
