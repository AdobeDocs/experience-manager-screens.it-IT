---
title: Incorporare un’applicazione REACT utilizzando l’editor SPA dell’AEM e Integrare con AEM Screens Analytics
seo-title: Embedding a REACT application using the AEM SPA Editor and Integrating with AEM Screens Analytics
description: Segui questa pagina per scoprire come incorporare un’applicazione interattiva a pagina singola utilizzando REACT (o un Angular) utilizzando l’editor SPA dell’AEM che può essere configurato dai professionisti aziendali in AEM e come integrare l’applicazione interattiva con Adobe Analytics offline.
seo-description: Follow this page to learn how to embed an interactive single page application using REACT (or Angular) using the AEM SPA editor that can be configured by business professionals in AEM and also how to integrate your interactive application with offline Adobe Analytics.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Incorporare un’applicazione REACT utilizzando l’editor SPA dell’AEM e Integrare con AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Questa sezione descrive come incorporare un’applicazione interattiva a pagina singola utilizzando REACT (o un Angular) utilizzando l’editor SPA dell’AEM che può essere configurato dai professionisti del settore dell’AEM e come integrare l’applicazione interattiva con Adobe Analytics offline.

## Utilizzo dell’Editor SPA dell’AEM {#using-the-aem-spa-editor}

Per utilizzare l’Editor SPA dell’AEM, segui la procedura riportata di seguito:

1. Clona l’archivio dell’Editor SPA del AEM all’indirizzo [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Questo archetipo crea un progetto Adobe Experience Manager minimo come punto di partenza per i tuoi progetti SPA. Le proprietà che devono essere fornite quando si utilizza questo archetipo consentono di denominare come desiderato tutte le parti del progetto.

1. Segui le istruzioni readme per creare un progetto di archetipo per l’editor SPA AEM:

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
   >Utilizziamo **GroupId** as ***com.adobe.aem.screens*** e **ArtifactId** as ***SPA di esempio*** (impostazione predefinita). Puoi scegliere il tuo, se necessario.

1. Una volta creato il progetto, utilizza un IDE o un editor a tua scelta e importa il progetto Maven generato.
1. Implementare nell’istanza AEM locale utilizzando il comando ***mvn clean install -PautoInstallPackage***.

### Modifica di contenuti nell’app REACT {#editing-content-in-the-react-app}

Per modificare i contenuti nell’app REACT:

1. Accedi a `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (sostituisci il nome host, la porta e il nome del progetto, a seconda dei casi).
1. Dovresti essere in grado di modificare il testo visualizzato nell’applicazione Hello world.

### Aggiunta dell’app REACT interattiva ad AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Per aggiungere l’app REACT interattiva ad AEM Screens, segui i passaggi seguenti:

1. Crea un nuovo progetto AEM Screens. Consulta [Creazione e gestione di progetti](creating-a-screens-project.md) per ulteriori dettagli.

1. Crea un nuovo **Canale applicazione** (preferibilmente) (o modello 1x1 o canale multizona) nel **Canali** del progetto Screens.

   >[!NOTE]
   >**Canali sequenza** sono sconsigliati per questo caso d’uso, in quanto presentano una logica di presentazione intrinsecamente in conflitto con la natura interattiva dell’esperienza
   >Consulta [Creazione e gestione dei canali](managing-channels.md) per ulteriori dettagli.


1. Modifica un canale di sequenza e trascina e rilascia un componente di pagina incorporato.

   Consulta [Aggiunta di componenti a un canale](adding-components-to-a-channel.md) per ulteriori dettagli.

   >[!NOTE]
   >
   >Assicurati di aggiungere l’evento di interazione dell’utente quando assegni il canale alla visualizzazione.

1. Fai clic su **Modifica** dalla barra delle azioni per modificare le proprietà del canale.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Trascina la **Pagina incorporata** , o riutilizzare il componente esistente in un canale dell&#39;applicazione, e selezionare la home page sotto l&#39;applicazione mysamplespa, ad esempio, ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Assegna il canale a una visualizzazione.

   >[!NOTE]
   >Assicurati di aggiungere l’evento di interazione dell’utente quando assegni il canale alla visualizzazione.

1. Registra un lettore per questo progetto e assegnalo al display. Ora dovresti essere in grado di vedere l’applicazione interattiva in esecuzione su AEM Screens.

   Consulta [Registrazione dispositivo](device-registration.md) per informazioni dettagliate sulla registrazione di un dispositivo.

## Integrazione dell’SPA con Adobe Analytics con funzionalità offline tramite AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Segui i passaggi seguenti per integrare l’SPA con Adobe Analytics con funzionalità offline tramite AEM Screens:

1. Configurare Adobe Analytics in AEM Screens.

   Consulta [Configurazione di Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md) per scoprire come eseguire la sequenza in Adobe Analytics con AEM Screens e inviare eventi personalizzati utilizzando offline Adobe Analytics.

1. Modifica l’app React nell’IDE/editor che preferisci (in particolare il componente testo o un altro componente da cui vuoi iniziare a emettere eventi).
1. Aggiungi le informazioni di analisi utilizzando il modello dati standard all’evento di clic o a un altro evento che desideri acquisire per il componente.

   Consulta [Configurazione di Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md)s per ulteriori dettagli.

1. Chiama l’API di AEM Screens Analytics per salvare l’evento offline e inviarlo in modalità burst ad Adobe Analytics.

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
   >Il firmware del lettore aggiunge automaticamente ulteriori dettagli sul lettore e sul relativo ambiente di runtime ai dati di analisi personalizzati inviati. Di conseguenza, potrebbe non essere necessario acquisire i dettagli del sistema operativo o del dispositivo di basso livello, se non in caso di assoluta necessità. Devi solo concentrarti sui dati di analisi aziendale.
