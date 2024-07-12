---
title: Attivatori dati
description: Scopri i trigger di dati in AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Ottimizzazioni creative dinamiche {#dynamic-creative}

>[!NOTE]
>
>Un soggetto interessato tipico per questa attività è un implementatore AEM.

**Dynamic Creative Optimization**, o DCO, viene utilizzato per creare esperienze di segnaletica digitale che riflettono le circostanze specifiche di una determinata posizione in un dato momento e per un determinato utente.

Questo utilizzo viene anche definito &quot;appiattimento lato client&quot; dei contenuti.

Il ragionamento è garantire che ogni dispositivo di riproduzione o endpoint possa utilizzare set di dati per determinare il contenuto migliore da riprodurre automaticamente in base a vari fattori diversi.

Questa funzionalità elimina la necessità di un intervento umano costante durante l’authoring dei contenuti. Consente inoltre di ridurre il costo totale di proprietà per il funzionamento della rete e rende le esperienze digitali più pertinenti, contestuali ed efficaci.

Alcuni esempi:

* utilizzo del livello di inventario corrente dei prodotti di funzionalità
* temperatura esterna o tempo atmosferico
* la presenza di una campagna pubblicitaria dei media locali
* traffico web e persino eventi locali come quando un cliente sceglie un prodotto per esaminarlo

Tutti questi esempi e altro ancora possono essere utilizzati per fornire un livello più elevato di contesto e personalizzazione.

Una strategia di merchandising visivo che includa DCO può aumentare notevolmente il numero di visualizzatori di rete.

Esistono due tipi principali di trigger di dati:

* **Attivatori dati locali**: questi attivatori dati sono locali sul dispositivo. Ad esempio, se hai toccato lo schermo, viene attivato un sensore che attiva una risorsa di dati locale o un interruttore di canale.
* **Trigger dati remoti**: questo problema riguardava un cambio di canale attivato dai dati o un cambio di risorsa basato sui valori restituiti da un&#39;API del servizio Web.
