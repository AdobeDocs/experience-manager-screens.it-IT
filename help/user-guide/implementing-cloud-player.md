---
title: Implementazione di Cloud Player
seo-title: Implementing Cloud Player
description: Segui questa pagina per scoprire di più sull’implementazione di Cloud Player.
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 8d1b955e54650daf3a09b5f1c16f92f2e1143f2c
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Implementazione di Cloud Player  {#implementing-cloud-player}

Questa sezione descrive come implementare Cloud Player.

>[!NOTE]
>
>La compatibilità di Cloud Player richiede un browser moderno con supporto PWA per garantire prestazioni coerenti tra i vari dispositivi.

## Installazione di Cloud Player {#installing-cloud-player}

L’installazione di Cloud Player può variare su piattaforme diverse. In generale, per qualsiasi piattaforma con un browser moderno, puoi eseguire l’applicazione lettore cloud seguendo questi passaggi:

1. Apri il browser e immetti [URL del lettore cloud](https://player.adobescreens.com) nella barra degli indirizzi.
1. Il browser controlla se il lettore cloud è installabile e quindi mostra un’icona di installazione nella barra degli indirizzi.

![immagine](/help/user-guide/assets/cloud-player-install.png)

1. Fai clic sull’icona Installa e sul pulsante Installa nella finestra di dialogo di conferma. Cloud Player verrà installato come applicazione indipendente sul dispositivo e può essere avviato utilizzando un’icona.

### Opzione di installazione di Cloud Player {#cloud-player-install-option}

1. L’opzione di installazione per un PWA è nota anche come &quot;Aggiungi alla schermata iniziale&quot; o funzione A2HS.  Il supporto per l’installazione di PWA dal web varia in base al browser e alla piattaforma.
1. Ogni browser ha criteri diversi per verificare se l’app PWA è installabile o meno. Generalmente il browser controlla questi (maggiori dettagli qui):
   * Se l’applicazione dispone di un file json manifesto con le chiavi minime necessarie per installare l’app sulla piattaforma, ad esempio nome, icone, start_url, visualizzazione
   * Se l&#39;applicazione dispone di un file di service worker con un listener di eventi di recupero.
   * L’app deve essere servita tramite https.
1. L’opzione Installa potrebbe essere visibile in posizioni diverse in browser e tipi di dispositivo diversi. Alcuni browser potrebbero nascondere l’icona Installa nella barra dei menu delle opzioni.

## Provisioning di massa di Cloud Player {#bulk-provisioning}

Per eseguire il provisioning in blocco del lettore cloud su più dispositivi:

1. Scegli una soluzione MDM che supporti l’esecuzione di un browser con un URL in modalità Kiosk (Chiosco).
1. Per applicare le stesse configurazioni a tutti i dispositivi, segui questi passaggi:
   1. Host config.json su un server in modo che sia accessibile, ad esempio: https://&lt;config_server_host>/config.json
   1. Per installare Cloud Player e applicare le configurazioni ospitate, utilizza l’URL del lettore cloud, ad esempio: https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. L’applicazione Cloud Player cerca config.json nella directory principale di &lt;config_server_host>, analizza config.json per ottenere le configurazioni personalizzate e applicale.
   1. Queste configurazioni verranno applicate a ogni ricaricamento del lettore.

## Provisioning in blocco su Chrome OS {#bulk-provisioning-chrome}

Per ulteriori informazioni sul provisioning in blocco su Chrome OS, consulta: [Installare Cloud Player su Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## Configurazione richiesta per le istanze AEM {#bulk-provisioning-config-aem}

In base al tipo di istanza AEM, seleziona una delle seguenti guide per abilitare CORS b/w AEM &amp; cloud player:
* [AEM on-premise/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

## Supporto offline per il recupero di contenuti esterni {#offline-support}

In vari scenari di utilizzo, i canali possono richiedere il recupero di contenuto da un’origine esterna (ad esempio, widget meteo o applicazioni a pagina singola integrate in Commerce) che non può fornire supporto offline. Per abilitare la funzionalità offline per questi casi d’uso specifici, Cloud Player offre il supporto per l’intestazione personalizzata.
Cloud Player utilizza una strategia di cache Network First, ovvero tenta di recuperare il contenuto dalla rete (quindi aggiorna la cache con l’ultima versione), tornando al contenuto memorizzato nella cache, se disponibile. Per implementare il supporto offline per tale recupero di contenuto, l’intestazione personalizzata deve essere inclusa nella richiesta. Successivamente, la richiesta con l’intestazione personalizzata verrà memorizzata nella cache del lettore, facilitando l’accesso offline al contenuto e mantenendo la strategia di cache Network First.

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
