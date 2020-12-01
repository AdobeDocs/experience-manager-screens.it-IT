---
title: Attivazione mirata inventario vendita al dettaglio
seo-title: Attivazione mirata inventario vendita al dettaglio
description: Questo caso d'uso mostra il magazzino al dettaglio per tre diverse maglie colorate. A seconda del numero di maglie disponibili in magazzino che viene registrato in Google Sheets, l'immagine (rosso, verde, o blu felpa) con il numero più alto è visualizzata sullo schermo.
seo-description: Questo caso d'uso mostra il magazzino al dettaglio per tre diverse maglie colorate. A seconda del numero di maglie disponibili in magazzino che viene registrato in Google Sheets, l'immagine (rosso, verde, o blu felpa) con il numero più alto è visualizzata sullo schermo.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
translation-type: tm+mt
source-git-commit: a7d3ec582dde83ed6efb08a6c3c6a75cc0820970
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---


# Attivazione mirata inventario vendita al dettaglio {#retail-inventory-targeted-activation}

Il seguente esempio illustra tre diverse immagini basate sui valori di Google Sheet.

## Descrizione {#description}

Questo caso d&#39;uso mostra il magazzino al dettaglio per tre diverse maglie colorate. A seconda del numero di maglie disponibili in magazzino che viene registrato in Google Sheets, l&#39;immagine (rosso, verde, o blu felpa) con il numero più alto è visualizzata sullo schermo.

Per questo caso d&#39;uso, il maglione rosso, verde o blu verrà visualizzato sul vostro schermo in base al valore più alto del numero di maglie che è disponibile.

## Precondizioni {#preconditions}

Prima di iniziare ad implementare l&#39;attivazione del targeting delle scorte per la vendita al dettaglio, è necessario apprendere come impostare ***Data Store***, ***Segmentazione dell&#39;audience*** e ***Enable Targeting for Channels*** in un progetto AEM Screens .

Per informazioni dettagliate, fare riferimento a [Configurazione di ContextHub in  AEM Screens](configuring-context-hub.md).

## Flusso di base {#basic-flow}

Per implementare il caso di utilizzo Attivazione magazzino al dettaglio, effettuate le seguenti operazioni:

1. **Compilazione dei fogli di Google**

   1. Passare al foglio di Google ContextHubDemo.
   1. Aggiungete tre colonne (rosso, verde e blu) con i valori corrispondenti per tre diverse maglie.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurazione dell&#39;audience in base ai requisiti**

   1. Andate ai segmenti del pubblico (fate riferimento a ***Passaggio 2: Impostazione della segmentazione dell&#39;audience*** in **[Configurazione di ContextHub  pagina AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Aggiungete tre nuovi segmenti **For_Red**, **For_Green** e **For_Blue**.

   1. Selezionare **For_Red** e fare clic su **Edit** dalla barra delle azioni.

   1. Trascinare e rilasciare il **Confronto: Proprietà - Property** nell&#39;editor e fare clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/2** dall&#39;elenco a discesa in **First Property name**

   1. Dal menu a discesa, selezionare **Operatore** come **maggiore di**

   1. Selezionare **Tipo di dati** come **numero**

   1. Selezionare **googlesheets/value/1/1** dall&#39;elenco a discesa in **Second Property name**.

   1. Trascinare **un altro confronto: Proprietà - Property** nell&#39;editor e fare clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/2** dall&#39;elenco a discesa in **First Property name**.

   1. Dal menu a discesa, selezionare **Operatore** come **maggiore di**

   1. Selezionare **Data Type** come **number**

   1. Selezionare **googlesheets/value/1/0** dall&#39;elenco a discesa in **Second Property name**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Analogamente, modificate e aggiungete le regole delle proprietà di confronto al segmento **For_Blue** come illustrato nella figura seguente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Analogamente, modificate e aggiungete le regole di proprietà di confronto al segmento** For_Green **come illustrato nella figura seguente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Noterete che per i segmenti **For_Green** e **For_Green**, i dati non possono essere risolti nell&#39;editor perché solo il primo confronto è valido da ora come dai valori nel Google Sheet.

1. Navigare e selezionare il canale **DataDrivenRetail** (un canale di sequenza), quindi fare clic su **Edit** dalla barra delle azioni.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >È necessario impostare la scheda **ContextHub** **Configurations** utilizzando il canale **Properties** —> **Personalization**.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   È necessario selezionare sia il **Marchio** che l&#39; **Area** per elencare correttamente le attività all&#39;avvio del processo di targeting.

1. **Aggiunta di un’immagine predefinita**

   1. Aggiungete un&#39;immagine predefinita al canale e fate clic su **Targeting**.
   1. Selezionare **Marchio** e **Attività** dal menu a discesa, quindi fare clic su **Avvia targeting**.

   1. Fai clic su **Inizia impostazione destinazione**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Prima di iniziare il targeting, è necessario aggiungere i segmenti (**For_Green**, **For_Red** e **For_Blue**) facendo clic su **+ Add Experience Targeting** dalla barra laterale come illustrato nella figura seguente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Aggiungete le immagini a tutti e tre gli scenari, come illustrato di seguito.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Verifica dell’anteprima**

   1. Fare clic su **Anteprima.** Inoltre, aprite il foglio di Google e aggiornate il relativo valore.
   1. Modificate il valore per tutte e tre le colonne e noterete gli aggiornamenti delle immagini di visualizzazione in base al valore più alto nell&#39;inventario.

   ![retail_result](assets/retail_result.gif)

