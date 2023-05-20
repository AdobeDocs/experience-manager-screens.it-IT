---
title: Note sulla versione per Feature Pack 202103
description: "Segui questa pagina per ottenere informazioni sul Feature Pack di AEM Screens 202103 rilasciato il 5 marzo 2021."
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Note sulla versione per Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). Screens fornisce supporto per la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 7.

Puoi scaricare il feature pack più recente per AEM Screens versione 6.5.7 da [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID. Accedi a **Adobe Experience Manager** e cerca **Schermi** per ottenere l’ultimo feature pack con titolo **AEM 6.5 Screens FP7**.

## Data di pubblicazione {#release-date}

La data di rilascio del Feature Pack 202103 per AEM Screens è il 5 marzo 2021.

### Novità {#what-is-new}

* **Registrazione automatica dei lettori in AEM Screens**

   Registrare manualmente migliaia di giocatori in massa è molto complicato e aggiunge tempo e costi. Per semplificare questo processo, la funzione di Registrazione automatica dei lettori consente di specificare una chiave pre-condivisa in AEM che può essere fornita in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

   Fai riferimento a [Registrazione automatica dei lettori](/help/user-guide/auto-registration-players.md) per ulteriori dettagli.


* **Provisioning in blocco di Android Player tramite Enterprise Mobility Management**

   Quando si distribuisce il lettore Android in massa, diventa noioso registrare manualmente ogni singolo lettore con AEM. Si consiglia vivamente di utilizzare una soluzione EMM (Enterprise Mobility Management) come VMWare Airwatch, MobileIron o Samsung Knox per effettuare il provisioning e gestire l&#39;installazione in remoto. AEM Screens Android Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.

   Fai riferimento a [Provisioning in blocco di Android Player tramite Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) per ulteriori dettagli.


### Correzioni di bug {#bug-fixes}

* Prestazioni migliorate per l&#39;elaborazione `clientlib` e `asset hashes`.

* La migrazione di SmartSync interromperebbe il lettore se la cache non venisse invalidata.

* Le cache non in linea non sono state create se l&#39;assegnazione aveva *OfflineConfig*.

* Aggiornamenti al lettore Tizen interrotti perché il criterio del referente strict-origin-when-cross-origin non è supportato.

* Modifica della pianificazione del canale assegnato *Si ripete* il campo stava interrompendo l’interfaccia utente.

* L’aggiornamento del contenuto offline non riusciva con eccezioni di query.

* L’intervallo di tempo tra le transizioni durante l’interazione nell’esperienza interattiva è ora fisso.

* La richiesta di aggiornamento della configurazione non è riuscita causava la visualizzazione di una schermata vuota.

### Lettori AEM Screens rilasciati {#released-aem-screens-players}

Sono stati rilasciati i seguenti lettori AEM Screens per AEM 6.5 Feature Pack 7:

* Chrome OS
* Windows
* Linux

#### Download di AEM Screens Player  {#aem-screens-player-downloads}

Per scaricare il lettore AEM Screens più recente e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
