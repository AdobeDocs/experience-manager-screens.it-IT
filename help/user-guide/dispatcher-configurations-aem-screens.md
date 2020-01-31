---
title: Configurazioni del dispatcher per AEM Screens
seo-title: Configurazioni del dispatcher per AEM Screens
description: Questa pagina illustra le linee guida per la configurazione del dispatcher per un progetto AEM Screens.
seo-description: Questa pagina illustra le linee guida per la configurazione del dispatcher per un progetto AEM Screens.
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: 9bee12b69ae85e84572b6f9e8c70f792895d9a32

---


# Configurazioni del dispatcher per AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager.

La pagina seguente contiene le linee guida per la configurazione del dispatcher per un progetto AEM Screens.

>[!NOTE]
>Se è disponibile un dispatcher, è possibile impedire le connessioni al servlet di registrazione filtrando le regole del dispatcher.
>In assenza di dispatcher, disattivate il servlet di registrazione nell’elenco dei componenti OSGi.

## Prerequisiti {#pre-requisites}

Prima di configurare il dispatcher per un progetto AEM Screens, è necessario disporre di conoscenze preliminari sul dispatcher.

Per ulteriori informazioni, consultate [Configurazione del dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) .

## Configurazione di Dispatcher {#configuring-dispatcher}

Segui i passaggi indicati di seguito per configurare il dispatcher per un progetto AEM Screens.

### Passaggio 1: Configurazione delle intestazioni client {#step-configuring-client-headers}

Aggiungi quanto segue alla `/clientheaders`sezione:

**X-Richiesto-Con**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Passaggio 2: Configurazione dei filtri per le schermate {#step-configuring-screens-filters}

Per configurare i filtri Schermi, aggiungi quanto segue a ***/filtro ***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Passaggio 3: Disattivazione della cache del dispatcher {#step-disabling-dispatcher-cache}

Disattiva il caching del dispatcher per il percorso ***/content/screens ***.
