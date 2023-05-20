---
title: Monitoraggio del supporto
seo-title: Support Monitoring for AEM Screens
description: La pagina descrive il monitoraggio del supporto per la guida alle best practice di AEM Screens
seo-description: The page describes Support Monitoring for AEM Screens Best Practices Guide
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '209'
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

   * Verifica *anteprima* per verificare se sul canale è visualizzata una schermata nera
   * Registra un *lettore chrome locale* (come estensione) sul laptop per visualizzare la schermata e vedere se appare una schermata nera.
   * Clic con il pulsante destro del mouse e verifica *registri applicabili*.

   Inoltre, se questo problema non si verifica sul lettore locale ma solo sul dispositivo:

   * Verifica *tipo di file multimediale* (in uso) che potrebbero avere problemi sul dispositivo e confermare se il contenuto è stato scaricato correttamente localmente (interfaccia utente amministratore cancella cache del canale).
   * Includi qualsiasi *registri dispositivo* nel ticket per la risoluzione rapida dei problemi.
   * *Raccogli registri* dal dispositivo dell’AEM.


## Monitoraggio dei dispositivi {#device-monitoring}

Monitoraggio del dispositivo relativo al monitoraggio del dispositivo fisico se si verifica un problema di schermata vuota:

1. Se si verifica un problema a schermo vuoto:

   * Controlla se *visualizzare* è acceso.
   * Controlla se *computer* è acceso e sta inviando il segnale.
   * Clic destro, verifica e controlla *registri applicabili*.
