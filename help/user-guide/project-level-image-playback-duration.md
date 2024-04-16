---
title: Durata riproduzione immagine a livello di progetto
description: Scopri come definire la durata di riproduzione delle immagini a livello di progetto.
contentOwner: jsyal
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 1%

---


# Durata riproduzione immagine a livello di progetto {#project-level-image-playback}

## Panoramica {#overview}

Questa funzione consente di definire la durata di riproduzione dell’immagine a livello di progetto. Per impostazione predefinita, tutte le immagini ereditano questa durata di riproduzione. Se a livello di progetto non è definita alcuna durata, la riproduzione predefinita di 8 secondi continua.

### Prerequisiti {#prerequisites}

Prima di utilizzare questa funzione, imposta un progetto come prerequisito per iniziare a implementarla. Ad esempio:

1. Crea un progetto AEM Screens (in questo esempio, **RiproduzioneLivelloProgetto**).
1. Crea un canale di sequenza come **PlayBackChannel** in **Canali** cartella.
1. Aggiungi contenuto a **PlayBackChannel**.

   ![risorse](assets/image_playback1.png)

   Ad esempio, l’immagine seguente mostra le immagini aggiunte al **PlayBackChannel** editor:

   ![risorse](assets/image_playback2.png)

## Modifica dell&#39;assegnazione della durata di riproduzione immagine a livello di progetto {#editing-project-level-image-playback-duration-assignment}

La sezione seguente spiega come modificare la durata di riproduzione del contenuto in un progetto AEM Screens.

### Aggiornamento della durata di riproduzione per le immagini a livello di progetto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Se desideri aggiornare la durata di riproduzione di un’immagine o a livello di canale, consulta [Durata riproduzione immagine a livello di canale](channel-level-image-playback.md).

Per informazioni su come aggiornare la durata di riproduzione delle immagini a livello di progetto, effettua le seguenti operazioni:

1. Passare al progetto **RiproduzioneLivelloProgetto** e fai clic su **Proprietà** dalla barra delle azioni.
   ![risorse](assets/image_playback3.png)

1. Fare clic su tutte le immagini del canale e fare clic sull&#39;icona chiave inglese in alto a sinistra (come illustrato nella figura riportata di seguito) per aprire la finestra di dialogo Configurazione a livello di canale.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. Il **Pagina** viene visualizzata.

   >[!NOTE]
   >
   >Per impostazione predefinita, le immagini in un canale sono impostate su una durata di riproduzione di 8 secondi e i video vengono riprodotti alla durata predefinita.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modifica il **Durata** da 8000 (millisecondi) a 3000 (millisecondi), ovvero 3 secondi. Seleziona il segno di spunta in alto a destra del **Pagina** in modo da salvare le modifiche.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualizzazione del risultato {#viewing-the-result}

Dopo aver aggiornato la durata di riproduzione del canale (in questo esempio, tutte e tre le immagini), le immagini vengono ora riprodotte per 3 secondi anziché 8 secondi (valore predefinito).

![channel_preview](assets/channel_preview.gif)

