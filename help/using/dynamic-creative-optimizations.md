---
title: Attivatori dati
description: Scopri i trigger di dati in AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 261
ht-degree: 0%

---

# Ottimizzazioni Dynamic Creative {#dynamic-creative}

>[!NOTE]
>
>Una delle parti interessate per questa attività è un implementatore di AEM.

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
