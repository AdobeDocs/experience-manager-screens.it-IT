---
title: Supporto delle miniature per i video in AEM Screens
description: Questa pagina descrive come aggiungere il supporto per le miniature per i video in Screens.
index: false
source-git-commit: 07b5b6159b09c0c1301a5e782dfe959d0b83a7d2
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Supporto delle miniature per video {#thumbnail-support-videos}

## Introduzione {#introduction}

Un autore di contenuti può definire una miniatura per i video in modo che l’immagine possa essere utilizzata come segnaposto e possa testare correttamente la riproduzione e il targeting del contenuto, mentre il video effettivo viene finalizzato dal team appropriato. L&#39;immagine può anche essere utilizzata, nel caso in cui la riproduzione del video non riesca.

L’aggiunta del supporto per un’immagine in miniatura sul componente video consente al cliente di aggiungere correttamente un componente valido nel canale, con contenuto effettivo, ed eseguire eventuali configurazioni di targeting prima che il video venga effettivamente distribuito.

>[!NOTE]
>L’immagine miniatura, se impostata sul componente video, viene riprodotta in caso di errore di riproduzione video sul lettore. Questo consente di inviare il messaggio desiderato al pubblico (riproducendo il contenuto) anziché ignorarlo completamente.

Il supporto per le miniature consente di:

* Prepara un’esperienza di canale quando i video non sono ancora pronti o quando non desideri necessariamente testare un download di risorse di grandi dimensioni sui lettori.

* Imposta un meccanismo di fallback, in caso di problemi di riproduzione sul dispositivo.

## Utilizzo delle miniature nei video {#using-thumbnails}

Per usare le miniature nei video, effettua le seguenti operazioni:

1. Passa a un canale Screens esistente o creane uno nuovo.

1. Seleziona il canale e fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.

1. Aggiungi o modifica un componente video esistente, come illustrato nella figura riportata di seguito.

1. Seleziona il video e fai clic sull&#39;icona *chiave inglese* per aprire le proprietà del video.

1. Viene visualizzata la finestra di dialogo **Video** in cui viene visualizzata la zona di rilascio **Miniatura**.

1. Trascina e rilascia un’immagine dal selettore delle risorse nella zona di rilascio **Miniatura** e fai clic su **Fine**.

1. Fai clic su **Anteprima**.

1. Se un video è impostato sul componente, il video verrà riprodotto. In caso contrario, e la miniatura è impostata, la miniatura viene riprodotta. In caso contrario, il componente viene considerato non configurato e verrà ignorato.

## Casi d&#39;uso supportati quando si utilizza la miniatura nei video {#understand-use-case}

La miniatura nei video supporta i seguenti casi d’uso:

* Un componente video non configurato verrà ignorato.

* Un componente video con solo le miniature impostate riproduce la miniatura.

* Un componente video con sia il video (se il video ha una rappresentazione corretta) che il set di miniature riprodurranno il video.

* Un componente video con il set di video riproduce la miniatura, in caso di errore di riproduzione, oppure passa all’elemento successivo nel caso in cui la miniatura non sia configurata.
