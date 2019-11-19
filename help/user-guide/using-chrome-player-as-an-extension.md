---
title: Utilizzo di Chrome Player come estensione
seo-title: Utilizzo di Chrome Player come estensione
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Utilizzo di Chrome Player come estensione {#using-chrome-player}

Il lettore ChromeOS può essere installato come il plugin Chrome Browser in modalità sviluppatore senza richiedere un dispositivo effettivamente chrome player.

>[!CAUTION]
>
> L'utilizzo di Chrome Player come estensione per la risoluzione dei problemi è consigliato per dimostrazioni rapide, debugging e anche per risolvere i problemi dei clienti. Questo meccanismo non dovrebbe essere utilizzato per le installazioni di produzione che richiedono la modalità Kiosk e la gestione centrale.

Seguite questa pagina per informazioni sull'installazione del lettore Chrome come estensione del browser.

1. Clicca qui per scaricare l'ultimo Chrome Player.

1. Decomprimete il file e salvatelo su disco.

1. Aprite il browser Chrome e fate clic sul menu a 3 punti e selezionate **Altri strumenti** da **Estensioni** situato nell'angolo superiore destro oppure andate direttamente a `chrome://extensions`.

1. Attivate la modalità **Sviluppatore** dall'angolo in alto a destra.

1. Fare clic su **Carica non imballato** dall'angolo in alto a sinistra e caricare Chrome Player decompresso.

1. Controlla il plug-in di AEM Screens Chrome Player se è disponibile nell'elenco delle estensioni.

1. Aprite una nuova scheda e fate clic sull'icona App dall'angolo in alto a sinistra oppure passate direttamente a `chrome://apps`.

1. Fate clic sul plug-in **di** AEM Screens per avviare Chrome Player.
   >[!NOTE]
   >
   > Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premere **esc** per uscire dalla modalità a schermo intero.


## Suggerimenti avanzati per il debug {#advanced-debugging-tips}

1. Una volta che il lettore ha scaricato localmente il contenuto, è possibile sfogliare il contenuto scaricato localmente accedendo `http://localhost:24502`a.

   >[!NOTE]
   >
   > Se l'URL di cui sopra non funziona significa che al lettore non viene assegnato uno schermo o che il contenuto non è stato scaricato correttamente. Controllare la scheda di rete per la configurazione del lettore JSON per verificare se i dettagli corretti sono ottenuti dal lettore e per eventuali problemi di rete nel download.

1. È possibile fare clic con il pulsante destro del mouse e ispezionare tre livelli del lettore cromo
   **Debug del contenuto**: Fare clic con il pulsante destro del mouse ed esaminare il contenuto per eseguire il debug del contenuto in esecuzione (nel menu contestuale dovrebbe essere presente un elemento denominato "Esamina")

   **Debug firmware**: Visualizzare l'interfaccia utente di amministrazione, quindi fare clic con il pulsante destro del mouse ed esaminare per eseguire il debug del codice firmware (lettore) (dovrebbe essere disponibile un'opzione per ispezionare e ispezionare la pagina di background e simulare il riavvio del browser)

   **Debug pagina** di sfondo: Visualizzate l'interfaccia utente di amministrazione, quindi fate clic con il pulsante destro del mouse ed esaminate la pagina in background (per servizi in background come il server http)

## Aggiornamento dell’estensione del lettore {#upgrading-player}

Seguire i passaggi indicati di seguito per aggiornare l'estensione del lettore se viene rilasciata una nuova versione del lettore. Potete inoltre seguire le istruzioni riportate di seguito per testare gli scenari di aggiornamento:

1. Chiudi tutte le istanze di chrome e lettore in esecuzione
1. Rinominare la vecchia cartella con i file del lettore
1. Estrarre il nuovo file ZIP nella stessa posizione della cartella precedente
1. Avvia Chrome e passa a `chrome://extensions`
1. Controllare l'icona del lettore e fare clic sul pulsante di aggiornamento o ricarica