---
title: Utilizzo di rappresentazioni adattive in AEM Screens
description: Scopri come utilizzare le rappresentazioni adattive in AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

# Utilizzo di rappresentazioni adattive in AEM Screens {#adaptive-renditions}

## Introduzione {#introduction}

Le rappresentazioni adattive consentono ai dispositivi di fare clic automaticamente sulla rappresentazione migliore per un dispositivo in base alle regole definite dal cliente. I dispositivi scaricano e riproducono automaticamente la rappresentazione più appropriata di una risorsa in base a queste regole, consentendo ai clienti di concentrarsi solo sulla progettazione della *principale* esperienza.

## Obiettivo {#objective}

In qualità di autore di contenuti AEM Screens, ora puoi configurare i rendering di risorse specifiche per il dispositivo in modo che vengano scaricati e riprodotti automaticamente senza dover creare manualmente tutte le varianti di contenuto.
Dopo che uno sviluppatore ha aggiunto le proprietà e le regole di mappatura della rappresentazione, puoi applicare la mappatura alle risorse e quindi includerle in un canale AEM Screens.

>[!IMPORTANT]
>Prima di iniziare a utilizzare le rappresentazioni adattive in un canale AEM Screens, l’Adobe consiglia di conoscere la panoramica e la configurazione dell’architettura di questa funzione. Consulta [Rappresentazioni adattive: panoramica dell’architettura e configurazioni](/help/user-guide/adaptive-renditions.md).

## Utilizzo di rappresentazioni adattive nei canali {#using-adaptive-renditions}

>[!NOTE]
>Dopo aver aggiunto [proprietà di mappatura rappresentazione per il progetto Schermi](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) e [regole di mappatura rappresentazione](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)In qualità di autore di contenuti, ora puoi applicare le rappresentazioni alle risorse.

### Applicazione delle rappresentazioni alle risorse {#apply-renditions-assets}

Per applicare le rappresentazioni alle risorse da utilizzare nel canale Schermi presentazione, effettua le seguenti operazioni.

1. Accedi a **Risorse** nell’istanza AEM.
1. Crea una versione della risorsa che si adatti meglio alla visualizzazione del signage, ad esempio: `seahorse.jpg`.
1. Scegli il pattern di denominazione della rappresentazione, ad esempio:`landscape`, simile a quanto definito in **pattern** proprietà in **CRXDE Liti**. Consulta [Aggiunta di regole di mappatura rappresentazione](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) per ulteriori dettagli.
1. Clic **Aggiungi rappresentazione** per caricare la rappresentazione, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Fai clic sul file della risorsa rinominato. La rappresentazione che state aggiungendo deve contenere il pattern (definito nel passaggio 3), ad esempio: `seahorse-landscape.png`.
1. Dopo aver aggiunto la risorsa, fai clic sulla risorsa e fai clic su **Gestisci pubblicazione** dalla barra delle azioni per pubblicare la risorsa.

   ![immagine](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Consulta [Aggiornamento dei contenuti on-demand](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content) per ulteriori informazioni sulla gestione delle pubblicazioni e sulla distribuzione degli aggiornamenti dei contenuti da Author a Publish sul dispositivo.

## Strategia di migrazione {#migration-strategy}

>[!IMPORTANT]
>Per le reti di grandi dimensioni, l&#39;Adobe raccomanda che la migrazione sia effettuata gradualmente per mitigare i rischi. Il motivo è che la funzione può introdurre modifiche nel formato di archiviazione del manifesto e dei file. Aggiunta di `sling:configRef` per l’intero progetto, tutti i lettori devono essere aggiornati a Feature Pack 6.5.9. Se hai aggiornato alcuni lettori, aggiungi `sling:configRef` solo per gli schermi, le posizioni o le cartelle di canali con tutti i lettori aggiornati a Feature Pack 6.5.9.

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
