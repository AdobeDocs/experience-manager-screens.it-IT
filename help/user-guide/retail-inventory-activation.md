---
title: Attivazione mirata inventario retail
seo-title: Attivazione mirata inventario retail
description: Questo caso d'uso mostra il magazzino al dettaglio per tre felpe colorate diverse. A seconda del numero di felpe disponibili in magazzino che è registrato in Google Sheets, l'immagine (rosso, verde, o blu felpa) con il numero più alto è visualizzata sullo schermo.
seo-description: Questo caso d'uso mostra il magazzino al dettaglio per tre felpe colorate diverse. A seconda del numero di felpe disponibili in magazzino che è registrato in Google Sheets, l'immagine (rosso, verde, o blu felpa) con il numero più alto è visualizzata sullo schermo.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# Attivazione mirata inventario retail {#retail-inventory-targeted-activation}

Il seguente caso d’uso illustra tre diverse immagini in base ai valori presenti nel foglio di Google.

## Descrizione {#description}

Questo caso d&#39;uso mostra il magazzino al dettaglio per tre felpe colorate diverse. A seconda del numero di felpe disponibili in magazzino che è registrato in Google Sheets, l&#39;immagine (rosso, verde, o blu felpa) con il numero più alto è visualizzata sullo schermo.

Per questo caso d&#39;uso, il maglione rosso, verde o blu verrà visualizzato sul vostro schermo in base al valore più alto del numero di maglioni che è disponibile.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l&#39;attivazione del targeting di inventario per la vendita al dettaglio, devi imparare a configurare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per canali*** in un progetto AEM Screens.

Per informazioni dettagliate, consulta [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) .

## Flusso di base {#basic-flow}

Segui i passaggi seguenti per implementare il caso di utilizzo di Attivazione dell’inventario al dettaglio:

1. **Popolamento dei fogli di Google**

   1. Passa al foglio di Google ContextHubDemo.
   1. Aggiungi tre colonne (rosso, verde e blu) con i corrispondenti valori per tre felpe diverse.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurazione del pubblico in base ai requisiti**

   1. Passa ai segmenti del pubblico (fai riferimento a ***Passaggio 2: Impostazione della segmentazione del pubblico*** nella pagina **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Aggiungi tre nuovi segmenti **For_Red**, **For_Green** e **For_Blue**.

   1. Seleziona **For_Red** e fai clic su **Modifica** nella barra delle azioni.

   1. Trascina e rilascia il **Confronto : Proprietà - Proprietà** all&#39;editor e fai clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/2** dal menu a discesa in **Nome proprietà**

   1. Seleziona **Operatore** come **maggiore di** dal menu a discesa

   1. Seleziona **Tipo di dati** come **numero**

   1. Seleziona **googlesheets/value/1/1** dal menu a discesa in **Secondo nome proprietà**.

   1. Trascina **un altro confronto : Proprietà - Proprietà** all&#39;editor e fai clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/2** dal menu a discesa in **Nome proprietà**.

   1. Seleziona **Operatore** come **maggiore di** dal menu a discesa

   1. Seleziona **Tipo di dati** come **numero**

   1. Seleziona **googlesheets/value/1/0** dal menu a discesa in **Secondo nome proprietà**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Allo stesso modo, modifica e aggiungi le regole delle proprietà di confronto al segmento **For_Blue** come mostrato nella figura seguente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Analogamente, modifica e aggiungi le regole di proprietà di confronto al segmento ** For_Green **come mostrato nella figura seguente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Noterai che per i segmenti **For_Green** e **For_Green**, i dati non possono essere risolti nell&#39;editor in quanto solo il primo confronto è valido a partire da ora secondo i valori di Google Sheet.

1. Naviga e seleziona il canale **DataDrivenRetail** (un canale di sequenza) e fai clic su **Modifica** nella barra delle azioni.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Dovresti aver impostato la scheda **ContextHub** **Configurazioni** utilizzando il canale **Proprietà** —> **Personalizzazione**.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   È necessario selezionare sia il **Marchio** che l&#39; **Area** affinché le attività siano elencate correttamente all&#39;avvio del processo di targeting.

1. **Aggiunta di un’immagine predefinita**

   1. Aggiungi un&#39;immagine predefinita al tuo canale e fai clic su **Targeting**.
   1. Seleziona **Marchio** e **Attività** dal menu a discesa, quindi fai clic su **Avvia targeting**.

   1. Fai clic su **Inizia impostazione destinazione**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Prima di iniziare il targeting, è necessario aggiungere i segmenti (**For_Green**, **For_Red** e **For_Blue**) facendo clic su **+ Aggiungi targeting esperienza** dalla barra laterale come mostrato nella figura seguente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Aggiungi le immagini a tutti e tre gli scenari, come mostrato di seguito.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Controllo dell’anteprima**

   1. Fare clic su **Anteprima.** Inoltre, apri il tuo foglio di Google e aggiorna il suo valore.
   1. Modifica il valore per tutte e tre le colonne e noterai gli aggiornamenti dell&#39;immagine di visualizzazione in base al valore più alto nell&#39;inventario.

   ![retail_result](assets/retail_result.gif)

