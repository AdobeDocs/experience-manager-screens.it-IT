---
title: Configurazione di ContextHub in AEM Screens
seo-title: Configurazione di ContextHub in AEM Screens
description: Segui questa pagina per saperne di più su ContextHub nel motore di targeting per definire l'archivio dati allo scopo di modificare il contenuto dell'attivatore dati.
seo-description: Segui questa pagina per saperne di più su ContextHub nel motore di targeting per definire l'archivio dati allo scopo di modificare il contenuto dell'attivatore dati.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 2a36ecd81d250f449e3fa870309674bf2dc771d0

---


# Configurazione di ContextHub in AEM Screens {#configuring-contexthub-in-aem-screens}

In questa sezione viene illustrato come creare e gestire le modifiche delle risorse basate sui dati utilizzando un archivio dati.

## Termini chiave {#key-terms}

Prima di iniziare a creare e gestire canali basati sulle scorte nel progetto AEM Screens, devi conoscere alcuni dei termini chiave importanti e rilevanti per i diversi scenari.

**Marchio** Si riferisce alla descrizione del progetto di alto livello.

**Area** Fa riferimento al nome del progetto AEM Screens, ad esempio Digital Ad Signage

**Attività** Definisce la categoria della regola, ad esempio basata su magazzino, basata su meteo, basata sulla disponibilità del reparto e così via.

**Audience** Definisce la regola.

**Segmento** Si riferisce alla versione della risorsa da riprodurre per la regola data, ad esempio se la temperatura è inferiore a 50 gradi fahrenheit, lo schermo visualizza l&#39;immagine di un caffè caldo altrimenti una bevanda fredda.

Il diagramma seguente fornisce una rappresentazione visiva del modo in cui le configurazioni ContextHub coincidono con l&#39;attività, l&#39;audience e i canali.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Premesse {#preconditions}

Prima di iniziare a configurare le configurazioni Context Hub per un progetto AEM Screens, è necessario configurare Google Sheets (a scopo dimostrativo).

>[!IMPORTANT]
>
>Google Sheets è utilizzato nell&#39;esempio seguente come un sistema di database di esempio da cui i valori vengono recuperati ed è esclusivamente a scopo educativo. Adobe non supporta l&#39;utilizzo di Google Sheets per ambienti di produzione.
>
>Per ulteriori informazioni, consulta [Ottenere la chiave](https://developers.google.com/maps/documentation/javascript/get-api-key) API nella documentazione di Google.

## Passaggio 1: Impostazione di un archivio dati {#step-setting-up-a-data-store}

È possibile impostare l&#39;archivio dati come evento I/O locale o come evento del database locale.

L’esempio seguente illustra le attivazioni dei dati a livello di risorsa per visualizzare un evento del database locale che imposta un archivio dati, ad esempio un foglio Excel, che consente di utilizzare le configurazioni ContextHub e il percorso dei segmenti per il canale AEM Screens.

Una volta impostato correttamente il foglio di Google, ad esempio come illustrato di seguito:

![image](/help/user-guide/assets/context-hub/context-hub1.png)

La seguente convalida è ciò che verrà visualizzato quando si verifica la connessione immettendo i due valori, ID *foglio di* Google e chiave ** API nel formato seguente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![image](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
> L’esempio specifico riportato di seguito mostra i fogli di Google come un archivio dati che attiverà la modifica delle risorse se il valore è superiore a 100 o inferiore a 50.

## Passaggio 2: Impostazione delle configurazioni dello store {#step-setting-store-configurations}

1. **Passaggio a ContextHub**

   Andate all’istanza di AEM e fate clic sull’icona degli strumenti dalla barra laterale sinistra. Fate clic su **Siti** > **ContextHub**, come illustrato nella figura riportata di seguito.

   ![image](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creazione di una nuova configurazione ContextHub Store**

   1. Andate al contenitore di configurazione denominato come **schermate**.

   1. Fate clic su **Crea** > **Crea contenitore** di configurazione e immettete il titolo come **ContextHubDemo**.

      ![image](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Andate** a **ContextHubDemo** > **Crea** configurazione **** ContentHub e fate clic su **Salva**.

      >[!NOTE]
      > Dopo aver fatto clic su **Salva** , verrete visualizzati nella schermata Configurazione **** ContextHub.

   1. Dalla schermata Configurazione **** ContextHub, fate clic su **Crea** > Configurazione **ContentHub Store.**

      ![image](/help/user-guide/assets/context-hub/context-hub5.png)

   1. Immettete il **Titolo** come **Google Sheets**, **Store Name** as **googlesheets**, e **Store Type** **** **** come contexthub.Generic-jsonp e fate clic su Next.

      ![image](/help/user-guide/assets/context-hub/context-hub6.png)

      >[!NOTE]
      >
      >In AEM 6.4, immettete il Titolo **** configurazione come **foglio di calcolo** e il Tipo **** store come **contexthub.Generic-jsonp**.

   1. Immettete la configurazione json specifica. Ad esempio, potete utilizzare il seguente json a scopo dimostrativo e fare clic su **Salva** . Verrà visualizzata la configurazione dello store denominata **Google Sheets** nella configurazione ContextHub.

      >[!IMPORTANT]
      >Sostituite il codice con *&lt;ID foglio>* e *&lt;Chiave API>* che avete recuperato durante la configurazione dei fogli di Google.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      Nel codice di esempio sopra, **pollInterval** definisce la frequenza con cui i valori vengono aggiornati (in ms).
Sostituisci il codice con il tuo *&lt;ID foglio>* e *&lt;Chiave API>* che hai recuperato durante la configurazione dei fogli di Google.

      >[!CAUTION]
      Se create le configurazioni del vostro archivio Google Sheets al di fuori della cartella globale (ad esempio nella cartella del progetto), il targeting non funzionerà.

1. **Impostazione della segmentazione dello store**

   1. Andate a Configurazione **ContentHub Store.** e create un&#39;altra configurazione nel contenitore di configurazione delle schermate e impostate il **Titolo** come **segmentazione-contexthub**, Nome **** archivio come **segmentazione** e Tipo **** **** archivio comeaem.segmentationStore.

      ![image](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
È necessario saltare il processo di definizione del json e lasciarlo vuoto.


## Passaggio 3: Impostazione di segmenti in Audience {#setting-up-audience}

1. **Creazione di segmenti nel pubblico**

   1. Passa dall’istanza di AEM a **Personalizzazione** > **Audience** > **Schermate**.

   1. Fate clic su **Crea** > **Crea segmento hub contesto.** Viene visualizzata la finestra di dialogo **Nuovo segmento** ContextHub.

   1. Enter the **Title** as **Higherthan50** and click **Create**. Analogamente, create un altro segmento denominato **Lowerthan50**.

      ![image](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Seleziona il segmento **Higherthan50** e fai clic su **Proprietà** dalla barra delle azioni.
      ![image](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Selezionate la scheda **Personalizzazione** dalle proprietà **** segmento. Impostate il percorso **** ContextHub su `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Segments Path** su `/conf/screens/settings/wcm/segments` e fate clic su **Save (Salva**), come illustrato nella figura riportata di seguito.

      ![image](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Analogamente, imposta anche il percorso **** ContextHub e il percorso **** dei segmenti per il segmento **inferiore a 50** .

## Passaggio 4: Impostazione del marchio e dell&#39;area {#setting-brand-area}

Segui i passaggi indicati di seguito per creare un marchio nelle tue attività e nella tua area sotto il marchio:

1. **Creazione di un marchio nelle attività**

   1. Passa dall’istanza di AEM a **Personalizzazione** > **Attività**.

   1. Fate clic su **Crea** > **Crea marchio**.

   1. Select **Brand** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. Il marchio viene ora creato come illustrato di seguito.

      ![image](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema noto:
Per aggiungere un&#39;area, rimuovete lo schema dall&#39;URL, ad esempio
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creazione di un’area nel marchio**

   Per creare un&#39;area del marchio, effettuate le seguenti operazioni:

   1. Fate clic su **Crea** , quindi su **Crea area**.

      ![image](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Select **Area** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
Verrà creata un&#39;area nel marchio.

## Passaggio 5: Creazione di segmenti in un&#39;attività {#step-setting-up-audience-segmentation}

Dopo aver configurato un archivio dati e definito l&#39;attività (marchio e area), segui i passaggi descritti di seguito per creare segmenti nell&#39;attività.

1. **Creazione di segmenti nelle attività**

   1. Passa dall’istanza di AEM a **Personalizzazione** > **Attività** > **ScreensBrand** >**ScreensValue**.

   1. Fate clic su **Crea** > **Crea attività.** Viene visualizzata la procedura guidata **Configura attività** .

   1. Immettere il **Titolo** come **ValoreCheck50** e **Nome** come **valorecheck50**. Selezionate il motore **di** targeting come **ContextHub (AEM)** dall&#39;elenco a discesa e fate clic su **Avanti**.

      ![image](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Fate clic su **Aggiungi esperienza** dalla procedura guidata **Configura attività**.

   1. In **Audiences**, selezionate **Higherthan50** e fate clic su **Add Experience** (Aggiungi esperienza **), quindi immettete il** Titolo **come** maggiore di 50 **** **** Namecome più alto di 50. Click **Ok**.

   1. In **Audiences**, selezionate il **valore inferiore a 50** e fate clic su **Add Experience** (Aggiungi esperienza), quindi immettete il **titolo** come **inferiore a 50** **** **** Nomebassocome basso50. Click **Ok**.

      ![image](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Click **Next** and then **Save**. **L&#39;attività ValueCheck50** ora è stata creata e configurata.

      ![image](/help/user-guide/assets/context-hub/context-hub16.png)

## Passaggio 5: Modifica dei segmenti in Audiences{#editing-audience-segmentation}

1. **Modifica dei segmenti**

   1. Passa dall’istanza di AEM a **Personalizzazione** > **Audience** > **Schermate**.

   1. Selezionate il segmento **Superiore a 50** e fate clic su **Modifica** nella barra delle azioni.

   1. Trascinate e rilasciate il **confronto: Proprietà - Componente valore** per l’editor.

   1. Fare clic sull&#39;icona chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con un valore** .

   1. Selezionate **googlesheets/value/1/0** dall’elenco a discesa in Nome **** proprietà.

      >[!NOTE]
I **googlesheets/value/1/0** si riferiscono alla riga 2 e alla colonna come compilati nei google sheet nella figura seguente:

      ![image](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Selezionate **Operatore** come **maggiore di** dal menu a discesa.

   1. Immettere il **valore** come **70**.

      >[!NOTE]
      AEM convalida i dati provenienti da Google Sheet visualizzando il segmento come verde.

      ![image](/help/user-guide/assets/context-hub/context-hub18.png)
   Analogamente, modificate i valori delle proprietà su **Lowerthan50**.

   1. Trascinate e rilasciate il **confronto: Proprietà - Componente valore** per l’editor.

   1. Fare clic sull&#39;icona chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con un valore** .

   1. Selezionate **googlesheets/value/1/0** dall’elenco a discesa in Nome **** proprietà.

   1. Selezionate **Operatore** come **minore di** dal menu a discesa.

   1. Immettere il **valore** come **50**.



## Abilitazione del targeting nei canali {#step-enabling-targeting-in-channels}

Seguite i passaggi indicati di seguito per abilitare il targeting nei canali.

1. Passa a uno dei canali AEM Screens. I passaggi seguenti dimostrano come abilitare il targeting utilizzando **DataDrivenChannel** creato in un canale AEM Screens.

1. Selezionate il canale **TargetChannel** e fate clic su **Proprietà** dalla barra delle azioni.

   ![image](/help/user-guide/assets/context-hub/context-hub19.png)

1. Selezionate la scheda **Personalizzazione** per impostare le configurazioni ContextHub.

   1. Impostate il percorso **** ContextHub su `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Segments Path** su `/conf/screens/settings/wcm/segments` e fate clic su **Save**(Salva).

   1. Click **Save &amp; Close**.

      >[!NOTE]
      Usa ContextHub e il percorso Segments, dove hai salvato inizialmente le configurazioni e i segmenti dell&#39;hub di contesto.

      ![image](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Spostatevi e selezionate il canale **TargetChannel** , quindi fate clic su **Modifica** nella barra delle azioni.

      >[!NOTE]
      Se avete impostato tutto correttamente, l&#39;opzione **Targeting** viene visualizzata nel menu a discesa dall&#39;editor, come illustrato nella figura riportata di seguito.

      ![image](/help/user-guide/assets/context-hub/context-hub21.png)

## Ulteriori informazioni: Esempi di utilizzo {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto AEM Screens, puoi seguire i diversi casi d’uso per comprendere in che modo le risorse attivate dai dati svolgono un ruolo fondamentale nei diversi settori:

1. **[Attivazione mirata inventario vendita al dettaglio](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro viaggio](local-temperature-activation.md)**
1. **[Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)**
