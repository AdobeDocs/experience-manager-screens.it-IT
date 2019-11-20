---
title: Transizione da ContentSync a SmartSync
seo-title: Transizione da ContentSync a SmartSync
description: Seguite questa pagina per informazioni sulla funzione SmartSync e su come passare da ContentSync a SmartSync.
seo-description: Seguite questa pagina per informazioni sulla funzione SmartSync e su come passare da ContentSync a SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 66c741bb73bd5deb2bb5b06dd46f2e407d9c4b7e

---


# Transizione da ContentSync a SmartSync {#transitioning-from-contentsync-to-smartsync}

Questa sezione fornisce una panoramica della funzione SmartSync e di come riduce al minimo il carico/lo storage del server e il traffico di rete per ridurre i costi.

## Panoramica {#overview}

SmartSync è l'ultimo meccanismo utilizzato da AEM Screens. Sostituisce il metodo corrente utilizzato per memorizzare nella cache i canali offline e distribuirli al lettore.

Viene eseguito sia sul lato server che sul lato client.

**Sul lato** server:

* Il contenuto dei canali, comprese le risorse, viene memorizzato nella cache in */var/contentsync*.
* La cache viene esposta ai lettori tramite un manifesto che descrive il contenuto disponibile per una visualizzazione.

**Sul lato** client:

* Player aggiorna il contenuto in base al manifesto generato in precedenza.

### Vantaggi di SmartSync {#benefits-of-using-smartsync}

La funzione SmartSync offre diversi vantaggi al progetto AEM Screens. Consente

* Riduzione drastica del traffico di rete e dei requisiti di storage lato server
* Player scarica in modo intelligente le risorse solo se la risorsa risulta mancante o modificata
* Ottimizzazioni dello storage lato server e lato client

>[!NOTE]
>
>Adobe consiglia vivamente di utilizzare SmartSync per i progetti AEM Screens.

## Migrazione da ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Se avete già installato AEM 6.3 Feature Pack 5 e AEM 6.4 Feature Pack 3, potete abilitare SmartSync per le risorse per migliorare l'utilizzo dello spazio su disco. Per abilitare SmartSync, segui la sezione seguente per passare da ContentSync a SmartSync, abilitando in tal modo SmartSync.
>
>SmartSync è disponibile per Screens Player con i server AEM 6.4.3 FP3 supportati.
>
>Per scaricare il lettore più recente, consulta i download [di](https://download.macromedia.com/screens/) AEM Screens Player. La tabella seguente descrive la versione minima del lettore richiesta per ciascuna piattaforma:

| **Piattaforma** | **Versione minima del lettore supportato** |
|---|---|
| Android | 3.3.72 |
| Sistema operativo Chrome | 1.0.136 |
| Windows | 1.0.136 |

Per passare da ContentSync a SmartSync, effettuate le seguenti operazioni:

1. La migrazione da ContentSync a SmartSync richiede la cancellazione della cache ContentSync prima di attivare SmartSync.

   Andate alla console ContentSync dall'istanza utilizzando il collegamento ***https://localhost:4502/libs/cq/contentsync/content/console.html*** e fate clic su **Cancella cache**, come illustrato nella figura seguente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >È necessario cancellare tutta la cache del contenuto prima di utilizzare SmartSync per la prima volta.

1. Passa alla configurazione **della console Web di** Adobe Experience Manager tramite l’istanza di AEM —&gt; icona a forma di martello —&gt; **Operazioni** —&gt; Console **** Web.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Viene aperta la configurazione della console Web di Adobe Experience Manager **s. Cercare *offline contentservices*.

   Per cercare la proprietà **Screens Offline Content Service** , premere **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Fate clic su **Salva** per abilitare la proprietà **Screens Offline Content Services** e quindi utilizzate SmartSync per AEM Screens.
1. Dopo aver attivato SmartSync, devi accedere al progetto e fare clic su **Aggiorna contenuto** offline *(dalla barra delle azioni),* come mostrato nella figura seguente.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)