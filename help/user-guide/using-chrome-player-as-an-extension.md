---
title: Utilizzo di Chrome Player come estensione
description: Scopri come installare il lettore Chrome come estensione del browser per AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Utilizzo di Chrome Player come estensione {#using-chrome-player}

Il lettore ChromeOS può essere installato come plug-in del browser Chrome in modalità sviluppatore senza richiedere un dispositivo lettore Chrome effettivo.

>[!CAUTION]
>
> L’utilizzo del lettore Chrome come estensione per la risoluzione dei problemi è consigliato per le demo rapide, il debug e anche per la risoluzione dei problemi dei clienti. Non utilizzare questo meccanismo per implementazioni in produzione che richiederebbero la modalità chiosco e la gestione centralizzata.

Segui questa pagina per informazioni sull’installazione del lettore Chrome come estensione del browser.

1. Fai clic [qui](https://download.macromedia.com/screens/) per scaricare il lettore Chrome più recente.

1. Decomprimi e salva su disco.

1. Apri il browser Chrome e fai clic sul menu con tre punti, quindi fai clic su **Altri strumenti** da **Estensioni** nell&#39;angolo in alto a destra oppure passa direttamente a `chrome://extensions`.

1. Attiva la modalità **Sviluppatore** dall&#39;angolo superiore destro.

1. Fai clic su **Carica decompresso** dall&#39;angolo in alto a sinistra e carica il lettore Chrome decompresso.

1. Controlla il plug-in del lettore AEM Screens Chrome se è disponibile nell’elenco delle estensioni.

1. Apri una nuova scheda e fai clic sull&#39;icona App in alto a sinistra, oppure passa direttamente a `chrome://apps`.

1. Fai clic su **AEM Screens Plugin** per avviare il lettore Chrome.

   >[!NOTE]
   >
   > Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premere **Esc** per uscire dalla modalità a schermo intero.


## Suggerimenti per il debug avanzato {#advanced-debugging-tips}

1. Quando il lettore ha scaricato il contenuto localmente, è possibile sfogliare il contenuto scaricato localmente scegliendo `http://localhost:24502`.

   >[!NOTE]
   >
   > Se l’URL indicato sopra non funziona, significa che al lettore non è assegnata una visualizzazione o che il contenuto non è stato scaricato correttamente. Controlla la scheda di rete per il JSON di configurazione del lettore per vedere se il lettore ottiene i dettagli corretti e per eventuali problemi di rete nel download.

1. Fare clic con il pulsante destro del mouse e controllare tre livelli del lettore Chrome.
   **Debug del contenuto**: fare clic con il pulsante destro del mouse e controllare il contenuto per eseguire il debug del contenuto in esecuzione (nel menu di scelta rapida dovrebbe essere presente un singolo elemento denominato &quot;Inspect&quot;)

   **Debug del firmware**: visualizza l&#39;interfaccia utente di amministrazione, quindi fai clic con il pulsante destro del mouse e controlla per eseguire il debug del codice del firmware(player). Dovrebbe essere disponibile un’opzione per esaminare la pagina di sfondo e simulare un riavvio del browser.

   **Pagina di debug in background**: visualizza l&#39;interfaccia utente amministratore, quindi fai clic con il pulsante destro del mouse e controlla la pagina di sfondo (per i servizi in background come il server http).

## Aggiornamento dell&#39;estensione del lettore {#upgrading-player}

Se viene rilasciata una nuova versione del lettore, segui i passaggi indicati di seguito per aggiornare l’estensione del lettore. Puoi anche seguire le istruzioni riportate di seguito per verificare gli scenari di aggiornamento:

1. Chiudere tutte le istanze di Chrome e del lettore in esecuzione
1. Rinomina la vecchia cartella con i file del lettore
1. Estrai il nuovo file ZIP nella stessa posizione della cartella precedente
1. Avvia Chrome e passa a `chrome://extensions`
1. Seleziona l’icona del lettore e fai clic sul pulsante Aggiorna o ricarica
