---
title: Note sulla versione per Feature Pack 202103
description: Ulteriori informazioni sul Feature Pack di AEM Screens 202103 rilasciato il 5 marzo 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---

# Note sulla versione per Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>L’Adobe consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). AEM Screens fornisce supporto per la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 7.

Puoi scaricare l’ultimo Feature Pack per AEM Screens versione 6.5.7 da [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID. Accedi a **Adobe Experience Manager** e cerca **Schermi** per ottenere l’ultimo Feature Pack con titolo **AEM 6.5 Screens FP7**.

## Data di rilascio {#release-date}

La data di rilascio del Feature Pack 202103 per AEM Screens è il 5 marzo 2021.

### Novità {#what-is-new}

* **Registrazione automatica dei lettori in AEM Screens**

  La registrazione manuale in blocco di migliaia di giocatori è complicata e aggiunge tempo e costi. Per semplificare questo processo, la funzione di Registrazione automatica dei lettori consente di specificare una chiave già condivisa in AEM. È possibile eseguire il provisioning di questa chiave in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

  Consulta [Registrazione automatica dei lettori](/help/user-guide/auto-registration-players.md) per ulteriori dettagli.


* **Provisioning in blocco di Android™ Player tramite Enterprise Mobility Management**

  Quando si distribuisce il lettore Android™ in massa, diventa noioso registrare ogni lettore manualmente con l&#39;AEM. Si consiglia vivamente di utilizzare una soluzione EMM (Enterprise Mobility Management) come `VMWare Airwatch`, `MobileIron`, o `Samsung Knox` per il provisioning e la gestione dell&#39;installazione in remoto. AEM Screens Android™ Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.

  Consulta [Provisioning in blocco di Android™ Player tramite Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) per ulteriori dettagli.


### Correzioni di bug {#bug-fixes}

* Prestazioni migliorate per l&#39;elaborazione `clientlib` e `asset hashes`.

* La migrazione di SmartSync interromperebbe il lettore se la cache non venisse invalidata.

* Le cache non in linea non sono state create se l&#39;assegnazione aveva *OfflineConfig*.

* Aggiornamenti a `Tizen` lettore che si è rotto perché il criterio referente strict-origin-when-cross-origin non è supportato.

* Modifica della pianificazione del canale assegnato *Si ripete* il campo stava interrompendo l’interfaccia utente.

* L’aggiornamento del contenuto offline non riusciva con eccezioni di query.

* L’intervallo di tempo tra le transizioni durante l’interazione in un’esperienza interattiva è ora fisso.

* Una richiesta di aggiornamento della configurazione non riuscita ha causato la visualizzazione di schermate vuote.

### Lettori AEM Screens rilasciati

Sono stati rilasciati i seguenti lettori AEM Screens per AEM 6.5 Feature Pack 7:

* Chrome OS
* Windows
* Linux®

#### Download di AEM Screens Player

Per scaricare il lettore AEM Screens più recente e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
