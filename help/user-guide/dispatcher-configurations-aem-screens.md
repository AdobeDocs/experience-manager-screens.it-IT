---
title: Configurazioni del Dispatcher per AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: In questa pagina sono illustrate le linee guida per la configurazione di Dispatcher per un progetto AEM Screens.
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Configurazioni del Dispatcher per AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager.

La pagina seguente fornisce le linee guida per configurare Dispatcher per un progetto AEM Screens.

>[!NOTE]
>
>Se è disponibile un dispatcher, le connessioni al servlet di registrazione possono essere impedite filtrando nelle regole del dispatcher.
>
>Se non è presente alcun dispatcher, disabilita il servlet di registrazione nell’elenco dei componenti OSGi.

Prima di configurare Dispatcher per un progetto AEM Screens, è necessario avere una conoscenza preventiva di Dispatcher.
Fai riferimento a [Configurazione di Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) per ulteriori dettagli.

## Configurazione di Dispatcher per la versione del manifesto v2 {#configuring-dispatcher}

>[!IMPORTANT]
>Le seguenti configurazioni di Dispatcher si applicano solo alla versione v2 di Manifest. Fai riferimento a [Configurazioni del Dispatcher per la versione v3 del manifesto](#configuring-dispatcherv3) per la versione del manifesto v3.

I lettori o i dispositivi AEM Screens utilizzano una sessione autenticata per accedere anche alle risorse nelle istanze di pubblicazione. Pertanto, quando disponi di più istanze di pubblicazione, le richieste devono sempre andare alla stessa istanza di pubblicazione in modo che la sessione autenticata sia valida per tutte le richieste provenienti dai lettori/dispositivi AEM Screens.

Segui i passaggi seguenti per configurare Dispatcher per un progetto AEM Screens.

### Abilitazione di sessioni permanenti {#enable-sticky-session}

Se desideri utilizzare più istanze di pubblicazione gestite da un singolo dispatcher, dovrai aggiornare `dispatcher.any` file per abilitare la coerenza

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Se un’istanza Publish è gestita da un dispatcher, l’abilitazione della coerenza nel dispatcher non sarà di aiuto, in quanto il load balancer può inviare ogni richiesta al dispatcher. In questo caso, fai clic su **Abilita** in **Adesività** per abilitarlo a livello di load balancer, come illustrato nella figura seguente:

![immagine](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Ad esempio, se utilizzi AWS ALB, consulta [Gruppi target per i load balancer delle applicazioni](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) per abilitare la fedeltà a livello ALB. Abilita la fedeltà per 1 giorno.

### Passaggio 1: configurazione delle intestazioni client {#step-configuring-client-headers}

Aggiungi quanto segue a `/clientheaders`sezione:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Passaggio 2: configurazione dei filtri di Screens {#step-configuring-screens-filters}

Per configurare i filtri di Screens, aggiungi quanto segue a ***/filter***.

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

Disattiva il caching del dispatcher per ***Percorso /content/screens***.

Screens Player utilizza una sessione autenticata, pertanto Dispatcher non memorizza in cache nessuna delle richieste di Screens Player per `channels/assets`.

Per abilitare la cache per le risorse in modo che vengano servite dalla cache del dispatcher, devi:

* Aggiungi `/allowAuthorization 1` in `/cache` sezione
* Aggiungi le seguenti regole a `/rules` sezione di `/cache`

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

## Configurazione di Dispatcher per la versione v3 del manifesto{#configuring-dispatcherv3}

Assicurati di consentire questi filtri e regole di cache nei dispatcher che presentano le istanze di pubblicazione per il funzionamento di Screens.

### Prerequisiti per la versione del manifesto v3{#prerequisites3}

Prima di configurare Dispatcher (versione manifesto v3) per AEM Screens, assicurati di seguire questi due prerequisiti:

* Assicurati di utilizzare `v3 manifests`. Accedi a `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` e garantire che `Enable ContentSync Cache` non è selezionato.

* Assicurati che l’agente di svuotamento del dispatcher sia configurato in `/etc/replication/agents.publish/dispatcher1useast1Agent` nell’istanza Publish.

   ![immagine](/help/user-guide/assets/dispatcher/dispatcher-1.png)

   ![immagine](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filtri  {#filter-v3}

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

* Aggiungi `/allowAuthorized "1"` a `/cache` sezione in `publish_farm.any`.

* Tutti i lettori Screens utilizzeranno una sessione autenticata per connettersi all’AEM (authoring/pubblicazione). Dispatcher pronto all’uso non memorizza in cache questi URL, quindi è necessario abilitarli.

* Aggiungi `statfileslevel "10"` a `/cache` sezione in `publish_farm.any`
Questo supporterà la memorizzazione in cache fino a 10 livelli dalla directory principale dei documenti della cache e di conseguenza l’annullamento della validità quando il contenuto viene pubblicato, anziché annullare la validità di tutto. Puoi modificare questo livello in base alla profondità della struttura del contenuto

* Aggiungi quanto segue a `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Aggiungi le seguenti regole a `/rules` sezione in `/cache` in `publish_farm.any` o in un file incluso da `publish_farm.any`:

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

Se utilizzi campagne mirate con AEM Screens, il `segments.js file` Quando aggiungi e pubblichi nuovi segmenti su AEM, deve essere annullata la validità dell’assistenza fornita dal dispatcher. Senza questa regola di invalidazione, le nuove campagne mirate non funzioneranno sul lettore Screens (verrà invece mostrato il contenuto predefinito).

* Aggiungi una regola di invalidazione a `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Regola da aggiungere:

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

* Questa regola garantisce che `segments.js` il file viene invalidato e, se modificato, viene recuperato il file più recente.
