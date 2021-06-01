---
title: Analytics con AEM Screens
seo-title: Analytics con AEM Screens
description: La pagina descrive Analytics con AEM Screens
seo-description: La pagina descrive l’analisi con AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Analytics con AEM Screens {#analytics-screens}

>[!NOTE]
>
>I soggetti più comuni a questa attività sono i Marketing/Business Strategist.

AEM Screens offre la possibilità di acquisire localmente ogni evento tracciabile eseguito da ciascun dispositivo di riproduzione. Questi dati verranno memorizzati localmente fino a quando non sarà possibile caricarli nel cloud per l’elaborazione. Oltre a tutti i dati evento, vengono aggiunti anche un deviceID e una marca temporale. In questo modo è possibile distinguere i dati di un lettore da un altro e, se lo si desidera, i dati eseguiti in momenti diversi della giornata possono essere valutati separatamente.

Ci sono due ragioni fondamentali per cui possiamo voler acquisire questi dati.

Il primo prevede **cicli di feedback e apprendimento automatico**, mentre il secondo prevede la **creazione di grafici, dashboard e report** destinati al consumo umano.

Nel caso di utilizzo del ciclo di feedback, non ci occupiamo di report visivi o dashboard, ma vogliamo definire regole che AEM eseguire per la modifica del contenuto. Utilizzando ed elaborando tutti i dati evento del lettore Screens da un certo periodo di tempo, possiamo definire una regola che valuta l&#39;efficacia di image1 rispetto a image2. Combinando i dati di vendita con i dati di riproduzione, AEM determinare che image1 ha un impatto molto maggiore sulle vendite e indica automaticamente a tutti i giocatori di utilizzare image1.

Il secondo caso d’uso con analytics consiste nell’elaborare eventi di riproduzione e dati di utilizzo per il consumo umano tramite report e dashboard.
Possiamo utilizzare questi dati per creare una mappa di calore di un&#39;esperienza interattiva per determinare la mappa di percorso preferita attraverso la nostra applicazione. Possiamo anche scegliere la creazione di un dashboard che fornisce un&#39;interpretazione grafica del numero di volte in cui i consumatori interagiscono con la nostra applicazione.

