---
title: Utilizzo di rappresentazioni adattive in AEM Screens
description: Scopri come utilizzare le rappresentazioni adattive in AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Utilizzo di rappresentazioni adattive in AEM Screens {#adaptive-renditions}

## Introduzione {#introduction}

Le rappresentazioni adattive consentono ai dispositivi di fare clic automaticamente sulla rappresentazione migliore per un dispositivo in base a regole definite dal cliente. I dispositivi scaricano e riproducono automaticamente il rendering più appropriato di una risorsa in base a queste regole. Consente ai clienti di concentrarsi sulla progettazione dell&#39;esperienza *main*.

## Obiettivo {#objective}

In qualità di autore di contenuti AEM Screens, ora puoi configurare le rappresentazioni di risorse specifiche per il dispositivo in modo che vengano scaricate e riprodotte automaticamente senza dover creare manualmente tutte le varianti di contenuto.
Dopo che uno sviluppatore ha aggiunto le proprietà e le regole di mappatura della rappresentazione, puoi applicare la mappatura alle risorse e quindi includerle in un canale AEM Screens.

>[!IMPORTANT]
>Prima di iniziare a utilizzare le rappresentazioni adattive in un canale AEM Screens, l’Adobe consiglia di conoscere la panoramica e la configurazione dell’architettura di questa funzione. Consulta [Rappresentazioni adattive: panoramica dell&#39;architettura e configurazioni](/help/user-guide/adaptive-renditions.md).

## Utilizzo di rappresentazioni adattive nei canali {#using-adaptive-renditions}

>[!NOTE]
>Dopo aver aggiunto la proprietà [rendition-mapping al progetto Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) e le [regole di rendering-mapping](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), in qualità di autore del contenuto sei pronto per applicare le rappresentazioni alle risorse.

### Applicazione delle rappresentazioni ad Assets {#apply-renditions-assets}

Per applicare le rappresentazioni alle risorse da utilizzare nel canale Screens per presentazioni, effettua le seguenti operazioni.

1. Passa alla cartella **Assets** nell&#39;istanza AEM.
1. Creare una versione della risorsa più adatta alla visualizzazione della segnaletica, ad esempio `seahorse.jpg`.
1. Scegli il pattern di denominazione della rappresentazione, ad esempio `landscape`, simile a quello definito nella proprietà **pattern** in **CRXDE Liti**. Per ulteriori dettagli, vedere [Aggiunta delle regole di mapping delle rappresentazioni](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules).
1. Fai clic su **Aggiungi rappresentazione** per caricare la rappresentazione, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Fai clic sul file della risorsa rinominato. La copia trasformata che si sta aggiungendo deve contenere il modello (definito nel passaggio 3), ad esempio `seahorse-landscape.png`.
1. Dopo aver aggiunto la risorsa, fai clic sulla risorsa e fai clic su **Gestisci pubblicazione** nella barra delle azioni per pubblicare la risorsa.

   ![immagine](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Per ulteriori informazioni sulla gestione della pubblicazione e sulla distribuzione degli aggiornamenti del contenuto da Author a Publish al dispositivo, consulta [Aggiornamento dei contenuti on-demand](https://experienceleague.adobe.com/it/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content).

## Strategia di migrazione {#migration-strategy}

>[!IMPORTANT]
>Per le reti di grandi dimensioni, l&#39;Adobe raccomanda che la migrazione sia effettuata gradualmente per mitigare i rischi. Il motivo è che la funzione può introdurre modifiche nel formato di archiviazione del manifesto e dei file. L&#39;aggiunta di `sling:configRef` all&#39;intero progetto comporta l&#39;aggiornamento di tutti i lettori a Feature Pack 6.5.9. Se hai aggiornato alcuni lettori, aggiungi `sling:configRef` solo alle visualizzazioni, alle posizioni o alle cartelle di canale in cui tutti i lettori sono stati aggiornati a Feature Pack 6.5.9.

Il diagramma seguente illustra la strategia di migrazione per le reti di grandi dimensioni:

![immagine](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Per abilitare la funzione, aggiungi almeno una regola di mappatura e assicurati che la configurazione di mappatura rappresentazione sia risolvibile nel contesto di visualizzazioni e canali. Per eseguire la migrazione, segui i passaggi seguenti:

1. Aggiungi [Regole di mappatura rappresentazione](/help/user-guide/adaptive-renditions.md).
1. Crea una cartella per i nuovi canali e aggiungi un riferimento che punti alla configurazione di mappatura rappresentazione.
1. Crea canali che sostituiscono quelli precedenti e carica le rappresentazioni.
1. Riassegna visualizzazioni ai nuovi canali.
1. Aggiungi un riferimento alle visualizzazioni o alle posizioni migrate che puntano alla configurazione di mappatura rappresentazione.
1. Ripetere i punti 3, 4 e 5 per tutti i restanti canali e display.

   >[!NOTE]
   >Dopo aver completato la migrazione, assicurati di rimuovere tutti i riferimenti di configurazione da canali, visualizzazioni e posizioni e di aggiungerne uno singolo al nodo del contenuto del progetto.
