---
title: Supporto di miniature per video in AEM Screens
description: Scopri come aggiungere il supporto per miniature per video in AEM Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 2%

---

# Supporto delle miniature per video {#thumbnail-support-videos}

## Introduzione {#introduction}

Un autore di contenuti può definire una miniatura per video in modo che l’immagine venga utilizzata come segnaposto. È in grado di testare correttamente la riproduzione e il targeting dei contenuti, mentre il team appropriato finalizza il video effettivo. L’immagine può essere utilizzata anche in caso di interruzione della riproduzione del video.

L’aggiunta di supporto per un’immagine miniatura sul componente video consente al cliente di aggiungere correttamente un componente valido nel canale, con il contenuto effettivo ed eseguire eventuali configurazioni di targeting prima che il video venga consegnato.

>[!NOTE]
>L’immagine miniatura, se impostata sul componente video, viene riprodotta in caso di errore di riproduzione video sul lettore. Questo fallback consente di inviare il messaggio desiderato al pubblico (riproducendo il contenuto) invece di saltarlo completamente.

Il supporto delle miniature consente di:

* Prepara un’esperienza di canale quando i video non sono ancora pronti o quando non desideri necessariamente testare il download di una risorsa di grandi dimensioni sui lettori

* Imposta un meccanismo di fallback, nel caso in cui si verifichino problemi di riproduzione sul dispositivo.

## Utilizzo delle miniature nei video {#using-thumbnails}

Per usare una miniatura nei video, segui la procedura indicata di seguito:

1. Passa a un canale AEM Screens esistente o creane uno.

1. Fai clic sul canale e fai clic su **Modifica** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Aggiungi o modifica un componente video esistente, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Fai clic sul video e sull&#39;icona *chiave inglese*.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. Viene visualizzata la finestra di dialogo **Video** in cui è possibile visualizzare la zona di rilascio **Miniatura**.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Trascina e rilascia un&#39;immagine dal selettore risorse alla zona di rilascio **Miniatura** e fai clic su **Fine**.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Fare clic su **Anteprima**.

1. Se un video è impostato sul componente, viene riprodotto. In caso contrario, e la miniatura è impostata, la miniatura viene riprodotta. In caso contrario, il componente viene considerato non configurato e viene saltato.

## Casi d’uso supportati durante l’utilizzo della miniatura nei video {#understand-use-case}

La miniatura nei video supporta i seguenti casi d’uso:

* Viene saltato un componente video senza alcuna configurazione.

* Un componente video con solo la miniatura impostata riproduce la miniatura.

* Un componente video con il video (se il video ha una rappresentazione corretta) e il set di miniature riproduce il video.

* Un componente video con il set di video riproduce la miniatura, se si verifica un errore di riproduzione, o passa all’elemento successivo nel caso in cui la miniatura non sia configurata.
