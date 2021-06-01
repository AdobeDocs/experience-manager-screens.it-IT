---
title: Test e garanzia della qualità
seo-title: Test e garanzia della qualità per AEM Screens
description: La pagina descrive la Guida alle best practice per Test e Quality Assurance per AEM Screens
seo-description: La pagina descrive la Guida alle best practice per Test e Quality Assurance per AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# Test e garanzia della qualità {#testing-quality}

>[!NOTE]
>L’azionista tipico di questa attività è un integratore A/V.

Man mano che ci avviciniamo all&#39;effettiva implementazione della rete di digital signage, dovremmo creare un piano di test e controllo qualità che affronti ogni elemento della rete, compresi tutti i componenti hardware, tutti i componenti software e tutti i componenti di rete.
Nella fase, devono essere costruiti e testati tutti i sistemi di prova.

È necessario creare una lista di controllo che identifichi tutti i KPI definiti in precedenza e li misuri risultati finali.

>[!NOTE]
>
>Questa fase dovrebbe essere utilizzata anche come strumento per la creazione di un&#39;installazione e di una guida utente che possa essere successivamente fornita con l&#39;apparecchiatura e conservata sul posto per riferimenti futuri.

Vanno considerati i seguenti elementi:

## 1. Considerazioni meccaniche {#mechanical-considerations}

Si raccomandano le seguenti considerazioni meccaniche:

* montaggio a schermo
* montaggio del lettore
* ventilazione
* periferiche
* gestione dei cavi
* rete dei dispositivi

## 2. Considerazioni sul software {#software-considerations}

Si consiglia di tenere presenti le seguenti considerazioni software:

* registrazione del dispositivo
* pubblicazione multimediale
* riproduzione
* dipendenze del database (definite in precedenza)


## 3. Considerazioni sulla gestione dei dispositivi {#device-management-considerations}

AEM Screens include un modulo Device Control Center che consente la gestione degli endpoint dell&#39;applicazione Screens Player.

Si riferisce a qualsiasi dispositivo hardware *player* che ha installato l&#39;applicazione Screens Player e viene registrato in un&#39;istanza di AEM.
Questo modulo consente di:

1. Registri degli errori dell&#39;applicazione del lettore di monitor
1. Gestione delle schermate remote
1. Gestire i download dei contenuti
1. Gestire i problemi di riavvio dell&#39;applicazione

Per informazioni dettagliate su ***Centro controllo dispositivi***, consulta [Centro controllo dispositivi per la risoluzione dei problemi](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) in **Guida utente di AEM Screens**.

>[!CAUTION]
>
> Non utilizzare Device Control Center per:
> 1. Installa nuove versioni dell&#39;applicazione player
> 1. Monitoraggio delle risorse a livello di sistema
> 1. Risoluzione dei problemi relativi agli errori a livello di sistema
> 1. Consenti intervento desktop remoto



>[!NOTE]
>
> Adobe consiglia di utilizzare piattaforme dedicate di gestione dei dispositivi di terze parti per tutte le distribuzioni.

La piattaforma specifica scelta dipende da una serie di fattori, tra cui il ***sistema operativo di destinazione***, i ***requisiti del progetto*** e il ***numero di punti finali***.

Alcuni esempi sono:

* Gestione dispositivi Google Chrome
* TeamViewer
* AirWatch
* 42Ingranaggi
* Middleware proprietario dell&#39;integratore AV
