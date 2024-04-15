---
title: Utilizzo di Chrome Player come estensione
description: Scopri come installare il lettore chrome come estensione del browser per AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Utilizzo di Chrome Player come estensione {#using-chrome-player}

Il lettore ChromeOS può essere installato come plug-in del browser Chrome in modalità sviluppatore senza richiedere il dispositivo effettivo del lettore Chrome.

>[!CAUTION]
>
> L’utilizzo di Chrome Player come estensione per la risoluzione dei problemi è consigliato per le demo rapide, il debug e anche per la risoluzione dei problemi dei clienti. Non utilizzare questo meccanismo per implementazioni in produzione che richiederebbero la modalità chiosco e la gestione centralizzata.

Segui questa pagina per informazioni sull’installazione del lettore chrome come estensione del browser.

1. Seleziona [qui](https://download.macromedia.com/screens/) per scaricare il lettore Chrome più recente.

1. Decomprimi e salva su disco.

1. Apri il browser Chrome, seleziona il menu con 3 puntini e fai clic su **Altri strumenti** da **Estensioni** nell’angolo in alto a destra o passa direttamente a `chrome://extensions`.

1. Accendere il **Sviluppatore** dall&#39;angolo superiore destro.

1. Seleziona **Carica decompresso** dall’angolo in alto a sinistra e carica Chrome Player decompresso.

1. Controlla il plug-in AEM Screens Chrome Player se è disponibile nell’elenco delle estensioni.

1. Apri una nuova scheda e seleziona l’icona App dall’angolo in alto a sinistra, oppure passa direttamente a `chrome://apps`.

1. Seleziona **Plug-in AEM Screens** in modo da poter avviare Chrome Player.

   >[!NOTE]
   >
   > Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premi **Esc** per uscire dalla modalità a tutto schermo.


## Suggerimenti per il debug avanzato {#advanced-debugging-tips}

1. Quando il lettore ha scaricato il contenuto localmente, puoi sfogliare il contenuto scaricato localmente accedendo a `http://localhost:24502`.

   >[!NOTE]
   >
   > Se l’URL indicato sopra non funziona, significa che al lettore non è assegnata una visualizzazione o che il contenuto non è stato scaricato correttamente. Controlla la scheda di rete per il JSON di configurazione del lettore per vedere se il lettore ottiene i dettagli corretti e per eventuali problemi di rete nel download.

1. Fare clic con il pulsante destro del mouse e controllare tre livelli del lettore Chrome.
   **Debug del contenuto**: fai clic con il pulsante destro del mouse e controlla il contenuto per eseguire il debug del contenuto in esecuzione (nel menu di scelta rapida dovrebbe essere presente un singolo elemento denominato &quot;Inspect&quot;)

   **Debug del firmware**: visualizza l’interfaccia utente di amministrazione, quindi fai clic con il pulsante destro del mouse e controlla per eseguire il debug del codice firmware(player). Dovrebbe essere disponibile un’opzione per esaminare e controllare la pagina di sfondo e simulare il riavvio del browser.

   **Pagina di sfondo debug**: visualizza l’interfaccia utente di amministrazione, quindi fai clic con il pulsante destro del mouse e controlla la pagina di sfondo (per i servizi in background come http server).

## Aggiornamento dell&#39;estensione del lettore {#upgrading-player}

Se viene rilasciata una nuova versione del lettore, segui i passaggi indicati di seguito per aggiornare l’estensione del lettore. Puoi anche seguire le istruzioni riportate di seguito per verificare gli scenari di aggiornamento:

1. Chiudere tutte le istanze di Chrome e del lettore in esecuzione
1. Rinomina la vecchia cartella con i file del lettore
1. Estrai il nuovo file ZIP nella stessa posizione della cartella precedente
1. Avvia Chrome e passa a `chrome://extensions`
1. Seleziona l’icona del lettore e il pulsante Aggiorna o ricarica
