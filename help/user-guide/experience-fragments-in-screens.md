---
title: Utilizzo di Frammenti esperienza
description: Scopri come utilizzare i frammenti di esperienza in AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 1%

---

# Utilizzo di Frammenti esperienza {#using-experience-fragments}

Questa pagina tratta i seguenti argomenti:

* **Panoramica**
* **Utilizzo di Frammenti esperienza in AEM Screens**
* **Propagazione delle modifiche alla pagina**

## Panoramica {#overview}

Un ***Frammento esperienza*** è un gruppo di uno o più componenti, inclusi il contenuto e il layout, a cui è possibile fare riferimento all’interno delle pagine. I frammenti di esperienza possono contenere qualsiasi componente, ad esempio uno o più componenti che possono contenere qualsiasi elemento all’interno di un sistema paragrafo a cui si fa riferimento nell’esperienza completa o richiesto da un terzo endpoint.


## Utilizzo di Frammenti esperienza in AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>L’esempio che segue utilizza **`We.Retail`** come progetto dimostrativo da cui viene applicato il frammento di esperienza da una **Sites** a un progetto AEM Screens.

Ad esempio, il seguente flusso di lavoro illustra l’utilizzo di frammenti di esperienza di `We.Retail` in Sites. Puoi scegliere una pagina web e utilizzare tale contenuto nel tuo canale AEM Screens in uno dei tuoi progetti.

### Prerequisiti {#pre-requisites}

**Creazione di un progetto demo con un canale**

***Creazione di un progetto***

1. Per creare un progetto, seleziona **Crea progetto Screens**.
1. Inserisci il titolo come **DemoProject**.
1. Seleziona **Salva**.

A **DemoProject** viene aggiunto al tuo AEM Screens.

***Creazione di un canale***

1. Accedi a **DemoProject** hai creato e seleziona la **Canali** cartella.

1. Seleziona **Crea** dalla barra delle azioni, in modo da poter aprire la procedura guidata.
1. Scegli la **Canale sequenza** dalla procedura guidata e seleziona **Successivo**.

1. Inserisci il **Titolo** as **TestChannel** e seleziona **Crea**.

A **TestChannel** è stato aggiunto al tuo **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Creazione di un frammento esperienza {#creating-an-experience-fragment}

Segui i passaggi seguenti per applicare il contenuto da **`We.Retail`** al tuo **TestChannel** in **DemoProject**.

1. **Passare a una pagina Sites in We.Retail**

   1. Passa a Sites e seleziona **`We.Retail`** > **Stati Uniti** > **Inglese** > **Attrezzatura** e seleziona questa pagina per utilizzarla come frammento di esperienza per il canale Screens.

   1. Seleziona **Modifica** dalla barra delle azioni, in modo da poter aprire la pagina da utilizzare come frammento di esperienza per il canale Screens.

1. **Riutilizzo del contenuto**

   1. Seleziona il frammento da includere nel canale.
   1. Seleziona l’ultima icona a destra per aprire **Converti in frammento esperienza** .

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Creazione di un frammento esperienza**

   1. Scegli la **Azione** as **Creare un nuovo frammento esperienza**.

   1. Seleziona la **Percorso principale**.
   1. Seleziona la **Modello**. Scegli la **Frammento esperienza - Variante schermi** modello qui (valore nel campo `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Inserisci il **Titolo frammento** as **ScreensFragment**.

   1. Per completare la creazione di un nuovo frammento di esperienza, seleziona il segno di spunta.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Nota: per selezionare un&#39;opzione più semplice, selezionare il segno di spunta a destra del campo per aprire la finestra di dialogo di selezione.

1. **Creazione di Live Copy di un frammento esperienza**

   1. Passa alla home page dell’AEM.
   1. Seleziona **Frammenti esperienza** ed evidenzia **ScreensFragment** e fai clic su **Variante come Live Copy**, come illustrato nella figura seguente:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Seleziona la **ScreensFragment** da **Crea Live Copy** e fai clic su **Successivo**.

   d. Inserire **Titolo** e **Nome** as **Schermi**.

   e. Seleziona **Crea** in modo da poter creare la Live Copy.

   f. Seleziona **Fine** in modo da tornare a **ScreensFragment** pagina.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Dopo aver creato il frammento Screens, puoi modificarne le proprietà. Seleziona il frammento e fai clic su **Proprietà** dalla barra delle azioni.

   **Modifica delle proprietà di un frammento Screens**

   1. Accedi a **ScreensFragment** (creato nei passaggi precedenti) e fare clic su **Proprietà** dalla barra delle azioni.

   1. Seleziona la **Configurazione offline** come illustrato nella figura riportata di seguito.

   È possibile aggiungere **Librerie lato client** (Java™ e css) e **File statici** nel frammento di esperienza.

   L’esempio seguente mostra l’aggiunta di librerie lato client e dei font come parte di file statici nel frammento di esperienza.  ![frammento](assets/fragment.gif)

1. **Utilizzo di Frammento esperienza come componente nel canale Screens**

   1. Passa al canale Screens in cui desideri utilizzare il **Schermi** frammento.
   1. Seleziona la **TestChannel** e fai clic su **Modifica** dalla barra delle azioni.

   1. Fai clic sull’icona dei componenti nella scheda laterale.
   1. Trascina la **Frammento esperienza** al tuo canale.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Selezionare **Frammento esperienza** e seleziona l’icona in alto a sinistra (chiave inglese) per aprire **Frammento esperienza** .

   f. Seleziona la **Schermi** live copy del frammento creato in *Passaggio 3* in **Percorso**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Seleziona la **Schermi** live copy del frammento creato in *Passaggio 3* nel **Frammento esperienza**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Inserire i millisecondi in **Durata**.

   i. Seleziona la **Configurazione offline** dal **Frammenti esperienza** in modo da poter definire le librerie lato client e i file statici.

   >[!NOTE]
   >
   >Per aggiungere librerie lato client, o i file statici in aggiunta a quanto configurato nel passaggio (4), puoi aggiungere da **Configurazione offline** scheda in **Frammento esperienza** .

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Selezionare il segno di spunta per completare il processo.

### Convalida del risultato {#validating-the-result}

Dopo aver completato i passaggi precedenti, puoi convalidare il frammento di esperienza in **ChannelOne** da:

1. Navigazione a **TestChannel**.
1. Selezione del **Anteprima** dalla barra delle azioni.

Visualizza il contenuto da **Sites** pagina (Live Copy del frammento di esperienza) nel canale, come illustrato nella figura seguente:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagazione delle modifiche alla pagina {#propagating-changes-from-the-master-page}

***Live Copy*** si riferisce alla copia (dell’origine), gestita dalle azioni di sincronizzazione definite dalle configurazioni di rollout.

Poiché il frammento di esperienza creato è una Live Copy da **Sites** e modifichi quel particolare frammento dalla pagina principale, visualizzi le modifiche nel tuo canale. In alternativa, puoi visualizzare la destinazione in cui hai utilizzato il frammento di esperienza.

>[!NOTE]
>
>Per ulteriori informazioni su Live Copy, consulta Riutilizzo del contenuto: Gestore multisito e Live Copy.

Segui i passaggi seguenti per propagare le modifiche dal canale principale al canale di destinazione:

1. Seleziona il frammento di esperienza dalla sezione **Sites** (principale) e fai clic sull’icona della matita per modificare gli elementi nel frammento di esperienza.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Seleziona il frammento di esperienza e fai clic sull’icona a forma di chiave inglese per aprire la finestra di dialogo e modificare le immagini.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. Il **Griglia prodotti** viene visualizzata.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. È possibile modificare qualsiasi immagine. Ad esempio, qui la prima immagine viene sostituita in questo frammento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Seleziona il frammento di esperienza e fai clic sull’icona Rollout per propagare le modifiche al frammento utilizzato nel canale.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Seleziona Rollout.

   Noterai che le modifiche vengono implementate.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Convalida delle modifiche {#validating-the-changes}

Per confermare le modifiche apportate al canale, segui la procedura riportata di seguito:

1. Accedi a **Schermi** > **Canali** > **TestChannel**.

1. Clic **Anteprima** dalla barra delle azioni.

L’immagine seguente illustra le modifiche apportate al **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
