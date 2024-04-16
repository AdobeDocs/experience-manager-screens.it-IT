---
title: Supporto di miniature per video in AEM Screens
description: Scopri come aggiungere il supporto per miniature per video in AEM Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# Supporto delle miniature per video {#thumbnail-support-videos}

## Introduzione {#introduction}

Un autore di contenuti può definire una miniatura per video in modo che l’immagine venga utilizzata come segnaposto e possa testare correttamente la riproduzione e il targeting del contenuto, mentre il video effettivo viene finalizzato dal team appropriato. L’immagine può essere utilizzata anche in caso di interruzione della riproduzione del video.

L’aggiunta di supporto per un’immagine miniatura sul componente video consente al cliente di aggiungere correttamente un componente valido nel canale, con il contenuto effettivo ed eseguire eventuali configurazioni di targeting prima che il video venga consegnato.

>[!NOTE]
>L’immagine miniatura, se impostata sul componente video, viene riprodotta in caso di errore di riproduzione video sul lettore. Questo ti consente di inviare il messaggio desiderato al pubblico (riproducendo il contenuto) invece di saltarlo completamente.

Il supporto delle miniature consente di:

* Prepara un’esperienza di canale quando i video non sono ancora pronti o quando non desideri necessariamente testare il download di una risorsa di grandi dimensioni sui lettori

* Imposta un meccanismo di fallback, nel caso in cui si verifichino problemi di riproduzione sul dispositivo.

## Utilizzo delle miniature nei video {#using-thumbnails}

Per usare la miniatura nei video, segui la procedura indicata di seguito:

1. Passa a un canale AEM Screens esistente o creane uno.

1. Fai clic sul canale e fai clic su **Modifica** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Aggiungi o modifica un componente video esistente, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Fai clic sul video e fai clic su *chiave inglese* icona.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. Il **Video** viene visualizzata la finestra di dialogo in cui è possibile visualizzare **Miniatura** zona di rilascio.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Trascina e rilascia un’immagine dal selettore risorse al **Miniatura** rilascia la zona e fai clic su **Fine**.

   ![immagine](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Clic **Anteprima**.

1. Se un video è impostato sul componente, viene riprodotto. In caso contrario, e la miniatura è impostata, la miniatura viene riprodotta. In caso contrario, il componente viene considerato non configurato e viene saltato.

## Casi d’uso supportati durante l’utilizzo della miniatura nei video {#understand-use-case}

La miniatura nei video supporta i seguenti casi d’uso:

* Viene saltato un componente video senza alcuna configurazione.

* Un componente video con solo la miniatura impostata riproduce la miniatura.

* Un componente video con il video (se il video ha una rappresentazione corretta) e il set di miniature riproduce il video.

* Un componente video con il set di video riproduce la miniatura, se si verifica un errore di riproduzione, o passa all’elemento successivo nel caso in cui la miniatura non sia configurata.
