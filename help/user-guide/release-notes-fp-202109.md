---
title: Note sulla versione per Feature Pack 202109
description: Segui questa pagina per ottenere informazioni su AEM Screens Feature Pack 202109 rilasciato il 23 settembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: c49cce64fe34e0611f086de5ac1c363589e3dc14
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 1%

---

# Note sulla versione per Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). Screens supporta la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 9.

Scarica l’ultimo pacchetto di funzioni per AEM Screens 6.5.9 dalla versione [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID. Passa a **Adobe Experience Manager** tabulazione e ricerca **Schermi** per ottenere il pacchetto di funzioni più recente denominato **AEM 6.5 Screens FP9**.

## Data di pubblicazione {#release-date}

La data di rilascio per AEM Screens Feature Pack 202109 è il 23 settembre 2021.

### Novità {#what-is-new}

* **Supporto delle miniature per video**

   Supporto delle miniature per i video in ora supportato in AEM Screens. Un autore di contenuti può definire una miniatura per i video in modo che l’immagine possa essere utilizzata come segnaposto e possa testare correttamente la riproduzione e il targeting del contenuto, mentre il video effettivo viene finalizzato dal team appropriato. L&#39;immagine può anche essere utilizzata, nel caso in cui la riproduzione del video non riesca.
Vedi [Supporto delle miniature per video](/help/user-guide/thumbnail-support.md) per ulteriori dettagli.

* **Monitoraggio della riproduzione di base**

   AEM Screens supporta ora il monitoraggio di base della riproduzione. Ora il lettore riporta diverse metriche di riproduzione per ciascun ping (per impostazione predefinita, 30 secondi). In base alle metriche, fornisce la possibilità di rilevare vari casi edge (esperienza bloccata, schermo vuoto, problemi di pianificazione, ecc.). Questa funzione consente al team di monitorare da remoto se un lettore riproduce correttamente i contenuti, migliora la reattività a schermi vuoti o esperienze interrotte sul campo e diminuisce il rischio di mostrare un’esperienza non funzionante all’utente finale.
Vedi [Monitoraggio della riproduzione di base](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) per ulteriori dettagli.

* **Aggiornamenti al rapporto sull’assegnazione del contenuto**

   Il rapporto sull’assegnazione dei contenuti è ora ottimizzato e migliorato con un’esperienza utente migliorata. Il rapporto scaricabile visualizza le entità correlate al lettore migliorate, come posizioni, visualizzazioni e dispositivi, in una scheda del foglio di calcolo e le informazioni del fornitore del contenuto, come canali e risorse in un’altra scheda.
Vedi [Rapporto sull&#39;assegnazione dei contenuti](/help/user-guide/content-assignment-report.md) per ulteriori dettagli.

* **Rendering adattivi**

   Le rappresentazioni adattive consentono ai dispositivi di selezionare automaticamente il rendering migliore per un dispositivo in base alle regole definite dal cliente.

   In qualità di sviluppatore di AEM Screens, ora puoi configurare rappresentazioni di risorse specifiche per dispositivo da scaricare e riprodurre automaticamente senza dover creare manualmente tutte le varianti di contenuto. Vedi [Rappresentazioni adattive: Panoramica e configurazioni dell&#39;architettura](/help/user-guide/adaptive-renditions.md) per ulteriori dettagli.

   Inoltre, in qualità di autore dei contenuti di AEM Screens, puoi configurare le risorse per l’utilizzo di rappresentazioni adattive e anche eseguire la migrazione dei dispositivi per reti di grandi dimensioni per sfruttare questa funzione nei tuoi canali AEM Screens. Vedi [Utilizzo di rappresentazioni adattive in AEM Screens](/help/user-guide/using-adaptive-renditions.md) per ulteriori dettagli.

* **Supporto per i manifesti V3**

   Ora puoi configurare il Dispatcher per la versione 3 di Manifest. Per abilitare il manifesto v3, devi configurare:

   * Aggiorna dispatcher

   * Aggiorna componente personalizzato

   * Disattiva ContentSync in `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`

   * Abilita SmartSync in `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`

   * Vedi [Configurazione di Dispatcher per la versione v3 del manifesto](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) per ulteriori dettagli.
   * Se utilizzi componenti personalizzati come parte di manifesti v3, consulta [Modello per gestori personalizzati](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).


### Correzioni di bug {#bug-fixes}

**Lato del lettore**

* Sono stati risolti gli errori di caching dei file sostituendo le risorse con le rappresentazioni.

* I lettori ora espongono solo le rappresentazioni delle risorse, se è presente la mappatura del rendering.

* ping migliorato per la riautenticazione se la risposta non è JSON valida.

* I nomi/ruoli dei canali numerici hanno causato una schermata vuota.

* Scarica le rappresentazioni ottimizzate tramite SmartSync.

* La mappatura è stata trasformata in elenco di chiavi di rendering.

* È stato rimosso l’accesso a `cmd.exe` e `reg.exe` nel lettore Windows.

* Un lettore deve segnalare il proprio ultimo evento di riproduzione riuscito.

* Un lettore deve segnalare il proprio stato di riproduzione.

* Player non scarica nuovamente le risorse quando `ALL` La cache viene cancellata.

* In qualità di amministratore del lettore, ora puoi scegliere un nome per il lettore.

* La rimozione dell&#39;assegnazione del canale dalla visualizzazione non si riflette sul lettore.

* Se il lettore viene ricaricato durante il download dell&#39;aggiornamento del canale, ignora l&#39;aggiornamento.

* Il componente Pagina incorporata ora rispetta l’evento touch.

* È ora supportato il provisioning remoto di Tizen Player.

**Lato server**

* Il video di Target non viene visualizzato
* Race condition durante la trasmissione dei dati di visualizzazione a sottosezioni.

* L&#39;anteprima del canale non funziona per i canali contenenti video.

* Modalità Anteprima visualizzata vuota per il canale a schermo diviso.

* Le miniature video vengono rese vuote con le rappresentazioni adattive abilitate.

* Aggiorna automaticamente il manifesto del canale se la pagina di riferimento è pubblicata.

* I dispositivi eliminati ora non bloccano la coda di replica Screens.

* Il manifesto non conteneva contenuto di destinazione né pagine incorporate di Sites. Questo problema è stato risolto.

* Il nuovo componente immagine di base viene ora aggiunto al manifesto del canale.

* È ora supportato il download di rappresentazioni ottimizzate tramite SmartSync.

* Riproduci rendering ottimizzato per tutte le risorse.

* È stato aggiunto il supporto per più tipi di provider di contenuti

* La strategia di riproduzione in sequenza incorporata è stata interrotta e ora è stata corretta.

* Manifesto offline utilizzando il parametro della richiesta `wcmmode` per la voce html, rendendola non memorizzabile nella cache.

* La sequenza incorporata dinamica vuota talvolta causava la visualizzazione in bianco.

* Il lettore ora ne segnala lo stato di riproduzione.

* Riproduzione video in corso `Tiny mode` e non riprodotto come video a schermo intero sul dispositivo e il problema è risolto ora.

### Lettori AEM Screens rilasciati {#released-aem-screens-players}

I seguenti lettori AEM Screens vengono rilasciati per AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Download di AEM Screens Player  {#aem-screens-player-downloads}

Per scaricare l&#39;ultimo lettore AEM Screens e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
