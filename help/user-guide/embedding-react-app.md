---
title: Incorporare un’applicazione REACT utilizzando l’editor SPA dell’AEM e Integrare con AEM Screens Analytics
description: Scopri come incorporare un’applicazione interattiva a pagina singola utilizzando REACT (o un Angular) utilizzando l’editor SPA dell’AEM.
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---

# Incorporare un’applicazione REACT utilizzando l’editor SPA dell’AEM e Integrare con AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Puoi incorporare un’applicazione interattiva a pagina singola utilizzando REACT (o Angular). A tale scopo, utilizza l’editor SPA dell’AEM configurato dai professionisti del settore AEM. Scopri anche come integrare l’applicazione interattiva con Adobe Analytics offline.

## Utilizzo dell’Editor SPA dell’AEM {#using-the-aem-spa-editor}

Per utilizzare l’Editor SPA dell’AEM, segui la procedura riportata di seguito:

1. Clona l&#39;archivio dell&#39;editor SPA AEM all&#39;indirizzo [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Questo archetipo crea un progetto Adobe Experience Manager minimo come punto di partenza per i tuoi progetti SPA. Le proprietà che devono essere fornite quando si utilizza questo archetipo consentono di denominare come desiderato tutte le parti del progetto.

1. Per creare un progetto dell’archetipo dell’editor SPA dell’AEM, segui le istruzioni riportate di seguito:

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
   >In questa documentazione viene utilizzato **GroupId** come ***com.adobe.aem.screens*** e **ArtifactId** come ***My Sample SPA*** (valori predefiniti). Puoi scegliere il tuo, se necessario.

1. Dopo la creazione del progetto, utilizza un IDE o un editor a tua scelta e importa il progetto Maven generato.
1. Distribuisci nell&#39;istanza AEM locale utilizzando il comando ***mvn clean install -PautoInstallPackage***.

### Modifica di contenuti nell’app REACT {#editing-content-in-the-react-app}

Per modificare i contenuti nell’app REACT:

1. Passa a `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (sostituisci il nome host, la porta e il nome del progetto come applicabile).
1. Possibilità di modificare il testo visualizzato nell&#39;applicazione Hello World.

### Aggiunta dell’app REACT interattiva ad AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Per aggiungere l’app REACT interattiva ad AEM Screens, segui i passaggi seguenti:

1. Crea un progetto AEM Screens. Per ulteriori dettagli, vedere [Creazione e gestione di progetti](creating-a-screens-project.md).
1. Crea un **Canale applicazione** (preferibilmente) (o un modello 1x1 o un canale multizona) nella cartella **Canali** del progetto AEM Screens.

   >[!NOTE]
   >**I canali della sequenza** sono sconsigliati per questo caso d&#39;uso perché hanno una logica di presentazione intrinseca in conflitto con la natura interattiva dell&#39;esperienza.
   >Per ulteriori dettagli, vedere [Creazione e gestione dei canali](managing-channels.md).

1. Modifica un canale di sequenza e trascina e rilascia un componente di pagina incorporato.

   Per ulteriori dettagli, vedere [Aggiunta di componenti a un canale](adding-components-to-a-channel.md).

   >[!NOTE]
   >
   >Assicurati di aggiungere l’evento di interazione dell’utente quando assegni il canale alla visualizzazione.

1. Fai clic su **Modifica** nella barra delle azioni per modificare le proprietà del canale.

   ![schermata_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Trascina e rilascia il componente **Pagina incorporata** o riutilizza il componente esistente in un canale dell&#39;applicazione, quindi fai clic sulla home page sotto l&#39;applicazione mysamplespa, ad esempio ***/content/mysamplespa/en/home***.

   ![schermata_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Assegna il canale a una visualizzazione.

   >[!NOTE]
   >Assicurati di aggiungere l’evento di interazione dell’utente quando assegni il canale alla visualizzazione.

1. Registra un lettore per questo progetto e assegnalo al display. Ora puoi vedere la tua applicazione interattiva in esecuzione su AEM Screens.

   Per ulteriori informazioni sulla registrazione di un dispositivo, vedere [Registrazione dispositivo](device-registration.md).

## Integrazione dell’SPA con Adobe Analytics con funzionalità offline tramite AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Segui i passaggi seguenti per integrare l’SPA con Adobe Analytics con funzionalità offline tramite AEM Screens:

1. Configurare Adobe Analytics in AEM Screens.

   Consulta [Configurazione di Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md) per ulteriori informazioni su come eseguire la sequenza in Adobe Analytics con AEM Screens e inviare eventi personalizzati utilizzando offline Adobe Analytics.

1. Modifica l’app React nell’IDE/editor che preferisci (in particolare il componente testo o un altro componente da cui vuoi iniziare a emettere eventi).
1. Aggiungi le informazioni di analisi utilizzando il modello dati standard all’evento di clic o all’altro evento che desideri acquisire per il componente.

   Per ulteriori dettagli, vedere [Configurazione di Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md).

1. Chiama l’API di AEM Screens Analytics in modo da poter salvare l’evento offline e inviarlo in modalità Burst ad Adobe Analytics.

   Ad esempio:

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
   >Il firmware del lettore aggiunge automaticamente ulteriori dettagli sul lettore e sul relativo ambiente di runtime ai dati di analisi personalizzati inviati. Di conseguenza, potrebbe essere necessario acquisire i dettagli relativi al sistema operativo/dispositivo di basso livello, se non necessario. Concentrati sui dati di analisi aziendale.
