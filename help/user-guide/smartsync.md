---
title: Transizione da ContentSync a SmartSync
seo-title: Transizione da ContentSync a SmartSync
description: Segui questa pagina per scoprire la funzione SmartSync e come puoi passare da ContentSync a SmartSync.
seo-description: Segui questa pagina per scoprire la funzione SmartSync e come puoi passare da ContentSync a SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
feature: Amministrazione di schermi
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---

# Transizione da ContentSync a SmartSync {#transitioning-from-contentsync-to-smartsync}

Questa sezione fornisce una panoramica della funzione SmartSync e di come riduce al minimo il carico/lo storage del server e il traffico di rete per ridurre i costi.

## Panoramica {#overview}

SmartSync è l’ultimo meccanismo utilizzato da AEM Screens. Sostituisce il metodo corrente utilizzato per memorizzare in cache i canali offline e consegnarli al lettore.

Viene eseguito sia sul lato server che sul lato client.

**Sul lato** server:

* Il contenuto dei canali, incluse le risorse, è memorizzato nella cache in */var/contentsync*.
* La cache viene esposta ai lettori tramite un manifesto che descrive il contenuto disponibile per una visualizzazione.

**Sul lato** client:

* Il lettore aggiorna il contenuto in base al manifesto generato in precedenza.

### Vantaggi di SmartSync {#benefits-of-using-smartsync}

La funzione SmartSync offre diversi vantaggi al progetto AEM Screens. Permette

* Riduzione drastica del traffico di rete e dei requisiti di storage lato server
* Player scarica in modo intelligente le risorse solo se la risorsa è mancante o modificata
* Ottimizzazioni dello storage lato server e lato client

>[!NOTE]
>
>Adobe consiglia vivamente di utilizzare SmartSync per i progetti AEM Screens.

## Migrazione da ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Se AEM 6.3 Feature Pack 5 e AEM 6.4 Feature Pack 3 è già stato installato, è possibile abilitare SmartSync per le risorse per migliorare l&#39;utilizzo dello spazio su disco. Per abilitare SmartSync, segui la sezione seguente per passare da ContentSync a SmartSync, abilitando in tal modo SmartSync.
>
>SmartSync è disponibile per Screens Player con server supportati AEM 6.4.3 FP3.
>
>Fai riferimento a [AEM Screens Player Downloads](https://download.macromedia.com/screens/) per scaricare l&#39;ultimo lettore. La tabella seguente descrive la versione minima del lettore richiesta per ciascuna piattaforma:

| **Platform** | **Versione minima del lettore supportata** |
|---|---|
| Android | 3.3.72 |
| Sistema operativo Chrome | 1,0,136 |
| Windows | 1,0,136 |

Segui i passaggi seguenti per passare da ContentSync a SmartSync:

1. La migrazione da ContentSync a SmartSync richiede la cancellazione della cache ContentSync prima di attivare SmartSync.

   Passa alla console ContentSync dalla tua istanza utilizzando il collegamento ***https://localhost:4502/libs/cq/contentsync/content/console.html*** e fai clic su **Cancella cache**, come illustrato nella figura seguente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >È necessario cancellare tutta la cache del contenuto prima di utilizzare SmartSync per la prima volta.

1. Passa a **Configurazione della console Web Adobe Experience Manager** tramite AEM istanza —> icona a forma di martello —> **Operazioni** —> **Console web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Viene** aperta la configurazione della console Web Adobe Experience Manager. Cerca *offlinecontentservice*.

   Per cercare la proprietà **Screens Offline Content Service** , premi **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Fai clic su **Salva** per abilitare la proprietà **Screens Offline Content Services** e quindi utilizza SmartSync per AEM Screens.
1. Dopo aver abilitato SmartSync, devi accedere al progetto e fare clic su **Aggiorna contenuto offline** *(dalla barra delle azioni),* come mostrato nella figura seguente.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
