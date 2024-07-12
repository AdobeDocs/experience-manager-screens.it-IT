---
title: Configurazioni Dispatcher per AEM Screens
description: In questa pagina sono illustrate le linee guida per la configurazione di un Dispatcher per un progetto AEM Screens.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Configurazioni Dispatcher per AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher è lo strumento di caching o di bilanciamento del carico di Adobe Experience Manager o entrambi.

La pagina seguente fornisce le linee guida per la configurazione di un Dispatcher per un progetto AEM Screens.

>[!NOTE]
>
>Se è disponibile un Dispatcher, è possibile impedire le connessioni al servlet di registrazione filtrando nelle regole di Dispatcher.
>
>Se non è presente alcun Dispatcher, disattiva il servlet di registrazione nell’elenco dei componenti OSGi.

Prima di configurare Dispatcher per un progetto AEM Screens, è necessario avere una conoscenza di Dispatcher.
Per ulteriori dettagli, vedere [Configurazione di Dispatcher](https://experienceleague.adobe.com/it/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration).

## Configurazione di Dispatcher per la versione del manifesto v2 {#configuring-dispatcher}

>[!IMPORTANT]
>Le seguenti configurazioni di Dispatcher si applicano solo alla versione v2 di Manifest. Consulta [Configurazioni Dispatcher per Manifest versione v3](#configuring-dispatcherv3) per Manifest versione v3.

I lettori o i dispositivi AEM Screens utilizzano una sessione autenticata per accedere anche alle risorse nelle istanze Publishing. Quando disponi di più istanze di pubblicazione, le richieste devono sempre andare alla stessa istanza di pubblicazione in modo che la sessione autenticata sia valida per tutte le richieste provenienti dai lettori o dai dispositivi AEM Screens.

Segui i passaggi seguenti per configurare Dispatcher per un progetto AEM Screens.

### Abilitazione di sessioni permanenti {#enable-sticky-session}

Se desideri utilizzare più istanze di pubblicazione gestite da un singolo Dispatcher, aggiorna il file `dispatcher.any` per abilitare la coerenza.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Se disponi di un’istanza Publish gestita da un Dispatcher, l’abilitazione della coerenza in Dispatcher non aiuta, perché il load balancer può inviare ogni richiesta a Dispatcher. In questo caso, fai clic su **Abilita** nel campo **Permanenza** per attivarlo a livello di load balancer, come illustrato nella figura seguente:

![immagine](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Ad esempio, se utilizzi AWS ALB, consulta [Gruppi di destinazione per i load balancer dell&#39;applicazione](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) per abilitare la fedeltà a livello ALB. Abilita la fedeltà per un giorno.

### Passaggio 1: configurazione delle intestazioni client {#step-configuring-client-headers}

Aggiungi quanto segue alla sezione `/clientheaders`:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Passaggio 2: configurazione dei filtri di Screens {#step-configure-screens-filters}

Per configurare i filtri di Screens, aggiungi quanto segue a ***`/filter`***.

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

### Passaggio 3: disabilitazione della cache di Dispatcher {#step-disabling-dispatcher-cache}

Disabilita il caching di Dispatcher per il percorso ***/content/screens***.

I lettori Screens utilizzano sessioni autenticate, pertanto Dispatcher non memorizza in cache nessuna delle richieste dei lettori Screens per `channels/assets`.

Per abilitare la cache per le risorse in modo che vengano servite dalla cache di Dispatcher, effettua le seguenti operazioni:

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

## Configurazione di Dispatcher per la versione del manifesto v3{#configuring-dispatcherv3}

Assicurati di consentire questi filtri e regole di cache nei dispatcher che presentano le istanze Publishing per il funzionamento di Screens.

### Prerequisiti per la versione del manifesto v3{#prerequisites3}

Prima di configurare un Dispatcher (versione manifesto v3) per AEM Screens, segui questi due prerequisiti:

* Assicurarsi di utilizzare `v3 manifests`. Passare a `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` e assicurarsi che `Enable ContentSync Cache` sia deselezionato.

* Verificare che l&#39;agente di svuotamento del Dispatcher sia configurato in `/etc/replication/agents.publish/dispatcher1useast1Agent` nell&#39;istanza di pubblicazione.

  ![immagine](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![immagine](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filtri {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### Regole cache {#cache-rules-v3}

* Aggiungi `/allowAuthorized "1"` alla sezione `/cache` in `publish_farm.any`.

* Tutti i lettori AEM Screens utilizzano una sessione autenticata per connettersi all’AEM (authoring/pubblicazione). Poiché un Dispatcher non memorizza in cache questi URL, devi abilitarli.

* Aggiungi `statfileslevel "10"` a `/cache` sezione in `publish_farm.any`
Questa regola supporta la memorizzazione in cache fino a dieci livelli dalla directory principale dei documenti della cache e di conseguenza l’annullamento della validità quando il contenuto viene pubblicato, anziché annullare la validità di tutto. Puoi modificare questo livello in base alla profondità della struttura del contenuto

* Aggiungi quanto segue a `/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* Aggiungere le regole seguenti alla sezione `/rules` in `/cache` in `publish_farm.any` o in un file incluso da `publish_farm.any`:

  ```
  ## Don't cache CSRF login tokens
  /0001
      {
      /glob "/libs/granite/csrf/token.json"
      /type "deny"
      }
  ## Allow Dispatcher Cache for Screens channels
  /0002
      {
          /glob "/content/screens/*.html"
          /type "allow"
      }
  ## Allow Dispatcher Cache for Screens offline manifests
  /0003
      {
      /glob "/content/screens/*.manifest.json"
      /type "allow"
      }
  ## Allow Dispatcher Cache for Assets
  /0004
      {
  
      /glob "/content/dam/*"
      /type "allow"
      }
  ## Disable Dispatcher Cache for Screens devices json
  /0005
      {
      /glob "/home/users/screens/*.json"
      /type "deny"
      }
  ## Disable Dispatcher Cache for Screens svc json
  /0006
      {
      /glob "/content/screens/svc.json"
      /type "deny"
      }
  ```

### Aggiungi regola di invalidazione per segment.js {#invalidsegmentjs}

Se utilizzi campagne mirate con AEM Screens, le `segments.js file` servite da Dispatcher devono essere invalidate, poiché aggiungi e pubblichi nuovi segmenti su AEM. Senza questa regola di invalidazione, le nuove campagne mirate non funzionano su AEM Screens Player (mostra invece il contenuto predefinito).

* Aggiungere una regola di invalidazione a `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Regola da aggiungere:

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* Questa regola assicura che il file `segments.js` sia invalidato e che venga recuperato il più recente dopo la modifica.
