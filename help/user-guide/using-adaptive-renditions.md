---
title: Utilizzo di rappresentazioni adattive in AEM Screens
description: Questa pagina descrive come utilizzare le rappresentazioni adattive in AEM Screens.
index: false
source-git-commit: 08f47e6542a7832f64d5d0dde9cdd463176f5f5d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 1%

---

# Utilizzo di rappresentazioni adattive {#adaptive-renditions}

## Introduzione {#introduction}

Le rappresentazioni adattive consentono ai dispositivi di selezionare automaticamente il rendering migliore per un dispositivo in base alle regole definite dal cliente. I dispositivi scaricheranno e riprodurranno automaticamente il rendering più appropriato di una risorsa in base a queste regole, consentendo ai clienti di concentrarsi solo sulla progettazione dell&#39;esperienza *principale*.

## Obiettivo {#objective}

In qualità di autore dei contenuti di AEM Screens, ora puoi configurare rappresentazioni di risorse specifiche per dispositivo da scaricare e riprodurre automaticamente senza dover creare manualmente tutte le varianti di contenuto.

Pertanto, se hai implementato una varietà di dispositivi, l’utilizzo di questa funzione consentirà al dispositivo di scaricare e riprodurre automaticamente il rendering più appropriato di una risorsa in base alle regole.

>[!IMPORTANT]
>Prima di iniziare a utilizzare le rappresentazioni adattive, in un canale AEM Screens, è consigliabile conoscere la Panoramica e la configurazione architettoniche di questa funzione. Consulta Rappresentazioni adattive: Panoramica dell&#39;architettura e configurazioni per ulteriori dettagli.

## Strategia di migrazione {#migration-strategy}

>[!IMPORTANT]
>Per le reti di grandi dimensioni, si raccomanda che la migrazione venga effettuata gradualmente per attenuare i rischi, in quanto la funzione introdurrà modifiche nel formato di archiviazione del file e del manifesto.

Il diagramma seguente illustra la strategia di migrazione per le reti di grandi dimensioni:

![immagine](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Per abilitare la funzione, aggiungi almeno una regola di mappatura e assicurati che la configurazione della mappatura del rendering sia risolvibile nel contesto di visualizzazioni e canali. Per eseguire la migrazione, effettua le seguenti operazioni:

1. Aggiungi [Regole di mappatura rappresentazioni](/help/user-guide/adaptive-renditions.md).
1. Crea una cartella per i nuovi canali e aggiungi un riferimento che punta alla configurazione di mappatura del rendering.
1. Crea nuovi canali sostituendo quelli precedenti e carica le rappresentazioni.
1. Riassegna le visualizzazioni ai nuovi canali.
1. Aggiungi un riferimento alle visualizzazioni o alle posizioni migrate che puntano alla configurazione di mappatura del rendering.
1. Ripetere i passaggi 3, 4 e 5 per tutti i canali e le visualizzazioni rimanenti.

   >[!NOTE]
   >Dopo aver completato la migrazione, assicurati di rimuovere tutti i riferimenti di configurazione dai canali, dalle visualizzazioni e dalle posizioni e di aggiungerne uno singolo al nodo di contenuto del progetto.


## Caricamento di rappresentazioni e utilizzo di rappresentazioni adattive in un canale AEM Screens {#upload-renditions}

1. Crea una versione della risorsa più adatta alla visualizzazione di segnaletica, ad esempio `portrait orientation`.

1. Scegli il pattern di denominazione del rendering, ad esempio,`portrait`.

1. Rinomina il file della risorsa in modo che contenga il pattern, ad esempio `my_asset_portrait.png`.

1. Fai clic su **Aggiungi rappresentazione** per caricare il rendering, come mostrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-rendition.png)