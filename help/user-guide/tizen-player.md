---
title: Tizen Player
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
translation-type: tm+mt
source-git-commit: 835da341fcee8e4abb3375c43a0a130d3f79d859
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per  AEM Screens, effettuate le seguenti operazioni:

1. Andate alla pagina dei download [**di**](https://download.macromedia.com/screens/) AEM 6.5 Player per scaricare Tizen Player.

1. Installare il file Tizen Player (.zip) dal computer locale.

## Impostazione del server locale e Estrazione dei file ZIP {#setting-local-server}

Per configurare il server locale e copiare i file estratti, effettuate le seguenti operazioni:

1. Ottenere l&#39;indirizzo IP del computer locale.

   >[!NOTE]
   >È possibile ottenere l&#39;indirizzo IP dal terminale del computer utilizzando i seguenti comandi:
   >* **Mac**: `ifconfig`
   >* **Windows**: `ipconfig`


1. Dal terminale, andate alla stessa directory della cartella del programma di installazione decompressa e verificate che il localhost funzioni.

   >[!NOTE]
   >Per **Mac**, digitate `http://localhost` e verificate che il `http` server sia in esecuzione.

1. Il lettore Tizen scaricherà il programma di installazione dal server locale.

1. Copiate i due file estratti `AEMScreensPlayer.wgt` e `sssp_config.xml` in `/Library/WebServer/Documents`.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Seguire i passaggi indicati di seguito sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens  sul dispositivo:

1. Accedete al dispositivo Samsung e puntate al server localhost.
1. Selezionate **Impostazioni** di avvio URL dalle **Impostazioni** e immettete l&#39;indirizzo IP del server localhost.
1. Installa Web App.
1. Selezionate **Remote** dalla modalità **Sviluppatore**.
1.  AEM Screens Player dovrebbe ora installarsi automaticamente sul dispositivo Samsung.


