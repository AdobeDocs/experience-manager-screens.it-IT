---
title: Note sulla versione per Feature Pack 202103
description: Ulteriori informazioni sul Feature Pack di AEM Screens 202103 rilasciato il 5 marzo 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
TQID: https://experienceleague.adobe.com/x7dgY8u-SdWo2JRK1W2uqRWtHy2wtXdAnIcS0gRoxiY
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 407
ht-degree: 4%

---

# Note sulla versione per Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). AEM Screens fornisce supporto per la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 7.

Puoi scaricare il Feature Pack più recente per AEM Screens versione 6.5.7 dal [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) tramite il tuo Adobe ID. Passa alla scheda **Adobe Experience Manager** e cerca **Screens** per ottenere l&#39;ultimo Feature Pack con titolo **AEM 6.5 Screens FP7**.

## Data di pubblicazione {#release-date}

La data di rilascio del Feature Pack 202103 per AEM Screens è il 5 marzo 2021.

### Novità {#what-is-new}

* **Registrazione automatica dei lettori in AEM Screens**

  La registrazione manuale in blocco di migliaia di giocatori è complicata e aggiunge tempo e costi. Per semplificare questo processo, la funzione di Registrazione automatica dei lettori consente di specificare una chiave già condivisa in AEM. È possibile eseguire il provisioning di questa chiave in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

  Per ulteriori dettagli, vedere [Registrazione automatica dei lettori](/help/user-guide/auto-registration-players.md).


* **Provisioning in blocco di Android™ Player tramite Enterprise Mobility Management**

  Quando si distribuisce in massa il lettore Android™, diventa noioso registrare ogni lettore manualmente con AEM. Si consiglia vivamente di utilizzare una soluzione EMM (Enterprise Mobility Management) come `VMWare Airwatch`, `MobileIron` o `Samsung Knox` per eseguire il provisioning e gestire la distribuzione in remoto. AEM Screens Android™ Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.

  Per ulteriori informazioni, vedere [Provisioning in blocco di Android™ Player tramite Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation).


### Correzioni di bug {#bug-fixes}

* Prestazioni migliorate per il calcolo di `clientlib` e `asset hashes`.

* La migrazione di SmartSync interromperebbe il lettore se la cache non venisse invalidata.

* Le cache offline non sono state create se l&#39;assegnazione aveva *OfflineConfig*.

* Aggiornamenti al lettore `Tizen` non riusciti perché il criterio del referente strict-origin-when-cross-origin non è supportato.

* La modifica del campo *Repeats* della pianificazione del canale assegnato interrompeva l&#39;interfaccia utente.

* L’aggiornamento del contenuto offline non riusciva con eccezioni di query.

* L’intervallo di tempo tra le transizioni durante l’interazione in un’esperienza interattiva è ora fisso.

* Una richiesta di aggiornamento della configurazione non riuscita ha causato la visualizzazione di schermate vuote.

### Lettori AEM Screens rilasciati

Sono stati rilasciati i seguenti lettori AEM Screens per AEM 6.5 Feature Pack 7:

* CHROME OS
* Windows
* Linux®

#### Download di AEM Screens Player

Per scaricare il lettore AEM Screens più recente e ulteriori informazioni sulle correzioni di bug, vedi **[Download del lettore AEM Screens](https://download.macromedia.com/screens/index.html)**.
