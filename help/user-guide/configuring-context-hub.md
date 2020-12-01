---
title: Configurazione di ContextHub in  AEM Screens
seo-title: Configurazione di ContextHub in  AEM Screens
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
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 1%

---


# Configurazione di ContextHub in  AEM Screens {#configuring-contexthub-in-aem-screens}

In questa sezione viene illustrato come creare e gestire le modifiche delle risorse basate sui dati utilizzando un archivio dati.

## Termini chiave {#key-terms}

Prima di iniziare a creare e gestire canali basati sulle scorte nel progetto AEM Screens , è necessario conoscere alcuni dei termini chiave importanti e rilevanti per i diversi scenari.

**** Marchio: si riferisce alla descrizione del progetto di alto livello.

**** AreaIndica il nome  progetto AEM Screens, ad esempio Digital Ad Signage

**** AttivitàDefinisce la categoria della regola, ad esempio basata su magazzino, basata su meteo, basata sulla disponibilità del reparto e così via.

**** AudienceDefinisce la regola.

**** SegmentIndica la versione della risorsa da riprodurre per la regola specificata, ad esempio se la temperatura è inferiore a 50 gradi fahrenheit, lo schermo visualizza un&#39;immagine di un caffè caldo altrimenti una bevanda fredda.

Il diagramma seguente fornisce una rappresentazione visiva del modo in cui le configurazioni ContextHub coincidono con l&#39;attività, l&#39;audience e i canali.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Precondizioni {#preconditions}

Prima di iniziare a configurare le configurazioni Context Hub per un progetto AEM Screens , devi configurare Google Sheets (a scopo dimostrativo).

>[!IMPORTANT]
>
>Google Sheets è utilizzato nell&#39;esempio seguente come un sistema di database di esempio da cui i valori vengono recuperati ed è esclusivamente a scopo educativo.  Adobe non supporta l&#39;utilizzo di Google Sheets per gli ambienti di produzione.
>
>Per ulteriori informazioni, consultare [Ottieni chiave API](https://developers.google.com/maps/documentation/javascript/get-api-key) nella documentazione di Google.

## Passaggio 1: Impostazione di un archivio dati {#step-setting-up-a-data-store}

È possibile impostare l&#39;archivio dati come evento I/O locale o come evento del database locale.

L&#39;esempio seguente illustra le attivazioni dei dati a livello di risorsa per mostrare un evento del database locale che imposta un archivio dati, ad esempio un foglio Excel, che consente di utilizzare le configurazioni ContextHub e il percorso dei segmenti per  canale AEM Screens.

Una volta impostato correttamente il foglio di Google, ad esempio come illustrato di seguito:

![immagine](/help/user-guide/assets/context-hub/context-hub1.png)

La seguente convalida è ciò che verrà visualizzato quando si verifica la connessione immettendo i due valori: *ID foglio di Google* e *Chiave API* nel formato seguente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![immagine](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>L’esempio specifico riportato di seguito mostra i fogli di Google come un archivio dati che attiverà la modifica delle risorse se il valore è superiore a 100 o inferiore a 50.

## Passaggio 2: Impostazione delle configurazioni dello store {#step-setting-store-configurations}

1. **Passaggio a ContextHub**

   Passate all’istanza AEM e fate clic sull’icona degli strumenti dalla barra laterale sinistra. Fare clic su **Sites** —> **ContextHub**, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creazione di una nuova configurazione ContextHub Store**

   1. Andate al contenitore di configurazione denominato **screens**.

   1. Fare clic su **Crea** > **Crea contenitore di configurazione** e inserire il titolo come **ContextHubDemo**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Andate** a  **ContextHubDemo** >  **** **CreateContentHub** Configuratione fate clic su  **Salva**.

      >[!NOTE]
      > Dopo aver fatto clic su **Save**, sarà visualizzata la schermata **ContextHub Configuration**.

   1. Dalla schermata **Configurazione ContextHub**, fare clic su **Crea** > **Configurazione ContentHub Store..**

      ![immagine](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >Come parte del Feature Pack 4 AEM 6.5 o del Feature Pack 8 AEM 6.4, i clienti devono aggiornare `/conf/screens/settings/cloudsettings` a `sling:Folder`.
      >
      >Effettua le seguenti operazioni:
      >
      >1. Passare al CRXDE Lite e quindi a `/conf/screens/settings/cloudsettings`.
      >1. Controllare se `cloudsettings jcr:primaryType` è in `sling:Folder`. Se `jcr:primaryType` non è in `sling:folder`, procedere con i passaggi successivi.
      >1. Fare clic con il pulsante destro del mouse su `/conf/screens/settings` e creare un nuovo nodo con *name* come **cloud settings1** e *Type* come **sling:Folder** e salvare le modifiche.
      >1. Spostate tutti i nodi sotto `/conf/screens/settings/cloudsettings` in `cloudsettings1`.
      >1. Eliminare `cloudsettings` e salvare.
      >1. Rinominare `cloudsettings1` in `cloudsettings` e salvare.
      >1. A questo punto, è opportuno notare che /conf/screens/settings/cloudsettings ha `jcr:primaryType` come `sling:Folder`.

      >
      >Prima o dopo l’aggiornamento, effettuate le seguenti operazioni in fase di creazione e pubblicazione.

   1. Inserire il **Titolo** come **Fogli di Google**, **Nome store** come **googlesheets** e **Tipo store** come **contexthub.Generic-jsonp** e fare clic **Next**.

      >[!CAUTION]
      >Se utilizzate Adobe Experience Manager (AEM) 6.4, immettete il **Titolo configurazione** come **googlesheets** e il **Tipo store** come **contexthub.Generic-jsonp**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Immettete la configurazione json specifica. Ad esempio, potete utilizzare il seguente json a scopo dimostrativo e fare clic su **Salva** e vedrete la configurazione dello store denominata **Google Sheets** nella configurazione ContextHub.

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
      Sostituite il codice con l&#39; *&lt;ID foglio>* e *&lt;Chiave API>* che avete recuperato durante la configurazione dei fogli di Google.

      >[!CAUTION]
      Se create le configurazioni del vostro archivio Google Sheets al di fuori della cartella globale (ad esempio nella cartella del progetto), il targeting non funzionerà.


1. **Impostazione della segmentazione dello store**

   1. Andate a **Configurazione ContentHub Store.** e create un&#39;altra configurazione dello store nel contenitore di configurazione delle schermate e impostate  **** Titleas  **segmentation-contexthub**,  **Store** Name  **** segmentatione  **Store** Typeas  **aem.segmentation**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Fare clic su **Next**, quindi su **Save**.

      >[!NOTE]
È necessario saltare il processo di definizione del json e lasciarlo vuoto.


## Passaggio 3: Impostazione dei segmenti in Audience {#setting-up-audience}

1. **Creazione di segmenti nel pubblico**

   1. Passa dall&#39;istanza AEM a **Personalizzazione** > **Audiences** > **schermi**.

   1. Fare clic su **Crea** > **Crea segmento di Context Hub.** Viene visualizzata la finestra di dialogo  **Nuovo** segmento ContextHub.

   1. Immettere il **Titolo** come **Superiore a 50** e fare clic su **Crea**. Analogamente, create un altro segmento denominato **Lowerthan50**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Selezionare il segmento **Higherthan50** e fare clic su **Properties** dalla barra delle azioni.
      ![immagine](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Selezionare la scheda **Personalizzazione** dalla scheda **Proprietà segmento**. Impostate **ContextHub Path** su `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Segments Path** su `/conf/screens/settings/wcm/segments` e fate clic su **Save**, come illustrato nella figura riportata di seguito.

      ![immagine](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Allo stesso modo, imposta anche il segmento **ContextHub Path** e **Segments Path** per **Lowerthan50**.

## Passaggio 4: Impostazione del marchio e dell&#39;area {#setting-brand-area}

Segui i passaggi indicati di seguito per creare un marchio nelle tue attività e nella tua area sotto il marchio:

1. **Creazione di un marchio nelle attività**

   1. Passa dall&#39;istanza AEM a **Personalizzazione** > **Attività**.

   1. Fare clic su **Crea** > **Crea marchio**.

   1. Selezionare **Marchio** dalla procedura guidata **Crea pagina** e fare clic su **Avanti**.

   1. Immettete il **Titolo** come **ScreensBrand** e fate clic su **Crea**. Il marchio viene ora creato come illustrato di seguito.

      ![immagine](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema noto:
Per aggiungere un&#39;area, rimuovete lo schema dall&#39;URL, ad esempio
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creazione di un’area nel marchio**

   Per creare un&#39;area del marchio, effettuate le seguenti operazioni:

   1. Fare clic su **Crea**, quindi su **Crea area**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Selezionare **Area** dalla procedura guidata **Crea pagina** e fare clic su **Avanti**.

   1. Immettete il **Titolo** come **ScreensValue** e fate clic su **Crea**.
Verrà creata un&#39;area nel marchio.

## Passaggio 5: Creazione di segmenti in un&#39;attività {#step-setting-up-audience-segmentation}

Dopo aver configurato un archivio dati e definito l&#39;attività (marchio e area), segui i passaggi descritti di seguito per creare segmenti nell&#39;attività.

1. **Creazione di segmenti nelle attività**

   1. Passa dall&#39;istanza AEM a **Personalizzazione** > **Attività** > **ScreensBrand** >**ScreensValue**.

   1. Fare clic su **Crea** > **Crea attività.** Le Procedure  **Guidate Configura Attività** .

   1. Immettere il **Titolo** come **ValoreCheck50** e **Nome** come **valoreCheck50**. Selezionate il **motore di targeting** come **ContextHub (AEM)** dal menu a discesa e fate clic su **Next**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Fare clic su **Aggiungi esperienza** dalla **Configura attività guidata**.

   1. In **Audiences**, selezionare il **Higherthan50** e fare clic su **Add Experience** e inserire il **Title** come **Higherthan50** **Name** 12/>superiore a 50 **.** Fare clic su **Ok**.

   1. In **Audiences**, selezionare il **Lowerthan50** e fare clic su **Add Experience** e inserire il **Title** come **lowerthan50** **Name** come a12/>Lower50 **.** Fare clic su **Ok**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Fare clic su **Next**, quindi su **Save**. **L&#39;** attività ValueCheck50 ora è stata creata e configurata.

      ![immagine](/help/user-guide/assets/context-hub/context-hub16.png)

## Passaggio 5: Modifica dei segmenti in Audiences{#editing-audience-segmentation}

1. **Modifica dei segmenti**

   1. Passa dall&#39;istanza AEM a **Personalizzazione** > **Audiences** > **schermi**.

   1. Selezionare il segmento **Superiore a 50**, quindi fare clic su **Modifica** dalla barra delle azioni.

   1. Trascinare e rilasciare il confronto **: Proprietà - Componente Value** nell&#39;editor.

   1. Fare clic sull&#39;icona chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con valore**.

   1. Selezionare **googlesheets/value/1/0** dall&#39;elenco a discesa in **Nome proprietà**.

      >[!NOTE]
I  **googlesheets/value/1/0** si riferiscono alla riga 2 e alla colonna come compilati nei google sheet nella figura seguente:

      ![immagine](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Selezionare **Operatore** come **maggiore di** dal menu a discesa.

   1. Immettere il **Valore** come **70**.

      >[!NOTE]
      Il AEM convalida i dati provenienti da Google Sheet mostrando il segmento come verde.

      ![immagine](/help/user-guide/assets/context-hub/context-hub18.png)
   Allo stesso modo, modificate i valori delle proprietà in **Lowerthan50**.

   1. Trascinare e rilasciare il confronto **: Proprietà - Componente Value** nell&#39;editor.

   1. Fare clic sull&#39;icona chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con valore**.

   1. Selezionare **googlesheets/value/1/0** dall&#39;elenco a discesa in **Nome proprietà**.

   1. Selezionare **Operatore** come **minore di** dal menu a discesa.

   1. Immettere il **Valore** come **50**.



## Abilitazione del targeting nei canali {#step-enabling-targeting-in-channels}

Seguite i passaggi indicati di seguito per abilitare il targeting nei canali.

1. Andate a uno dei canali AEM Screens . I passaggi seguenti dimostrano come abilitare il targeting utilizzando **DataDrivenChannel** creato in un canale AEM Screens .

1. Selezionare il canale **TargetChannel** e fare clic su **Properties** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/context-hub/context-hub19.png)

1. Selezionate la scheda **Personalizzazione** per impostare le configurazioni ContextHub.

   1. Impostate il percorso **ContextHub** su `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Segments Path** su `/conf/screens/settings/wcm/segments` e fate clic su **Save**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      Usa ContextHub e il percorso Segments, dove hai salvato inizialmente le configurazioni e i segmenti dell&#39;hub di contesto.

      ![immagine](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Navigare e selezionare il canale **TargetChannel** e fare clic su **Edit** dalla barra delle azioni.

      >[!NOTE]
      Se avete impostato tutto correttamente, nel menu a discesa dell&#39;editor verrà visualizzata l&#39;opzione **Targeting**, come illustrato nella figura riportata di seguito.

      ![immagine](/help/user-guide/assets/context-hub/context-hub21.png)

## Ulteriori informazioni: Esempi di utilizzo {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto  AEM Screens, potete seguire i diversi casi d’uso per comprendere in che modo le risorse attivate dai dati svolgono un ruolo fondamentale nei diversi settori:

1. **[Attivazione mirata inventario vendita al dettaglio](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro viaggio](local-temperature-activation.md)**
1. **[Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)**
