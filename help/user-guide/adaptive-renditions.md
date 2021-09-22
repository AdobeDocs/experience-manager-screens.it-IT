---
title: Rappresentazioni adattive in AEM Screens
description: Questa pagina descrive la Panoramica dell’architettura e le configurazioni per le rappresentazioni adattive in AEM Screens.
index: false
source-git-commit: 951fd38d5f69cdab1bf9b23f07b4e92075e87baf
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 1%

---


# Rappresentazioni adattive: Panoramica e configurazioni dell&#39;architettura {#adaptive-renditions}

## Introduzione {#introduction}

Le rappresentazioni adattive consentono ai dispositivi di selezionare automaticamente il rendering migliore per un dispositivo in base alle regole definite dal cliente. I dispositivi scaricheranno e riprodurranno automaticamente il rendering più appropriato di una risorsa in base a queste regole, consentendo ai clienti di concentrarsi solo sulla progettazione dell&#39;esperienza *principale*.

## Obiettivo {#objective}

In qualità di sviluppatore di AEM Screens, ora puoi configurare rappresentazioni di risorse specifiche per dispositivo da scaricare e riprodurre automaticamente senza dover creare manualmente tutte le varianti di contenuto. È necessario configurare le rappresentazioni adattive prima che un autore di contenuti possa utilizzare questa funzione in un canale AEM Screens.

## Panoramica dell&#39;architettura {#architectural-overview}

Le rappresentazioni adattive si basano sull’idea di avere più rappresentazioni di risorse denominate in base a una convenzione di denominazione specifica. La decisione di riprodurre un rendering specifico viene presa valutando espressioni di query multimediali che possono essere risolte solo su dispositivi con funzionalità previste.

La possibilità di avere un pattern di denominazione del rendering associato definisce una regola di mappatura del rendering, ad esempio verticale o orizzontale, come illustrato nella figura riportata di seguito. Dopo aver calcolato tutte le espressioni disponibili, il lettore Screens raccoglierà i pattern di denominazione corrispondenti alle regole corrispondenti. I pattern vengono utilizzati per trovare le rappresentazioni corrette durante la riproduzione della sequenza, cercando i pattern nei nomi delle rappresentazioni.

![immagine](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Aggiunta di una proprietà di mappatura rendering al progetto Screens {#rendition-mapping-new}

Per abilitare la funzione Rendering adattivo, devono essere presenti le seguenti regole di mappatura e la configurazione in base al contesto (CA) deve essere risolvibile per i canali e i display.

>[!NOTE]
>Per ulteriori informazioni sulle configurazioni in base al contenuto, consulta [qui](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Per configurare la configurazione, effettua le seguenti operazioni:

1. Passa a **CRXDE Lite**. Controlla se la configurazione **rendition-mapping** esiste in `/conf/screens/sling:configs/rendition-mapping`, come illustrato nella figura seguente.

   >![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Se hai installato l&#39;ultimo Feature Pack 202109, in CRXDE Lite verrà visualizzata la struttura del nodo **rendition-mapping** precompilata in `/conf/screens/sling:configs/rendition-mapping`. Per informazioni sull’ultimo pacchetto di funzioni, consulta [Note sulla versione per Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md) .
   >Per i progetti esistenti, assicurati che al progetto Screens sia associata la configurazione **rendition-mapping** . Per ulteriori informazioni, consulta la sezione [Aggiunta di mappature rappresentazioni a un progetto esistente](#rendition-mapping-existing) .

### Aggiunta di una proprietà di mappatura rendering a un progetto esistente {#rendition-mapping-existing}

1. Passa a **CRXDE Lite**.

1. Definisci esplicitamente l’associazione di mappatura del rendering aggiungendo la proprietà `sling:configRef` che punta a `/conf/screens` al nodo del contenuto del progetto, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Configurazione di Author e Publish {#setup-author-publish}

Prima di utilizzare le rappresentazioni adattive, considera i seguenti consigli in Author e Publish (Creazione e pubblicazione):

* La mappatura delle rappresentazioni deve essere replicata manualmente.

* Le rappresentazioni delle risorse non vengono replicate per impostazione predefinita. Tutte le risorse rilevanti devono essere replicate manualmente.

## Aggiunta di regole di mappatura rendering {#add-rendition-mapping-rules}

1. Per aggiungere una regola di mappatura è necessario creare un nodo di tipo `nt:unstructured` sotto il nodo **rendition-mapping**.

1. Aggiungi la proprietà espressione con il valore contenente l’espressione query.

   >[!NOTE]
   >Per ulteriori informazioni, consulta [Utilizzo della sintassi delle query multimediali](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) .

1. Aggiungi la proprietà pattern con il valore contenente il pattern di denominazione del rendering che verrà selezionato, se l’espressione viene valutata su true.

   ![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## Passaggi successivi {#next-steps}

Dopo aver configurato e caricato le rappresentazioni, come autore di contenuti, ora puoi utilizzare le rappresentazioni adattive e anche migrare i dispositivi per reti di grandi dimensioni per usufruire di questa funzione nei tuoi canali AEM Screens. Per ulteriori informazioni, consulta [Utilizzo di rappresentazioni adattive](/help/user-guide/using-adaptive-renditions.md) .
