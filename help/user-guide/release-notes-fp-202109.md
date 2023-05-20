---
title: Note sulla versione per Feature Pack 202109
description: Segui questa pagina per ottenere informazioni sui 202109 di AEM Screens Feature Pack rilasciati il 23 settembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: b56844c66bfa980013b610523842c7ac0c30f44d
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# Note sulla versione per Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Si consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager (AEM). Screens fornisce supporto per la manutenzione della piattaforma AEM 6.3 Screens.

## Disponibilità {#availability}

AEM Screens ha rilasciato AEM 6.5 Feature Pack 9.

Puoi scaricare il feature pack più recente per AEM Screens versione 6.5.9 da [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID. Accedi a **Adobe Experience Manager** e cerca **Schermi** per ottenere l’ultimo feature pack con titolo **Schermi FP9 di AEM 6.5**.

## Data di pubblicazione {#release-date}

La data di pubblicazione del Feature Pack 202109 per AEM Screens è il 23 settembre 2021.

### Novità {#what-is-new}

* **Supporto delle miniature per video**

   Il supporto miniature per video è ora supportato in AEM Screens. Un autore di contenuti può definire una miniatura per video in modo che l’immagine possa essere utilizzata come segnaposto e testare correttamente la riproduzione e il targeting del contenuto, mentre il video effettivo è in fase di finalizzazione da parte del team appropriato. L’immagine può essere utilizzata anche nel caso in cui la riproduzione del video non riesca.
Consulta [Supporto miniature per video](/help/user-guide/thumbnail-support.md) per ulteriori dettagli.

* **Monitoraggio della riproduzione di base**

   AEM Screens ora supporta il monitoraggio di base della riproduzione. Ora il lettore riporta diverse metriche di riproduzione per ciascun ping (30 secondi per impostazione predefinita). In base alle metriche, consente di rilevare vari casi limite (esperienza bloccata, schermata vuota, problemi di pianificazione, ecc.). Questa funzione consente al team di monitorare da remoto se un lettore riproduce correttamente i contenuti, migliora la reattività a schermate vuote o esperienze bloccate sul campo e diminuisce il rischio di mostrare all’utente finale un’esperienza non funzionante.
Consulta [Monitoraggio della riproduzione di base](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) per ulteriori dettagli.

* **Aggiornamenti al rapporto Assegnazione contenuti**

   Il report sull’assegnazione dei contenuti ora è ottimizzato e migliorato con una migliore esperienza utente. Il rapporto scaricabile mostra le entità relative al lettore migliorate, come posizioni, visualizzazioni e dispositivi, in una scheda del foglio di calcolo e le informazioni sul provider di contenuti, come canali e risorse in un’altra scheda.
Consulta [Rapporto assegnazione contenuti](/help/user-guide/content-assignment-report.md) per ulteriori dettagli.

* **Rappresentazioni adattive**

   Le rappresentazioni adattive consentono ai dispositivi di selezionare automaticamente la rappresentazione migliore per un dispositivo in base alle regole definite dal cliente.

   In qualità di sviluppatore di AEM Screens, ora puoi configurare i rendering di risorse specifiche per il dispositivo in modo che vengano scaricati e riprodotti automaticamente senza dover creare manualmente tutte le varianti di contenuto. Consulta [Rappresentazioni adattive: panoramica dell’architettura e configurazioni](/help/user-guide/adaptive-renditions.md) per ulteriori dettagli.

   Inoltre, in qualità di Autore di contenuti AEM Screens, puoi configurare le risorse per l’utilizzo di rappresentazioni adattive e migrare i dispositivi per reti di grandi dimensioni per usufruire di questa funzione, nei canali AEM Screens. Consulta [Utilizzo di rappresentazioni adattive in AEM Screens](/help/user-guide/using-adaptive-renditions.md) per ulteriori dettagli.

* **Supporto per manifesti V3**

   Ora puoi configurare Dispatcher per la versione v3 del manifesto. Per abilitare il manifesto v3, è necessario:

   * Cancella tutti i processi di contenuto offline in sospeso sia in Creazione che in Pubblicato

      * Passa a crx/de in fase di authoring e pubblicazione

      * Fai clic su Strumenti —> Query

      * Nella query utilizza `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`

      * Verranno elencati tutti i processi di contenuto offline attualmente in esecuzione o in sospeso nella coda

      * Attendi che non siano più presenti processi di contenuto offline restituiti dalla query
   * Disattiva ContentSync in `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`

   * Abilitare SmartSync in `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`

   * Aggiorna dispatcher

   * Aggiorna componente personalizzato


   * Consulta [Configurazione di Dispatcher per la versione v3 del manifesto](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) per ulteriori dettagli.
   * Se utilizzi componenti personalizzati come parte dei manifesti v3, vedi [Modello per gestori personalizzati](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).



### Correzioni di bug {#bug-fixes}

**Lato lettore**

* Sono stati risolti gli errori di memorizzazione nella cache dei file sostituendo le risorse con rappresentazioni.

* I lettori ora espongono solo i rendering delle risorse, se è presente la mappatura dei rendering.

* È stato migliorato il ping per la nuova autenticazione se la risposta non è un JSON valido.

* I nomi/ruoli dei canali numerici hanno causato la visualizzazione di una schermata vuota.

* Scarica le rappresentazioni ottimizzate tramite SmartSync.

* La mappatura è stata trasformata in elenco di chiavi di rappresentazione.

* Rimosso l’accesso a `cmd.exe` e `reg.exe` in windows player.

* Un lettore deve segnalare il suo ultimo evento di riproduzione riuscito.

* Un lettore deve segnalare il suo stato di riproduzione.

* Il lettore non scarica nuovamente le risorse quando `ALL` Cache cancellata.

* In qualità di amministratore del lettore, ora puoi scegliere un nome per il lettore.

* La rimozione dell’assegnazione del canale dalla visualizzazione non si riflette sul lettore.

* Se il lettore viene ricaricato durante il download dell’aggiornamento del canale, l’aggiornamento viene ignorato.

* Il componente Pagina incorporata ora rispetta l’evento di contatto.

* È ora supportato il provisioning remoto del lettore Tizen.

**Lato server**

* Il video di destinazione non viene visualizzato
* Race condition sulla trasmissione dei dati del display alle sottosequenze.

* L’anteprima canale non funziona per i canali contenenti video.

* Modalità Anteprima che mostra il valore vuoto per il canale schermo diviso.

* Le miniature video risultano vuote con le rappresentazioni adatte abilitate.

* Aggiorna automaticamente il manifesto del canale se viene pubblicata la pagina di riferimento.

* I dispositivi eliminati ora non bloccano la coda di replica Screens.

* Il manifesto non conteneva contenuto di destinazione né pagine incorporate in Sites. Questo problema è stato risolto.

* Al manifesto del canale vengono ora aggiunti i nuovi componenti immagine di base.

* È ora supportato il download di rappresentazioni ottimizzate tramite SmartSync.

* Riproduci il rendering ottimizzato per tutte le risorse.

* È stato aggiunto il supporto per più tipi di provider di contenuti

* La strategia di riproduzione della sequenza incorporata è stata interrotta e ora è stata corretta.

* Manifesto offline utilizzando il parametro di richiesta `wcmmode` per la voce html, rendendola non memorizzabile in cache.

* A volte, una sequenza dinamica incorporata vuota causava la visualizzazione di una schermata vuota.

* Il lettore ora segnala il suo stato di riproduzione.

* Riproduzione del video in corso `Tiny mode` e non viene riprodotto come video a schermo intero sul dispositivo e il problema è risolto ora.

### Lettori AEM Screens rilasciati {#released-aem-screens-players}

Sono stati rilasciati i seguenti lettori AEM Screens per AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Download di AEM Screens Player  {#aem-screens-player-downloads}

Per scaricare il lettore AEM Screens più recente e ulteriori informazioni sulle correzioni di bug, consulta **[Download di AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
