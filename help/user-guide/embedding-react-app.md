---
title: Incorporazione di un’applicazione REACT tramite l’editor AEM SPA e integrazione con  AEM Screens Analytics
seo-title: Incorporazione di un’applicazione REACT tramite l’editor AEM SPA e integrazione con  AEM Screens Analytics
description: Seguite questa pagina per apprendere come incorporare un’applicazione interattiva a pagina singola utilizzando REACT (o Angular) con l’editor AEM SPA che può essere configurato dai professionisti aziendali in AEM e come integrare l’applicazione interattiva con  Adobe Analytics offline.
seo-description: Seguite questa pagina per apprendere come incorporare un’applicazione interattiva a pagina singola utilizzando REACT (o Angular) con l’editor AEM SPA che può essere configurato dai professionisti aziendali in AEM e come integrare l’applicazione interattiva con  Adobe Analytics offline.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---


# Incorporazione di un’applicazione REACT tramite l’editor AEM SPA e integrazione con  AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Questa sezione descrive come incorporare un’applicazione interattiva a pagina singola utilizzando REACT (o Angular) con l’editor AEM SPA che può essere configurato dai professionisti aziendali in AEM e come integrare l’applicazione interattiva con  Adobe Analytics offline.

## Utilizzo di AEM SPA Editor {#using-the-aem-spa-editor}

Seguite i passaggi indicati di seguito per utilizzare l&#39;Editor AEM SPA:

1. Clonate il repo AEM SPA Editor all&#39;indirizzo [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Questo archetipo crea un progetto Adobe Experience Manager minimo come punto di partenza per i vostri progetti SPA. Le proprietà che devono essere fornite quando si utilizza questo archetipo consentono di assegnare i nomi desiderati a tutte le parti del progetto.

1. Seguite le istruzioni per creare un progetto archetype AEM editor SPA:

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
1. Distribuisci nell&#39;istanza AEM locale utilizzando il comando ***mvn Clean install -PautoInstallPackage***.

### Modifica del contenuto nell&#39;app REACT {#editing-content-in-the-react-app}

Per modificare il contenuto nell&#39;app REACT:

1. Passate a `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (sostituite il nome host, la porta e il nome del progetto come applicabile).
1. Dovrebbe essere possibile modificare il testo visualizzato nell&#39;applicazione Hello world.

### Aggiunta dell’app REACT interattiva a  AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Per aggiungere l’app REACT interattiva a  AEM Screens, effettuate le seguenti operazioni:

1. Crea un nuovo progetto AEM Screens . Per ulteriori informazioni, consultate [Creazione e gestione di progetti](creating-a-screens-project.md) .

   >[!NOTE]
   >
   >Crea un canale **** sequenza durante la creazione di un canale nella cartella **Canali** del progetto Screens.
   >
   >
   >Per ulteriori informazioni, consulta [Creazione e gestione di canali](managing-channels.md) .

   ![screen_shot_2019-02-15at100330 am](assets/screen_shot_2019-02-15at100330am.png)

1. Modificate i canali di sequenza e trascinate e rilasciate un componente di pagina incorporato.

   Per ulteriori informazioni, consulta [Aggiunta di componenti a un canale](adding-components-to-a-channel.md) .

   >[!NOTE]
   >
   >Accertatevi di aggiungere l&#39;evento di interazione utente quando assegnate il canale al display.

1. Fate clic su **Modifica** nella barra delle azioni per modificare le proprietà del canale della sequenza.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Trascinare il componente Pagina **** incorporata e selezionare la pagina principale sotto l’applicazione mysamplespa, ad esempio ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registra un lettore rispetto a questo progetto e dovresti essere in grado di visualizzare l&#39;applicazione interattiva in esecuzione su  AEM Screens.

   Per informazioni dettagliate sulla registrazione di un dispositivo, fare riferimento a Registrazione [](device-registration.md) dispositivo.

## Integrazione dello SPA con  Adobe Analytics con funzionalità offline tramite  AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Seguite i passaggi indicati di seguito per integrare l&#39;app SPA con  Adobe Analytics con funzionalità offline tramite  AEM Screens:

1. Configurare  Adobe Analytics in  AEM Screens.

   Per informazioni su come [configurare  Adobe Analytics con  AEM Screens](configuring-adobe-analytics-aem-screens.md) per eseguire la sequenza  Adobe Analytics con  AEM Screens e inviare eventi personalizzati utilizzando  Adobe Analytics offline, fare riferimento aConfigurazione con.

1. Modificate l&#39;app di reazione nell&#39;IDE/nell&#39;editor desiderato (in particolare il componente di testo o altro componente che desiderate avviare con gli eventi di emissione).
1. Nell&#39;evento click o in un altro evento che si desidera acquisire per il componente, aggiungere le informazioni di analisi utilizzando il modello dati standard.

   Per ulteriori informazioni, consultate [Configurazione  Adobe Analytics con AEM](configuring-adobe-analytics-aem-screens.md)Screens.

1. Chiamate l&#39;API di AEM Screens Analytics  per salvare l&#39;evento offline e inviarlo in Burst a  Adobe Analytics.

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
   >Il firmware del lettore aggiunge automaticamente ulteriori dettagli sul lettore e il relativo ambiente di runtime ai dati di analisi personalizzati inviati. Di conseguenza, potrebbe non essere necessario acquisire i dettagli del sistema operativo/dispositivo di basso livello, a meno che non sia assolutamente necessario. Devi solo concentrarti sui dati di analisi aziendale.

