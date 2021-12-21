---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Guida di Adobe Experience Manager Screens
breadcrumb-title: Guida di AEM Screens
user-guide-description: Scopri come utilizzare una soluzione Digital Signage per pubblicare esperienze e interazioni digitali dinamiche e interattive.
feature-set: Experience Manager Screens
source-git-commit: 3602eda37d662017ec5a1d31735e42b6b6f0f89d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 18%

---


# Guida utente di AEM Screens {#user-guide}

+ [Introduzione a Screens](aem-screens-introduction.md)
+ Panoramica e guida di Kickstart {#overview}
   + [Guida di Kickstart](kickstart-for-aem-screens.md)
   + [Guida alle best practice per Screens](https://docs.adobe.com/content/help/it/experience-manager-screens/using/about-guide.html)
   + [Termini chiave](screens-glossary.md)
+ Nozioni di base sulla rete di digital signage {#digital-signage-network}
   + [Parte 1: Ruoli e responsabilità del progetto](project-roles-responsibilities.md)
   + [Parte 2: Considerazioni relative all’ambito dei progetti](project-considerations.md)
   + [Parte 3: Test, POC, Piloti e rollout](testing-pocs-pilots-rollouts.md)
   + [Parte 4: Gestione e distribuzione dei progetti](project-management-and-deployment.md)
   + [Parte 5: Considerazioni sul supporto](support-considerations.md)
+ Configurazione e amministrazione {#administering}
   + [Configurazioni server Screens](configuring-screens-introduction.md)
   + [Configurazione delle configurazioni del Dispatcher](dispatcher-configurations-aem-screens.md)
   + [Installazione di Screens Player](installing-screens-player.md)
   + [Collegamento del lettore Screens](working-with-screens-player.md)
   + [Registrazione dispositivo](device-registration.md)
   + [Impostazione degli ACL](setting-up-acls.md)
   + [Elenco di controllo della sicurezza di AEM Screens](security-checklist.md)
   + [Transizione da ContentSync a SmartSync](smartsync.md)
   + [Importazione di nuovi progetti da file](project-importer.md)
   + [Replica degli attivatori di dati sui server di pubblicazione](replicating-data-triggers.md)
   + [Configurazione degli agenti di replica Screens](configure-screens-replication.md)
   + Considerazioni specifiche per il cliente {#installing-client}
      + [Lettore del sistema operativo Chrome](implementing-chrome-os-player.md)
      + [Utilizzo di Chrome Player come estensione per la risoluzione dei problemi](using-chrome-player-as-an-extension.md)
      + [Lettore Android](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Giocatore Tizen](tizen-player.md)
      + [Registrazione automatica dei giocatori](auto-registration-players.md)
   + Pubblicazione autore {#author-publish}
      + [Panoramica dell’architettura Author-Publish](author-publish-architecture-overview.md)
      + [Configurazione di Author e Publish](author-and-publish.md)
   + Integrazione di Analytics con AEM Screens {#analytics-integration}
      + [Integrazione di Adobe Analytics](adobe-analytics-integration-aem-screens.md)
      + [Configurazione di Adobe Analytics con AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Esempi di authoring e casi d’uso {#authoring}
   + Configurazione di un progetto Screens {#setting-up-projects}
      + [Creazione e gestione di progetti](creating-a-screens-project.md)
      + [Creazione e gestione dei canali](managing-channels.md)
      + [Creazione e gestione delle visualizzazioni](managing-displays.md)
      + [Creazione e gestione delle posizioni](managing-locations.md)
      + [Creazione e gestione delle pianificazioni](managing-schedules.md)
      + [Gestione dei dispositivi](managing-devices.md)
      + Assegnazione dei canali{#assigning-channels} 
         + [Assegnazione dei canali](channel-assignment-latest-fp.md)
         + [Assegnazione canale: Pacchetti funzioni AEM Screens precedenti](channel-assignment.md)
   + Utilizzo delle funzionalità di base dei prodotti {#product-features}
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
      + [Layout a più zone](multi-zone-layout-aem-screens.md)
      + [Rappresentazioni video](generating-renditions.md)
      + [Sequenza incorporata dinamica](dynamic-embedded-sequences.md)
      + [Durata della riproduzione di immagini in serie a livello di canale](channel-level-image-playback.md)
      + [Sincronizzazione dei comandi](using-command-sync.md)
      + [Authoring con Data Triggers](authoring-data-triggers.md)
      + [Riconoscimento vocale](voice-recognition.md)
      + [Rapporto assegnazione contenuti](content-assignment-report.md)
      + [Supporto delle miniature per video](thumbnail-support.md)
      + [Utilizzo di rappresentazioni adattive in AEM Screens](using-adaptive-renditions.md)
   + Gestione degli aggiornamenti dei contenuti {#content-updates}
      + [Aggiornamento dei contenuti on-demand](on-demand-content.md)
      + [Aggiornamento dei contenuti as-a-service](content-update-as-a-service.md)
      + [Aggiornamento dei contenuti tramite Screens Launch](launches.md)
   + Esempi di casi d’uso {#use-case-examples}
      + [Canali di emergenza](emergency-channel.md)
      + [Attivazione temperatura centro viaggi](local-temperature-activation.md)
      + [Attivazione prenotazione alberghiera](hospitality-reservation-activation.md)
      + [Attivazione mirata inventario retail](retail-inventory-activation.md)
      + [Applicazione delle transizioni](applying-transitions.md)
      + [Transizioni da più aree a più aree](multizone-to-singlezone.md)
      + [Canale TakeOver per uso singolo](single-use-takeover-channel.md)
      + [Canale TakeOver per uso permanente](perpetual-takeover-channel.md)
+ Risorse per sviluppatori e API {#developing}
   + [API REST](rest-api.md)
   + [Sviluppo di un componente personalizzato per AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Canali offline](offline-channels.md)
   + [Estensione di un componente AEM Screens](extending-component-tutorial-develop.md)
   + [Creazione di componenti](creating-components.md)
   + [Incorporazione di un’applicazione REACT tramite AEM editor SPA e integrazione con AEM Screens Analytics](embedding-react-app.md)
   + [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)
   + [Creazione di modelli personalizzati per i layout MultiZone](creating-custom-templates-multizone-layouts.md)
   + [Applicazione di branding e stile personalizzati per le sovrapposizioni di testo](custom-branding-text-overlays.md)
   + [Rappresentazioni adattive: Panoramica e configurazioni dell&#39;architettura](/help/user-guide/adaptive-renditions.md)
+ Risoluzione dei problemi e domande frequenti {#troubleshooting}
   + [Domande frequenti su AEM Screens](aem-screens-faqs.md)
   + [Risoluzione dei problemi relativi al Centro di controllo dei dispositivi](monitoring-screens.md)
   + [Configurazione della riproduzione video](troubleshoot-videos.md)
+ Note sulla versione {#release-notes}
   + [Note sulla versione per Feature Pack 202112](release-notes-fp-202112.md)
   + [Note sulla versione per Feature Pack 202109](release-notes-fp-202109.md)
   + [Note sulla versione per Feature Pack 202105](release-notes-fp-202105.md)
   + [Note sulla versione per Feature Pack 202103](release-notes-fp-202103.md)
   + [Note sulla versione per Feature Pack 202011](release-notes-fp-202011.md)
   + [Note sulla versione per Feature Pack 2008](release-notes-fp-202008.md)
   + [Note sulla versione per Feature Pack 2004](release-notes-fp-202004.md)
   + [Note sulla versione per Feature Pack 2001](release-notes-fp-202001.md)
   + [Note sulla versione per Feature Pack 201909](release-notes-fp-201909.md)
   + [Note sulla versione per Feature Pack 201907](release-notes-fp-201907.md)
   + [Note sulla versione per Feature Pack 201905](screens-release-notes-fp-201905.md)
   + [Note sulla versione per Feature Pack 201812](release-notes-fp-201812.md)
   + [Note sulla versione per Feature Pack 2018-09](screens-release-notes.md)
