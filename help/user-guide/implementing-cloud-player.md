---
title: Implementazione di Cloud Player
description: Scopri l’implementazione di Cloud Player.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 6720e20f5254e869bde814bd167730e426d0f8fe
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---

# Implementazione di Cloud Player {#implementing-cloud-player}

AEM Screens offre tradizionalmente applicazioni di riproduzione native distinte per varie piattaforme, tra cui ChromeOS, Windows, Android™ e `Tizen`. Tuttavia, in risposta alle esigenze in continua evoluzione degli utenti, Adobe ha introdotto una soluzione innovativa: AEM Screens Cloud Player.

Cloud Player rappresenta una deviazione significativa dalle precedenti applicazioni native di Adobe. Si tratta di un’app web progressiva (PWA), ospitata su un server. Questo approccio trasformativo consente ai clienti di utilizzare un lettore indipendente dalla piattaforma, in grado di funzionare direttamente all’interno di un browser web.

Accedere a Cloud Player è semplice come visitare `https://player.adobescreens.com`. Gli utenti possono installarlo sul proprio dispositivo, indipendentemente dalla piattaforma, e godere di esperienze di digital signage fluide. La compatibilità di Cloud Player dipende dalla presenza di un browser moderno con supporto PWA, che garantisce prestazioni coerenti tra i vari dispositivi. Dì addio agli aggiornamenti manuali e ciao a un lettore che offre automaticamente correzioni e funzionalità, garantendo sempre a portata di mano le funzionalità più recenti. Questo passaggio a un Cloud Player basato su PWA segna una straordinaria evoluzione nelle offerte di digital signage di Adobe, rendendole più accessibili, versatili e facili da usare rispetto al passato.

Questa sezione descrive come implementare Cloud Player.

>[!NOTE]
>
>La compatibilità di Cloud Player richiede un browser moderno con supporto PWA per garantire prestazioni coerenti tra i vari dispositivi.

## Installazione di Cloud Player {#installing-cloud-player}

L’installazione di Cloud Player può variare su piattaforme diverse. In generale, per qualsiasi piattaforma con un browser moderno, puoi eseguire l’applicazione lettore cloud seguendo questi passaggi:

1. Apri il browser e immetti l&#39;[URL del lettore cloud](https://player.adobescreens.com/content/dam/universal-player/firmware.html) nella barra degli indirizzi.
1. Il browser controlla se Cloud Player è installabile e quindi mostra un’icona di installazione nella barra degli indirizzi.

   ![immagine](/help/user-guide/assets/cloud-player-install.png)

1. Fai clic sull’icona Installa e sul pulsante Installa nella finestra di dialogo di conferma. Cloud Player viene installato come applicazione indipendente sul dispositivo e può essere avviato utilizzando un’icona.

>[!NOTE]
>
>### Opzione di installazione di Cloud Player {#cloud-player-install-option}
>
>1. L’opzione di installazione per un PWA è nota anche come &quot;Aggiungi alla schermata iniziale&quot; o funzione A2HS. Il supporto per l’installazione di PWA dal web varia in base al browser e alla piattaforma.
>1. Ogni browser ha criteri diversi per verificare se l’app PWA è installabile o meno. In genere, il browser può verificare (ulteriori dettagli qui):
>
>* Se l’applicazione dispone di un file json manifesto con chiavi minime richieste per l’installazione dell’app sulla piattaforma, ovvero nome, icone, start_url, visualizzazione
>* Se l&#39;applicazione dispone di un file di service worker con un listener di eventi di recupero
>* L’app deve essere servita tramite https
>
>1. L’opzione di installazione potrebbe essere visibile in posizioni diverse in browser e tipi di dispositivi diversi. Alcuni browser potrebbero nascondere l’icona Installa nella barra dei menu delle opzioni.

## Provisioning di massa di Cloud Player {#bulk-provisioning}

Per eseguire il provisioning in blocco del lettore cloud su più dispositivi:

1. Scegli una soluzione MDM che supporti l’esecuzione di un browser con un URL in modalità Kiosk (Chiosco).
1. Per applicare le stesse configurazioni a tutti i dispositivi, segui questi passaggi:

   1. Host config.json su un server in modo che sia accessibile, ad esempio: `https://<config_server_host>/config.json`
   1. Per installare il lettore cloud e applicare le configurazioni ospitate, utilizza l&#39;URL del lettore cloud, ad esempio: `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. L’applicazione Cloud Player cerca config.json nella directory principale di &lt;config_server_host>, quindi analizza il file config.json per ottenere le configurazioni personalizzate e applicarle.
   1. Queste configurazioni vengono applicate a ogni ricaricamento del lettore.

## Provisioning in blocco su Chrome OS {#bulk-provisioning-chrome}

Ulteriori informazioni sul provisioning in blocco nel sistema operativo Chrome. Consulta [Installare Cloud Player su Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/chromeos-install-cloud-player). &lt;!— `https://www.adobe.com/go/aem_screens_cloud_player_en` >

## Configurazione richiesta per le istanze AEM {#bulk-provisioning-config-aem}

In base al tipo di istanza dell’AEM, fai clic su una delle seguenti guide per abilitare CORS b/w AEM e Cloud Player:

* [Assistenza locale AEM/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams) <!-- `https://www.adobe.com/go/aem_screens_cors_ams_en` -->

* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs) <!-- `https://www.adobe.com/go/aem_screens_cors_aemaacs_en` -->


>[!NOTE]
>
>## App Chrome obsolete da Google
>
>1. App Chrome su hardware Chrome OS:
>
>Google ha attivamente dichiarato obsolete le app Chrome a favore delle app PWA, con una migrazione pianificata fino a gennaio 2025. Pertanto, l’app AEM Screens Player sul sistema operativo Chrome cessa di funzionare in base alla timeline condivisa. L’Adobe esorta gli utenti che attualmente utilizzano Chrome Player in produzione a pianificare la transizione a Screens Cloud Player.
>
>1. Chrome Extension Player su Mac, Windows e Linux®:
>
>A causa del processo di rimozione di Google, a partire dalla versione 114 di Google Chrome, Screens Chrome Extension Player non è più supportato. L’Adobe consiglia di passare al rispettivo Screens Cloud Player per tutti i requisiti di sviluppo e test.

## Supporto offline per il recupero di contenuti esterni {#offline-support}

In vari scenari di utilizzo, i canali possono richiedere il recupero di contenuto da un’origine esterna (ad esempio, widget meteo o applicazioni a pagina singola integrate in Commerce) che non è in grado di fornire supporto offline. Per abilitare la funzionalità offline per questi casi d’uso specifici, Cloud Player offre il supporto per l’intestazione personalizzata.

Cloud Player utilizza una strategia di cache Network First, ovvero tenta di recuperare il contenuto dalla rete (quindi aggiorna la cache con l’ultima versione), tornando al contenuto memorizzato nella cache, se disponibile. Per implementare il supporto offline per tale recupero di contenuto, l’intestazione personalizzata deve essere inclusa nella richiesta. Quindi, la richiesta con l’intestazione personalizzata viene memorizzata nella cache del lettore, facilitando l’accesso offline al contenuto e mantenendo la strategia di cache Network First.

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## Feedback

Adobe dà valore al tuo feedback. Condividi le tue opinioni con noi tramite questo [modulo](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
