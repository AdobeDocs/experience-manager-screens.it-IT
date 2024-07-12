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
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 1%

---

# Utilizzo di Frammenti esperienza {#using-experience-fragments}

Questa pagina tratta i seguenti argomenti:

* **Panoramica**
* **Utilizzo di frammenti di esperienza in AEM Screens**
* **Propagazione delle modifiche alla pagina**

## Panoramica {#overview}

Un ***frammento esperienza*** è un gruppo di uno o più componenti, inclusi il contenuto e il layout, a cui è possibile fare riferimento all&#39;interno delle pagine. I frammenti di esperienza possono contenere qualsiasi componente. Ad esempio, può contenere uno o più componenti che possono contenere qualsiasi elemento all’interno di un sistema paragrafo a cui si fa riferimento nell’esperienza completa o richiesto da un terzo endpoint.


## Utilizzo di Frammenti esperienza in AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>Nell&#39;esempio seguente viene utilizzato **`We.Retail`** come progetto demo da cui il frammento di esperienza viene applicato da una pagina **Sites** a un progetto AEM Screens.

Ad esempio, il seguente flusso di lavoro illustra l&#39;utilizzo dei frammenti di esperienza di `We.Retail` in Sites. Puoi scegliere una pagina web e utilizzare tale contenuto nel tuo canale AEM Screens in uno dei tuoi progetti.

### Prerequisiti {#pre-requisites}

**Creazione di un progetto demo con un canale**

***Creazione di un progetto***

1. Per creare un progetto, fare clic su **Crea progetto Screens**.
1. Immetti il titolo come **Progetto demo**.
1. Fai clic su **Salva**.

Un **DemoProject** è stato aggiunto al tuo AEM Screens.

***Creazione di un canale***

1. Passa al **DemoProject** creato e fai clic sulla cartella **Channels**.

1. Fai clic su **Crea** nella barra delle azioni per aprire la procedura guidata.
1. Scegli il modello **Canale sequenza** dalla procedura guidata e fai clic su **Avanti**.

1. Immetti il **Titolo** come **TestChannel** e fai clic su **Crea**.

**TestChannel** aggiunto al **DemoProject**.\
![schermata_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Creazione di un frammento esperienza {#creating-an-experience-fragment}

Segui i passaggi seguenti per applicare il contenuto di **`We.Retail`** al tuo **TestChannel** in **DemoProject**.

1. **Passa a una pagina Sites in We.Retail**

   1. Passa a Sites e fai clic su **`We.Retail`** > **Stati Uniti** > **Inglese** > **Attrezzature**, quindi fai clic su questa pagina per utilizzarla come frammento di esperienza per il tuo canale Screens.

   1. Fai clic su **Modifica** nella barra delle azioni per aprire la pagina da utilizzare come frammento di esperienza per il canale Screens.

1. **Riutilizzo del contenuto**

   1. Fai clic sul frammento da includere nel canale.
   1. Fai clic sull&#39;ultima icona a destra per aprire la finestra di dialogo **Converti in frammento di esperienza**.

   ![schermata_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Creazione di un frammento esperienza**

   1. Scegli **Azione** come **Crea un nuovo frammento esperienza**.

   1. Fai clic sul **percorso principale**.
   1. Fai clic sul **modello**. Scegli il modello **Frammento esperienza - Variante Screens** qui (valore nel campo `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Immetti il **Titolo frammento** come **ScreensFragment**.

   1. Per completare la creazione di un nuovo frammento di esperienza, fai clic sul segno di spunta.

   ![schermata_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Per selezionare un&#39;opzione più semplice, fare clic sul segno di spunta a destra del campo per aprire la finestra di dialogo di selezione.

1. **Creazione di Live Copy del frammento esperienza**

   1. Passa alla home page dell’AEM.
   1. Fai clic su **Frammenti esperienza**, evidenzia **ScreensFragment** e fai clic su **Variante come Live Copy**, come illustrato nella figura seguente:

   ![schermata_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Fai clic su **ScreensFragment** dalla procedura guidata **Crea Live Copy** e fai clic su **Avanti**.

   d. Immetti **Titolo** e **Nome** come **Screens**.

   e. Fai clic su **Crea** per creare la Live Copy.

   f. Fai clic su **Fine** per tornare alla pagina **ScreensFragment**.

   ![schermata_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Dopo aver creato un frammento AEM Screens, puoi modificarne le proprietà. Fai clic sul frammento e fai clic su **Proprietà** nella barra delle azioni.

   **Modifica delle proprietà di un frammento di Screens**

   1. Passa a **ScreensFragment** (creato nei passaggi precedenti) e fai clic su **Proprietà** nella barra delle azioni.

   1. Fare clic sulla scheda **Configurazione offline**, come illustrato nella figura seguente.

   Puoi aggiungere **Librerie lato client** (Java™ e CSS) e **File statici** al frammento di esperienza.

   L’esempio seguente mostra l’aggiunta di librerie lato client e dei font come parte di file statici nel frammento di esperienza.  ![frammento](assets/fragment.gif)

1. **Utilizzo del frammento di esperienza come componente nel canale Screens**

   1. Passa al canale Screens in cui desideri utilizzare il frammento **Screens**.
   1. Fai clic su **TestChannel** e fai clic su **Modifica** nella barra delle azioni.

   1. Fai clic sull’icona dei componenti nella scheda laterale.
   1. Trascina e rilascia il **Frammento esperienza** nel tuo canale.

   ![schermata_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Fai clic sul componente **Frammento esperienza** e fai clic sull&#39;icona in alto a sinistra (chiave inglese) per aprire la finestra di dialogo **Frammento esperienza**.

   f. Fai clic sulla **Screens** Live Copy del frammento creato in *Passaggio 3* in **Percorso**.

   ![schermata_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Fai clic sulla **Screens** Live Copy del frammento creato in *Passaggio 3* nel **Frammento esperienza**.

   ![schermata_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Immetti i millisecondi in **Durata**.

   i. Fai clic sulla **configurazione offline** dalla finestra di dialogo **Frammenti esperienza** per definire le librerie lato client e i file statici.

   >[!NOTE]
   >
   >Per aggiungere le librerie lato client o i file statici oltre a quelli configurati nel passaggio (4), puoi aggiungere dalla scheda **Configurazione offline** nella finestra di dialogo **Frammento esperienza**.

   ![schermata_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Fare clic sul segno di spunta per completare il processo.

### Convalida del risultato {#validating-the-result}

Dopo aver completato i passaggi precedenti, puoi convalidare il frammento di esperienza in **ChannelOne**:

1. Accesso a **TestChannel**.
1. Seleziona **Anteprima** dalla barra delle azioni.

Visualizza il contenuto della pagina **Sites** (Live Copy del frammento di esperienza) nel tuo canale, come illustrato nella figura seguente:\
![schermata_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagazione delle modifiche alla pagina {#propagating-changes-from-the-master-page}

***Live Copy*** fa riferimento alla copia (dell&#39;origine), gestita dalle azioni di sincronizzazione definite dalle configurazioni di rollout.

Poiché il frammento di esperienza creato è una Live Copy dalle pagine **Sites** e si modifica quel particolare frammento dalla pagina principale, è possibile visualizzare le modifiche nel canale. In alternativa, puoi visualizzare la destinazione in cui hai utilizzato il frammento di esperienza.

>[!NOTE]
>
>Per ulteriori informazioni su Live Copy, consulta Riutilizzo del contenuto: Gestore multisito e Live Copy.

Segui i passaggi seguenti per propagare le modifiche dal canale principale al canale di destinazione:

1. Fai clic sul frammento di esperienza dalla pagina **Sites** (principale) e fai clic sull&#39;icona a forma di matita per modificare gli elementi nel frammento di esperienza.

   ![schermata_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Fai clic sul frammento di esperienza e fai clic sull’icona a forma di chiave inglese per aprire la finestra di dialogo e modificare le immagini.

   ![schermata_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. Viene visualizzata la finestra di dialogo **Griglia prodotto**.

   ![schermata_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. È possibile modificare qualsiasi immagine. Ad esempio, qui la prima immagine viene sostituita in questo frammento.

   ![schermata_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Fai clic sul frammento di esperienza e sull’icona Rollout per propagare le modifiche al frammento utilizzato nel canale.

   ![schermata_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Fai clic su Rollout.

   Noterai che le modifiche vengono implementate.

   ![schermata_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Convalida delle modifiche {#validating-the-changes}

Per confermare le modifiche apportate al canale, segui la procedura riportata di seguito:

1. Passa a **Screens** > **Canali** > **TestChannel**.

1. Fai clic su **Anteprima** nella barra delle azioni.

L&#39;immagine seguente illustra le modifiche apportate al **TestChannel**:\
![schermata_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
