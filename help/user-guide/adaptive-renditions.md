---
title: Rappresentazioni adattive in AEM Screens
description: Questa pagina descrive la Panoramica dell’architettura e le configurazioni per le rappresentazioni adattive in AEM Screens.
index: false
source-git-commit: 898eb8e7e9b7442aead9fb6fb89c2646aef65e05
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 1%

---


# Rappresentazioni adattive: Panoramica e configurazioni dell&#39;architettura {#adaptive-renditions}

## Introduzione {#introduction}

Le rappresentazioni adattive consentono ai dispositivi di selezionare automaticamente il rendering migliore per un dispositivo in base alle regole definite dal cliente. I dispositivi scaricheranno e riprodurranno automaticamente il rendering più appropriato di una risorsa in base a queste regole, consentendo ai clienti di concentrarsi solo sulla progettazione dell&#39;esperienza *principale*.

## Obiettivo {#objective}

In qualità di sviluppatore di AEM Screens, ora puoi configurare rappresentazioni di risorse specifiche per dispositivo da scaricare e riprodurre automaticamente senza dover creare manualmente tutte le varianti di contenuto. Per poter utilizzare questa funzione in un canale AEM Screens, è necessario configurare le rappresentazioni adattive.

Pertanto, se hai implementato una varietà di dispositivi, l’utilizzo di questa funzione consentirà al dispositivo di scaricare e riprodurre automaticamente il rendering più appropriato di una risorsa in base alle regole.

## Panoramica dell&#39;architettura {#architectural-overview}

Le rappresentazioni adattive si basano sull’idea di avere più rappresentazioni di risorse denominate in base a una convenzione di denominazione specifica. La decisione di riprodurre un rendering specifico viene presa valutando espressioni di query multimediali che possono essere risolte solo su dispositivi con funzionalità previste. La capacità di avere un pattern di denominazione del rendering associato definisce una regola di mappatura del rendering. Dopo aver calcolato tutte le espressioni disponibili, il lettore Screens raccoglierà i pattern di denominazione corrispondenti alle regole corrispondenti. I pattern vengono utilizzati per trovare le rappresentazioni corrette durante la riproduzione della sequenza, cercando i pattern nei nomi delle rappresentazioni.

![immagine](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Configurazione dell’impostazione per l’utilizzo delle rappresentazioni adattive {#setup-adaptive-renditions}

Per abilitare la funzione Rendering adattivo, le regole di mappatura devono essere presenti e la configurazione CA deve essere risolvibile per i canali e le visualizzazioni:

1. Controlla se la configurazione della mappatura del rendering esiste in `JCR`. Tutti i pacchetti di funzioni più recenti dispongono di questa struttura di nodi precompilata.

   >[!NOTE]
   >Tutti i pacchetti di funzioni più recenti dispongono di questa struttura di nodi precompilata.

   ![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. Assicurati che al progetto Screens sia associata la configurazione di mappatura del rendering.

   * Ogni nuovo progetto creato con la procedura guidata di progetto Screens conterrà un riferimento alla configurazione della mappatura del rendering.

      ![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * In una versione precedente dei progetti Screens, è necessario definire esplicitamente l’associazione aggiungendo la proprietà `sling:configRef` che punta a `/conf/screens` al nodo del contenuto del progetto.

      ![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)

## Strategia di migrazione {#migration-strategy}

>[!IMPORTANT]
>Per le reti di grandi dimensioni, si raccomanda che la migrazione venga effettuata gradualmente per attenuare i rischi, in quanto la funzione introdurrà modifiche nel formato di archiviazione del file e del manifesto.

Il diagramma seguente illustra la strategia di migrazione per le reti di grandi dimensioni:

![immagine](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Per abilitare la funzione, aggiungi almeno una regola di mappatura e assicurati che la configurazione della mappatura del rendering sia risolvibile nel contesto di visualizzazioni e canali. Per eseguire la migrazione, effettua le seguenti operazioni:

1. Aggiungi [Regole di mappatura rappresentazioni](#adding-rendition-mapping-rules).
1. Crea una cartella per i nuovi canali e aggiungi un riferimento che punta alla configurazione di mappatura del rendering.
1. Crea nuovi canali sostituendo quelli precedenti e carica le rappresentazioni.
1. Riassegna le visualizzazioni ai nuovi canali.
1. Aggiungi un riferimento alle visualizzazioni o alle posizioni migrate che puntano alla configurazione di mappatura del rendering.
1. Ripetere i passaggi 3, 4 e 5 per tutti i canali e le visualizzazioni rimanenti.
1. Dopo aver completato la migrazione, rimuovi tutti i riferimenti di configurazione dai canali, dalle visualizzazioni e dalle posizioni e aggiungi un singolo riferimento al nodo di contenuto del progetto.

## Configurazione di Author e Publish {#setup-author-publish}

Prima di utilizzare le rappresentazioni adattive, considera i seguenti consigli in Author e Publish (Creazione e pubblicazione):

* La mappatura delle rappresentazioni deve essere replicata manualmente.

* Le rappresentazioni delle risorse non vengono replicate per impostazione predefinita. Tutte le risorse rilevanti devono essere replicate manualmente.

## Aggiunta di regole di mappatura rendering {#add-rendition-mapping-rules}

1. Per aggiungere una regola di mappatura è necessario creare un nodo di tipo `nt:unstructured` sotto il nodo di rendering-mapping.

1. Aggiungi la proprietà espressione con il valore contenente l’espressione query.

   >[!NOTE]
   >Per ulteriori informazioni, consulta [Utilizzo della sintassi delle query multimediali](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) .

1. Aggiungi la proprietà pattern con il valore contenente il pattern di denominazione del rendering che verrà selezionato, se l’espressione viene valutata su true.

   ![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## Caricamento delle rappresentazioni {#upload-renditions}

1. Crea una versione della risorsa più adatta alla visualizzazione di segnaletica, ad esempio `portrait orientation`.

1. Scegli il pattern di denominazione del rendering, ad esempio,`portrait`.

1. Rinomina il file della risorsa in modo che contenga il pattern, ad esempio `my_asset_portrait.png`.

1. Fai clic su **Aggiungi rappresentazione** per caricare il rendering, come mostrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-rendition.png)

## Passaggi successivi {#next-steps}

Dopo aver configurato e caricato i rendering, puoi ora utilizzare le rappresentazioni adattive nei tuoi canali AEM Screens. Per ulteriori informazioni, consulta Utilizzo di rappresentazioni adattive .
