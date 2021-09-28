---
title: Utilizzo di rappresentazioni adattive in AEM Screens
description: Questa pagina descrive come utilizzare le rappresentazioni adattive in AEM Screens.
source-git-commit: 68e7a47d7a9b10d1d3fecb7a7f7d96bbbde1c48a
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Utilizzo di rappresentazioni adattive in AEM Screens {#adaptive-renditions}

## Introduzione {#introduction}

Le rappresentazioni adattive consentono ai dispositivi di selezionare automaticamente il rendering migliore per un dispositivo in base alle regole definite dal cliente. I dispositivi scaricheranno e riprodurranno automaticamente il rendering più appropriato di una risorsa in base a queste regole, consentendo ai clienti di concentrarsi solo sulla progettazione dell&#39;esperienza *principale*.

## Obiettivo {#objective}

In qualità di autore dei contenuti di AEM Screens, ora puoi configurare rappresentazioni di risorse specifiche per dispositivo da scaricare e riprodurre automaticamente senza dover creare manualmente tutte le varianti di contenuto.
Una volta che uno sviluppatore aggiunge le proprietà e le regole di mappatura del rendering, è ora pronto per applicare la mappatura del rendering alle risorse e successivamente includerle in un canale AEM Screens.

>[!IMPORTANT]
>Prima di iniziare a utilizzare le rappresentazioni adattive, in un canale AEM Screens, è consigliabile conoscere la Panoramica e la configurazione architettoniche di questa funzione. Consulta [Rappresentazioni adattive: Panoramica dell&#39;architettura e configurazioni](/help/user-guide/adaptive-renditions.md) per ulteriori dettagli.

## Utilizzo di rappresentazioni adattive nei canali {#using-adaptive-renditions}

>[!NOTE]
>Dopo aver aggiunto [proprietà di mappatura rendering al progetto Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) e [regole di mappatura rendering](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), come autore del contenuto ora puoi applicare i rendering alle risorse.

### Applicazione di rappresentazioni alle risorse {#apply-renditions-assets}

Segui i passaggi riportati di seguito per applicare rappresentazioni alle risorse, che desideri utilizzare nel canale Tour Screens:

1. Passa alla cartella **Risorse** nell’istanza AEM.

1. Crea una versione della risorsa più adatta alla visualizzazione di segnaletica, ad esempio `seahorse.jpg`.

1. Scegli il pattern di denominazione del rendering, ad esempio`landscape`, simile a quello definito nella proprietà **pattern** in **CRXDE Lite**. Per ulteriori informazioni, consulta [Aggiunta di regole di mappatura rappresentazioni](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) .

1. Rinomina il file della risorsa in modo che contenga il pattern (definito nel passaggio 3), ad esempio `seahorse-landscape.png`.

1. Fai clic su **Aggiungi rappresentazione** per caricare il rendering, come mostrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/add-rendition.png)

1. Dopo aver aggiunto la risorsa, selezionala e fai clic su **Gestisci pubblicazione** nella barra delle azioni per pubblicarla.

   ![immagine](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Per ulteriori informazioni sulla gestione della pubblicazione e sulla distribuzione degli aggiornamenti dei contenuti da Author a Publish al dispositivo, consulta [Aggiornamento dei contenuti on-demand](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) .


## Strategia di migrazione {#migration-strategy}

>[!IMPORTANT]
>Per le reti di grandi dimensioni, si raccomanda che la migrazione venga effettuata gradualmente per attenuare i rischi, in quanto la funzione introdurrà modifiche nel formato di archiviazione del file e del manifesto. L&#39;aggiunta di `sling:configRef` all&#39;intero progetto comporta l&#39;aggiornamento di tutti i lettori al Feature Pack 6.5.9. Nel caso in cui alcuni dei lettori siano stati aggiornati, è necessario aggiungere il `sling:configRef` solo alle cartelle di display, posizioni o canali con tutti i lettori aggiornati al Feature Pack 6.5.9.

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

