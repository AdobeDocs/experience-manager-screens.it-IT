---
title: Monitoraggio del supporto
description: Scopri come monitorare il supporto per la Guida alle best practice di AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Monitoraggio del supporto {#support-monitoring}

Questa sezione fornisce le best practice relative alla gestione delle anomalie dei dispositivi e dei contenuti in un progetto di digital signage.

Il monitoraggio del supporto include:

* **Monitoraggio dei dispositivi**
* **Monitoraggio dei contenuti**

## Monitoraggio dei contenuti {#content-monitoring}

Il monitoraggio dei contenuti consente di risolvere i problemi relativi a contenuti non visualizzati correttamente sullo schermo:

1. Se si verifica un problema a schermo vuoto:

   * Controlla la *anteprima* in modo da poter vedere se il canale mostra una schermata nera.
   * Registra un *lettore chrome locale* (come estensione) sul notebook per visualizzare la schermata e vedere se è visualizzata una schermata nera.
   * Fare clic con il pulsante destro del mouse, esaminare e controllare *registri applicabili*.

   Inoltre, se il problema non si verifica sul lettore locale ma solo sul dispositivo:

   * Controlla la *tipo di file multimediale* (in uso) che potrebbero avere problemi con il dispositivo e confermare se il contenuto è stato scaricato correttamente localmente (interfaccia utente amministratore cancella cache del canale).
   * Includi qualsiasi *registri dispositivo* nel ticket per la risoluzione rapida dei problemi.
   * *Raccogli registri* dal dispositivo dell’AEM.

## Monitoraggio dei dispositivi {#device-monitoring}

Monitoraggio del dispositivo relativo al monitoraggio del dispositivo fisico se si verifica un problema di schermata vuota:

1. Se si verifica un problema a schermo vuoto:

   * Controlla se *visualizzare* è acceso.
   * Controlla se *computer* è acceso e invia un segnale.
   * Clic con il pulsante destro del mouse, controlla e controlla *registri applicabili*.
