---
title: Configurazioni del dispatcher per  AEM Screens
seo-title: Configurazioni del dispatcher per  AEM Screens
description: In questa pagina sono illustrate le linee guida per la configurazione del dispatcher per un progetto AEM Screens .
seo-description: In questa pagina sono illustrate le linee guida per la configurazione del dispatcher per un progetto AEM Screens .
translation-type: tm+mt
source-git-commit: 4a1fb81fa343983093590c36ccb6a4fd110cdad2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 9%

---


# Configurazioni del dispatcher per  AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager.

La pagina seguente illustra le linee guida per la configurazione del dispatcher per un progetto AEM Screens .

>[!NOTE]
>
>Se è disponibile un dispatcher, è possibile impedire le connessioni al servlet di registrazione filtrando le regole del dispatcher.
>
>Se non è presente alcun dispatcher, disattivate il servlet di registrazione nell’elenco dei componenti OSGi.

## Prerequisiti {#pre-requisites}

Prima di configurare il dispatcher per un progetto AEM Screens , è necessario disporre di conoscenze preliminari sul dispatcher.

Per ulteriori informazioni, vedere [Configurazione del dispatcher](https://docs.adobe.com/content/help/it-IT/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html).

## Configurazione di Dispatcher {#configuring-dispatcher}

Per configurare il dispatcher per un progetto AEM Screens , procedi come indicato di seguito.

### Abilitazione delle sessioni permanenti {#enable-sticky-session}

Se si desidera utilizzare più di un&#39;istanza di pubblicazione con il dispatcher, sarà necessario aggiornare il file `dispatcher.any`.

```xml
/stickyConnections {
  /paths
  {
    "/content/screens"
    "/home/users/screens"
    "/libs/granite/csrf/token.json"
  }
}
```

### Passaggio 1: Configurazione delle intestazioni client {#step-configuring-client-headers}

Aggiungere quanto segue alla sezione `/clientheaders`:

**X-Richiesto-Con**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Passaggio 2: Configurazione dei filtri per schermate {#step-configuring-screens-filters}

Per configurare i filtri Screens, aggiungi quanto segue a ***/filter***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Passaggio 3: Disattivazione della cache del dispatcher {#step-disabling-dispatcher-cache}

Disabilitare il caching del dispatcher per ***/content/screens path***.

I lettori dello schermo utilizzano una sessione autenticata, pertanto il dispatcher non memorizza nella cache nessuna delle richieste dei lettori dello schermo per `channels/assets`.

Per abilitare la cache per le risorse in modo che le risorse vengano servite dalla cache del dispatcher, dovete:

* Aggiungi `/allowAuthorization 1` nella sezione `/cache`
* Aggiungere le regole seguenti alla sezione `/rules` di `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
