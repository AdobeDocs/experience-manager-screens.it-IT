---
title: Configurazione di ContextHub in AEM Screens
seo-title: Configurazione di ContextHub in AEM Screens
description: Segui questa pagina per informazioni su ContextHub nel motore di destinazione per definire l'archivio dati allo scopo di modificare il contenuto dell'attivatore dati.
seo-description: Segui questa pagina per informazioni su ContextHub nel motore di destinazione per definire l'archivio dati allo scopo di modificare il contenuto dell'attivatore dati.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: Sviluppo di schermi
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 1%

---


# Configurazione di ContextHub in AEM Screens {#configuring-contexthub-in-aem-screens}

Questa sezione sottolinea come creare e gestire le modifiche alle risorse basate sui dati utilizzando un archivio dati.

## Termini chiave {#key-terms}

Prima di iniziare a creare e gestire i canali basati sulle scorte nel progetto AEM Screens, devi conoscere alcuni dei termini chiave importanti e rilevanti per i diversi scenari.

**** BrandFa riferimento alla descrizione del progetto di alto livello.

**** AreaFa riferimento al nome del progetto AEM Screens, ad esempio Digital Ad Signage

**** AttivitàDefinisce la categoria di regole come Basata su inventario, Basata su tempo, Basata sulla disponibilità del reparto e così via.

**** AudienceDefinisce la regola.

**** SegmentSi riferisce alla versione della risorsa da riprodurre per la regola data, ad esempio se la temperatura è inferiore a 50 gradi fahrenheit, lo schermo visualizza l&#39;immagine di un caffè caldo altrimenti di una bevanda fredda.

Il diagramma seguente fornisce una rappresentazione visiva di come le configurazioni ContextHub coincidono con attività, pubblico e canali.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Condizioni preliminari {#preconditions}

Prima di iniziare a configurare le configurazioni Context Hub per un progetto AEM Screens, devi configurare Google Sheets (a scopo dimostrativo).

>[!IMPORTANT]
>
>Google Sheets è utilizzato nell&#39;esempio seguente come un sistema di database di esempio da cui i valori vengono recuperati ed è esclusivamente a scopo educativo. Adobe non supporta l’utilizzo di Google Sheets per ambienti di produzione.
>
>Per ulteriori informazioni, consulta [Ottieni chiave API](https://developers.google.com/maps/documentation/javascript/get-api-key) nella documentazione di Google.

## Passaggio 1: Impostazione di un archivio dati {#step-setting-up-a-data-store}

È possibile impostare l’archivio dati come evento I/O locale o come evento di database locale.

L’esempio seguente di trigger a livello di risorsa mostra un evento di database locale che imposta un archivio dati, ad esempio un foglio Excel, che consente di utilizzare le configurazioni ContextHub e il percorso dei segmenti per il canale AEM Screens.

Una volta configurato correttamente il foglio google, ad esempio come mostrato di seguito:

![immagine](/help/user-guide/assets/context-hub/context-hub1.png)

La seguente convalida è ciò che verrà visualizzato quando si controlla la connessione immettendo i due valori *ID di Google sheet* e *Chiave API* nel formato seguente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![immagine](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>L’esempio specifico seguente mostra i fogli google come archivio dati che attiveranno la modifica delle risorse se il valore è superiore a 100 o inferiore a 50.

## Passaggio 2: Configurazione delle configurazioni del negozio {#step-setting-store-configurations}

1. **Navigazione a ContextHub**

   Passa all’istanza AEM e fai clic sull’icona degli strumenti nella barra laterale sinistra. Fai clic su **Sites** —> **ContextHub**, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creazione di una nuova configurazione dell’archivio ContextHub**

   1. Passa al contenitore di configurazione denominato **screens**.

   1. Fai clic su **Crea** > **Crea contenitore di configurazione** e immetti il titolo come **ContextHubDemo**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **** Passa a  **ContextHubDemo**  >  **** **Crea configurazione** ContentHub  **e fai clic su** Salva.

      >[!NOTE]
      > Dopo aver fatto clic su **Salva** ti troverai nella schermata **Configurazione ContextHub**.

   1. Dalla schermata **Configurazione ContextHub**, fai clic su **Crea** > **Configurazione ContentHub Store..**

      ![immagine](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >Come parte del Feature Pack 4 di AEM 6.5 o del Feature Pack 8 di AEM 6.4, i clienti devono aggiornare `/conf/screens/settings/cloudsettings` a `sling:Folder`.
      >
      >Effettua le seguenti operazioni:
      >
      >1. Passa a CRXDE Lite e quindi a `/conf/screens/settings/cloudsettings`.
      >1. Controlla se `cloudsettings jcr:primaryType` è in `sling:Folder`. Se il `jcr:primaryType` non è compreso in `sling:folder`, procedi ai passaggi successivi.
      >1. Fai clic con il pulsante destro del mouse su `/conf/screens/settings` e crea un nuovo nodo con *nome* come **cloudsettings1** e *Tipo* come **sling:Folder** e salva le modifiche.
      >1. Sposta tutti i nodi sotto `/conf/screens/settings/cloudsettings` a `cloudsettings1`.
      >1. Elimina `cloudsettings` e salva.
      >1. Rinomina `cloudsettings1` in `cloudsettings` e salva.
      >1. A questo punto è necessario notare che /conf/screens/settings/cloudsettings ha `jcr:primaryType` come `sling:Folder`.

      >
      >Segui questi passaggi in authoring e pubblicazione prima o dopo l’aggiornamento.

   1. Inserisci il **Titolo** come **Fogli di Google**, **Nome del negozio** come **fogli di Google** e **Tipo di archivio** come **contexthub.generic-jsonp** e **Successivo**.

      >[!CAUTION]
      >Se utilizzi Adobe Experience Manager (AEM) 6.4, immetti il **Titolo configurazione** come **googlesheets** e il **Tipo di archivio** come **contexthub.generic-jsonp**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Immetti la tua configurazione json specifica. Ad esempio, puoi utilizzare il seguente json a scopo dimostrativo e fare clic su **Salva** e vedrai la configurazione dell&#39;archivio intitolata **Google Sheets** nella configurazione ContextHub.

      >[!IMPORTANT]
      >Assicurati di sostituire il codice con il tuo *&lt;Sheet ID>* e *&lt;API Key>*, che hai recuperato durante la configurazione dei fogli Google.

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
      Nel codice di esempio riportato sopra, **pollInterval** definisce la frequenza con cui i valori vengono aggiornati (in ms).
      Sostituisci il codice con il tuo *&lt;Sheet ID>* e *&lt;API Key>*, recuperato durante la configurazione dei fogli di Google.

      >[!CAUTION]
      Se crei le configurazioni dell’archivio di Google Sheets al di fuori della cartella globale (ad esempio nella cartella del progetto), il targeting non funzionerà automaticamente.


1. **Impostazione della segmentazione dello store**

   1. Passa a **Configurazione archivio ContentHub.** crea un’altra configurazione dell’archivio nel contenitore di configurazione delle schermate e imposta  **** Titleas  **segmentation-contexthub**,  **Store** Name  **** segmentatione  **Store** Typeas  **aem.segmentation**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Fare clic su **Avanti**, quindi su **Salva**.

      >[!NOTE]
Devi saltare il processo di definizione del json e lasciarlo vuoto.


## Passaggio 3: Configurazione dei segmenti nel pubblico {#setting-up-audience}

1. **Creazione di segmenti in Audiences**

   1. Passa dall&#39;istanza AEM a **Personalizzazione** > **Audiences** > **screens**.

   1. Fai clic su **Crea** > **Crea segmento di Context Hub.** Viene visualizzata la finestra di dialogo  **Nuovo** segmento ContextHub .

   1. Inserisci il **Titolo** come **Superiore a 50** e fai clic su **Crea**. Allo stesso modo, crea un altro segmento denominato **Lowerthan50**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Seleziona il segmento **Superiore a 50** e fai clic su **Proprietà** nella barra delle azioni.
      ![immagine](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Seleziona la scheda **Personalizzazione** da **Proprietà segmento**. Imposta il percorso **ContextHub** su `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Percorso segmenti** su `/conf/screens/settings/wcm/segments` e fai clic su **Salva**, come mostrato nella figura seguente.

      ![immagine](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Allo stesso modo, imposta anche il segmento **ContextHub Path** e **Segments Path** per **Lowerthan50**.

## Passaggio 4: Configurazione del marchio e dell’area {#setting-brand-area}

Segui i passaggi riportati di seguito per creare un marchio nelle attività e nell’area sotto il marchio:

1. **Creazione di un marchio nelle attività**

   1. Passa dall&#39;istanza AEM a **Personalizzazione** > **Attività**.

   1. Fai clic su **Crea** > **Crea marchio**.

   1. Seleziona **Marchio** dalla procedura guidata **Crea pagina** e fai clic su **Avanti**.

   1. Inserisci il **Titolo** come **ScreensBrand** e fai clic su **Crea**. Il tuo marchio viene ora creato come mostrato di seguito.

      ![immagine](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema noto:
Per aggiungere un’area, rimuovere il master dall’URL, ad esempio
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creazione di un’area nel brand**

   Per creare un’area del marchio, effettua le seguenti operazioni:

   1. Fare clic su **Crea**, quindi su **Crea area**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Seleziona **Area** dalla procedura guidata **Crea pagina** e fai clic su **Avanti**.

   1. Inserisci il **Titolo** come **ScreensValue** e fai clic su **Crea**.
Verrà creata un’area nel tuo marchio.

## Passaggio 5: Creazione di segmenti in un’attività {#step-setting-up-audience-segmentation}

Dopo aver configurato un archivio dati e definito l’attività (marchio e area), segui i passaggi seguenti per creare segmenti nell’attività.

1. **Creazione di segmenti nelle attività**

   1. Passa dall’istanza AEM a **Personalizzazione** > **Attività** > **ScreensBrand** >**ScreensValue**.

   1. Fai clic su **Crea** > **Crea attività.** Le Procedure  **Guidate Configura Attività** .

   1. Inserisci il **Titolo** come **ValoreCheck50** e **Nome** come **valoreCheck50**. Seleziona il **motore di targeting** come **ContextHub (AEM)** dal menu a discesa e fai clic su **Avanti**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Fai clic su **Aggiungi esperienza** nella **Configurazione guidata attività**.

   1. In **Tipi di pubblico**, seleziona **Più alto di 50** e fai clic su **Aggiungi esperienza** e immetti **Titolo** come **più alto di 50** **Nome** come &lt;a 12/>superiore a 50 **.** Fare clic su **Ok**.

   1. In **Tipi di pubblico**, seleziona il **Lowerthan50** e fai clic su **Aggiungi esperienza** e immetti il **Titolo** come **inferiore a 50** **Nome** come a12/>lowerthan50 **.** Fare clic su **Ok**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Fare clic su **Avanti**, quindi su **Salva**. **L’attività ValueCheck50** viene ora creata e configurata.

      ![immagine](/help/user-guide/assets/context-hub/context-hub16.png)

## Passaggio 5: Modifica dei segmenti in Audiences{#editing-audience-segmentation}

1. **Modifica dei segmenti**

   1. Passa dall&#39;istanza AEM a **Personalizzazione** > **Audiences** > **screens**.

   1. Seleziona il segmento **Superiore a 50** e fai clic su **Modifica** nella barra delle azioni.

   1. Trascina e rilascia il **Confronto: Proprietà - Componente Value** nell&#39;editor.

   1. Fai clic sull&#39;icona a forma di chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con valore** .

   1. Seleziona **googlesheets/value/1/0** dal menu a discesa in **Nome proprietà**.

      >[!NOTE]
Il  **foglio googlesheets/value/1/0** si riferisce alla riga 2 e alla colonna compilati nei fogli google nella figura seguente:

      ![immagine](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Seleziona **Operatore** come **maggiore di** dal menu a discesa.

   1. Inserisci il **Valore** come **70**.

      >[!NOTE]
      Il AEM convalida i dati da Google Sheet mostrando il segmento come verde.

      ![immagine](/help/user-guide/assets/context-hub/context-hub18.png)
   Allo stesso modo, modifica i valori della proprietà in **Lowerthan50**.

   1. Trascina e rilascia il **Confronto: Proprietà - Componente Value** nell&#39;editor.

   1. Fai clic sull&#39;icona a forma di chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con valore** .

   1. Seleziona **googlesheets/value/1/0** dal menu a discesa in **Nome proprietà**.

   1. Seleziona **Operatore** come **minore di** dal menu a discesa.

   1. Inserisci il **Valore** come **50**.



## Abilitazione del targeting nei canali {#step-enabling-targeting-in-channels}

Segui i passaggi seguenti per abilitare il targeting nei tuoi canali.

1. Passa a uno dei canali AEM Screens. I passaggi seguenti mostrano come abilitare il targeting utilizzando **DataDrivenChannel** creato in un canale AEM Screens.

1. Seleziona il canale **TargetChannel** e fai clic su **Proprietà** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/context-hub/context-hub19.png)

1. Seleziona la scheda **Personalizzazione** per impostare le configurazioni di ContextHub.

   1. Imposta il percorso **ContextHub** su `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Percorso segmenti** su `/conf/screens/settings/wcm/segments` e fai clic su **Salva**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      Utilizza ContextHub e il percorso Segmenti, in cui hai inizialmente salvato le configurazioni e i segmenti dell&#39;hub di contesto.

      ![immagine](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Naviga e seleziona il canale **TargetChannel** e fai clic su **Modifica** nella barra delle azioni.

      >[!NOTE]
      Se hai configurato tutto correttamente, vedrai l&#39;opzione **Targeting** nel menu a discesa dall&#39;editor, come mostrato nella figura seguente.

      ![immagine](/help/user-guide/assets/context-hub/context-hub21.png)

## Ulteriori informazioni: Esempi di casi d&#39;uso {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto AEM Screens, puoi seguire i diversi casi d’uso per comprendere in che modo i dati che hanno attivato le risorse svolgono un ruolo fondamentale in settori diversi:

1. **[Attivazione mirata inventario retail](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro viaggi](local-temperature-activation.md)**
1. **[Attivazione prenotazione alberghiera](hospitality-reservation-activation.md)**
