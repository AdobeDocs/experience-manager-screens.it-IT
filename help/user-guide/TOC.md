---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Guida di Adobe Experience Manager Screens
breadcrumb-title: Guida di AEM Screens
user-guide-description: Scopri come utilizzare una soluzione Digital Signage per pubblicare esperienze e interazioni digitali dinamiche e interattive.
feature-set: Experience Manager Screens
feature: Content
role: User
source-git-commit: b055ab685a1dcf5d53552971ecea42bffd81b848
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 14%

---


# Guida utente di AEM Screens {#user-guide}

+ [Introduzione a Screens](aem-screens-introduction.md)
+ Panoramica e guida Kick-Start {#overview}
   + [Guida di Kickstart](kickstart-for-aem-screens.md)
   + [Guida alle best practice per Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/using/about-guide.html?lang=it)
   + [Termini chiave](screens-glossary.md)
+ Nozioni di base sulla rete di digital signage {#digital-signage-network}
   + [Parte 1: Ruoli e responsabilità del progetto](project-roles-responsibilities.md)
   + [Parte 2: Considerazioni relative all’ambito dei progetti](project-considerations.md)
   + [Parte 3: Test, POC, Piloti e rollout](testing-pocs-pilots-rollouts.md)
   + [Parte 4: Gestione e realizzazione del progetto](project-management-and-deployment.md)
   + [Parte 5: Considerazioni di supporto](support-considerations.md)
+ Configurazione e amministrazione {#administering}
   + [Configurazioni server Screens](configuring-screens-introduction.md)
   + [Configurazione delle configurazioni del Dispatcher](dispatcher-configurations-aem-screens.md)
   + [Installazione di Screens Player](installing-screens-player.md)
   + [Collegamento del lettore Screens](working-with-screens-player.md)
   + [Registrazione dispositivo](device-registration.md)
   + [Impostazione di ACL](setting-up-acls.md)
   + [Elenco di controllo della sicurezza di AEM Screens](security-checklist.md)
   + [Transizione da ContentSync a SmartSync](smartsync.md)
   + [Nuova importazione progetti da file](project-importer.md)
   + [Replica di Data Triggers su server di pubblicazione](replicating-data-triggers.md)
   + [Configurazione degli agenti di replica di Screens](configure-screens-replication.md)
   + Considerazioni specifiche sul client {#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [Utilizzo di Chrome Player come estensione per la risoluzione dei problemi](using-chrome-player-as-an-extension.md)
      + [Lettore Android](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Giocatore Tizen](tizen-player.md)
      + [Lettore cloud](implementing-cloud-player.md)
      + [Registrazione automatica dei lettori](auto-registration-players.md)
      + [Uso del telecomando](implementing-remote-control.md)
   + Pubblicazione autore {#author-publish}
      + [Panoramica dell’architettura Author-Publish](author-publish-architecture-overview.md)
      + [Configurazione di Author e Publish](author-and-publish.md)
   + Integrazione di Analytics con AEM Screens {#analytics-integration}
      + [Integrazione di Adobe Analytics](adobe-analytics-integration-aem-screens.md)
      + [Configurazione di Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Esempi di authoring e casi d’uso {#authoring}
   + Configurazione di un progetto Schermi {#setting-up-projects}
      + [Creazione e gestione di progetti](creating-a-screens-project.md)
      + [Creazione e gestione dei canali](managing-channels.md)
      + [Creazione e gestione delle visualizzazioni](managing-displays.md)
      + [Creazione e gestione delle posizioni](managing-locations.md)
      + [Creazione e gestione delle pianificazioni](managing-schedules.md)
      + [Gestione dei dispositivi](managing-devices.md)
      + Assegnazione dei canali {#assigning-channels}
         + [Assegnazione canale](channel-assignment-latest-fp.md)
         + [Assegnazione canale: Feature Pack precedenti di AEM Screens](channel-assignment.md)
   + Utilizzo delle funzionalità core del prodotto {#product-features}
      + [Sovrapposizione testo](text-overlay.md)
      + [Aggiornamento offline in blocco](bulk-offline-update.md)
      + [Servizio notifiche AEM Screens](screens-notifications-service.md)
      + [Utilizzo di Frammenti esperienza](experience-fragments-in-screens.md)
      + [Attivazione a livello di risorsa](asset-level-scheduling.md)
      + [Attivazione a livello di canale](channel-level-activation.md)
      + [Creazione e gestione di una Live Copy](managing-livecopy.md)
      + [Creazione di un flusso di lavoro di spaziatura video](creating-a-video-padding-workflow.md)
      + [Aggiunta di componenti a un canale](adding-components-to-a-channel.md)
      + [Sequenze incorporate](embedded-sequences.md)
      + [Layout multizona](multi-zone-layout-aem-screens.md)
      + [Rappresentazioni video](generating-renditions.md)
      + [Sequenza incorporata dinamica](dynamic-embedded-sequences.md)
      + [Durata riproduzione immagine in blocco a livello di canale](channel-level-image-playback.md)
      + [Sincronizzazione comandi](using-command-sync.md)
      + [Authoring con Data Triggers](authoring-data-triggers.md)
      + [Riconoscimento vocale](voice-recognition.md)
      + [Rapporto assegnazione contenuti](content-assignment-report.md)
      + [Supporto delle miniature per video](thumbnail-support.md)
      + [Utilizzo di rappresentazioni adattive in AEM Screens](using-adaptive-renditions.md)
   + Gestione degli aggiornamenti dei contenuti {#content-updates}
      + [Aggiornamento dei contenuti on-demand](on-demand-content.md)
      + [Aggiornamento contenuto as a service](content-update-as-a-service.md)
      + [Aggiornamento dei contenuti tramite Screens Launch](launches.md)
   + Esempi di casi d’uso {#use-case-examples}
      + [Canali di emergenza](emergency-channel.md)
      + [Attivazione temperatura centro di viaggio](local-temperature-activation.md)
      + [Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)
      + [Attivazione con targeting magazzino vendita al dettaglio](retail-inventory-activation.md)
      + [Applicazione delle transizioni](applying-transitions.md)
      + [Transizioni da più zone a zona singola](multizone-to-singlezone.md)
      + [Canale TakeOver per singolo utilizzo](single-use-takeover-channel.md)
      + [Canale TakeOver per uso permanente](perpetual-takeover-channel.md)
+ Risorse per sviluppatori e API {#developing}
   + [API REST](rest-api.md)
   + [Sviluppo di un componente personalizzato per AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Canali offline](offline-channels.md)
   + [Estensione di un componente AEM Screens](extending-component-tutorial-develop.md)
   + [Creazione di componenti](creating-components.md)
   + [Incorporazione di un’applicazione REACT tramite l’Editor SPA dell’AEM e Integrazione con AEM Screens Analytics](embedding-react-app.md)
   + [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)
   + [Creazione di modelli personalizzati per i layout multizona](creating-custom-templates-multizone-layouts.md)
   + [Applicazione di branding e stile personalizzati per le sovrapposizioni di testo](custom-branding-text-overlays.md)
   + [Rappresentazioni adattive: panoramica dell’architettura e configurazioni](/help/user-guide/adaptive-renditions.md)
+ Risoluzione dei problemi e domande frequenti {#troubleshooting}
   + [Domande frequenti su AEM Screens](aem-screens-faqs.md)
   + [Risoluzione dei problemi di Device Control Center](monitoring-screens.md)
   + [Configurazione riproduzione video](troubleshoot-videos.md)
+ Note sulla versione {#release-notes}
   + [Note sulla versione per Feature Pack 202204](release-notes-fp-202204.md)
   + [Note sulla versione per Feature Pack 202203](release-notes-fp-202203.md)
   + [Note sulla versione per Feature Pack 202112](release-notes-fp-202112.md)
   + [Note sulla versione per Feature Pack 202109](release-notes-fp-202109.md)
   + [Note sulla versione per Feature Pack 202105](release-notes-fp-202105.md)
   + [Note sulla versione per Feature Pack 202103](release-notes-fp-202103.md)
   + [Note sulla versione per Feature Pack 202011](release-notes-fp-202011.md)
   + [Note sulla versione per Feature Pack 202008](release-notes-fp-202008.md)
   + [Note sulla versione per Feature Pack 202004](release-notes-fp-202004.md)
   + [Note sulla versione per Feature Pack 202001](release-notes-fp-202001.md)
   + [Note sulla versione per Feature Pack 201909](release-notes-fp-201909.md)
   + [Note sulla versione per Feature Pack 201907](release-notes-fp-201907.md)
   + [Note sulla versione per Feature Pack 201905](screens-release-notes-fp-201905.md)
   + [Note sulla versione per Feature Pack 201812](release-notes-fp-201812.md)
   + [Note sulla versione per Feature Pack 201809](screens-release-notes.md)
