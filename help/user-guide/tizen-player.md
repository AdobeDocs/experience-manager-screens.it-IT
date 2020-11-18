---
title: Tizen Player
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
translation-type: tm+mt
source-git-commit: b439cfab068dcbbfab602ad8d31aaa2781bde805
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per  AEM Screens, effettuate le seguenti operazioni:

1. Andate alla pagina dei download [**di**](https://download.macromedia.com/screens/) AEM 6.5 Player per scaricare Tizen Player.

1. Installare il file Tizen Player (.zip) dal computer locale.

1. Ottenere l&#39;indirizzo IP del computer locale.

   >[!NOTE]
   >Per **Mac** e **Windows** digitare il comando `ifconfig` nel terminale.

1. Dal terminale, andate alla stessa directory della cartella del programma di installazione decompressa e verificate che il localhost funzioni.

   >[!NOTE]
   >Per **Mac**, digitate `http://localhost` e verificate che il `http` server sia in esecuzione.

1. Il lettore Tizen scaricherà il programma di installazione dal server locale.

1. Copiate i due file estratti `AEMScreensPlayer.wgt` e `sssp_config.xml` in `/Library/WebServer/Documents`.

### Aggiornamenti di configurazione sul dispositivo SamSung {#config-updates}

Seguire i passaggi indicati di seguito sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens  sul dispositivo:

1. Fare clic sul pulsante **Home** dal telecomando Samsung.
1. Selezionate **URL Launcher** dalle **impostazioni**.
1. Selezionate **Remote** dalla modalità Sviluppatore.
1. Installate l&#39;app Web e immettete l&#39;indirizzo IP del computer.
 AEM Screens Player deve essere installato automaticamente sul dispositivo Samsung.


