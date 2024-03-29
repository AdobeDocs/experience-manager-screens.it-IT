---
title: Test e garanzia della qualità
seo-title: Testing and Quality Assurance for AEM Screens
description: La pagina descrive la Guida alle best practice per test e controllo qualità per AEM Screens
seo-description: The page describes Testing and Quality Assurance for AEM Screens Best Practices Guide
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# Test e garanzia della qualità {#testing-quality}

>[!NOTE]
>Questa attività è in genere gestita da un integratore A/V.

Man mano che ci avviciniamo all&#39;effettiva implementazione della rete di digital signage, dobbiamo creare un piano di test e controllo qualità che affronti ogni elemento della rete, inclusi tutti i componenti hardware, software e di rete.
Durante la fase, si dovrebbero costruire e collaudare completamente interi sistemi di test.

È necessario creare un elenco di controllo che identifichi tutti gli indicatori KPI definiti in precedenza e misuri il risultato finale rispetto a tali indicatori.

>[!NOTE]
>
>Questa fase dovrebbe essere utilizzata anche come strumento per la creazione di un manuale di installazione e di istruzioni per l&#39;uso, che potrà essere successivamente fornito con l&#39;apparecchiatura e conservato in loco per riferimento futuro.

Devono essere presi in considerazione i seguenti elementi:

## 1. Considerazioni meccaniche {#mechanical-considerations}

Si raccomandano le seguenti considerazioni meccaniche:

* montaggio su display
* installazione del lettore
* ventilazione
* accessori periferici
* gestione dei cavi
* rete di dispositivi

## 2. Considerazioni sul software {#software-considerations}

Si consiglia di tenere presenti le seguenti considerazioni sul software:

* registrazione dispositivo
* pubblicazione di contenuti multimediali
* Riproduzione
* dipendenze del database (definite in precedenza)


## 3. Considerazioni sulla gestione dei dispositivi {#device-management-considerations}

AEM Screens include un modulo Device Control Center che consente la gestione degli endpoint dell’applicazione di riproduzione Screens.

Si riferisce a qualsiasi *player* dispositivo hardware su cui è installata l’applicazione di riproduzione Screens e che è registrato in un’istanza di AEM.
Questo modulo consente di:

1. Registri di errore dell’applicazione del lettore di monitor
1. Gestione delle schermate remote
1. Gestire i download dei contenuti
1. Gestire i problemi di riavvio dell’applicazione

Per informazioni dettagliate su ***Centro controllo dispositivi***, fare riferimento a [Risoluzione dei problemi di Device Control Center](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) in **Guida utente di AEM Screens**.

>[!CAUTION]
>
> Non utilizzare Centro controllo dispositivi per:
> 1. Installare nuove versioni dell’applicazione del lettore
> 1. Monitorare le risorse a livello di sistema
> 1. Risolvere i problemi relativi agli errori a livello di sistema
> 1. Consenti intervento desktop remoto



>[!NOTE]
>
> L’Adobe consiglia di utilizzare piattaforme di gestione dei dispositivi di terze parti dedicate per tutte le distribuzioni.

La piattaforma specifica scelta dipende da una serie di fattori, tra cui ***sistema operativo di destinazione***, ***requisiti del progetto*** e ***numero di punti finali***.

Alcuni esempi sono:

* Gestione dei dispositivi Google Chrome
* TeamViewer
* AirWatch
* 42Gears
* Middleware proprietario di AV Integrator
