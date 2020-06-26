---
title: Gestione del traffico di rete
description: La pagina descrive le impostazioni di rete standard e come gestire il traffico di rete.
translation-type: tm+mt
source-git-commit: 173ce977549ed64e3750bb751a8fe1b27e277aa2
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---


# Gestione del traffico di rete {#managing-network-traffic}

Una configurazione di rete può avere diverse strutture. Questa sezione descrive le impostazioni di rete e gli approcci generici più comuni seguiti all&#39;interno di un&#39;organizzazione.

Questa guida presenta un&#39;introduzione ai server proxy, seguiti dalle diverse strutture di rete configurate all&#39;interno di diverse organizzazioni.

>[!NOTE]
>
>**Requisiti di rete AEM Screens**
>
>I AEM Screens comunicano direttamente con AEM come Cloud Service, pertanto è necessario stabilire una connessione stabile tra i due nodi. I firewall sono assolutamente obbligatori per l&#39;accesso a Internet commerciale e come cliente devi capire quali porte di comunicazione devono essere aperte in questi firewall e altri componenti di rete relativi alla sicurezza IT.

## Panoramica sui server proxy {#proxy-servers}

Una connessione Internet si basa sull&#39;utilizzo di un server proxy. Un server proxy è un computer dedicato o un sistema software in esecuzione su un computer che funge da intermediario tra un dispositivo endpoint, ad esempio un computer, e un altro server da cui un utente o un client richiede un servizio. Il server proxy può esistere nello stesso computer di un server firewall o in un server separato, che inoltra le richieste attraverso il firewall.

Un vantaggio di un server proxy è rappresentato dal fatto che la cache può essere utilizzata da tutti gli utenti. Se uno o più siti Internet sono frequentemente richiesti, è probabile che si trovino nella cache del proxy e questo migliora ulteriormente il tempo di risposta dell&#39;utente. Un proxy può anche registrare le proprie interazioni, che possono essere utilizzate per la risoluzione dei problemi.

Quando un server proxy riceve una richiesta per una risorsa Internet (ad esempio una pagina Web o durante la connessione a un server di pubblicazione AEM), esegue la scansione della cache locale degli URL precedentemente denominati URL. Se la pagina viene trovata, viene restituita all’utente senza inoltrare la richiesta a Internet. Se la pagina non è presente nella cache, il server proxy (funge da client) per conto dell’utente e richiede la pagina dal server in Internet. Quando il contenuto viene restituito, il server proxy lo collega alla richiesta originale e lo inoltra all&#39;utente.

## Informazioni sulle impostazioni di rete standard {#network-setups}

Per implementare una configurazione di rete, è necessario fare riferimento ai seguenti scenari con i relativi punti di forza e dettagli di distribuzione.

La presente Guida evidenzia quattro diversi tipi di impostazioni di rete all&#39;interno di un&#39;organizzazione:

* **[Rete Internet diretta (via cavo/wireless)](/help/using/direct-internet-network.md)**
* **[Rete mobile diretta](/help/using/mobile-network.md)**
* **[Rete mobile con Mobile Data Router e Componenti di rete attivi](/help/using/mobile-network-router.md)**
* **[Rete aziendale chiusa (cablata/wireless)](/help/using/enclosed-corporate-network.md)**

La tabella seguente illustra i diversi tipi di configurazione di rete con vantaggi e svantaggi:

| Configurazione della rete | Vantaggi | Svantaggi |
|--- |--- |--- |
| **Rete Internet diretta (via cavo/wireless)** | Facile e semplice da<br>installareSetUpBuona scelta per<br>installazioni di medie dimensioni o di grandi dimensioniLa rete dedicata può essere<br>incapsulataPochi punti di<br>erroreRelativamente<br>poco costosaBuona scalabilità | Piano dati Internet obbligatorio |
| **Rete mobile diretta** | Facile da<br>configurareBuona scelta per<br>installazioni di medie e grandi dimensioniBuona<br>scalabilitàSchermi incapsulati | Connessione Internet obbligatoria |
| **Rete mobile con Mobile Data Router e Componenti di rete attivi** | Facile da<br>configurareBuona scelta per<br>installazioni di medie e grandi dimensioniLa rete dedicata può essere<br>incapsulataPochi punti di<br>erroreRelativamente<br>poco costosaBuona scalabilità | Piano dati Internet obbligatorio |
| **Rete aziendale chiusa (cablata/wireless)** | Elevata flessibilità e<br>scalabilitàAltamente sicura grazie alle diverse linee di<br>difesaReti<br>IncapsulateFacile da monitorare e<br>mantenereAffidabile | Complicato e<br>costosoConsigliato per gli specialisti di rete o integratori di sistemi |
