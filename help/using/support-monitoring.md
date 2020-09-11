---
title: Monitoraggio del supporto
seo-title: Monitoraggio del supporto per  AEM Screens
description: La pagina descrive la Guida alle procedure ottimali per il monitoraggio del supporto  AEM Screens
seo-description: La pagina descrive la Guida alle procedure ottimali per il monitoraggio del supporto  AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Monitoraggio del supporto {#support-monitoring}

Questa sezione descrive le procedure ottimali per la gestione delle anomalie dei dispositivi e dei contenuti in un progetto di digital signage.

Il monitoraggio del supporto include:

* **Monitoraggio dispositivo**
* **Monitoraggio dei contenuti**

## Monitoraggio dei contenuti {#content-monitoring}

Il monitoraggio dei contenuti consente di risolvere i problemi relativi al contenuto non visualizzato correttamente sullo schermo:

1. Se si verifica un problema di schermata vuota:

   * Controlla *anteprima* per vedere se il canale mostra una schermata nera
   * Registrare un lettore *cromo* locale (come estensione) sul computer portatile su quel display e vedere se mostra una schermata nera.
   * Fare clic con il pulsante destro del mouse ed esaminare i registri *applicabili*.

   Inoltre, se ciò non si verifica sul lettore locale ma solo sul dispositivo:

   * Controllate il tipo *di* supporto (utilizzato) che potrebbe presentare problemi sul dispositivo e verificate se il contenuto è stato scaricato correttamente localmente (la cache del canale dell&#39;interfaccia utente amministratore è stata cancellata).
   * Per la risoluzione rapida dei problemi, includete tutti i registri *del* dispositivo nel ticket.
   * *Raccogliere i registri* dal dispositivo da AEM.


## Monitoraggio dispositivo {#device-monitoring}

Monitoraggio del dispositivo correlato al monitoraggio del dispositivo fisico in caso di problemi relativi allo schermo vuoto:

1. Se si verifica un problema di schermata vuota:

   * Verificare se il *display* è acceso.
   * Verificare se il *computer* è acceso e invia il segnale.
   * Fare clic con il pulsante destro del mouse, ispezionare e controllare i registri ** applicabili.

