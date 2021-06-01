---
title: Gestione del traffico di rete
description: La pagina descrive le impostazioni di rete standard e come gestire il traffico di rete.
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---


# Gestione del traffico di rete {#managing-network-traffic}

Una configurazione di rete può avere diverse strutture. Questa sezione descrive le configurazioni di rete più comuni e gli approcci generalizzati seguiti all&#39;interno di un&#39;organizzazione.

Questa guida evidenzia un&#39;introduzione ai server proxy seguita dalle diverse strutture di rete configurate all&#39;interno di organizzazioni diverse.

>[!NOTE]
>**Requisiti di rete di AEM Screens**
>AEM Screens comunica direttamente con il AEM come Cloud Service, pertanto è necessario stabilire una connessione stabile tra i due nodi. I firewall sono assolutamente obbligatori per l’accesso a Internet a fini commerciali e come cliente devi capire quali porte di comunicazione devono essere aperte in questi firewall e in altri componenti di rete relativi alla sicurezza IT.

## Panoramica sui server proxy {#proxy-servers}

Una connessione Internet si basa sull&#39;utilizzo di un server proxy. Un server proxy è un computer dedicato o un sistema software in esecuzione su un computer che funge da intermediario tra un dispositivo endpoint, ad esempio un computer, e un altro server da cui un utente o un client richiede un servizio. Il server proxy può esistere nella stessa macchina di un server firewall o in un server separato, che inoltra le richieste tramite il firewall.

Un vantaggio di un server proxy è che la sua cache può servire tutti gli utenti. Se uno o più siti Internet sono frequentemente richiesti, è probabile che si trovino nella cache del proxy e questo migliora ulteriormente il tempo di risposta dell&#39;utente. Un proxy può anche registrare le sue interazioni, che possono essere utilizzate per la risoluzione dei problemi.

Quando un server proxy riceve una richiesta per una risorsa Internet (ad esempio una pagina Web o durante la connessione a un server di pubblicazione AEM), esegue la scansione della cache locale degli url precedentemente chiamati. Se trova la pagina, la restituisce all’utente senza inoltrare la richiesta a Internet. Se la pagina non è nella cache, il server proxy (agisce come client) per conto dell’utente e richiede la pagina dal server in Internet. Quando il contenuto viene restituito, il server proxy lo relaziona alla richiesta originale e lo inoltra all&#39;utente.

## Informazioni sulle impostazioni di rete standard {#network-setups}

Per implementare una configurazione di rete, è necessario fare riferimento ai seguenti scenari con i relativi punti di forza e dettagli di distribuzione.

In questa guida vengono illustrati quattro diversi tipi di configurazioni di rete all&#39;interno di un&#39;organizzazione:

* **[Rete Internet diretta (cablata/wireless)](/help/using/direct-internet-network.md)**
* **[Rete mobile diretta](/help/using/mobile-network.md)**
* **[Rete mobile con router dati mobile e componenti di rete attivi](/help/using/mobile-network-router.md)**
* **[Rete aziendale chiusa (cablata/wireless)](/help/using/enclosed-corporate-network.md)**

La tabella seguente illustra i diversi tipi di configurazioni di rete con vantaggi e svantaggi:

| Configurazione di rete | Vantaggi | Svantaggi |
|--- |--- |--- |
| **Rete Internet diretta (cablata/wireless)** | Facile e diretto da configurare<br>Una buona scelta per installazioni di medie dimensioni o di grandi dimensioni<br>La rete dedicata può essere incapsulata<br>Pochi punti di guasto<br>Relativamente poco costoso<br>Buona scalabilità | Piano dati Internet obbligatorio |
| **Rete mobile diretta** | Facile da configurare<br>Buona scelta per installazioni di medie o grandi dimensioni<br>Buona scalabilità<br>Schermi incapsulati | Connessione Internet obbligatoria |
| **Rete mobile con router dati mobile e componenti di rete attivi** | Facile da configurare<br>È possibile scegliere tra installazioni di medie e grandi dimensioni<br>La rete dedicata può essere incapsulata<br>Alcuni punti di errore<br>Relativamente poco costosi<br>Buona scalabilità | Piano dati Internet obbligatorio |
| **Rete aziendale chiusa (cablata/wireless)** | Elevata flessibilità e scalabilità<br>Altamente sicura a causa di diverse linee di difesa<br>Reti incapsulate<br>Facile da monitorare e mantenere<br>Affidabile | Complicato e costoso<br>Consigliato per gli specialisti di rete o gli integratori di sistema |
