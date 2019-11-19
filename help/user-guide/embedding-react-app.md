---
title: Incorporazione di un’applicazione REACT tramite AEM SPA Editor e integrazione con AEM Screens Analytics
seo-title: Incorporazione di un’applicazione REACT tramite AEM SPA Editor e integrazione con AEM Screens Analytics
description: Segui questa pagina per apprendere come incorporare un’applicazione interattiva a pagina singola tramite REACT (o Angular) con l’editor AEM SPA che può essere configurato da professionisti aziendali in AEM e come integrare l’applicazione interattiva con Adobe Analytics offline.
seo-description: Segui questa pagina per apprendere come incorporare un’applicazione interattiva a pagina singola tramite REACT (o Angular) con l’editor AEM SPA che può essere configurato da professionisti aziendali in AEM e come integrare l’applicazione interattiva con Adobe Analytics offline.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Incorporazione di un’applicazione REACT tramite AEM SPA Editor e integrazione con AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Questa sezione descrive come incorporare un’applicazione interattiva a pagina singola tramite REACT (o Angular) con l’editor AEM SPA che può essere configurato da professionisti aziendali in AEM e come integrare l’applicazione interattiva con Adobe Analytics offline.

## Utilizzo di AEM SPA Editor {#using-the-aem-spa-editor}

Per utilizzare AEM SPA Editor, effettuate le seguenti operazioni:

1. Clona il repo di AEM SPA Editor all’indirizzo [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Questo archetipo crea un progetto Adobe Experience Manager minimo come punto di partenza per i tuoi progetti SPA. Le proprietà che devono essere fornite quando si utilizza questo archetipo consentono di assegnare i nomi desiderati a tutte le parti del progetto.

1. Segui le istruzioni per creare un progetto archetipo dell’editor AEM SPA:

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >Utilizziamo **GroupId** come ***com.adobe.aem.screens*** e **ArtifactId** come ***My Sample SPA*** (che è l’impostazione predefinita). Potete scegliere il vostro secondo necessità.

1. Una volta creato il progetto, utilizzate un IDE o un editor di vostra scelta e importate il progetto Maven generato.
1. Distribuisci nell’istanza locale di AEM utilizzando il comando ***mvn Clean install -PautoInstallPackage***.

### Modifica del contenuto nell'app REACT {#editing-content-in-the-react-app}

Per modificare il contenuto nell'app REACT:

1. Passate a `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (sostituite il nome host, la porta e il nome del progetto come applicabile).
1. Dovrebbe essere possibile modificare il testo visualizzato nell'applicazione Hello world.

### Aggiunta dell'app REACT interattiva a AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Per aggiungere l’app REACT interattiva alle schermate AEM, effettuate le seguenti operazioni:

1. Crea un nuovo progetto AEM Screens. Per ulteriori informazioni, consultate [Creazione e gestione di progetti](creating-a-screens-project.md) .

   >[!NOTE]
   >
   >Crea un canale **** sequenza durante la creazione di un canale nella cartella **Canali** del progetto Screens.
   >
   >
   >Per ulteriori informazioni, consultate [Creazione e gestione di canali](managing-channels.md) .

   ![screen_shot_2019-02-15at100330 am](assets/screen_shot_2019-02-15at100330am.png)

1. Modificate i canali di sequenza e trascinate e rilasciate un componente di pagina incorporato.

   Per ulteriori informazioni, consulta [Aggiunta di componenti a un canale](adding-components-to-a-channel.md) .

   >[!NOTE]
   >
   >Accertatevi di aggiungere l'evento di interazione utente quando assegnate il canale al display.

1. Fate clic su **Modifica** nella barra delle azioni per modificare le proprietà del canale della sequenza.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Trascinare il componente Pagina **** incorporata e selezionare la pagina principale sotto l’applicazione mysamplespa, ad esempio ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registra un lettore rispetto a questo progetto e dovresti essere in grado di visualizzare l'applicazione interattiva in esecuzione su AEM Screens.

   Per informazioni dettagliate sulla registrazione di un dispositivo, fare riferimento a Registrazione [](device-registration.md) dispositivo.

## Integrazione dell'API con Adobe Analytics con la funzionalità offline tramite AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Seguite i passaggi indicati di seguito per integrare l'API con Adobe Analytics con funzionalità offline tramite AEM Screens:

1. Configurare Adobe Analytics in AEM Screens.

   Fate riferimento a [Configuring Adobe Analytics with AEM Screens (configuring-adobe-analytics-aem-screens.md)] (Configurazione di Adobe Analytics con AEM Screens) per informazioni su come eseguire la sequenza in Adobe Analytics con AEM Screens e inviare eventi personalizzati tramite Adobe Analytics offline).

1. Modificate l'app di reazione nell'IDE/nell'editor desiderato (in particolare il componente di testo o altro componente che desiderate avviare con gli eventi di emissione).
1. Nell'evento click o in un altro evento che si desidera acquisire per il componente, aggiungere le informazioni di analisi utilizzando il modello dati standard.

   Per ulteriori informazioni, consultate [Configurazione di Adobe Analytics con AEM](configuring-adobe-analytics-aem-screens.md)Screens.

1. Chiama l’API di analisi di AEM Screens per salvare l’evento offline e inviarlo in Burst ad Adobe Analytics.

   Esempio,

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >Il firmware del lettore aggiunge automaticamente ulteriori dettagli sul lettore e il relativo ambiente di runtime ai dati di analisi personalizzati inviati. Di conseguenza, potrebbe non essere necessario acquisire i dettagli del sistema operativo/dispositivo di basso livello, a meno che non sia assolutamente necessario. È sufficiente concentrarsi sui dati di analisi aziendale.

