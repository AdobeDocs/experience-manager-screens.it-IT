---
title: Note sulla versione per Feature Pack 202109
description: Segui questa pagina per ottenere informazioni su AEM Screens Feature Pack 202105 rilasciato il 23 settembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 1%

---

# Note sulla versione per Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). Screens supporta la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 9.

Scarica l&#39;ultimo pacchetto di funzioni per la versione di AEM Screens 6.5.9 dal [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) utilizzando il tuo Adobe ID. Passa alla scheda **Adobe Experience Manager** e cerca **Screens** per ottenere l&#39;ultimo pacchetto di funzioni intitolato **AEM 6.5 Screens FP9**.

## Data di rilascio {#release-date}

La data di rilascio per AEM Screens Feature Pack 202109 è il 23 settembre 2021.

### Novità {#what-is-new}

* **Supporto delle miniature per video**

   Supporto delle miniature per i video in ora supportato in AEM Screens. Un autore di contenuti può definire una miniatura per i video in modo che l’immagine possa essere utilizzata come segnaposto e possa testare correttamente la riproduzione e il targeting del contenuto, mentre il video effettivo viene finalizzato dal team appropriato. L&#39;immagine può anche essere utilizzata, nel caso in cui la riproduzione del video non riesca.
Per ulteriori informazioni, consulta Supporto miniature per video .

* **Monitoraggio della riproduzione di base**

   AEM Screens supporta ora il monitoraggio di base della riproduzione. Ora il lettore riporta diverse metriche di riproduzione per ciascun ping (per impostazione predefinita, 30 secondi). In base alle metriche, fornisce la possibilità di rilevare vari casi edge (esperienza bloccata, schermo vuoto, problemi di pianificazione, ecc.). Questa funzione consente al team di monitorare da remoto se un lettore riproduce correttamente i contenuti, migliora la reattività a schermi vuoti o esperienze interrotte sul campo e diminuisce il rischio di mostrare un’esperienza non funzionante all’utente finale.
Per ulteriori informazioni, consulta Monitoraggio di base della riproduzione .

* **Aggiornamenti al rapporto sull’assegnazione del contenuto**

   Il rapporto sull’assegnazione dei contenuti è ora ottimizzato e migliorato con un’esperienza utente migliorata. Il rapporto scaricabile visualizza le entità correlate al lettore migliorate, come posizioni, visualizzazioni e dispositivi, in una scheda del foglio di calcolo e le informazioni del fornitore del contenuto, come canali e risorse in un’altra scheda.

* **Supporto per i manifesti V3**

   Ora puoi configurare il Dispatcher per la versione 3 di Manifest. Per ulteriori informazioni, consulta [Configurazione di Dispatcher per la versione manifesto v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) .
Inoltre, se utilizzi componenti personalizzati come parte dei manifesti v3, consulta [Modello per gestori personalizzati](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).


### Correzioni di bug {#bug-fixes}

**Lato del lettore**

* Sono stati risolti gli errori di caching dei file sostituendo le risorse con le rappresentazioni.

* I lettori ora espongono solo le rappresentazioni delle risorse, se è presente la mappatura del rendering.

* È ora possibile impostare gli avvisi slack in base ai registri splunk.

* Ottimizzazione del ping per la riautenticazione se la risposta non è JSON valido.

* I nomi/ruoli dei canali numerici hanno causato una schermata vuota.

* Scarica le rappresentazioni ottimizzate tramite SmartSync.

* Trasforma la mappatura in un elenco di chiavi di rendering.

* Rimuovere l&#39;accesso a cmd.exe e reg.exe in windows player.

* Limita le chiamate token csrf.

* Un lettore deve segnalare il proprio ultimo evento di riproduzione riuscito.

* Un lettore deve segnalare il proprio stato di riproduzione.

* Il lettore non scarica nuovamente le risorse quando la cache `ALL` è cancellata.

* In qualità di amministratore del lettore, ora puoi scegliere un nome per il lettore.

* La rimozione dell&#39;assegnazione del canale dalla visualizzazione non si riflette sul lettore.

* Se il lettore viene ricaricato durante il download dell&#39;aggiornamento del canale, ignora l&#39;aggiornamento.

* Il componente Pagina incorporata non rispetta l’evento di contatto .

* È ora supportato il provisioning remoto di Tizen Player.

**Lato server**

* Il video di Target non viene visualizzato
* Race condition durante la trasmissione dei dati di visualizzazione a sottosezioni.

* L&#39;anteprima del canale non funziona per i canali contenenti video.

* Modalità Anteprima visualizzata vuota per il canale a schermo diviso.

* Le miniature video vengono rese vuote con le rappresentazioni adattive abilitate.

* Aggiorna automaticamente il manifesto del canale se la pagina di riferimento è pubblicata.

* I canali JSON non includono canali personalizzati (#942)

* I dispositivi eliminati ora non bloccano la coda di replica Screens.

* Il manifesto non contiene contenuto di destinazione né pagine incorporate di Sites.

* Nuovo componente immagine di base non aggiunto al manifesto del canale.

* È ora supportato il download di rappresentazioni ottimizzate tramite SmartSync.

* Riproduci rendering ottimizzato per tutte le risorse.

* È stato aggiunto il supporto per più tipi di provider di contenuti

* La strategia di riproduzione in sequenza incorporata è stata interrotta e ora è stata corretta.

* Manifesto offline utilizzando il parametro di richiesta `wcmmode` per la voce html, rendendolo inmemorizzabile nella cache.

* Una sequenza incorporata dinamica vuota a volte causa la visualizzazione in bianco.

* Un lettore deve segnalare il proprio stato di riproduzione.

* Il video viene riprodotto in `Tiny mode` e non viene riprodotto come video a schermo intero sul dispositivo.

* Le password OSGi sono visibili come testo normale.


### Lettori AEM Screens rilasciati {#released-aem-screens-players}

I seguenti lettori AEM Screens vengono rilasciati per AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Download di AEM Screens Player  {#aem-screens-player-downloads}

Per scaricare l&#39;ultimo lettore AEM Screens e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
