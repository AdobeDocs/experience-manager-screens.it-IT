---
title: Tizen Player
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
translation-type: tm+mt
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per  AEM Screens, effettuate le seguenti operazioni:

1. Andate alla pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installare il file Tizen Player (.zip) dal computer locale.

## Configurazione del server locale ed estrazione dei file ZIP {#setting-local-server}

Per configurare il server locale e copiare i file estratti, effettuate le seguenti operazioni:

1. Ottenere l&#39;indirizzo IP del computer locale.
   >[!NOTE]
   >Per informazioni su come abilitare il server locale sulla piattaforma, consulta la documentazione ufficiale.

1. Dal terminale, andate alla stessa directory della cartella del programma di installazione decompressa e verificate che il localhost funzioni.

1. Il lettore Tizen scaricherà il programma di installazione dal server locale.

1. Copiate i due file estratti come `AEMScreensPlayer.wgt` e `sssp_config.xml` nella directory principale del server locale.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Seguire i passaggi indicati di seguito sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens  sul dispositivo:

1. Vai al tuo dispositivo Samsung.

1. Fare clic sul pulsante **Home** utilizzando il telecomando del dispositivo e selezionare **Impostazioni di avvio URL**.

1. Immettete l&#39;indirizzo IP del server localhost.

1. Selezionare **Remote** dalla **Modalità Sviluppatore**.

1. Fare clic sul pulsante **Home** dal telecomando del dispositivo e selezionare **URL Launcher**.

1.  AEM Screens Player dovrebbe ora installare e avviare automaticamente sul dispositivo Samsung.



