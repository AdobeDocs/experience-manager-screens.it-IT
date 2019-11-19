---
title: Canale basato su inventario
seo-title: Canale basato su inventario
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canale basato su inventario{#inventory-driven-channel}

## Guida introduttiva ai canali guidati da magazzino {#getting-started-with-inventory-driven-channels}

In questa sezione viene illustrato un esempio di utilizzo che mette in evidenza la creazione e la gestione di una modifica di risorse basata sui dati tramite Google Sheets.

### Premesse {#preconditions}

Prima di iniziare questo caso di utilizzo, accertatevi di comprendere come:

* **[Creare e gestire canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori primari {#primary-actors}

Autori contenuto

### Terminoli {#terminolgies}

Seguite i termini riportati di seguito che svolgono un ruolo significativo nella comprensione e configurazione del progetto nei diversi casi di utilizzo:

**Attività** fa riferimento alla categoria.

**Area** Progetto principale

**Pubblico** Posizione dei dati

**Marchio** di riferimento

**Segmento** : un contenitore di risorse a cui si sta tentando di eseguire il targeting.

### Flusso di base: Impostazione del progetto {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**Prerequisito:**
>
>Prima di approfondire i dettagli relativi alla configurazione e all’utilizzo di modifiche di risorse basate sui dati nel progetto, accertati di creare un progetto AEM Screens con un canale di sequenza. A scopo dimostrativo, viene creato un progetto denominato **DataDrivenAsset** e al progetto vengono aggiunti canali di sequenza denominati **DataDrivenRestaurant**, **DataDrivenTextOverlay**, **DataDrivenWeather** e **DataDrivenRetail** , come illustrato nella figura seguente.
>
>La creazione di quattro canali diversi è solo a scopo dimostrativo e presenta quattro casi d’uso diversi in diversi canali. Se desiderate seguire un solo caso d'uso come vostro requisito, non esitate a creare un solo canale di sequenza.

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

Seguite le sezioni seguenti per creare un progetto di esempio sulla creazione e gestione di una modifica di risorse basata sui dati tramite Google Sheets in un progetto AEM Screens:

## Passaggio 1: Impostazione del database {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets è utilizzato nel seguente sistema di database di esempio da cui i valori vengono recuperati ed è esclusivamente a scopo educativo. Adobe non supporta l'utilizzo di Google Sheets per ambienti di produzione.
>
>Per ulteriori informazioni, consulta [Ottenere la chiave](https://developers.google.com/maps/documentation/javascript/get-api-key) API nella documentazione di Google.

1. Accedi a Google Docs.

   >[!NOTE]
   >
   >Prima di creare un nuovo Google Sheet è necessario disporre di un account in Google Drive.

1. Avviate un nuovo foglio di calcolo vuoto. Aggiungete il contenuto al vostro foglio di Google e salvatelo. A scopo dimostrativo, Google Sheet è denominato **ContextHubDemo**.
1. Fate clic su **Condividi** nell’angolo in alto a destra del foglio di Google per aprire la finestra di dialogo **Condividi con altri** . Fate clic su **Avanzate** e modificate le impostazioni su **Attivato - Chiunque abbia il collegamento**, come illustrato nella figura riportata di seguito.

   Questo passaggio consente di accedere ai valori nel foglio di Google.

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. Quando fate clic su **Salva** dal passaggio precedente, riceverete il collegamento per Google Sheet. Salvate il clic per i riferimenti futuri e fate clic su **Fine**.

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets è utilizzato nell'esempio seguente per scopi educativi. Adobe non supporta l'utilizzo di Google Sheets per ambienti di produzione.

## Passaggio 2: Abilitazione delle API REST di Google Sheets {#step-enabling-the-google-sheets-rest-apis}

Una volta configurato il tuo Google Sheet, devi abilitare Google Sheet REST API per accedere ai valori.

Per informazioni su come abilitare le API REST per Google Sheets, consulta la documentazione delle API Google.

1. Andate a [Google API Console](https://console.developers.google.com/apis/credentials). Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. Immettete Nome **** progetto come **AssetChange** e fate clic su **CREATE**.
1. Una volta creato il progetto, è necessario impostare la chiave API. Fate clic su **Crea credenziali** e selezionate **Chiave API **per generare la chiave API per il progetto. Salvate la chiave API per i riferimenti futuri.

   >[!NOTE]
   >
   >Questo progetto dimostrativo utilizza la chiave API gratuita di Google. Per ulteriori informazioni, potrebbe essere utile fare riferimento a prezzi e restrizioni sul sito Web Google **Get API Key** .

### Verifica della configurazione di Google Sheets {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;ID foglio&gt;/values/Sheet1?key=&lt;chiave API&gt;

Esempio:

Se il collegamento** Google Sheets** è *il seguente:*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`, quindi

**Id** foglio: `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**Chiave** API: `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Aggiungendo entrambi i valori nella sintassi precedente:

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Ora è possibile visualizzare i dati nel foglio.

## Passaggio 2: Configurazione di AEM per recuperare il contenuto dei Google Sheets {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

La sezione seguente descrive come configurare Adobe Experience Manager (AEM) per recuperare contenuti dai Google Sheets.

1. Andate all’istanza di AEM e fate clic sull’icona degli strumenti dalla barra laterale sinistra. Fate clic su **Siti** &gt; **ContextHub**, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Creare una nuova configurazione ContextHub Store**

   1. Passa a **globale** &gt; **predefinito** &gt; Configurazione **** ContextHub.

   1. Fate clic su** Crea &gt; Contenitore di configurazione **e immettete il titolo come** ContextHubDemo**.

   1. **** Andate **a** ContextHubDemo **&gt; Configurazione** ContentHub Store... per aprire la procedura guidata **Configura**
   1. Inserite il **Titolo** come **Google Sheets**, **Store Name** as **googlesheets**, e **Store Type** **comecontexthub.Generic-jsonp**
   1. Fai clic su **Avanti**
   1. Immettete la configurazione json specifica. Ad esempio, potete utilizzare il seguente json a scopo dimostrativo.
   1. Fai clic su **Salva**.

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >Nel codice di esempio sopra, **pollInterval** definisce la frequenza con cui i valori vengono aggiornati (in ms).
   >
   >
   >Sostituisci il codice con *&lt;ID foglio&gt;* e *&lt;Chiave API&gt;* recuperato dal **passaggio 1: Impostazione del database.**

   >[!CAUTION]
   Se create le configurazioni del vostro archivio Google Sheets al di fuori della cartella precedente (ad esempio nella cartella del progetto), il targeting non funzionerà.
   Se desiderate configurare le configurazioni dell'archivio Google Sheets al di fuori della cartella legacy globale, dovete impostare **Store Name** come **segmentazione** e **Store Type** come **aem.segmentation**. Inoltre, devi saltare il processo di definizione del json come definito sopra.

1. **Creazione di un marchio nelle attività**

   1. Passa dall’istanza AEM a **Personalizzazione** &gt; **Attività**

   1. Fai clic su** Crea** &gt; **Crea marchio**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. Il marchio viene ora creato come illustrato di seguito.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
Problema noto:
Per aggiungere un'area, rimuovete lo schema dall'URL, ad esempio
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. Creazione di un'area nel marchio**

   1. Fate clic su **Crea** &gt; **Crea area**

   1. Select **Area** from the** Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**. L'area verrà creata nell'attività.

1. **Creazione di segmenti nel pubblico**

   1. Passa dall’istanza AEM a **Personalizzazione** &gt; **Audience** &gt; **We.Retail**.
   1. Fate clic su **Crea** &gt; **Crea segmento** hub contesto. Si apre la finestra di dialogo Nuovo segmento ContextHub.
   1. Enter the **Title** as **SheetA1 1** and click **Create**. Analogamente, create un altro segmento denominato **SheetA2 2**.

1. **Modifica dei segmenti**

   1. Selezionate i **fogli di segmento A1 1** (creati nel passaggio (5)), quindi fate clic su **Modifica** nella barra delle azioni.

   1. Trascinate e rilasciate il **confronto: Proprietà - Componente valore** per l’editor.
   1. Fare clic sull'icona chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con un valore** .
   1. Selezionate **googlesheets/value/1/0** dall’elenco a discesa in Nome **** proprietà.

   1. Selezionare **Operatore** come **Equal **dal menu a discesa.

   1. Immettere il **valore** come **1**.
   >[!NOTE]
   AEM convalida i dati provenienti da Google Sheet visualizzando il segmento come verde.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   Allo stesso modo, modificate i valori delle proprietà in **Fogli A1 2**.

   1. Trascinate e rilasciate il **confronto: Proprietà - Componente valore** per l’editor.
   1. Fare clic sull'icona chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con un valore** .
   1. Selezionate **googlesheets/value/1/0** dall’elenco a discesa in Nome **** proprietà.

   1. Selezionare **Operatore** come **Equal **dal menu a discesa.

   1. Immettere il **valore** come **2**.
   >[!NOTE]
   Le regole applicate nei passaggi precedenti sono solo un esempio di come impostare i segmenti per l'implementazione dei seguenti casi di utilizzo.

## Passaggio 3: Impostazione delle configurazioni Context Hub nel canale AEM Screens {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

Segui i passaggi indicati di seguito per configurare le configurazioni ContextHub e il percorso dei segmenti per il canale AEM Screens.

1. Passa a uno dei canali AEM Screens (**DataDrivenRetail**) creati dall'utente come prerequisito.
1. Seleziona il canale (**DataDrivenRetail**) e fai clic su **Proprietà** dalla barra delle azioni.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Selezionate la scheda **Personalizzazione** per impostare le configurazioni ContextHub.

   1. Selezionate **ContextHub Path** come **libs** &gt; **settings** &gt; **cloud settings** &gt; **default** **** ****&gt;ContextHub Configurations, quindi fate clic suSelect.

   1. Selezionare il percorso **** Segmenti come **conf** &gt; **We.Retail **&gt; **impostazioni** &gt; **wcm** &gt; **segmenti** **** e fare clic su Seleziona.

   1. Fate clic su **Salva e chiudi**.
   >[!NOTE]
   Usa ContextHub e il percorso Segments, dove hai salvato inizialmente le configurazioni e i segmenti dell'hub di contesto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   Se non selezionate il **marchio** in Configurazione **** di targeting nella finestra di dialogo precedente, dovrete selezionare il marchio e l'attività all'avvio del processo di impostazione del targeting.

1. Selezionare **DataDrivenRetail** da **DataDrivenAssets** &gt; **Channels **e fare clic su **Edit** dalla barra delle azioni.

   >[!NOTE]
   Se avete impostato tutto correttamente, l'opzione **Targeting** viene visualizzata nel menu a discesa dall'editor, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Una volta configurate le configurazioni ContextHub per il canale, accertatevi di seguire i passaggi precedenti da 1 a 4, anche per gli altri tre canali di sequenza se desiderate seguire tutti i casi di utilizzo indicati di seguito.

## Caso d’uso 1: Attivazione magazzino al dettaglio {#use-case-retail-inventory-activation}

Il seguente esempio illustra tre diverse immagini basate sui valori di Google Sheet.

### Descrizione {#description}

Questo caso d'uso mostra il magazzino al dettaglio per tre diverse maglie colorate. A seconda del numero di maglie disponibili in magazzino che viene registrato in Google Sheets, l'immagine (rosso, verde, o blu felpa) con il numero più alto è visualizzata sullo schermo.

Per questo caso d'uso, il maglione rosso, verde o blu verrà visualizzato sul vostro schermo in base al valore più alto del numero di maglie che è disponibile.

### Procedura {#procedure}

Per implementare il caso di utilizzo Attivazione magazzino al dettaglio, effettuate le seguenti operazioni:

1. **Compilazione dei fogli di Google**

   1. Passare al foglio di Google ContextHubDemo.
   1. Aggiungete tre colonne (rosso, verde e blu) con i valori corrispondenti per tre diverse maglie.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurazione dell'audience in base ai requisiti**

   1. Andate ai segmenti nel pubblico (creati nel passaggio 5 della sezione ***Passaggio 2): Configurazione di AEM per recuperare il contenuto dei Google Sheets***).
   1. Aggiungete tre nuovi segmenti **For_Red**, **For_Green** e **For_Blue**.

   1. Selezionate **For_Red** e fate clic su **Modifica** nella barra delle azioni.

   1. Trascina e rilascia il **confronto: Proprietà - Proprietà** per l'editor e fare clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/2** dall'elenco a discesa in **Nome proprietà**

   1. Selezionare l' **operatore** come **maggiore di **dal menu a discesa

   1. Seleziona tipo **di** dati come **numero**

   1. Selezionare **googlesheets/value/1/1** dall'elenco a discesa in **Secondo nome proprietà**

   1. Trascinare e rilasciare **un altro confronto: Proprietà - Proprietà **nell'editor e fai clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/2** dall'elenco a discesa in **Nome proprietà**

   1. Selezionare l' **operatore** come **maggiore di **dal menu a discesa

   1. Seleziona tipo **di** dati come **numero**

   1. Selezionare **googlesheets/value/1/0** dall'elenco a discesa in **Secondo nome proprietà**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Analogamente, modificate e aggiungete le regole delle proprietà di confronto al segmento **For_Blue** come illustrato nella figura seguente:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Analogamente, modificate e aggiungete le regole di proprietà di confronto al segmento** For_Green **come illustrato nella figura seguente:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   Noterete che per i segmenti **For_Green** e **For_Green**, i dati non possono essere caricati nell'editor in quanto solo il primo confronto è valido da ora come dai valori in Google Sheet.

1. Selezionate il canale **DataDrivenRetail **o (un canale di sequenza) e fate clic su **Modifica** nella barra di azione.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   Avreste dovuto configurare le vostre **configurazioniContextHub** **configurando** il canale **Proprietà** —&gt; scheda **Personalizzazione** .

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Se non aggiungete il **marchio** in Configurazioni **di** targeting durante la configurazione di **ContextHub Configurazioni** per il progetto, come illustrato nell'immagine qui sopra, è necessario selezionare il **marchio** e l' **attività** quando si avvia il processo di targeting, nel passaggio successivo.

1. **Aggiunta di un’immagine predefinita**

   1. Aggiungete un'immagine predefinita al canale e fate clic su **Targeting**.
   1. Selezionate **Marchio** e **Attività** dal menu a discesa e fate clic su **Avvia targeting**.

   1. Fai clic su **Inizia impostazione destinazione**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Prima di iniziare il targeting, è necessario aggiungere i segmenti (**For_Green**, **For_Red** e **For_Blue**) facendo clic su **+ Aggiungi targeting** esperienza dalla barra laterale come mostrato nella figura seguente.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Aggiungete le immagini a tutti e tre gli scenari, come illustrato di seguito.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Verifica dell’anteprima**

   1. Fate clic su **Anteprima.** Inoltre, aprite il foglio di Google e aggiornate il relativo valore.
   1. Modificate il valore per tutte e tre le colonne e noterete gli aggiornamenti delle immagini di visualizzazione in base al valore più alto nell'inventario.
   ![retail_result](assets/retail_result.gif)

## Caso d’uso 2: Attivazione del tempo nel centro viaggi {#use-case-travel-center-weather-activation}

Il seguente esempio illustra due diverse immagini basate sui valori di Google Sheet.

### Descrizione {#description-1}

Per questo caso d'uso, se il tuo Google Sheets ha un Valore inferiore a 50, verrà visualizzata un'immagine con bevande calde e se il valore è maggiore o uguale a 50, verrà visualizzata l'immagine con bevande fredde. In caso di un altro valore o nessun valore, il lettore visualizzerà un'immagine predefinita.

### Procedura {#procedure-1}

Segui i passaggi indicati di seguito per implementare il caso di attivazione del tempo del centro viaggi per il tuo progetto AEM Screens:

1. **Compilazione dei fogli di Google**

   1. Passare al foglio di Google ContextHubDemo.
   1. Aggiungete una colonna con **Titolo1** con il valore corrispondente per la temperatura.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Andate ai segmenti nel pubblico (creati nel passaggio 5 della sezione ***Passaggio 2): Configurazione di AEM per recuperare il contenuto dei Google Sheets***).
   1. Selezionare i **fogli A1 1** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/0** dall'elenco a discesa in Nome **proprietà**

   1. Selezionare l' **operatore** come **maggiore o uguale a **dal menu a discesa

   1. Immettere il **valore** come **50**

   1. Analogamente, selezionare i Fogli** A1 2 **e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/0** dall'elenco a discesa in Nome **proprietà**

   1. Selezionare l' **operatore** come **less-than **dal menu a discesa

   1. Immettere il **valore** come **50**

1. Spostatevi e selezionate il canale (), quindi fate clic su **Modifica** nella barra delle azioni. Nell'esempio seguente, **DataDrivenWeather**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   Il canale deve già avere un'immagine predefinita e il pubblico deve essere preconfigurato come descritto nel passaggio (3)

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   Avreste dovuto configurare le vostre **configurazioniContextHub** **configurando** il canale **Proprietà** —&gt; scheda **Personalizzazione** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   Se non aggiungete il **marchio** in Configurazioni **di** targeting durante la configurazione di **ContextHub Configurazioni** per il progetto, come illustrato nell'immagine qui sopra, è necessario selezionare il **marchio** e l' **attività** quando si avvia il processo di targeting, nel passaggio successivo.

1. Selezionate **Targeting** dall'editor, selezionate **Marchio** e **Attività** dal menu a discesa, quindi fate clic su **Avvia targeting**.

   >[!NOTE]
   Se hai aggiunto il **marchio** in Configurazioni **di** targeting durante la configurazione delle configurazioni **** ContextHub per il progetto, non devi selezionare il **marchio** e l' **attività** in questo passaggio.

   ![new_activity3](assets/new_activity3.gif)

1. Verifica dell’anteprima

   1. Fate clic su **Anteprima.** Inoltre, aprite il foglio di Google e aggiornate il relativo valore.
   1. Modificate il valore impostando un valore inferiore a 50, dovreste essere in grado di visualizzare l'immagine delle bevande estive. Se il valore in Google Sheet è 50 o maggiore di quanto dovrebbe essere in grado di visualizzare l'immagine di una bevanda calda.
   ![result3](assets/result3.gif)

## Caso d’uso 3:Attivazione prenotazione ospitalità {#use-case-hospitality-reservation-activation}

Il seguente caso di utilizzo illustra due diverse immagini basate sui valori e sulla formula applicata in Google Sheet.

### Descrizione {#description-2}

Per questo caso d'uso, Google Sheet è popolato con percentuale di prenotazione su due ristoranti **Ristorante1** e **Ristorante2**. Una formula viene applicata in base ai valori di Restaurant1 e Restaurant2 e in base alla formula, il valore 1 o 2 viene assegnato alla colonna **AdTarget** .

Se il **Ristorante1** &gt; **Ristorante2**, il valore **AdTaget** è 1, altrimenti **AdTarget** è assegnato il valore 2. Il valore 1 genera l'opzione *Bistecca food* e il valore 2 mostra l'opzione *Thai food* sullo schermo.

### Approccio procedurale {#procedural-approach}

Segui i passaggi indicati di seguito per implementare il caso d’uso per l’attivazione della prenotazione di ospitalità per il progetto AEM Screens:

1. Compilazione dei fogli di Google e aggiunta della formula.

   Ad esempio, applicare la formula alla terza colonna **AdTarget**, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Andate ai segmenti nel pubblico (creati nel passaggio 5 della sezione ***Passaggio 2): Configurazione di AEM per recuperare il contenuto dei Google Sheets***).
   1. Selezionare i **fogli A1 1** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionate **googlesheets/value/1/2** dall’elenco a discesa in Nome **proprietà**

   1. Selezionare l' **operatore** come **uguale **dal menu a discesa

   1. Immettere il **valore** come **1**

   1. Analogamente, selezionare i Fogli** A1 2 **e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionate **googlesheets/value/1/2** dall’elenco a discesa in Nome **proprietà**

   1. Selezionare l' **operatore** come **2**

1. Spostatevi e selezionate il canale (), quindi fate clic su **Modifica** nella barra delle azioni. Nell'esempio seguente, **DataDrivenRestaurant**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   Il canale deve già avere un'immagine predefinita e il pubblico deve essere pre-configurato come descritto nel passaggio (3).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   Avreste dovuto configurare le vostre **configurazioniContextHub** **configurando** il canale **Proprietà** —&gt; scheda **Personalizzazione** .

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   Se non aggiungete il **marchio** in Configurazioni **di** targeting durante la configurazione di **ContextHub Configurazioni** per il progetto, come illustrato nell'immagine qui sopra, è necessario selezionare il **marchio** e l' **attività** quando si avvia il processo di targeting, nel passaggio successivo.

1. Selezionate **Targeting** dall'editor, selezionate **Marchio** e **Attività** dal menu a discesa, quindi fate clic su **Avvia targeting**.
1. Verifica dell’anteprima

   1. Fate clic su **Anteprima.** Inoltre, aprite il foglio di Google e aggiornate il relativo valore.
   1. Modificare il valore in Ristorante1 &gt; Ristorante2, si dovrebbe essere in grado di visualizzare l'immagine di una bistecca foto e Ristorante1 &lt; Ristorante12, si dovrebbe essere in grado di visualizzare la foto del cibo sul vostro schermo.
   ![result5](assets/result5.gif)

## Caso d’uso 4: Sovrapposizione testo bacheca digitale {#use-case-digital-menu-board-text-overlay}

Il seguente esempio illustra un caso di utilizzo della scheda di menu digitale comunemente diffuso nei ristoranti e nelle giunzioni fast food.

### Descrizione {#description-3}

Il seguente caso d’uso descrive l’utilizzo della sovrapposizione di testo in un canale sequenziale e come l’aggiornamento del valore del prezzo in Google Sheets attivi un aggiornamento nell’aggiornamento del componente della sovrapposizione di testo.

### Approccio procedurale {#procedural-approach-1}

Per implementare la scheda di menu digitale con le sovrapposizioni di testo, seguite i passaggi indicati di seguito:

1. **Compilazione dei fogli di Google**

   1. Passate ai vostri Google Sheets.
   1. Aggiungete una colonna con il valore del prezzo per il caso di utilizzo, come illustrato nella figura riportata di seguito.
   ![screen_shot_2019-05-05at111344 am](assets/screen_shot_2019-05-05at111344am.png)

1. **Aggiunta di un’immagine al canale della sequenza**

   1. Naviga e seleziona il canale (**DataDrivenAssets** —&gt; **Canali** —&gt; **DataDrivenTextOverlay**).

   1. Fai clic su **Modifica** nella barra delle azioni per aprire l'editor.
   1. Trascinate e rilasciate un’immagine della torta di mele nell’editor.
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **Aggiunta di sovrapposizione testo all’immagine**

   1. Selezionate l’immagine nell’editor e fate clic su Configura.
   1. Passate alla scheda Sovrapposizione **** testo e aggiungete la sovrapposizione di testo all’immagine. Per ottenere il valore dai tuoi Google Sheets, accertati che il valore sia racchiuso tra le parentesi graffe. Ad esempio, il prezzo viene recuperato dai fogli di Google e viene indicato come **{price}** durante la definizione della sovrapposizione di testo.

   1. Andate alla scheda **ContextHub** e configurate il valore che deve essere recuperato dai fogli di Google, come mostrato nella figura seguente.
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **Verifica dell’anteprima**

   <!-- Edit text in steps below. wonky-->

   1. Fate clic su **Anteprima**.  Inoltre, aprite il foglio di Google e aggiornate il relativo valore.
   1. Modificate il **prezzo** inferiore e noterete che il valore utilizzato nella sovrapposizione di testo viene aggiornato di conseguenza, come mostrato nella figura seguente.
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
