---
title: Note sulla versione per Feature Pack 202109
description: Scopri il Feature Pack 202109 di AEM Screens, rilasciato il 23 settembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# Note sulla versione per Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>L’Adobe consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). AEM Screens fornisce supporto per la manutenzione della piattaforma Screens AEM 6.3.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 9.

Puoi scaricare il Feature Pack più recente per AEM Screens versione 6.5.9 dal [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) tramite il tuo Adobe ID. Passa alla scheda **Adobe Experience Manager** e cerca **Screens** per ottenere il Feature Pack più recente con titolo **AEM 6.5 Screens FP9**.

## Data di rilascio {#release-date}

La data di pubblicazione del Feature Pack 202109 per AEM Screens è il 23 settembre 2021.

### Novità {#what-is-new}

* **Supporto miniature per video**

  Il supporto miniature per video è ora supportato in AEM Screens. Un autore di contenuti definisce una miniatura per video in modo che l’immagine venga utilizzata come segnaposto. Inoltre, sottopongono a test appropriati la riproduzione e il targeting dei contenuti, mentre il team appropriato finalizza il video effettivo. L’immagine può essere utilizzata anche in caso di interruzione della riproduzione del video.
Per ulteriori dettagli, consulta [Supporto miniature per video](/help/user-guide/thumbnail-support.md).

* **Monitoraggio della riproduzione di base**

  AEM Screens ora supporta il monitoraggio di base della riproduzione. Ora il lettore riporta diverse metriche di riproduzione per ciascun ping (30 secondi per impostazione predefinita). In base alle metriche, rileva vari casi limite (esperienza bloccata, schermata vuota, problemi di pianificazione e così via). Questa funzione consente al team di monitorare in remoto se un lettore riproduce correttamente i contenuti e migliora la reattività a schermate vuote o esperienze bloccate sul campo. Inoltre, riduce il rischio di mostrare all’utente finale un’esperienza non funzionante.
Per ulteriori dettagli, consulta [Monitoraggio della riproduzione di base](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring).

* **Aggiornamenti al report assegnazione contenuti**

  Il report sull’assegnazione dei contenuti ora è ottimizzato e migliorato con una migliore esperienza utente. Il rapporto scaricabile mostra entità migliorate relative al lettore. Tali entità includono posizioni, visualizzazioni e dispositivi in una scheda del foglio di calcolo. Include inoltre le informazioni sul provider di contenuti, come canali e risorse, in altre schede.
Per ulteriori dettagli, vedere [Report assegnazione contenuto](/help/user-guide/content-assignment-report.md).

* **Rappresentazioni adattive**

  Le rappresentazioni adattive consentono al dispositivo di fare clic automaticamente sulla rappresentazione migliore per un dispositivo in base a regole definite dal cliente.

  In qualità di sviluppatore di AEM Screens, ora puoi configurare i rendering di risorse specifiche per il dispositivo in modo che vengano scaricati e riprodotti automaticamente senza dover creare manualmente tutte le varianti di contenuto. Per ulteriori dettagli, consulta [Rappresentazioni adattive: panoramica dell&#39;architettura e configurazioni](/help/user-guide/adaptive-renditions.md).

  Inoltre, in qualità di autore di contenuti AEM Screens, puoi configurare le risorse per l’utilizzo di rappresentazioni adattive. Puoi anche eseguire la migrazione dei dispositivi per reti di grandi dimensioni per utilizzare questa funzione nei canali di AEM Screens. Per ulteriori dettagli, vedere [Utilizzo di rappresentazioni adattive in AEM Screens](/help/user-guide/using-adaptive-renditions.md).

* **Supporto per i manifesti V3**

  Ora puoi configurare Dispatcher per la versione del manifesto v3. Per abilitare il manifesto v3, effettuare le seguenti operazioni:

   * Cancella tutti i processi di contenuto offline in sospeso sia in fase di creazione che in fase di pubblicazione.

      * Passa a CRXDE Liti in Author e Publish.

      * Selezionate Strumenti (Tools) > Query.

      * Nella query, utilizzare `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`.

      * Elenca tutti i processi di contenuto offline attualmente in esecuzione o in sospeso nella coda.

      * Attendi che non siano più presenti processi di contenuto offline restituiti dalla query.

   * Disabilita ContentSync in `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

   * Abilitare SmartSync in `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

   * Aggiornare Dispatcher.

   * Aggiorna il componente personalizzato.


   * Per ulteriori dettagli, vedere [Configurazione di Dispatcher per la versione del manifesto v3](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3).
   * Se utilizzi componenti personalizzati come parte dei manifesti v3, vedi [Modello per gestori personalizzati](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).


### Correzioni di bug {#bug-fixes}

**Lato lettore**

* Sono stati risolti gli errori di memorizzazione nella cache dei file sostituendo le risorse con rappresentazioni.

* I lettori ora espongono solo i rendering delle risorse, se è presente la mappatura dei rendering.

* È stato migliorato il ping per la nuova autenticazione se la risposta non è un JSON valido.

* I nomi/ruoli dei canali numerici hanno causato la visualizzazione di una schermata vuota.

* Scarica le rappresentazioni ottimizzate tramite SmartSync.

* La mappatura è stata trasformata in un elenco di chiavi di rappresentazione.

* È stato rimosso l&#39;accesso a `cmd.exe` e `reg.exe` in Windows Player.

* Un lettore deve segnalare il suo ultimo evento di riproduzione riuscito.

* Un lettore deve segnalare il proprio stato di riproduzione.

* Il lettore non scarica nuovamente Assets quando la cache `ALL` viene cancellata.

* In qualità di amministratore del lettore, ora puoi scegliere un nome per il lettore.

* La rimozione dell’assegnazione del canale dalla visualizzazione non si riflette sul lettore.

* Se il lettore viene ricaricato durante il download dell’aggiornamento del canale, l’aggiornamento viene ignorato.

* Il componente Pagina incorporata ora rispetta l’evento di contatto.

* È ora supportato il provisioning remoto del lettore Tizen.

**Lato server**

* Il video di destinazione non viene visualizzato
* Race condition sulla trasmissione dei dati del display alle successive.

* L’anteprima canale non funziona per i canali contenenti video.

* Modalità Anteprima che mostra il valore vuoto per il canale schermo diviso.

* Le miniature video vengono visualizzate come vuote se sono abilitate le rappresentazioni adattive.

* Aggiorna automaticamente il manifesto del canale se la pagina di riferimento è pubblicata.

* I dispositivi eliminati ora non bloccano la coda di replica di Screens.

* Il manifesto non conteneva contenuto di destinazione o pagine incorporate in Sites. Questo bug è ora corretto.

* Al manifesto del canale viene ora aggiunto un nuovo componente immagine di base.

* È ora supportato il download di rappresentazioni ottimizzate tramite SmartSync.

* Riproduci il rendering ottimizzato per tutte le risorse.

* È stato aggiunto il supporto per più tipi di provider di contenuti

* La strategia di riproduzione della sequenza incorporata è stata interrotta e questo bug è ora corretto.

* Manifesto offline che utilizza il parametro di richiesta `wcmmode` per la voce html, rendendolo non memorizzabile in cache.

* A volte, una sequenza dinamica incorporata vuota causava la visualizzazione di una schermata vuota.

* Il lettore ora segnala il suo stato di riproduzione.

* Il video è stato riprodotto in `Tiny mode` e non è stato riprodotto come video a schermo intero sul dispositivo. Il problema è stato risolto.

### Lettori AEM Screens rilasciati

Sono stati rilasciati i seguenti lettori AEM Screens per AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Download di AEM Screens Player

Per scaricare il lettore AEM Screens più recente e ulteriori informazioni sulle correzioni di bug, vedi **[Download del lettore AEM Screens](https://download.macromedia.com/screens/index.html)**.
