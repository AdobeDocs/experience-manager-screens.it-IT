---
title: Note sulla versione per Screens Feature Pack 202401
description: Scopri AEM Screens Feature Pack 202401 rilasciato il 2 gennaio 2024.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: fe4f7d593ccea91f6109a0c759aea3faa37ae471
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 4%

---

# Note sulla versione per Feature Pack 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>L’Adobe consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager 6.5 (AEM 6.5). Ottieni informazioni sulla versione più recente da [qui](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/release-notes/release-notes).

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 11.1.

Puoi scaricare l’ultimo Feature Pack per AEM Screens versione 6.5.11.1 da [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID. Accedi a **Adobe Experience Manager** e cerca **Schermi** per ottenere l’ultimo Feature Pack con titolo **Schermi AEM 6.5 FP11.1**.

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
