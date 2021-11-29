---
title: Note sulla versione per Feature Pack 202105
description: '"Segui questa pagina per ottenere informazioni su AEM Screens Feature Pack 202105 rilasciato il 4 giugno 2021."'
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 02bc399d61f5666918caad9fce3d69d63f0782d7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 11%

---

# Note sulla versione per Feature Pack 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). Screens supporta la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 8.

Puoi scaricare l’ultimo pacchetto di funzioni per AEM Screens 6.5.8 dalla versione [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID. Passa a **Adobe Experience Manager** tabulazione e ricerca **Schermi** per ottenere il pacchetto di funzioni più recente denominato **FP8 di AEM 6.5 Screens**.

>[!IMPORTANT]
>È necessario installare una versione minima di AEM 6.5 Feature Pack 8 per il funzionamento del connettore AMS dopo aver installato i pacchetti `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` e `screens core bundles`.

## Data di pubblicazione {#release-date}

La data di rilascio per AEM Screens Feature Pack 202105 è il 4 giugno 2021.

### Novità {#what-is-new}

* **Blocco di una pagina in un canale AEM Screens**

   AEM Screens ora supporta *Blocco di una pagina*, come già implementato in AEM Sites. Adobe Experience Manager (AEM) consente di bloccare una pagina in modo che nessun altro possa modificarne il contenuto. Questa funzione è utile quando si devono apportare numerose modifiche a una pagina oppure se occorre bloccarla per un breve periodo di tempo.

* **Denominazione del dispositivo AEM Screens Player**

   I lettori AEM Screens ora includono la possibilità di inviare un nome di dispositivo ad Adobe Experience Manager (AEM).
Per impostazione predefinita, quando la registrazione in serie viene utilizzata per registrare un dispositivo, nel campo title viene inserito un nome utente generato dal sistema. In alternativa, un cliente può utilizzare un tag risorsa o un altro nome descrittivo in modo che sia visibile in AEM e facile da assegnare il contenuto appropriato.

   Per informazioni su come configurare il nome in ciascun sistema operativo supportato, consulta la seguente documentazione:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Sistema operativo Chrome](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Generazione manifesto**

   Generazione più rapida del manifesto del canale con prestazioni migliori, ad esempio l&#39;allocazione di meno risorse sul server.

### Correzioni di bug {#bug-fixes}

* Il lettore visualizzava uno schermo nero quando si passa al canale contenente una sequenza incorporata dinamica.
* I lettori Screens ora bloccano il passaggio a qualsiasi canale interrotto che evita ulteriormente l&#39;errore 404 o una pagina con un messaggio di errore.

### Lettori AEM Screens rilasciati {#released-aem-screens-players}

I seguenti lettori AEM Screens vengono rilasciati per AEM 6.5 Feature Pack 8:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Download di AEM Screens Player  {#aem-screens-player-downloads}

Per scaricare l&#39;ultimo lettore AEM Screens e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
