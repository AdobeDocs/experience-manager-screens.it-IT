---
title: Note sulla versione per Screens Feature Pack 202401
description: Segui questa pagina per ottenere informazioni sull’AEM Screens Feature Pack 202401 rilasciato il 2 gennaio 2024.
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: e172d2a4a3d2c1f3b555edc8f8ea41b663fc0a30
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---

# Note sulla versione per Feature Pack 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager 6.5 (AEM 6.5). Possiamo ottenere le informazioni più recenti sulla versione da [qui](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=en)

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 11.1.

Puoi scaricare il feature pack più recente per AEM Screens 6.5.11.1 dalla versione [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID. Accedi a **Adobe Experience Manager** e cerca **Schermi** per ottenere l’ultimo feature pack con titolo **Schermi AEM 6.5 FP11.1**.

## Data di rilascio {#release-date}

La data di rilascio del Feature Pack 202204 per AEM Screens è il 2 gennaio 2024.

### Novità {#what-is-new}

Questa versione include solo correzioni di sicurezza.

### Correzioni di bug {#bug-fixes}

* Problema XSS nel campo &quot;Testo inattivo&quot; del dispositivo AEM Screens. (SCRNS-2614)

* Problema XSS in `screens/dashboard/device.html` tramite `Clear cache` finestra di dialogo azione. (SCRNS-2632)

* Problema XSS nella configurazione del lettore Screens in `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Il file XSS memorizzato nei titoli dei dispositivi si attiva quando un dispositivo viene eliminato. (SCRNS-2653)

* Problema XSS in `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS riflesso con il parametro `item` a `/screens/register-device-wizard.html`. (SCRNS-2670)

* XSS riflesso in `screens/dashboard/device.html` tramite `returnPage` parametro. (SCRNS-3056)

* Apri Reindirizza su assign-device-wizard.html. (SCRNS-3444)

* Apri Reindirizza nel dashboard del dispositivo. (SCRNS-3443)

* Problema XSS in `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Pulsanti Pianificazione ricorrenza e Aggiungi pianificazione corretti e mancanti: problema rilevato nella programmazione dei canali. (SCRNS-2739)

#### Download di AEM Screens Player  {#aem-screens-player-downloads}

Per scaricare l’ultimo lettore AEM Screens, fai riferimento a **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
