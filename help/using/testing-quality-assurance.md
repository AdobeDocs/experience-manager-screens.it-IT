---
title: Test e garanzia della qualità
description: Scopri i test e il controllo della qualità per AEM Screens nella Guida alle best practice.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Test e garanzia della qualità {#testing-quality}

>[!NOTE]
>Una delle parti interessate per questa attività è un integratore audio-video.

Man mano che ti avvicini all&#39;implementazione della rete di digital signage, crea un piano di test e controllo qualità che affronti ogni elemento della rete, inclusi tutti i componenti hardware, software e di rete.
Durante la fase, si dovrebbero costruire e collaudare completamente interi sistemi di test.

È necessario creare un elenco di controllo che identifichi tutti i KPI definiti in precedenza e ne misuri i risultati finali.

>[!NOTE]
>
>Questa fase deve essere utilizzata anche come strumento per la creazione di un&#39;installazione e di una guida utente. Entrambi possono essere successivamente spediti con l&#39;apparecchiatura e tenuti in loco per riferimento futuro.

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

Si riferisce a qualsiasi dispositivo hardware *player* su cui è installata l&#39;applicazione del lettore Screens e che è registrato in un&#39;istanza dell&#39;AEM.
Questo modulo consente di:

1. Registri di errore dell’applicazione del lettore di monitor
1. Gestione schermate remote
1. Gestire i download dei contenuti
1. Gestire i problemi di riavvio dell’applicazione

Per informazioni dettagliate su ***Centro controllo dispositivi***, vedere [Risoluzione dei problemi di Centro controllo dispositivi](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) nella **Guida utente di AEM Screens**.

>[!CAUTION]
>
>Non utilizzare Centro controllo dispositivi per:
>
>* Installare nuove versioni dell’applicazione del lettore
>* Monitorare le risorse a livello di sistema
>* Risolvere i problemi relativi agli errori a livello di sistema
>* Consenti intervento desktop remoto


>[!NOTE]
>
> L’Adobe consiglia di utilizzare piattaforme di gestione dei dispositivi di terze parti dedicate per tutte le distribuzioni.

La piattaforma specifica scelta dipende da diversi fattori, tra cui ***sistema operativo di destinazione***, ***requisiti progetto*** e ***numero di endpoint***.

Di seguito sono riportati alcuni esempi:

* Gestione dispositivi Chrome Google
* TeamViewer
* AirWatch
* `42Gears`
* Middleware con integrazione audio-video proprietaria
