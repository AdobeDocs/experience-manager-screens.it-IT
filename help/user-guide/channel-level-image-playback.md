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
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Durata riproduzione immagine in blocco a livello di canale {#channel-level-bulk-image-playback-duration}

## Panoramica {#overview}

Quando create un canale di sequenza e aggiungete immagini ad esso, per impostazione predefinita, tutte le immagini assumono la durata di riproduzione definita nella configurazione a livello di canale. Ogni singola immagine può comunque ignorare l’impostazione predefinita e avere una durata di riproduzione diversa; questa operazione viene eseguita modificando la durata di riproduzione del componente immagine specifico.

### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, assicurati di aver impostato un progetto come prerequisito per iniziare a implementarla. Ad esempio:

1. Esempio di creazione di un progetto AEM Screens **ChannelLevelPlayback**.

1. Crea un canale di sequenza come **PlaybackChannel** in **Canali** cartella.

1. Aggiungi contenuto a **PlaybackChannel**.

## Modifica dell&#39;assegnazione della durata di riproduzione immagine a livello di canale {#editing-channel-level-image-playback-duration-assignment}

La sezione seguente spiega come modificare la durata di riproduzione dei contenuti in un canale AEM Screens.

### Aggiornamento della durata di riproduzione per le immagini in un canale {#updating-the-playback-duration-for-images-in-a-channel}

Segui i passaggi seguenti per scoprire come aggiornare l’assegnazione della durata di riproduzione dell’immagine a livello di canale:

1. Passa al canale della sequenza **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Seleziona **Modifica** dalla barra delle azioni.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Aggiungi due o più immagini nell’editor canali, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Selezionate tutte le immagini nel canale e l&#39;icona chiave inglese in alto a sinistra (come mostrato nella figura riportata di seguito) per aprire la finestra di dialogo Configurazione a livello di canale.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. Il **Pagina** viene visualizzata.

   >[!NOTE]
   >Per impostazione predefinita, le immagini in un canale sono impostate su una durata di riproduzione di 8 secondi.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modifica il **Durata** da 8000 (millisecondi) a 3000 (millisecondi), ovvero 3 secondi. Seleziona il segno di spunta in alto a destra del **Pagina** in modo da poter salvare le modifiche.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualizzazione del risultato {#viewing-the-result}

Dopo aver aggiornato la durata di riproduzione del canale (in questo esempio, tutte e tre le immagini), le immagini vengono ora riprodotte per 3 secondi anziché 8 secondi (valore predefinito).

![channel_preview](assets/channel_preview.gif)
