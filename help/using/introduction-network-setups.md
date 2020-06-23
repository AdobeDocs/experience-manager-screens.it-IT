---
title: Introduzione alle impostazioni di rete standard
seo-title: Introduzione alle impostazioni di rete standard
description: La pagina descrive le impostazioni di rete standard
seo-description: La pagina descrive le impostazioni di rete standard
translation-type: tm+mt
source-git-commit: 0be82fcc46166ec0613bd658a0caeab83bd72551
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# Gestione del traffico di rete {#managing-network-traffic}

Una configurazione di rete può avere diverse strutture. Questa sezione fornisce una panoramica delle strutture di rete implementate in un ambiente. Esistono diverse impostazioni che a volte vengono implementate da zero.

In questa sezione viene illustrata un&#39;introduzione ai server proxy, seguita dalle diverse strutture di rete configurate con organizzazioni diverse.

>[!NOTE]
>**Requisiti di rete AEM Screens **>I AEM Screens comunicano direttamente con AEM Cloud Service, pertanto è necessario stabilire una connessione stabile tra questi due nodi. I firewall sono assolutamente obbligatori per l&#39;accesso a Internet commerciale e il Cliente ha bisogno di sapere quali porte di comunicazione devono essere aperte nei firewall e altri componenti di rete relativi alla sicurezza IT che sono sotto il controllo del Cliente.

## Server proxy {#proxy-servers}

Un server proxy è un computer dedicato o un sistema software in esecuzione su un computer che funge da intermediario tra un dispositivo endpoint, come un computer, e un altro server da cui un utente o un client richiede un servizio. Il server proxy può esistere nello stesso computer di un server firewall o in un server separato, che inoltra le richieste attraverso il firewall.

Un vantaggio di un server proxy è rappresentato dal fatto che la sua cache può essere utilizzata da tutti gli utenti. Se uno o più siti Internet sono frequentemente richiesti, è probabile che si trovino nella cache del proxy, il che migliorerà il tempo di risposta dell&#39;utente. Un proxy può anche registrare le sue interazioni, il che può essere utile per la risoluzione dei problemi.

## Informazioni sulle impostazioni di rete standard {#network-setups}

Per implementare una configurazione di rete, è necessario fare riferimento ai seguenti scenari con i punti di forza e i dettagli di distribuzione.

Esistono tre tipi principali di configurazione della rete:

1. [Rete Internet diretta (via cavo/wireless)](/help/using/direct-internet-network.md)
1. [Rete mobile diretta](/help/using/mobile-network.md)
1. [Rete mobile con Mobile Data Router e Componenti di rete attivi](/help/using/mobile-network-router.md)
1. [Rete aziendale chiusa (cablata/wireless)](/help/using/enclosed-corporate-network.md)

La tabella seguente illustra i diversi tipi di configurazione di rete con vantaggi e svantaggi:

<table>
 <tbody>
  <tr>
   <td><strong>Configurazione della rete</strong></td>
   <td><strong>Vantaggi</strong></td>
   <td><strong>Svantaggi</strong></td>
  </tr>
  <tr>
   <td><strong>Accesso diretto a Internet</strong></td>
   <td>Facile e semplice da configurareUp<br>Buona scelta per installazioni<br>dedicate di medie dimensioni o di grandi dimensioni<br>Pochi punti di errore<br>Relativamente conveniente<br>Buona scalabilità</td>
   <td>Piano dati Internet appropriato obbligatorio</td>
  </tr>
    <tr>
   <td><strong>Rete mobile diretta</strong></td>
   <td>Facile e semplice da configurareUp<br>Buona scelta per installazioni<br>di medie dimensioni o di grandi dimensioni<br>Schermate incapsulate di buona scalabilità
</td>
   <td>Connessione Internet appropriata obbligatoria</td>
  </tr>
    <tr>
<tr>
   <td><strong>Rete mobile con Mobile Data Router e Componenti di rete attivi</strong></td>
   <td>Facile e semplice da configurareUp<br>Buona scelta per installazioni<br>di medie dimensioni o di grandi dimensioniRete dedicata può essere racchiusa<br>Pochi punti di errore<br>Relativamente conveniente<br>Buona scalabilità</br></td>
   <td>Piano dati Internet appropriato obbligatorio</td>
  </tr>
    <tr>

<td><strong>Rete aziendale chiusa</strong></td>
   <td>Elevata flessibilità e scalabilità<br>Altamente sicura grazie alle diverse linee di difesa<br>Reti<br>incapsulate facili da monitorare e mantenere<br>affidabili</td>
   <td>Consigliati specialisti di<br>rete o integratori di sistemi complicati e costosi</td>
  </tr>
  </tr>
 </tbody>
</table>


