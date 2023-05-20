---
title: Supporto di miniature per video in AEM Screens
description: Questa pagina descrive come aggiungere il supporto miniature per video in Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: ec58cd9171e359b451eaad7015d42b41ef1bff3f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---

# Supporto delle miniature per video {#thumbnail-support-videos}

## Introduzione {#introduction}

Un autore di contenuti può definire una miniatura per video in modo che l’immagine possa essere utilizzata come segnaposto e testare correttamente la riproduzione e il targeting del contenuto, mentre il video effettivo è in fase di finalizzazione da parte del team appropriato. L’immagine può essere utilizzata anche nel caso in cui la riproduzione del video non riesca.

L’aggiunta di supporto per un’immagine miniatura sul componente video consente al cliente di aggiungere correttamente un componente valido nel canale, con il contenuto effettivo ed eseguire eventuali configurazioni di targeting prima che il video venga effettivamente distribuito.

>[!NOTE]
>L’immagine miniatura, se impostata sul componente video, viene riprodotta in caso di errore di riproduzione video sul lettore. Questo consente di inviare al pubblico il messaggio desiderato (riproducendo il contenuto) invece di saltarlo completamente.

Il supporto delle miniature consente di:

* Prepara un’esperienza di canale quando i video non sono ancora pronti o quando non desideri necessariamente testare il download di una risorsa di grandi dimensioni sui lettori

* Imposta un meccanismo di fallback, nel caso in cui si verifichino problemi di riproduzione sul dispositivo.

## Utilizzo delle miniature nei video {#using-thumbnails}

Per usare la miniatura nei video, segui la procedura indicata di seguito:

1. Passa a un canale Screens esistente o creane uno nuovo.

1. Seleziona il canale e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Aggiungi o modifica un componente video esistente, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Seleziona il video e fai clic sul pulsante *chiave inglese* per aprire le proprietà del video.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. Il **Video** viene visualizzata la finestra di dialogo in cui è possibile visualizzare **Miniatura** zona di rilascio.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Trascina e rilascia un’immagine dal selettore risorse al **Miniatura** rilascia la zona e fai clic su **Fine**.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Fai clic su **Anteprima**.

1. Se un video è impostato sul componente, il video verrà riprodotto. In caso contrario, e la miniatura è impostata, verrà riprodotta. In caso contrario, il componente viene considerato non configurato e verrà ignorato.

## Casi d’uso supportati durante l’utilizzo della miniatura nei video {#understand-use-case}

La miniatura nei video supporta i seguenti casi d’uso:

* Un componente video senza alcuna configurazione verrà ignorato.

* La miniatura viene riprodotta da un componente video contenente solo la serie di miniature.

* Il video verrà riprodotto da un componente video con il video (se il video ha una rappresentazione corretta) e la miniatura impostata.

* Un componente video con il set di video riprodurrà la miniatura, in caso di errore di riproduzione, o passerà all’elemento successivo nel caso in cui la miniatura non sia configurata.
