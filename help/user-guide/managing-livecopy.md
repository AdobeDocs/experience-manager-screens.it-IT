---
title: Creazione e gestione di una Live Copy
description: Scopri come creare e gestire Live Copy dei canali in AEM Screens.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 5%

---

# Creazione e gestione di una Live Copy {#creating-and-managing-a-live-copy}

Questa pagina descrive come creare e gestire Live Copy dei canali.

Una ***Live Copy*** è una copia del contenuto specifico del sito per il quale viene mantenuta una relazione live con il sorgente originale. Questa relazione live consente alla Live Copy di ereditare il contenuto e le proprietà di pagina dal sorgente.

Questa pagina descrive la creazione di una Live Copy di un canale, la visualizzazione delle proprietà, il controllo dello stato e la propagazione delle modifiche da un canale alla relativa Live Copy.


## Creazione della Live Copy {#creating-a-live-copy}

Segui i passaggi seguenti per creare una Live Copy di un canale nella cartella del progetto.

1. Fai clic sul collegamento Adobe Experience Manager (in alto a sinistra) e quindi su **Screens**. In alternativa, è possibile passare direttamente a: `http://localhost:4502/screens.html/content/screens`.

1. Passa al progetto Screens e fai clic su **Canali**.
1. Fai clic su **Crea** e su **Live Copy** per creare una Live Copy del canale.
1. Fare clic sulla destinazione e fare clic su **Avanti**.
1. Fai clic sul percorso in cui può risiedere la Live Copy.
1. Immetti il **Titolo** e il **Nome** nella pagina **Crea Live Copy**.

1. Fai clic su **Apri** per visualizzare il contenuto della nuova Live Copy o su **Fine** per tornare alla pagina principale.

In alternativa, consulta i passaggi seguenti per la rappresentazione visiva per creare una nuova Live Copy di un canale.

L&#39;esempio seguente mostra la creazione di una Live Copy (***IdleLiveCopy***) per ***Idle Channel*** con la cartella di destinazione come ***Channels***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Visualizzazione del contenuto del canale Live Copy {#viewing-content-of-the-live-copy-channel}

Una Live Copy è una copia di un canale esistente.

Per visualizzare il contenuto della Live Copy, consulta i passaggi seguenti:

1. Passa a Progetto Screens e fai clic sul percorso in cui hai creato originariamente una Live Copy, come illustrato nella sezione precedente. In questo caso, il percorso è stato scelto come cartella **Canali**

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Fai clic su **Modifica** nella barra delle azioni.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Quando visualizzi il contenuto di un canale Live Copy, visualizzi un elemento aggiuntivo nel menu come **Stato Live Copy**. Per ulteriori dettagli, consulta la sezione di seguito.

### Visualizzazione delle proprietà di una Live Copy {#viewing-properties-of-a-live-copy}

Inoltre, puoi visualizzare le proprietà del canale Live Copy.

1. Passa al tuo canale Live Copy e fai clic su **Proprietà** nella barra delle azioni.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Fai clic sulla scheda **Live Copy** per visualizzare i dettagli del tuo canale.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Stato della Live Copy   {#live-copy-status}

La modalità **Stato Live Copy**, come illustrato nella figura seguente, ti consente di visualizzare lo stato della relazione di tutte le risorse nel canale.

1. Fai clic su **Modifica** per scegliere lo **stato Live Copy**. Puoi anche visualizzare l’associazione del contenuto del canale al canale originale da cui viene generata la Live Copy.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Fai clic su **Stato Live Copy** per visualizzare la pagina di anteprima.

   Tutte le risorse con bordo verde mostrano che il contenuto viene ereditato dal canale originale.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Interruzione dell’ereditarietà {#breaking-the-inheritance}

Puoi anche annullare l’ereditarietà dalla Live Copy, in modo che il contenuto diventi indipendente dal ramo originale.

L&#39;esempio seguente mostra che si fa clic sull&#39;immagine in modalità di modifica e si fa clic sull&#39;icona **Annulla ereditarietà** in alto a destra.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagazione delle modifiche al canale Live Copy {#propagating-changes-to-the-live-copy-channel}

Se apporti modifiche o aggiornamenti nel canale originale, propagale anche tali modifiche al canale Live Copy.

Segui i passaggi seguenti per assicurarti che le modifiche vengano propagate dal canale originale al canale Live Copy:

1. Fai clic sul canale originale (***Canale inattivo***) e fai clic su **Modifica** nella barra delle azioni.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Apporta le modifiche a questo contenuto del canale. Ad esempio, elimina un’immagine da questo canale.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Fai clic sulla Live Copy del canale (***IdleLiveCopy***) e fai clic su **Modifica** nella barra delle azioni. L’immagine eliminata è ancora visibile nella Live Copy.

   Per propagare le modifiche, sincronizza il canale.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Per propagare le modifiche al canale Live Copy, passa al dashboard di AEM e fai clic sul canale Live Copy, quindi fai clic su **Proprietà** nella barra delle azioni.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Fai clic sulla scheda **Live Copy** e fai clic su **Sincronizza** nella barra delle azioni.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Fai clic su **Sincronizza**, quindi fai clic su **Salva e chiudi** per tornare al dashboard di AEM.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Ora l’immagine viene eliminata anche dal canale Live Copy.
