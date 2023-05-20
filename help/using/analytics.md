---
title: Analytics con AEM Screens
seo-title: Analytics with AEM Screens
description: La pagina descrive Analytics con AEM Screens
seo-description: The page describes the analytics with AEM Screens
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Le parti interessate tipiche di questa attività sono un Marketing/Business Strategist.

AEM Screens offre la possibilità di acquisire localmente ogni evento tracciabile eseguito da ogni dispositivo di riproduzione. Questi dati verranno memorizzati localmente fino a quando non potranno essere caricati nel cloud per l’elaborazione. Oltre a tutti i dati dell’evento, vengono aggiunti anche un deviceID e una marca temporale. In questo modo i dati di un lettore possono essere distinti da quelli di un altro lettore e, se necessario, i dati eseguiti in momenti diversi della giornata possono essere valutati separatamente.

Ci sono due motivi fondamentali per cui possiamo voler acquisire questi dati.

Il primo riguarda **cicli di feedback e apprendimento automatico** mentre il secondo riguarda **creazione di grafici, dashboard e report** destinati al consumo umano.

Nel caso di utilizzo del ciclo di feedback, non ci occupiamo di rapporti visivi o dashboard, ma vogliamo definire regole su cui l’AEM può eseguire per la modifica del contenuto. Consumando ed elaborando tutti i dati dell’evento del lettore Screens da un determinato periodo di tempo, possiamo definire una regola che valuta l’efficacia di image1 rispetto a image2. Combinando i dati di vendita con i dati di riproduzione, l&#39;AEM può determinare che image1 ha un impatto molto maggiore sulle vendite e istruisce automaticamente tutti i giocatori ad utilizzare image1.

Il secondo caso di utilizzo di Analytics consiste nell’elaborare eventi di riproduzione e dati di utilizzo per il consumo umano tramite rapporti e dashboard.
Potremmo utilizzare questi dati per creare una mappa di calore di un’esperienza interattiva per determinare la mappa di percorso preferita tramite la nostra applicazione. Possiamo anche scegliere di creare una dashboard che fornisca un’interpretazione grafica del numero di volte in cui i consumatori interagiscono con la nostra applicazione.
