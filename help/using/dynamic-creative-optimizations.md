---
title: Attivatori dati
description: Scopri i trigger di dati in AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
source-git-commit: a8055c5f859e401f7b1da4f5d95f1268dee243ad
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Ottimizzazioni creative dinamiche {#dynamic-creative}

>[!NOTE]
>
>Questa attività è in genere gestita da un implementatore AEM.

**Dynamic Creative Optimization** o DCO, viene utilizzato per creare esperienze di segnaletica digitale che riflettono le circostanze uniche di una determinata posizione in un dato momento e per un dato utente.

Questa operazione è anche definita appiattimento lato client dei contenuti.

Il motivo è garantire che ogni dispositivo di riproduzione o endpoint possa utilizzare set di dati per determinare automaticamente il contenuto migliore da riprodurre in base a vari fattori diversi.

Questo elimina la necessità di un intervento umano costante durante l’authoring dei contenuti. Consente inoltre di ridurre il costo totale di proprietà per il funzionamento della rete e rende le esperienze digitali più pertinenti, contestuali ed efficaci.

Alcuni esempi:

* utilizzo del livello di inventario corrente dei prodotti di caratteristiche
* temperatura esterna o tempo atmosferico
* la presenza di una campagna pubblicitaria dei media locali
* traffico web e persino eventi locali come quando un cliente sceglie un prodotto per esaminarlo

Tutti questi e altri possono essere utilizzati per fornire un livello più elevato di contesto e personalizzazione.

Una strategia di merchandising visivo che includa DCO può aumentare notevolmente il numero di visualizzatori di rete.

Esistono due tipi principali di trigger di dati:

* **Trigger dati locali**: questi trigger di dati sono locali sul dispositivo. Ad esempio, se hai toccato lo schermo, viene attivato un sensore che attiva la risorsa dati locale o l’interruttore del canale.
* **Attivatori di dati remoti**: questo includeva l’attivazione di un cambio di canale da parte dei dati o di un cambio di risorsa basato sui valori restituiti da un’API di servizio web.
