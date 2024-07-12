---
title: Monitoraggio del supporto
description: Scopri come monitorare il supporto per la Guida alle best practice di AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
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

   * Controlla l&#39;*anteprima* per verificare se sul canale è visualizzata una schermata nera.
   * Registra un *lettore Chrome locale* (come estensione) sul tuo laptop per visualizzarlo e verificare se è visualizzata una schermata nera.
   * Fare clic con il pulsante destro del mouse e verificare e controllare i *registri applicabili*.

   Inoltre, se il problema non si verifica sul lettore locale ma solo sul dispositivo:

   * Controllare il *tipo di supporto* (in uso) che potrebbe presentare problemi sul dispositivo e verificare che il contenuto sia stato scaricato correttamente localmente (Admin UI clear channel cache).
   * Includi *registri dispositivi* nel ticket per una rapida risoluzione dei problemi.
   * *Raccogli i registri* dal dispositivo da AEM.

## Monitoraggio dei dispositivi {#device-monitoring}

Monitoraggio del dispositivo relativo al monitoraggio del dispositivo fisico se si verifica un problema di schermata vuota:

1. Se si verifica un problema a schermo vuoto:

   * Verificare che *display* sia acceso.
   * Verificare che il *computer* sia acceso e stia inviando un segnale.
   * Fare clic con il pulsante destro del mouse, verificare e controllare *registri applicabili*.
