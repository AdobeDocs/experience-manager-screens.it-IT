---
title: Utilizzo di Chrome Player come estensione
seo-title: Utilizzo di Chrome Player come estensione
description: Segui questa pagina per scoprire come installare chrome player come estensione del browser.
seo-description: 'null'
feature: Amministrazione di schermi
role: Administrator
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---


# Utilizzo di Chrome Player come estensione {#using-chrome-player}

ChromeOS Player può essere installato come plugin del browser Chrome in modalità sviluppatore senza richiedere l&#39;effettivo dispositivo chrome player.

>[!CAUTION]
>
> L’utilizzo di Chrome Player come estensione per la risoluzione dei problemi è consigliato per dimostrazioni rapide, il debug e anche per risolvere i problemi dei clienti. Questo meccanismo non deve essere utilizzato per le distribuzioni di produzione che richiederebbero la modalità chiosco e la gestione centrale.

Segui questa pagina per scoprire come installare chrome player come estensione del browser.

1. Fai clic [qui](https://download.macromedia.com/screens/) per scaricare il lettore Chrome più recente.

1. Decomprimere e salvarlo sul disco.

1. Apri il browser Chrome e fai clic sul menu a 3 punti e seleziona **Altri strumenti** da **Estensioni** nell&#39;angolo in alto a destra o passa direttamente a `chrome://extensions`.

1. Attiva la modalità **Sviluppatore** dall&#39;angolo in alto a destra.

1. Fai clic su **Carica deimballato** dall&#39;angolo in alto a sinistra e carica il lettore Chrome decompresso.

1. Controlla il plugin AEM Screens Chrome Player se è disponibile nell&#39;elenco delle estensioni.

1. Apri una nuova scheda e fai clic sull’icona App dall’angolo in alto a sinistra oppure passa direttamente a `chrome://apps`.

1. Fai clic su **AEM Screens Plugin** per avviare Chrome Player.
   >[!NOTE]
   >
   > Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premere **esc** per uscire dalla modalità a schermo intero.


## Suggerimenti avanzati per il debug {#advanced-debugging-tips}

1. Una volta che il lettore ha scaricato localmente il contenuto, è possibile sfogliare quello scaricato localmente andando in `http://localhost:24502`.

   >[!NOTE]
   >
   > Se l’URL di cui sopra non funziona significa che al lettore non è stata assegnata una visualizzazione o che il contenuto non è stato scaricato correttamente. Controlla la scheda di rete per la configurazione del lettore JSON per vedere se il lettore ottiene i dettagli corretti e per eventuali problemi di rete nel download.

1. È possibile fare clic con il pulsante destro del mouse e ispezionare tre livelli del chrome player
   **Debug del contenuto**: Fai clic con il pulsante destro del mouse ed esamina il contenuto per eseguire il debug del contenuto in esecuzione (dovrebbe essere presente un singolo elemento denominato &quot;Inspect&quot; nel menu di scelta rapida)

   **Debug del firmware**: Visualizza l&#39;interfaccia utente amministratore e fai clic con il pulsante destro del mouse e controlla per eseguire il debug del codice del firmware (lettore) (dovrebbe essere presente un&#39;opzione per controllare e controllare la pagina di background e per simulare il riavvio del browser)

   **Pagina** in background di debug: Visualizza l’interfaccia utente amministratore, quindi fai clic con il pulsante destro del mouse ed esamina la pagina in background (per i servizi in background come il server http)

## Aggiornamento dell&#39;estensione del lettore {#upgrading-player}

Segui i passaggi seguenti per aggiornare l’estensione del lettore se viene rilasciata una nuova versione del lettore. Puoi anche seguire le istruzioni riportate di seguito per testare gli scenari di aggiornamento:

1. Chiudi tutte le istanze di Chrome e Player in esecuzione
1. Rinomina la vecchia cartella con i file del lettore
1. Estrarre il nuovo file ZIP nella stessa posizione della cartella precedente
1. Avvia Chrome e passa a `chrome://extensions`
1. Controlla l&#39;icona del lettore e fai clic sul pulsante aggiorna o ricarica