---
title: Note sulla versione per Feature Pack 202105
description: '"Segui questa pagina per ottenere informazioni su AEM Screens Feature Pack 202105 rilasciato il 4 giugno 2021."'
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: 444535b38fdf112939fdbf4c0f3f48e1cc28c902
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 10%

---

# Note sulla versione per Feature Pack 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). Screens supporta la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 8.

Scarica l&#39;ultimo pacchetto di funzioni per AEM Screens 6.5.8 dal [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) utilizzando il tuo Adobe ID. Passa alla scheda **Adobe Experience Manager** e cerca **Screens** per ottenere l&#39;ultimo pacchetto di funzioni intitolato **AEM 6.5 Screens FP8**.

## Data di rilascio {#release-date}

La data di rilascio per AEM Screens Feature Pack 202105 è il 4 giugno 2021.

### Novità {#what-is-new}

* **Blocco di una pagina in un canale AEM Screens**

   AEM Screens supporta ora il *blocco di una pagina*, come già implementato in AEM Sites. Adobe Experience Manager (AEM) consente di bloccare una pagina in modo che nessun altro possa modificarne il contenuto. Questa funzione è utile quando si devono apportare numerose modifiche a una pagina oppure se occorre bloccarla per un breve periodo di tempo.

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

#### Download di AEM Screens Player {#aem-screens-player-downloads}

Per scaricare l&#39;ultimo lettore AEM Screens e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
