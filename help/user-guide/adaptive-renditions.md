---
title: Panoramica e configurazioni dell’architettura di rappresentazioni adattive
description: Questa pagina descrive la panoramica dell’architettura e le configurazioni in CRXDE Liti per le rappresentazioni adattive in AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# Rappresentazioni adattive: panoramica dell’architettura e configurazioni {#adaptive-renditions}

## Introduzione {#introduction}

Le rappresentazioni adattive consentono ai dispositivi di selezionare automaticamente la rappresentazione migliore per un dispositivo in base alle regole definite dal cliente. I dispositivi scaricheranno e riprodurranno automaticamente la rappresentazione più appropriata di una risorsa in base a queste regole, consentendo ai clienti di concentrarsi solo sulla progettazione della *principale* esperienza.

## Obiettivo {#objective}

In qualità di sviluppatore di AEM Screens, ora puoi configurare i rendering di risorse specifiche per il dispositivo in modo che vengano scaricati e riprodotti automaticamente senza dover creare manualmente tutte le varianti di contenuto. È necessario configurare le rappresentazioni adattive prima che un autore di contenuti possa utilizzare questa funzione in un canale AEM Screens.

## Panoramica dell’architettura {#architectural-overview}

Le rappresentazioni adattive si basano sull’idea di avere più rappresentazioni di risorse denominate seguendo una convenzione di denominazione specifica. La decisione di riprodurre una rappresentazione specifica viene presa valutando le espressioni di query multimediali che possono essere risolte solo su dispositivi con funzionalità previste.

La possibilità di associare un pattern di denominazione delle rappresentazioni definisce una regola di mappatura delle rappresentazioni, ad esempio verticale o orizzontale, come illustrato nella figura seguente. Dopo aver calcolato tutte le espressioni disponibili, il lettore Screens raccoglierà i pattern di denominazione corrispondenti alle regole corrispondenti. I pattern vengono utilizzati per trovare le rappresentazioni corrette durante la riproduzione della sequenza, cercando i pattern nei nomi delle rappresentazioni.

![immagine](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Aggiunta della proprietà di mappatura rappresentazione al progetto Schermi {#rendition-mapping-new}

Per abilitare la funzione Rendering adattivi, è necessario che siano presenti le seguenti regole di mappatura e che la configurazione in base al contesto (CA) sia risolvibile per i canali e le visualizzazioni.

>[!NOTE]
>Per ulteriori informazioni sulle configurazioni basate sul contenuto, consulta [qui](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Per configurare la configurazione, segui i passaggi seguenti:

1. Accedi a **CRXDE Liti**. Seleziona, se **rendition-mapping** la configurazione esiste in `/conf/screens/sling:configs/rendition-mapping`, come illustrato nella figura seguente.

   >![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Se hai installato la versione più recente del Feature Pack 202109, potrai vedere **rendition-mapping** struttura del nodo precompilata in `/conf/screens/sling:configs/rendition-mapping` in CRXDE Lite. Consulta [Note sulla versione per Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md) per ottenere dettagli sul feature pack più recente.
   >Per i progetti esistenti, assicurati che il progetto Screens disponga del **rendition-mapping** configurazione associata. Consulta [Aggiunta della mappatura di rappresentazione a un progetto esistente](#rendition-mapping-existing) per ulteriori informazioni.

### Aggiunta di una proprietà di mappatura rappresentazione a un progetto esistente {#rendition-mapping-existing}

1. Accedi a **CRXDE Liti**.

1. Definire in modo esplicito l’associazione per il mapping della rappresentazione aggiungendo `sling:configRef` proprietà che punta a `/conf/screens` al nodo del contenuto del progetto, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Aggiunta di regole di mappatura rappresentazione {#add-rendition-mapping-rules}

Per aggiungere un nodo in Mappatura rappresentazione, effettua le seguenti operazioni:

1. Passa a questo percorso `/conf/screens/sling:configs/rendition-mapping` da **CRXDE Liti**.

1. Crea un nodo sotto **rendition-mapping**. Fai clic con il pulsante destro del mouse su **rendition-mapping** e fai clic su **Crea** > **Crea nodo**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Inserisci il **Nome** per la regola di mappatura come **rule1** e il nodo **Tipo** as **nt:unstructured** in **Crea nodo** . Fai clic su **OK**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. È necessario aggiungere la proprietà espressione con il valore contenente l’espressione della query.

   >[!NOTE]
   >Consulta [Utilizzo della sintassi per query multimediali](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) per ulteriori informazioni.

   Fai clic su **rule1** che hai creato e immetti **espressione** in **Nome** e **(orientamento:orizzontale)** in **Valore**, come illustrato di seguito. Fai clic su **Aggiungi**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Aggiungi la proprietà pattern con il valore contenente il pattern di denominazione della rappresentazione.

   >[!NOTE]
   >Il valore definito nella proprietà pattern verrà associato alla nuova rappresentazione della risorsa e sarà selezionato, se l’espressione viene valutata come true.

   Per aggiungere la proprietà pattern, fare clic su **rule1** che hai creato e immetti **pattern** in **Nome** e **orizzontale** in **Valore**, come illustrato di seguito. Fai clic su **Aggiungi**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Fai clic su **Salva tutto** e visualizzerai le proprietà sotto il nodo creato in **rendition-mapping**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## Passaggi successivi {#next-steps}

Dopo aver aggiunto le proprietà e le regole di mappatura delle rappresentazioni, ora in qualità di Autore di contenuti, puoi configurare le risorse per l’utilizzo di rappresentazioni adattive ed eseguire la migrazione dei dispositivi per reti di grandi dimensioni per usufruire di questa funzione, nei canali di AEM Screens. Consulta [Utilizzo di rappresentazioni adattive in AEM Screens](/help/user-guide/using-adaptive-renditions.md) per ulteriori dettagli.
