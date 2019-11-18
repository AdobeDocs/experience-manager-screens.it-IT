---
title: Test e garanzia della qualità
seo-title: Verifica e garanzia qualità per AEM Screens
description: La pagina descrive la Guida alle procedure ottimali per la verifica e la garanzia della qualità per AEM Screens.
seo-description: La pagina descrive la Guida alle procedure ottimali per la verifica e la garanzia della qualità per AEM Screens.
translation-type: tm+mt
source-git-commit: 12b1cc4f2b359742966c2073d233b0113459e2de

---


# Test e garanzia della qualità {#testing-quality}

>[!NOTE]
>
>Tipico azionista di questa attività è un integratore A/V.

Man mano che ci avviciniamo all'implementazione effettiva della rete di digital signage, dovremmo creare un piano Test e QA che affronti ogni elemento della rete, compresi tutti i componenti hardware, tutti i componenti software e tutti i componenti di rete.
Nella fase, devono essere costruiti e testati tutti i sistemi di prova.

È necessario creare un elenco di controllo che identifichi tutti i KPI definiti in precedenza e che misuri il risultato finale rispetto a tali indicatori.

Vanno considerati i seguenti elementi:

## 1. Considerazioni meccaniche {#mechanical-considerations}

Si raccomanda quanto segue:

* montaggio a schermo
* supporto del lettore
* ventilazione
* periferiche
* gestione dei cavi
* rete dei dispositivi

## 2. Considerazioni software {#software-considerations}

Sono consigliate le seguenti considerazioni software:

* registrazione del dispositivo
* pubblicazione multimediale
* riproduzione
* dipendenze del database (definite in precedenza)

>[!NOTE]
> Questa fase dovrebbe essere utilizzata anche come strumento per la creazione di una guida di installazione e utente che possa essere successivamente spedita con l'apparecchiatura e mantenuta sul posto per riferimento futuro.

## 3. Considerazioni sulla gestione dei dispositivi {#device-management-considerations}


AEM Screens include un modulo Device Control Center che consente la gestione dei punti finali dell'applicazione del lettore Screens.

Si riferisce a qualsiasi dispositivo hardware del *lettore* in cui è installata l’applicazione del lettore Screens e che è registrato in un’istanza di AEM.
Questo modulo consente di:

1. Monitorare i registri degli errori dell'applicazione
1. Gestione delle schermate remote
1. Gestire i download dei contenuti
1. Riavvio dell'applicazione

>[!CAUTION]
> È NECESSARIO NON UTILIZZARE Device Control Center PER:
>
> 1. Installare le nuove versioni dell'applicazione del lettore
> 1. Monitoraggio delle risorse a livello di sistema
> 1. Configurare le configurazioni a livello di sistema
> 1. Consente l'intervento del desktop remoto.



>[!NOTE]
> Adobe consiglia di utilizzare piattaforme dedicate di gestione dei dispositivi di terze parti per tutte le distribuzioni.

La piattaforma specifica scelta dipende da una serie di fattori, tra cui il sistema ***operativo*** di destinazione, i requisiti ***del*** progetto e il ***numero di punti*** finali.

Alcuni esempi sono:

* Gestione dispositivi Google Chrome
* TeamViewer
* AirWatch42
* Ingranaggi
* Soti