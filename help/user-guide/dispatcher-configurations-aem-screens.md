---
title: Configurazioni del Dispatcher per AEM Screens
seo-title: Configurazioni del Dispatcher per AEM Screens
description: Questa pagina illustra le linee guida per la configurazione del dispatcher per un progetto AEM Screens.
seo-description: Questa pagina illustra le linee guida per la configurazione del dispatcher per un progetto AEM Screens.
feature: Amministrazione di schermi
role: Developer, Business Practitioner
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 6%

---


# Configurazioni del Dispatcher per AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager.

La pagina seguente fornisce le linee guida per la configurazione del dispatcher per un progetto AEM Screens.

>[!NOTE]
>
>Se un dispatcher è disponibile, è possibile impedire le connessioni al servlet di registrazione filtrando nelle regole del dispatcher.
>
>Se non è presente alcun dispatcher, disattiva il servlet di registrazione nell’elenco dei componenti OSGi.

## Prerequisiti {#pre-requisites}

Prima di configurare il dispatcher per un progetto AEM Screens, è necessario disporre di conoscenze precedenti su Dispatcher.

Per ulteriori informazioni, consulta [Configurazione di Dispatcher](https://docs.adobe.com/content/help/it-IT/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) .

## Configurazione di Dispatcher {#configuring-dispatcher}

I lettori/dispositivi AEM Screens utilizzano una sessione autenticata per accedere alle risorse anche nelle istanze di pubblicazione. Quindi, quando disponi di più istanze di pubblicazione, le richieste devono sempre andare alla stessa istanza di pubblicazione in modo che la sessione autenticata sia valida per tutte le richieste provenienti dai lettori/dispositivi AEM Screens.

Segui i passaggi riportati di seguito per configurare il dispatcher per un progetto AEM Screens.

### Abilitazione di sessioni permanenti {#enable-sticky-session}

Se desideri utilizzare più istanze di pubblicazione fronte a un singolo dispatcher, devi aggiornare il file `dispatcher.any` per abilitare la persistenza

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Se disponi di un’istanza di pubblicazione fronte a un dispatcher, l’abilitazione della persistenza al dispatcher non sarà di aiuto in quanto il load balancer può inviare ogni richiesta al dispatcher. In questo caso, fai clic su **Abilita** nel campo **Atteggiamento** per attivarlo a livello di load balancer, come illustrato nella figura seguente:

![immagine](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Ad esempio, se utilizzi AWS ALB, fai riferimento a [Gruppi di destinazione per i bilanciatori di carico dell&#39;applicazione](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) per abilitare la persistenza a livello ALB. Abilita l&#39;adesività per 1 giorno.

### Passaggio 1: Configurazione delle intestazioni client {#step-configuring-client-headers}

Aggiungi quanto segue alla sezione `/clientheaders`:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Passaggio 2: Configurazione dei filtri Screens {#step-configuring-screens-filters}

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

### Passaggio 3: Disabilitazione della cache del dispatcher {#step-disabling-dispatcher-cache}

Disattiva la memorizzazione in cache del dispatcher per ***/content/screens path***.

I lettori Screens utilizzano una sessione autenticata, pertanto il dispatcher non memorizza nella cache alcuna delle richieste dei lettori dello schermo per `channels/assets`.

Per abilitare la cache per le risorse in modo che le risorse vengano servite dalla cache del dispatcher, devi:

* Aggiungi `/allowAuthorization 1` nella sezione `/cache`
* Aggiungi le regole seguenti alla sezione `/rules` di `/cache`

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
