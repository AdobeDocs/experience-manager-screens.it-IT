---
title: Analisi con  AEM Screens
seo-title: Analisi con  AEM Screens
description: La pagina descrive Analytics con  AEM Screens
seo-description: La pagina descrive l'analisi con  AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Analytics con  AEM Screens {#analytics-screens}

>[!NOTE]
>
>Gli azionisti tipici di questa attività sono i Marketing/Business Strategist.

 AEM Screens offre la possibilità di acquisire localmente ogni evento tracciabile eseguito da ogni dispositivo di riproduzione. Questi dati verranno memorizzati localmente fino a quando non sarà possibile caricarli nel cloud per l&#39;elaborazione. Oltre a tutti i dati dell&#39;evento, vengono aggiunti anche deviceID e timestamp. In questo modo i dati di un lettore possono essere distinti da un altro e i dati eseguiti in momenti diversi della giornata possono essere valutati separatamente, se lo si desidera.

Ci sono due ragioni fondamentali per cui potremmo voler acquisire questi dati.

Il primo prevede **cicli di feedback e apprendimento delle macchine**, mentre il secondo prevede la **creazione di grafici, dashboard e report** destinati al consumo umano.

Nel caso di utilizzo del ciclo di feedback, non ci occupiamo di rapporti visivi o dashboard, ma vogliamo definire regole che AEM eseguire per la modifica del contenuto. Utilizzando ed elaborando tutti i dati evento del lettore Screens da un determinato periodo di tempo, possiamo definire una regola che valuta l&#39;efficacia di image1 rispetto a image2. Combinando i dati di vendita con i dati di riproduzione, AEM determinare che image1 ha un impatto maggiore sulle vendite e istruisce automaticamente tutti i giocatori a utilizzare image1.

Il secondo caso d’uso con l’analisi consiste nell’elaborare gli eventi di riproduzione e i dati di utilizzo per il consumo umano tramite report e dashboard.
Possiamo utilizzare questi dati per creare una mappa di calore di un&#39;esperienza interattiva per determinare la mappa di viaggio preferita attraverso la nostra applicazione. Possiamo anche scegliere di creare un dashboard che fornisca un&#39;interpretazione grafica del numero di volte che i consumatori interagiscono con la nostra applicazione.

