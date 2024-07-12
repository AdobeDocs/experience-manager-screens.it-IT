---
title: Durata riproduzione immagine a livello di progetto
description: Scopri come definire la durata di riproduzione delle immagini a livello di progetto.
contentOwner: jsyal
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# Durata riproduzione immagine a livello di progetto {#project-level-image-playback}

## Panoramica {#overview}

Questa funzione consente di definire la durata di riproduzione dell’immagine a livello di progetto. Per impostazione predefinita, tutte le immagini ereditano questa durata di riproduzione. Se a livello di progetto non è definita alcuna durata, la riproduzione predefinita di 8 secondi continua.

### Prerequisiti {#prerequisites}

Prima di utilizzare questa funzione, imposta un progetto come prerequisito per iniziare a implementarla. Ad esempio:

1. Crea un progetto AEM Screens (in questo esempio, **RiproduzioneLivelloProgetto**).
1. Crea un canale di sequenza come **PlayBackChannel** nella cartella **Channels**.
1. Aggiungi contenuto a **PlayBackChannel**.

   ![risorse](assets/image_playback1.png)

   Ad esempio, nell&#39;immagine seguente sono illustrate le immagini aggiunte all&#39;editor **PlayBackChannel**:

   ![risorse](assets/image_playback2.png)

## Modifica dell&#39;assegnazione della durata di riproduzione immagine a livello di progetto {#editing-project-level-image-playback-duration-assignment}

La sezione seguente spiega come modificare la durata di riproduzione del contenuto in un progetto AEM Screens.

### Aggiornamento della durata di riproduzione per le immagini a livello di progetto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Se desideri aggiornare la durata di riproduzione di un&#39;immagine o a livello di canale, consulta [Durata di riproduzione immagine a livello di canale](channel-level-image-playback.md).

Per informazioni su come aggiornare la durata di riproduzione delle immagini a livello di progetto, effettua le seguenti operazioni:

1. Passa al progetto **RiproduzioneLivelloProgetto** e fai clic su **Proprietà** nella barra delle azioni.
   ![risorse](assets/image_playback3.png)

1. Fare clic su tutte le immagini del canale e fare clic sull&#39;icona chiave inglese in alto a sinistra (come illustrato nella figura riportata di seguito) per aprire la finestra di dialogo Configurazione a livello di canale.

   ![schermata_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. Viene visualizzata la finestra di dialogo **Pagina**.

   >[!NOTE]
   >
   >Per impostazione predefinita, le immagini in un canale sono impostate su una durata di riproduzione di 8 secondi e i video vengono riprodotti alla durata predefinita.

   ![schermata_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modifica la **Durata** da 8000 (millisecondi) a 3000 (millisecondi), ovvero 3 secondi. Seleziona il segno di spunta in alto a destra nella finestra di dialogo **Pagina** per salvare le modifiche.

   ![schermata_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualizzazione del risultato {#viewing-the-result}

Dopo aver aggiornato la durata di riproduzione del canale (in questo esempio, tutte e tre le immagini), le immagini vengono ora riprodotte per 3 secondi anziché 8 secondi (valore predefinito).

![channel_preview](assets/channel_preview.gif)

