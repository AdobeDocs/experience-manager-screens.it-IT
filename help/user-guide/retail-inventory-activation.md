---
title: Attivazione con targeting magazzino vendita al dettaglio
seo-title: Retail Inventory Targeted Activation
description: Questo caso d’uso presenta le scorte di magazzino al dettaglio per tre felpe colorate diverse. A seconda del numero di felpe disponibili che vengono registrate in Google Sheets, sullo schermo viene visualizzata l’immagine (felpa rossa, verde o blu) con il numero più alto.
seo-description: This Use Case showcases the retail inventory stock for three different colored sweatshirts. Depending on the number of sweatshirts available in stock that is recorded in Google Sheets, the image (red, green, or blue sweatshirt) with highest number is displayed on the screen.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Attivazione con targeting magazzino vendita al dettaglio {#retail-inventory-targeted-activation}

Il seguente caso d’uso illustra tre diverse immagini in base ai valori presenti nel foglio Google.

## Descrizione {#description}

Questo caso d’uso presenta le scorte di magazzino al dettaglio per tre felpe colorate diverse. A seconda del numero di felpe disponibili che vengono registrate in Google Sheets, sullo schermo viene visualizzata l’immagine (felpa rossa, verde o blu) con il numero più alto.

Per questo caso d’uso, il maglione rosso, verde o blu verrà visualizzato sullo schermo in base al valore più alto del numero di maglie disponibile.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l’attivazione del targeting dell’inventario di vendita al dettaglio, devi imparare a impostare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per i canali*** in un progetto AEM Screens.

Consulta [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) per informazioni dettagliate.

## Flusso di base {#basic-flow}

Per implementare il caso d’uso di Retail Inventory Activation, effettua le seguenti operazioni:

1. **Compilazione dei fogli di Google**

   1. Passa al foglio Google ContextHubDemo.
   1. Aggiungi tre colonne (rosso, verde e blu) con i valori corrispondenti per tre diverse felpe.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurazione dei tipi di pubblico in base ai requisiti**

   1. Passa ai segmenti del pubblico (consulta ***Passaggio 2: impostazione della segmentazione del pubblico*** in **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Aggiungi tre nuovi segmenti **For_Red**, **For_Green**, e **For_Blue**.

   1. Seleziona **For_Red** e fai clic su **Modifica** dalla barra delle azioni.

   1. Trascina la **Comparison : Proprietà - Proprietà** nell’editor e fai clic sull’icona configura per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/2** dall’elenco a discesa in **Nome prima proprietà**

   1. Seleziona la **Operatore** as **maggiore di** dal menu a discesa

   1. Seleziona **Tipo di dati** as **numero**

   1. Seleziona **googlesheets/value/1/1** dall’elenco a discesa in **Nome seconda proprietà**.

   1. Trascina **other Comparison : Proprietà - Proprietà** nell’editor e fai clic sull’icona configura per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/2** dall’elenco a discesa in **Nome prima proprietà**.

   1. Seleziona la **Operatore** as **maggiore di** dal menu a discesa

   1. Seleziona **Tipo di dati** as **numero**

   1. Seleziona **googlesheets/value/1/0** dall’elenco a discesa in **Nome seconda proprietà**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Allo stesso modo, modifica e aggiungi regole di proprietà di confronto a **For_Blue** come illustrato nella figura seguente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Analogamente, modificate e aggiungete regole di proprietà di confronto a** For_Green **segmento come mostrato nella figura seguente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Noterai che per i segmenti **For_Green** e **For_Green**, i dati non possono essere risolti nell’editor in quanto ora è valido solo il primo confronto in base ai valori presenti nel foglio di Google.

1. Naviga e seleziona il **DataDrivenRetail** channel (un canale sequencel) e fare clic su **Modifica** dalla barra delle azioni.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Avresti dovuto impostare il tuo **ContextHub** **Configurazioni** utilizzo del canale **Proprietà** > **Personalizzazione** scheda.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >È necessario selezionare entrambe le opzioni **Marchio** e **Superfici** affinché le attività vengano elencate correttamente quando avvii il processo di targeting.

1. **Aggiunta di un&#39;immagine predefinita**

   1. Aggiungi un’immagine predefinita al tuo canale e fai clic su **Targeting**.
   1. Seleziona **Marchio** e **Attività** dal menu a discesa e fai clic su **Inizia impostazione destinazione**.

   1. Clic **Inizia impostazione destinazione**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Prima di iniziare il targeting, devi aggiungere i segmenti (**For_Green**, **For_Red**, e **For_Blue**) facendo clic su **+ Aggiungi targeting esperienza** dalla barra laterale, come illustrato nella figura seguente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Aggiungi le immagini a tutti e tre i diversi scenari come mostrato di seguito.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Controllo dell’anteprima**

   1. Clic **Anteprima.** Inoltre, aprire Google Sheet e aggiornarne il valore.
   1. Modifica il valore per tutte e tre le colonne e noterai gli aggiornamenti dell’immagine di visualizzazione in base al valore più alto in magazzino.

   ![retail_result](assets/retail_result.gif)
