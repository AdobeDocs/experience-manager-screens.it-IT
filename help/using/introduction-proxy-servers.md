---
title: Informazioni sui server proxy
seo-title: Informazioni sui server proxy
description: La pagina descrive i server proxy
seo-description: La pagina descrive i server proxy
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Introduzione alle impostazioni di rete standard {#intro-standard-networks}

Una configurazione di rete può avere diverse strutture. Questa sezione fornisce una panoramica delle strutture di rete implementate in un ambiente. Esistono diverse impostazioni che a volte vengono implementate da zero.

In questa sezione viene illustrata un&#39;introduzione ai server proxy, seguita dalle diverse strutture di rete configurate con organizzazioni diverse.

## Server proxy {#proxy-servers}

Un server proxy è un computer dedicato o un sistema software in esecuzione su un computer che funge da intermediario tra un dispositivo endpoint, come un computer, e un altro server da cui un utente o un client richiede un servizio. Il server proxy può esistere nello stesso computer di un server firewall o in un server separato, che inoltra le richieste attraverso il firewall.

Un vantaggio di un server proxy è rappresentato dal fatto che la sua cache può essere utilizzata da tutti gli utenti. Se uno o più siti Internet sono frequentemente richiesti, è probabile che si trovino nella cache del proxy, il che migliorerà il tempo di risposta dell&#39;utente. Un proxy può anche registrare le sue interazioni, il che può essere utile per la risoluzione dei problemi.

## Informazioni sulle impostazioni di rete {#network-setups}

Per implementare una configurazione di rete, è necessario fare riferimento ai seguenti scenari con pro e contro.

Esistono tre tipi principali di configurazione della rete:

1. Configurazione di Internet Access
1. Configurazione della rete mobile
1. Configurazione della rete aziendale chiusa

La tabella seguente illustra i diversi tipi di configurazione di rete con vantaggi e svantaggi:

<table>
 <tbody>
  <tr>
   <td><strong>Configurazione della rete</strong></td>
   <td><strong>Vantaggi</strong></td>
   <td><strong>Svantaggi</strong></td>
  </tr>
  <tr>
   <td><strong>Configurazione di Internet Access</strong></td>
   <td>Facile e semplice da configurareUp<br>Buona scelta per installazioni<br>dedicate di medie dimensioni o di grandi dimensioni<br>Pochi punti di errore<br>Relativamente conveniente<br>Buona scalabilità</td>
   <td>Piano dati Internet appropriato obbligatorio</td>
  </tr>
    <tr>
   <td><strong>Configurazione della rete mobile</strong></td>
   <td>Facile e semplice da configurareUp<br>Buona scelta per installazioni<br>di medie dimensioni o di grandi dimensioniRete dedicata può essere racchiusa<br>Pochi punti di errore<br>Relativamente conveniente<br>Buona scalabilità</br></td>
   <td>Connessione Internet appropriata obbligatoria</td>
  </tr>
    <tr>
   <td><strong>Rete aziendale chiusa</strong></td>
   <td>Elevata flessibilità e scalabilità<br>Altamente sicura grazie alle diverse linee di difesa<br>Reti<br>incapsulate facili da monitorare e mantenere<br>affidabili</td>
   <td>Consigliati specialisti di<br>rete o integratori di sistemi complicati e costosi</td>
  </tr>
  </tr>
 </tbody>
</table>


