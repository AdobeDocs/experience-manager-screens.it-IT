---
title: Note sulla versione per Feature Pack 202105
description: Scopri AEM Screens Feature Pack 202105, rilasciato il 4 giugno 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 3%

---

# Note sulla versione per Feature Pack 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>L’Adobe consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). AEM Screens fornisce supporto per la manutenzione della piattaforma Screens AEM 6.3.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 8.

Puoi scaricare il Feature Pack più recente per AEM Screens versione 6.5.8 dal [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) tramite il tuo Adobe ID. Passa alla scheda **Adobe Experience Manager** e cerca **Screens** per ottenere il Feature Pack più recente con titolo **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>Installare la versione minima di AEM 6.5 Feature Pack 8 per il funzionamento del connettore AMS dopo aver installato i pacchetti `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` e `screens core bundles`.

## Data di rilascio {#release-date}

La data di rilascio del Feature Pack 202105 per AEM Screens è il 4 giugno 2021.

### Novità {#what-is-new}

* **Blocco della pagina in un canale AEM Screens**

  AEM Screens ora supporta *Il blocco di una pagina*, come già implementato in AEM Sites. Adobe Experience Manager (AEM) consente di bloccare una pagina in modo che nessun altro possa modificarne il contenuto. Questa funzione è utile quando si apportano numerose modifiche a una pagina specifica o quando è necessario bloccare una pagina per un breve periodo.

* **Denominazione dispositivo lettore AEM Screens**

  I lettori AEM Screens ora includono la funzionalità di invio di un nome di dispositivo a Adobe Experience Manager (AEM).
Per impostazione predefinita, quando si utilizza la registrazione in blocco per registrare un dispositivo, nel campo del titolo viene inserito un nome utente generato dal sistema. In alternativa, un cliente può utilizzare un tag risorsa o un altro nome descrittivo che lo renda visibile nell’AEM e faciliti l’assegnazione di contenuti appropriati.

  Per informazioni su come configurare il nome in ciascun sistema operativo supportato, consultare la seguente documentazione:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [CHROME OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generazione manifesto**

  Generazione più rapida di manifesti di canale con prestazioni migliorate, ad esempio l&#39;allocazione di meno risorse sul server.

### Correzioni di bug {#bug-fixes}

* Il lettore visualizzava una schermata nera quando si passava a un canale contenente una sequenza dinamica incorporata.
* I lettori Screens ora bloccano il passaggio a qualsiasi canale interrotto che evita ulteriormente un errore 404 o una pagina con un messaggio di errore.

### Lettori AEM Screens rilasciati

Sono stati rilasciati i seguenti lettori AEM Screens per AEM 6.5 Feature Pack 8:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Download di AEM Screens Player

Per scaricare il lettore AEM Screens più recente e ulteriori informazioni sulle correzioni di bug, vedi **[Download del lettore AEM Screens](https://download.macromedia.com/screens/index.html)**.
