---
title: Gestione del traffico di rete
description: La pagina descrive le impostazioni di rete standard e come gestire il traffico di rete.
translation-type: tm+mt
source-git-commit: 93cc11459e23d3eb22d865bedeb26deaf7135636
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# Gestione del traffico di rete {#managing-network-traffic}

Una configurazione di rete può avere diverse strutture. Questa sezione descrive le impostazioni di rete più comuni all&#39;interno della configurazione di rete di un&#39;organizzazione.

Questa guida presenta un&#39;introduzione ai server proxy, seguiti dalle diverse strutture di rete configurate all&#39;interno di diverse organizzazioni.

>[!NOTE]
>
>**Requisiti di rete AEM Screens**
>
>I AEM Screens comunicano direttamente con AEM come Cloud Service, pertanto è necessario stabilire una connessione stabile tra i due nodi. I firewall sono assolutamente obbligatori per l&#39;accesso a Internet commerciale e come cliente è necessario capire quali porte di comunicazione devono essere aperte nei firewall e in altri componenti di rete relativi alla sicurezza IT.

## Panoramica sui server proxy {#proxy-servers}

Una connessione Internet si basa sull&#39;utilizzo di un server proxy. Un server proxy è un computer dedicato o un sistema software in esecuzione su un computer che funge da intermediario tra un dispositivo endpoint, ad esempio un computer, e un altro server da cui un utente o un client richiede un servizio. Il server proxy può esistere nello stesso computer di un server firewall o in un server separato, che inoltra le richieste attraverso il firewall.

Un vantaggio di un server proxy è rappresentato dal fatto che la sua cache può essere utilizzata da tutti gli utenti. Se uno o più siti Internet sono frequentemente richiesti, è probabile che si trovino nella cache del proxy, il tempo di risposta dell&#39;utente aumenta. Un proxy può anche registrare le proprie interazioni, utilizzate per la risoluzione dei problemi.

## Informazioni sulle impostazioni di rete standard {#network-setups}

Per implementare una configurazione di rete, è necessario fare riferimento ai seguenti scenari con i relativi punti di forza e dettagli di distribuzione.

Esistono quattro tipi principali di configurazione della rete:

1. [Rete Internet diretta (via cavo/wireless)](/help/using/direct-internet-network.md)
1. [Rete mobile diretta](/help/using/mobile-network.md)
1. [Rete mobile con Mobile Data Router e Componenti di rete attivi](/help/using/mobile-network-router.md)
1. [Rete aziendale chiusa (cablata/wireless)](/help/using/enclosed-corporate-network.md)

La tabella seguente illustra i diversi tipi di configurazione di rete con vantaggi e svantaggi:

| Configurazione della rete | Vantaggi | Svantaggi |
|--- |--- |--- |
| Rete Internet diretta (via cavo/wireless) | Facile e semplice da<br>installareSetUpBuona scelta per<br>installazioni di medie dimensioni o di grandi dimensioniLa rete dedicata può essere<br>incapsulataPochi punti di<br>erroreRelativamente<br>poco costosaBuona scalabilità | Piano dati Internet obbligatorio |
| Rete mobile diretta | Facile da<br>configurareBuona scelta per<br>installazioni di medie e grandi dimensioniBuona<br>scalabilitàSchermi incapsulati | Connessione Internet obbligatoria |
| Rete mobile con Mobile Data Router e Componenti di rete attivi | Facile da<br>configurareBuona scelta per<br>installazioni di medie e grandi dimensioniLa rete dedicata può essere<br>incapsulataPochi punti di<br>erroreRelativamente<br>poco costosaBuona scalabilità | Piano dati Internet obbligatorio |
| Rete aziendale chiusa (cablata/wireless) | Elevata flessibilità e<br>scalabilitàAltamente sicura grazie alle diverse linee di<br>difesaReti<br>IncapsulateFacile da monitorare e<br>mantenereAffidabile | Complicato e<br>costosoConsigliato per gli specialisti di rete o integratori di sistemi |
