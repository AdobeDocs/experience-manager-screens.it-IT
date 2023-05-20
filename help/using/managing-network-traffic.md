---
title: Gestione del traffico di rete
description: La pagina descrive le impostazioni di rete standard e come gestire il traffico di rete.
exl-id: b6d8f4a3-fca2-4556-9455-b9e27b138154
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Gestione del traffico di rete {#managing-network-traffic}

Un&#39;installazione di rete può avere diverse strutture. Questa sezione descrive le impostazioni di rete e gli approcci generalizzati più comuni seguiti all’interno di un’organizzazione.

Questa guida presenta un&#39;introduzione ai server proxy, seguita dalle varie strutture di rete configurate all&#39;interno delle diverse organizzazioni.

>[!NOTE]
>**Requisiti di rete di AEM Screens**
>L’AEM Screens comunica direttamente con l’AEM as a Cloud Service, pertanto è necessario stabilire una connessione stabile tra i due nodi. I firewall sono assolutamente obbligatori per l&#39;accesso commerciale a Internet e, in qualità di cliente, è necessario capire quali porte di comunicazione devono essere aperte in questi firewall e in altri componenti di rete relativi alla sicurezza IT.

## Panoramica sui server proxy {#proxy-servers}

Una connessione Internet si basa sull&#39;utilizzo di un server proxy. Un server proxy è un computer dedicato o un sistema software in esecuzione su un computer che funge da intermediario tra un dispositivo endpoint, ad esempio un computer, e un altro server da cui un utente o un client richiede un servizio. Il server proxy può esistere nello stesso computer di un server firewall oppure in un server separato, che inoltra le richieste tramite il firewall.

Un vantaggio di un server proxy è che la sua cache può servire tutti gli utenti. Se uno o più siti Internet vengono richiesti di frequente, è probabile che si trovino nella cache del proxy e questo migliora ulteriormente il tempo di risposta dell’utente. Un proxy può anche registrare le sue interazioni, che possono essere utilizzate per la risoluzione dei problemi.

Quando un server proxy riceve una richiesta per una risorsa Internet (ad esempio una pagina Web o durante la connessione a un server di pubblicazione AEM), analizza la cache locale degli URL precedentemente denominati. Se trova la pagina, la restituisce all’utente senza inoltrare la richiesta a Internet. Se la pagina non è nella cache, il server proxy (agisce come un client) per conto dell’utente e richiede la pagina dal server in Internet. Quando il contenuto viene restituito, il server proxy lo mette in relazione con la richiesta originale e lo inoltra all&#39;utente.

## Informazioni sulle impostazioni di rete standard {#network-setups}

Per implementare un&#39;installazione di rete, è necessario fare riferimento ai seguenti scenari con i relativi punti di forza e dettagli di distribuzione.

In questa Guida vengono illustrati quattro diversi tipi di impostazioni di rete all&#39;interno di un&#39;organizzazione:

* **[Rete Internet diretta (cablata/wireless)](/help/using/direct-internet-network.md)**
* **[Direct Mobile Network](/help/using/mobile-network.md)**
* **[Rete mobile con router dati mobile e componenti di rete attivi](/help/using/mobile-network-router.md)**
* **[Rete aziendale chiusa (cablata/wireless)](/help/using/enclosed-corporate-network.md)**

Nella tabella seguente vengono illustrati i diversi tipi di configurazioni di rete con vantaggi e svantaggi:

| Configurazione della rete | Vantaggi | Svantaggi |
|--- |--- |--- |
| **Rete Internet diretta (cablata/wireless)** | Configurazione semplice e diretta<br>Ideale per installazioni di medie o grandi dimensioni<br>È possibile incapsulare una rete dedicata<br>Pochi punti di errore<br>Relativamente poco costoso<br>Buona scalabilità | Piano dati Internet obbligatorio |
| **Direct Mobile Network** | Facilità di configurazione<br>Buona scelta per installazioni di medie o grandi dimensioni<br>Buona scalabilità<br>Schermi incapsulati | Connessione Internet obbligatoria |
| **Rete mobile con router dati mobile e componenti di rete attivi** | Facilità di configurazione<br>Buona scelta per installazioni di medie o grandi dimensioni<br>È possibile incapsulare una rete dedicata<br>Pochi punti di errore<br>Relativamente poco costoso<br>Buona scalabilità | Piano dati Internet obbligatorio |
| **Rete aziendale chiusa (cablata/wireless)** | Elevata flessibilità e scalabilità<br>Altamente sicuro a causa di diverse linee di difesa<br>Reti incapsulate<br>Facilità di monitoraggio e manutenzione<br>Affidabile | Complicato e costoso<br>Consigliato per gli specialisti di rete o gli integratori di sistemi |
