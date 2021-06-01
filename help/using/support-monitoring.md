---
title: Monitoraggio del supporto
seo-title: Monitoraggio del supporto per AEM Screens
description: La pagina descrive la Guida alle best practice per il monitoraggio del supporto per AEM Screens
seo-description: La pagina descrive la Guida alle best practice per il monitoraggio del supporto per AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Monitoraggio del supporto {#support-monitoring}

Questa sezione fornisce best practice relative alla gestione delle anomalie nei dispositivi e nei contenuti in un progetto di digital signage.

Il monitoraggio del supporto include:

* **Monitoraggio dei dispositivi**
* **Monitoraggio dei contenuti**

## Monitoraggio dei contenuti {#content-monitoring}

Il monitoraggio dei contenuti consente di risolvere i problemi relativi al contenuto non visualizzato correttamente sullo schermo:

1. Se si verifica un problema relativo alla schermata vuota:

   * Controlla *anteprima* per vedere se il canale sta mostrando una schermata nera
   * Registra su quel display un *lettore chrome locale* (come estensione) e controlla se mostra uno schermo nero.
   * Fai clic con il pulsante destro del mouse e controlla *registri applicabili*.

   Inoltre, se questo non accade sul lettore locale ma solo sul dispositivo:

   * Controlla *il tipo di supporto* (in uso) che potrebbe avere problemi su quel dispositivo e conferma se il contenuto è stato scaricato correttamente localmente (la cache del canale cancellata dall&#39;interfaccia utente amministratore).
   * Includi tutti i *log dispositivo* nel ticket per la risoluzione rapida dei problemi.
   * *Raccogli* accessi dal dispositivo da AEM.


## Monitoraggio dei dispositivi {#device-monitoring}

Monitoraggio del dispositivo relativo al monitoraggio del dispositivo fisico in caso di problemi di schermo vuoto:

1. Se si verifica un problema relativo alla schermata vuota:

   * Controlla se il *display* è acceso.
   * Controlla se il *computer* è acceso e sta inviando il segnale.
   * Fai clic con il pulsante destro del mouse, controlla i *registri applicabili*.

