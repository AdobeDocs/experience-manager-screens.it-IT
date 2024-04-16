---
title: Transizione da ContentSync a SmartSync
description: Ulteriori informazioni sulla funzione SmartSync e su come passare da ContentSync a SmartSync.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Transizione da ContentSync a SmartSync {#transitioning-from-contentsync-to-smartsync}

In questa sezione viene fornita una panoramica della funzione SmartSync e del modo in cui riduce il carico/lo storage del server e il traffico di rete per ridurre i costi.

## Panoramica {#overview}

SmartSync è il meccanismo più recente utilizzato da AEM Screens. Serve come sostituzione del metodo corrente utilizzato per memorizzare in cache i canali offline e distribuirli al lettore.

Viene eseguito sia sul lato server che sul lato client.

**Sul lato server**:

* Il contenuto dei canali, incluse le risorse, è memorizzato nella cache in *`/var/contentsync`*.
* La cache viene esposta ai lettori tramite un manifesto che descrive il contenuto disponibile per una visualizzazione.

**Sul lato client**:

* Il contenuto del lettore viene aggiornato in base al manifesto generato in precedenza.

### Vantaggi dell&#39;utilizzo di SmartSync {#benefits-of-using-smartsync}

La funzione SmartSync offre diversi vantaggi al progetto AEM Screens, ad esempio i seguenti:

* Notevole riduzione del traffico di rete e dei requisiti di storage lato server.
* Il lettore scarica le risorse in modo intelligente solo se la risorsa risulta mancante o modificata.
* Ottimizzazioni dello storage lato server e lato client.

>[!NOTE]
>
>L’Adobe consiglia vivamente di utilizzare SmartSync per i progetti AEM Screens.

## Migrazione da ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Se hai già installato AEM 6.3 Feature Pack 5 e AEM 6.4 Feature Pack 3, puoi abilitare SmartSync per le risorse per migliorare l’utilizzo dello spazio su disco. Per abilitare SmartSync, seguire la sezione seguente per passare da ContentSync a SmartSync, abilitando così SmartSync.
>
>SmartSync è disponibile per Screens Player con server supportati AEM 6.4.3 FP3.
>
>Consulta la [Download di AEM Screens Player](https://download.macromedia.com/screens/) per scaricare il lettore più recente. La tabella seguente descrive la versione minima del lettore richiesta per ogni piattaforma:

| **Piattaforma** | **Versione minima del lettore supportata** |
|---|---|
| Android™ | 3.3.72 |
| Chrome OS | 1,0,136 |
| Windows | 1,0,136 |

Per passare da ContentSync a SmartSync, effettua le seguenti operazioni:

1. La migrazione da ContentSync a SmartSync richiede la cancellazione della cache di ContentSync prima di attivare SmartSync.

   Passa alla console ContentSync dalla tua istanza utilizzando il collegamento ***https://localhost:4502/libs/cq/contentsync/content/console.html*** e fai clic su **Cancella cache**, come illustrato nella figura seguente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Prima di utilizzare SmartSync per la prima volta, è necessario cancellare tutta la cache del contenuto.

1. Accedi a **Configurazione console Web Adobe Experience Manager** tramite istanza AEM > icona a forma di martello > **Operazioni** > **Console web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Configurazione console Web Adobe Experience Manager** viene aperto. Cerca *offlinecontentservice*.

   Per eseguire ricerche in **Servizio di contenuti offline Screens** proprietà, premere **Comando+F** per **Mac**, e **Ctrl+F** per **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Clic **Salva** per attivare **Screens Offline Content Services** e quindi utilizzare SmartSync per AEM Screens.
1. Dopo aver abilitato SmartSync, accedere al progetto e fare clic su **Aggiorna contenuto offline** *(dalla barra delle azioni),* come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
