---
title: Analisi con AEM Screens
seo-title: Analisi con AEM Screens
description: La pagina descrive Analytics con AEM Screens
seo-description: La pagina descrive la cronologia con AEM Screens
translation-type: tm+mt
source-git-commit: f01b69b860a3862e2b46f11b2d9b95dede742d9c

---


# Analisi con AEM Screens {#analytics-screens}

>[!NOTE]
>
>Gli azionisti tipici di questa attività sono i Marketing/Business Strategist.

AEM Screens consente di acquisire localmente ogni evento tracciabile eseguito da ciascun dispositivo di riproduzione. Questi dati verranno memorizzati localmente fino a quando non sarà possibile caricarli nel cloud per l'elaborazione. Oltre a tutti i dati dell'evento, vengono aggiunti anche deviceID e timestamp. In questo modo i dati di un lettore possono essere distinti da un altro e i dati eseguiti in momenti diversi della giornata possono essere valutati separatamente, se lo si desidera.

Ci sono due ragioni fondamentali per cui potremmo voler acquisire questi dati.

Il primo riguarda i cicli di **feedback e l'apprendimento** automatico, mentre il secondo riguarda la **creazione di grafici, dashboard e rapporti** destinati al consumo umano.

Nel caso di utilizzo del ciclo di feedback, non ci occupiamo di rapporti visivi o dashboard, ma piuttosto di definire regole che AEM può eseguire per la modifica del contenuto. Utilizzando ed elaborando tutti i dati evento del lettore Screens da un determinato periodo di tempo, possiamo definire una regola che valuta l'efficacia di image1 rispetto a image2. Combinando i dati di vendita con i dati di riproduzione, AEM può determinare che image1 ha un impatto molto maggiore sulle vendite e istruisce automaticamente tutti i lettori a utilizzare image1.

Il secondo caso d’uso con l’analisi consiste nell’elaborare gli eventi di riproduzione e i dati di utilizzo per il consumo umano tramite report e dashboard.
Possiamo utilizzare questi dati per creare una mappa di calore di un'esperienza interattiva per determinare la mappa di viaggio preferita attraverso la nostra applicazione. Possiamo anche scegliere di creare un dashboard che fornisca un'interpretazione grafica del numero di volte che i consumatori interagiscono con la nostra applicazione.

