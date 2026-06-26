---
title: Panoramica e configurazioni dell’architettura di rappresentazioni adattive
description: Scopri la panoramica dell’architettura e le configurazioni in CRXDE Lite per rappresentazioni adattive in AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
TQID: https://experienceleague.adobe.com/6kL7RJWr-AJQsQdBqE-GI8lI-6QQXTNiRXP4maEdmzA
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 718
ht-degree: 4%

---

# Rappresentazioni adattive: panoramica dell’architettura e configurazioni {#adaptive-renditions}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

## Introduzione {#introduction}

>[!CAUTION]
>Questa funzione è supportata solo su AEM on-premise (AEM 6.5). Non è supportato in AEM as a Cloud Service.

Le rappresentazioni adattive consentono ai dispositivi di fare clic automaticamente sulla rappresentazione migliore per un dispositivo in base a regole definite dal cliente. I dispositivi scaricano e riproducono automaticamente il rendering più appropriato di una risorsa in base a queste regole, consentendo ai clienti di concentrarsi solo sulla progettazione dell&#39;esperienza *principale*.

## Obiettivo {#objective}

In qualità di sviluppatore di AEM Screens, ora puoi configurare i rendering di risorse specifiche per il dispositivo in modo che vengano scaricati e riprodotti automaticamente senza dover creare manualmente tutte le varianti di contenuto. Configura le rappresentazioni adattive prima che un autore di contenuti possa utilizzare questa funzione in un canale AEM Screens.

## Panoramica dell’architettura {#architectural-overview}

Le rappresentazioni adattive si basano sull’idea di avere più rappresentazioni di una risorsa denominata seguendo una convenzione di denominazione specifica. La decisione di riprodurre una rappresentazione specifica viene presa valutando le espressioni di query multimediali che possono essere risolte solo su dispositivi con funzionalità previste.

La possibilità di associare un pattern di denominazione delle rappresentazioni definisce una regola di mappatura delle rappresentazioni, ad esempio verticale o orizzontale, come illustrato nella figura seguente. Dopo aver calcolato tutte le espressioni disponibili, il lettore Screens raccoglie i pattern di denominazione corrispondenti alle regole corrispondenti. I pattern vengono utilizzati per trovare le rappresentazioni corrette durante la riproduzione della sequenza, cercando i pattern nei nomi delle rappresentazioni.

![immagine](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Aggiunta della proprietà di mappatura rappresentazione al progetto Screens {#rendition-mapping-new}

Per abilitare la funzione Rendering adattivi, è necessario che siano presenti le seguenti regole di mappatura e che la configurazione in base al contesto (CA) sia risolvibile per i canali e le visualizzazioni.

>[!NOTE]
>Per ulteriori informazioni sulle configurazioni basate sul contenuto, consulta [qui](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Per configurare la configurazione, segui i passaggi seguenti:

1. Passa a **CRXDE Lite**. Verifica se la configurazione **rendition-mapping** esiste in `/conf/screens/sling:configs/rendition-mapping`, come illustrato nella figura seguente.

   >![immagine](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Se hai installato l&#39;ultimo Feature Pack 202109, visualizzerai la struttura del nodo **rendition-mapping** precompilata in `/conf/screens/sling:configs/rendition-mapping` in CRXDE Lite. Per informazioni dettagliate sull&#39;ultimo Feature Pack, consulta le [note sulla versione del Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md).   >Per i progetti esistenti, assicurati che al progetto Screens sia associata la configurazione **rendition-mapping**. Per ulteriori informazioni, vedere [Aggiunta del mapping di rappresentazione a un progetto esistente](#rendition-mapping-existing).

### Aggiunta di una proprietà di mappatura rappresentazione a un progetto esistente {#rendition-mapping-existing}

1. Passa a **CRXDE Lite**.

1. Definisci in modo esplicito l&#39;associazione di mappatura della rappresentazione aggiungendo la proprietà `sling:configRef` che punta a `/conf/screens` al nodo del contenuto del progetto, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Aggiunta di regole di mappatura rappresentazione {#add-rendition-mapping-rules}

Per aggiungere un nodo in Mappatura rappresentazione, effettua le seguenti operazioni:

1. Passare a questo percorso `/conf/screens/sling:configs/rendition-mapping` da **CRXDE Lite**.
1. Crea un nodo in **rendition-mapping**. Fare clic con il pulsante destro del mouse su **rendition-mapping** e scegliere **Crea** > **Crea nodo**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Immetti **Nome** per la regola di mappatura, ad esempio **regola1** e il nodo **Tipo** come **`nt:unstructured`** nella finestra di dialogo **Crea nodo**. Fai clic su **OK**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Aggiungi la proprietà espressione con il valore contenente l’espressione query.

   >[!NOTE]
   >Per ulteriori informazioni, consulta [Utilizzo della sintassi per query multimediali](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries).

   Fare clic su **regola1** creata e immettere la **espressione** in **Nome** e **(orientamento:landscape)** in **Valore**, come illustrato di seguito. Fai clic su **Aggiungi**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Aggiungi la proprietà pattern con il valore contenente il pattern di denominazione della rappresentazione.

   >[!NOTE]
   >Il valore definito nella proprietà pattern viene abbinato alla nuova rappresentazione della risorsa e, se l’espressione viene valutata come true, viene selezionato.

   Per aggiungere la proprietà pattern, fare clic su **regola1** creata e immettere il **pattern** in **Nome** e **paesaggio** in **Valore**, come illustrato di seguito. Fai clic su **Aggiungi**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Fai clic su **Salva tutto** e osserva le proprietà sotto il nodo creato in **rendition-mapping**.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Passaggi successivi {#next-steps}

Dopo aver aggiunto le proprietà e le regole per la mappatura delle rappresentazioni, in qualità di Autore di contenuti puoi configurare le risorse. Puoi utilizzare le rappresentazioni adattive ed eseguire la migrazione dei dispositivi per reti di grandi dimensioni per utilizzare questa funzione nei canali di AEM Screens. Per ulteriori informazioni, vedere [Utilizzo di rappresentazioni adattive in AEM Screens](/help/user-guide/using-adaptive-renditions.md).

