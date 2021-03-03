---
title: Note sulla versione per Feature Pack 202103
description: Nella pagina sono elencate le note sulla versione per Feature Pack 202103.
translation-type: tm+mt
source-git-commit: 34f93df3fa212eaae713b0c8686d95beeb0c7b67
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 2%

---


# Note sulla versione per Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). Screens supporta la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 7.

Scarica l&#39;ultimo pacchetto di funzioni per la versione 6.5.7 di AEM Screens dal [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) utilizzando il tuo Adobe ID. Passa alla scheda **Adobe Experience Manager** e cerca **Screens** per ottenere l&#39;ultimo pacchetto di funzioni intitolato **AEM 6.5 Screens FP7**.

## Data di rilascio {#release-date}

La data di rilascio per AEM Screens Feature Pack 202103 è il 8 marzo 2021.

### Novità {#what-is-new}

* **Registrazione e assegnazione in blocco di AEM Screens**

   La registrazione collettiva di migliaia di giocatori manualmente è molto ingombrante e aggiunge tempo e costi. Per semplificare questo processo, la funzione di registrazione in blocco ti consente di specificare una chiave pre-condivisa in AEM che può essere fornita in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

* **Provisioning in blocco di Android Player tramite Enterprise Mobility Management**

   Quando si distribuisce il lettore Android in blocco, diventa noioso registrare manualmente ogni singolo lettore con AEM. Si consiglia vivamente di utilizzare una soluzione EMM (Enterprise Mobility Management) come VMWare Airwatch, MobileIron o Samsung Knox per il provisioning e la gestione remota dell&#39;implementazione. AEM Screens Android Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.


### Correzioni di bug {#bug-fixes}

* Prestazioni migliorate per i computer `clientlib` e `asset hashes`.

* La migrazione di SmartSync interromperebbe il lettore se la cache non veniva invalidata.

* Le cache offline non sono state create se l&#39;oggetto Assignment aveva *OfflineConfig*.

* Sono stati aggiornati i problemi relativi al Tizen Player perché il criterio di riferimento &quot;rigorosamente&quot;-origin-when-cross-origin non è supportato.

* La modifica del campo &quot;Ripeti&quot; della pianificazione del canale assegnato causava l’interruzione dell’interfaccia utente.

* Errore durante l&#39;aggiornamento del contenuto offline con eccezioni di query.

* La migrazione di SmartSync ha interrotto il lettore, se la cache non è stata invalidata


### Lettori AEM Screens rilasciati {#released-aem-screens-players}

I seguenti lettori AEM Screens sono rilasciati per AEM 6.5 Feature Pack 7:

* Sistema operativo Chrome
* Windows
* Android
* Tizen
* Linux

#### Download di lettori AEM Screens {#aem-screens-player-downloads}

Per scaricare l&#39;ultimo lettore AEM Screens e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
