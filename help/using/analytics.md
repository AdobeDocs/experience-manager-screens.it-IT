---
title: Analytics con AEM Screens
description: Scopri Adobe Analytics con Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Le parti interessate tipiche di questa attività sono Marketing/Business Strategists.

AEM Screens può acquisire localmente ogni evento tracciabile eseguito da ogni dispositivo di riproduzione. Questi dati vengono memorizzati localmente fino a quando non possono essere caricati sul cloud per l’elaborazione. Oltre a tutti i dati dell’evento, vengono aggiunti anche un deviceID e una marca temporale. Questa funzionalità assicura che i dati di un lettore siano distinguibili da quelli di un altro. Inoltre, i dati eseguiti in momenti diversi della giornata possono essere valutati separatamente, se lo si desidera.

Esistono due motivi fondamentali per acquisire questi dati.

Il primo prevede **cicli di feedback e apprendimento automatico**, mentre il secondo **prevede la creazione di grafici, dashboard e report** destinati al consumo umano.

Nel caso di utilizzo del ciclo di feedback, non è necessario preoccuparsi dei rapporti visivi o delle dashboard, ma desideri definire regole su cui l’AEM può eseguire per la modifica del contenuto. Utilizzando ed elaborando tutti i dati evento del lettore Screens da un determinato periodo di tempo, puoi definire una regola che valuta l’efficacia di image1 rispetto a image2. Combinando i dati di vendita con i dati di riproduzione, l&#39;AEM può determinare che image1 ha un impatto maggiore sulle vendite e istruisce automaticamente tutti i giocatori ad utilizzare image1.

Il secondo caso di utilizzo con Analytics consiste nell’elaborare eventi di riproduzione e dati di utilizzo per il consumo umano tramite rapporti e dashboard.
Puoi utilizzare questi dati per creare una mappa di calore di un’esperienza interattiva per determinare la mappa di percorso preferita tramite l’applicazione. Puoi anche scegliere di creare una dashboard che fornisca un’interpretazione grafica del numero di volte in cui i consumatori interagiscono con l’applicazione.
