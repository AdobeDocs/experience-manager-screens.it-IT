---
title: Creazione e gestione di una Live Copy
seo-title: Gestione di LiveCopy
description: Questa pagina descrive come creare e gestire Live Copy dei canali.
seo-description: Segui questa pagina per creare una Live Copy di un canale, visualizzare le proprietà, controllare lo stato e propagare le modifiche da un canale alla sua Live Copy.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
feature: Creazione di esperienze in Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 86%

---


# Creazione e gestione di una Live Copy {#creating-and-managing-a-live-copy}

Questa pagina descrive come creare e gestire Live Copy dei canali.

Una ***Live Copy*** è una copia del contenuto specifico del sito per il quale viene mantenuta una relazione live con la sorgente originale. Questa relazione diretta consente alla Live Copy di ereditare il contenuto e le proprietà della pagina dalla sorgente.

Questa pagina descrive come creare la Live Copy di un canale, visualizzare le proprietà, controllare lo stato e propagare le modifiche apportate a un canale alla sua Live Copy.


## Creazione della Live Copy {#creating-a-live-copy}

Segui i passaggi riportati di seguito per creare una Live Copy di un canale nella cartella del progetto.

1. Seleziona il collegamento all’Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. In alternativa, puoi passare direttamente a: `http://localhost:4502/screens.html/content/screens`.

1. Accedi al progetto Screens e fai clic su **Canali**.
1. Fai clic su **Crea** e seleziona **Live Copy** per creare una Live Copy del canale.

1. Seleziona la destinazione e fai clic su **Avanti**.
1. Seleziona la posizione della Live Copy.
1. Immetti il **Titolo** e il **Nome** nella pagina **Crea Live Copy**.

1. Fai clic su **Apri** per visualizzare i contenuti della nuova Live Copy o su **Fine** per tornare alla pagina principale.

In alternativa, consulta i passaggi descritti di seguito per la rappresentazione visiva per creare una nuova Live Copy di un canale.

I seguenti esempi mostrano la creazione di una copia live (***IdleLiveCopy***) per il ***Canale inattivo*** con la cartella di destinazione come ***Canali***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Visualizzazione del contenuto del canale della Live Copy {#viewing-content-of-the-live-copy-channel}

La Live Copy è una copia di un canale già esistente.

Per visualizzare il contenuto della Live Copy, vedi i passaggi riportati di seguito:

1. Accedi al progetto Screens fai clic sulla posizione dove hai creato la Live Copy originariamente, come mostrato nella sezione precedente. (In questo caso, il percorso è stato scelto come cartella **Canali** )

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Fai clic su **Modifica** nella barra delle azioni per visualizzare il contenuto del canale.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Quando visualizzi il contenuto di un canale della copia dal vivo, vedrai un ulteriore oggetto nel menu, come **Stato Live Copy**. Per ulteriori informazioni, vedi la sezione di seguito.

### Visualizzazione delle proprietà della Live Copy {#viewing-properties-of-a-live-copy}

Puoi anche visualizzare le proprietà del tuo canale della Live Copy.

1. Accedi alle proprietà del canale della Live Copy e dalla barra delle azioni fai clic su **Proprietà**.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Seleziona la scheda **Live copy** per visualizzare i dettagli del canale.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Stato della Live Copy    {#live-copy-status}

La modalità **Stato della Live Copy**, come mostrato nella figura sotto, consente di visualizzare lo stato di relazione di tutte le risorse presenti nel canale.

1. Fai clic su **Modifica** per scegliere **Stato Live Copy** e visualizzare l&#39;associazione del contenuto del canale al canale originale (da cui viene generata la Live Copy).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Seleziona **Stato della Live Copy** per visualizzare la pagina di anteprima.

   Tutte le risorse con il bordo verde indicano che il contenuto è ereditato dal canale originale.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Interruzione dell’ereditarietà {#breaking-the-inheritance}

Puoi anche annullare l’ereditarietà della livecopy, in modo che il contenuto diventi indipendente dal ramo originale.

L’esempio seguente mostra che l’immagine è stata selezionata nella modalità di modifica e che si è fatto clic sul simbolo Annulla ereditarietà in alto a destra.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagazione delle modifiche al canale della Live Copy {#propagating-changes-to-the-live-copy-channel}

Se apporti cambiamenti o aggiornamenti al canale originale, devi propagare le modifiche al tuo canale Live Copy.

Segui i passaggi riportati di seguito per accertarti che le modifiche vengano applicate dal canale sorgente al canale Live Copy:

1. Seleziona il canale originale (***Canale inattivo***) e fai clic su **Modifica** nella barra delle azioni.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Apporta modifiche a questo contenuto del canale. Ad esempio, elimina un’immagine.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Seleziona la Live Copy del canale (***IdleLiveCopy***) e fai clic su **Modifica** nella barra delle azioni. Noterai che l’immagine che hai eliminato non è visibile nella Live Copy.

   Per propagare le modifiche, devi sincronizzare il canale.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Per propagare le modifiche al canale Live Copy, accedi alla dashboard di AEM, scegli il canale Live Copy e fai clic su **Proprietà** dalla barra delle azioni.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Seleziona la scheda **Live copy** e fai clic su **Sincronizza** dalla barra delle azioni.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Fai clic su **Sincronizza** per confermare le modifiche. Fai clic su **Salva e chiudi** per tornare al dashboard AEM.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Noterai che l’immagine ora è stata eliminata dal canale Live Copy.

