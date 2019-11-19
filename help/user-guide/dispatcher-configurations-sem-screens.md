---
title: Configurazioni del dispatcher per AEM Screens
seo-title: Configurazioni del dispatcher per AEM Screens
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: ea68ca72-bbe7-42d5-9043-97aea7edcd6e
contentOwner: jsyal
discoiquuid: 046ec5ae-600d-422f-aa59-c39f16cf71de
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configurazioni del dispatcher per AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager.

La pagina seguente contiene le linee guida per la configurazione del dispatcher per un progetto AEM Screens.

## Prerequisiti {#pre-requisites}

Prima di configurare il dispatcher per un progetto AEM Screens, è necessario disporre di conoscenze preliminari sul dispatcher.

Per ulteriori informazioni, consultate **[Configurazione del dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)** .

## Configurazione di Dispatcher {#configuring-dispatcher}

Segui i passaggi indicati di seguito per configurare il dispatcher per un progetto AEM Screens.

### Passaggio 1: Configurazione delle intestazioni client {#step-configuring-client-headers}

Aggiungi quanto segue alla `/clientheaders` sezione

**X-Richiesto-Con**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Passaggio 2: Configurazione dei filtri per le schermate {#step-configuring-screens-filters}

Per configurare i filtri Schermi, aggiungi quanto segue a ***/filtro***.

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

Disattiva il caching del dispatcher per il percorso ***/content/screens***.
