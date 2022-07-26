---
title: Configurazioni del Dispatcher per AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: Questa pagina illustra le linee guida per la configurazione del dispatcher per un progetto AEM Screens.
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 13c9ed116a310c2c17fd1cc3d2c56ef74620df4b
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 3%

---

# Configurazioni del Dispatcher per AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager.

La pagina seguente fornisce le linee guida per la configurazione del dispatcher per un progetto AEM Screens.

>[!NOTE]
>
>Se un dispatcher è disponibile, è possibile impedire le connessioni al servlet di registrazione filtrando nelle regole del dispatcher.
>
>Se non è presente alcun dispatcher, disattiva il servlet di registrazione nell’elenco dei componenti OSGi.

Prima di configurare il dispatcher per un progetto AEM Screens, è necessario disporre di conoscenze precedenti su Dispatcher.
Fai riferimento a [Configurazione di Dispatcher](https://docs.adobe.com/content/help/it-IT/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) per ulteriori dettagli.

## Configurazione di Dispatcher per la versione v2 del manifesto {#configuring-dispatcher}

>[!IMPORTANT]
>Le seguenti configurazioni del Dispatcher si applicano solo alla versione v2 Manifest. Fai riferimento a [Configurazioni del Dispatcher per la versione 3 di Manifest](#configuring-dispatcherv3) per la versione manifest v3.

I lettori o i dispositivi AEM Screens utilizzano una sessione autenticata per accedere alle risorse anche nelle istanze di pubblicazione. Quindi, quando disponi di più istanze di pubblicazione, le richieste devono sempre andare alla stessa istanza di pubblicazione in modo che la sessione autenticata sia valida per tutte le richieste provenienti dai lettori/dispositivi AEM Screens.

Segui i passaggi riportati di seguito per configurare il dispatcher per un progetto AEM Screens.

### Abilitazione di sessioni permanenti {#enable-sticky-session}

Se desideri utilizzare più istanze di pubblicazione fronte a un singolo dispatcher, dovrai aggiornare il `dispatcher.any` file per abilitare la persistenza

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Se disponi di un’istanza di pubblicazione fronte a un dispatcher, l’abilitazione della persistenza al dispatcher non sarà di aiuto in quanto il load balancer può inviare ogni richiesta al dispatcher. In questo caso, fai clic su **Abilita** in **Atteggiamento** per attivarlo a livello di load balancer, come illustrato nella figura seguente:

![immagine](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Ad esempio, se utilizzi AWS ALB, consulta [Gruppi di destinazione per i bilanciatori di carico dell&#39;applicazione](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) per abilitare la persistenza a livello di ALB. Abilita l&#39;adesività per 1 giorno.

### Passaggio 1: Configurazione delle intestazioni client {#step-configuring-client-headers}

Aggiungi quanto segue a `/clientheaders`sezione:

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

### Passaggio 3: Disattivazione della cache del Dispatcher {#step-disabling-dispatcher-cache}

Disattiva la memorizzazione in cache del dispatcher per ***/content/screens path***.

I lettori Screens utilizzano una sessione autenticata, in modo che il dispatcher non memorizzi nella cache nessuna delle richieste dei lettori Screens per `channels/assets`.

Per abilitare la cache per le risorse in modo che le risorse vengano servite dalla cache del dispatcher, devi:

* Aggiungi `/allowAuthorization 1` in `/cache` sezione
* Aggiungi le regole seguenti a `/rules` sezione `/cache`

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

Assicurati di consentire questi filtri e regole di cache nei dispatcher che fronteggiano le istanze di pubblicazione per il funzionamento di Screens.

### Prerequisiti per la versione 3 di Manifest{#prerequisites3}

Prima di configurare Dispatcher (versione manifest v3) per AEM Screens, verifica di seguire i due prerequisiti seguenti:

* Assicurati di utilizzare `v3 manifests`. Passa a `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` e assicurano che `Enable ContentSync Cache` è deselezionato.

* Assicurati che l’agente di flush del dispatcher sia configurato in `/etc/replication/agents.publish/dispatcher1useast1Agent` nell’istanza di pubblicazione.

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

### Regole di cache {#cache-rules-v3}

* Aggiungi `/allowAuthorized "1"` a `/cache` sezione `publish_farm.any`.

* Tutti i lettori Screens utilizzeranno la sessione autenticata per connettersi a AEM (autore/pubblicazione). Dispatcher standard non memorizza in cache questi url, pertanto è necessario attivarli.

* Aggiungi `statfileslevel "10"` a `/cache` sezione `publish_farm.any`
Questo supporterà il caching fino a 10 livelli dal docroot della cache e annullerà di conseguenza la validità quando il contenuto viene pubblicato anziché invalidare tutto. Puoi modificare questo livello in base alla profondità della struttura del contenuto

* Aggiungi quanto segue a `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Aggiungi le regole seguenti a `/rules` sezione `/cache` in `publish_farm.any` o in un file incluso da `publish_farm.any`:

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

### Aggiungi una regola di invalidazione per segment.js {#invalidsegmentjs}

Se aggiungi nuovi segmenti e li pubblichi, la `segments.js` il file gestito dal dispatcher non contiene le nuove voci che interrompevano il flusso di targeting sul dispositivo screens. Il file segment.js viene memorizzato nella cache a livello di dispatcher, ma non vi era alcuna regola di invalidazione per lo stesso file. Di conseguenza, è necessario aggiungere una regola di invalidazione.

* Aggiungi nuovi segmenti al `/conf/<project-name>/settings/wcm/segments.seg.js` file.

* Aggiungi una regola di invalidazione a `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Ecco la regola da aggiungere:

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/personalisation-hub/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* Questa regola assicura `segments.js` Il file viene invalidato e l’ultima viene recuperata quando viene modificato.
