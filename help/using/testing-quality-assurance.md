---
title: Test e garanzia della qualità
seo-title: Test e garanzia qualità per  AEM Screens
description: Nella pagina viene descritta la Guida alle procedure ottimali per i test e la garanzia della qualità per  AEM Screens
seo-description: Nella pagina viene descritta la Guida alle procedure ottimali per i test e la garanzia della qualità per  AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# Test e garanzia della qualità {#testing-quality}

>[!NOTE]
>Tipico azionista di questa attività è un integratore A/V.

Man mano che ci avviciniamo all&#39;implementazione effettiva della rete di digital signage, dovremmo creare un piano Test e QA che affronti ogni elemento della rete, compresi tutti i componenti hardware, tutti i componenti software e tutti i componenti di rete.
Nella fase, devono essere costruiti e testati tutti i sistemi di prova.

È necessario creare un elenco di controllo che identifichi tutti i KPI definiti in precedenza e che misuri il risultato finale rispetto a tali indicatori.

>[!NOTE]
>
>Questa fase dovrebbe essere utilizzata anche come strumento per la creazione di una guida di installazione e utente che possa essere successivamente spedita con l&#39;apparecchiatura e mantenuta sul posto per riferimento futuro.

Vanno presi in considerazione i seguenti elementi:

## 1. Considerazioni meccaniche {#mechanical-considerations}

Si raccomandano le seguenti considerazioni meccaniche:

* montaggio a schermo
* supporto del lettore
* ventilazione
* accessori periferici
* gestione dei cavi
* rete dei dispositivi

## 2. Considerazioni sul software {#software-considerations}

Sono consigliate le seguenti considerazioni software:

* registrazione del dispositivo
* pubblicazione multimediale
* riproduzione
* dipendenze del database (definite in precedenza)


## 3. Considerazioni sulla gestione dei dispositivi {#device-management-considerations}

 AEM Screens include un modulo Device Control Center che consente la gestione dei punti finali dell&#39;applicazione del lettore Screens.

Si riferisce a qualsiasi dispositivo hardware del *lettore* in cui è installata l&#39;applicazione del lettore Screens e che è registrato in un&#39;istanza di AEM.
Questo modulo consente di:

1. Monitorare i registri di errore dell’applicazione del lettore
1. Gestione delle schermate remote
1. Gestire i download dei contenuti
1. Gestire i problemi di riavvio dell’applicazione

Per informazioni dettagliate su ***Device Control Center***, consultare [Troubleshooting Device Control Center](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) (Risoluzione dei problemi relativi al Centro di controllo dispositivi) nella **Guida** utente di AEM Screens.

>[!CAUTION]
>
> Non utilizzare Device Control Center per:
> 1. Installare le nuove versioni dell&#39;applicazione del lettore
> 1. Monitoraggio delle risorse a livello di sistema
> 1. Risoluzione degli errori a livello di sistema
> 1. Consenti intervento desktop remoto



>[!NOTE]
>
>  Adobe consiglia di utilizzare piattaforme dedicate di gestione dei dispositivi di terze parti per tutte le distribuzioni.

La piattaforma specifica scelta dipende da una serie di fattori, tra cui il sistema ***operativo*** di destinazione, i requisiti ***del*** progetto e il ***numero di punti*** finali.

Alcuni esempi sono:

* Gestione dispositivi Google Chrome
* TeamViewer
* AirWatch
* 42Gears
* Middleware proprietario dell&#39;integratore AV
