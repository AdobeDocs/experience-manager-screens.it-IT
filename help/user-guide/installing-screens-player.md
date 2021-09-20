---
title: Installazione di Screens Player
seo-title: Installing Screens Player
description: Segui questa pagina per informazioni sull'installazione di AEM Screens Player disponibile.
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Installazione di AEM Screens Player {#installing-player}

Questa pagina descrive come installare AEM Screens Player.

## Lettore Screens disponibile {#available-players}

Il lettore AEM Screens è disponibile per Android, Chrome OS e Windows.

Per scaricare **AEM Screens Player**, visita la pagina [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) .

>[!NOTE]
>
>Una volta scaricato l&#39;ultimo Player (*.exe*), seguire i passaggi del lettore per completare l&#39;installazione ad-hoc:
>
>1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
>1. Passa a **Configurazione** dal menu di azione a sinistra e inserisci l&#39;indirizzo della posizione dell&#39;istanza AEM in **Server**, quindi fai clic su **Salva**.
>1. Fai clic sul collegamento **Registrazione** dal menu di azione a sinistra e sui passaggi seguenti per completare il processo di registrazione del dispositivo.


## Monitoraggio della riproduzione di base {#playback-monitoring}

Il lettore riporta varie metriche di riproduzione con ciascuna `ping` che per impostazione predefinita corrisponde a 30 secondi. In base a queste metriche, possiamo rilevare vari casi edge come esperienza bloccata, schermata vuota e problemi di pianificazione. Questo ci permette di capire e risolvere i problemi del dispositivo, e quindi di accelerare un&#39;indagine e le misure correttive con voi.

Il monitoraggio della riproduzione di base in un lettore AEM Screens consente di:

* Monitoraggio remoto, se un lettore riproduce correttamente il contenuto.

* Migliorare la reattività alle schermate vuote o alle esperienze interrotte nel campo .

* Riduce il rischio di mostrare all’utente finale un’esperienza non funzionante.

### Informazioni sulle proprietà {#understand-properties}

Le seguenti proprietà sono incluse in ogni `ping`:

| Proprietà | Descrizione |
|---|---|
| id {string} | identificatore del lettore |
| activeChannel {string} | in corso la riproduzione del percorso del canale, o null se non è pianificato nulla |
| activeElements {string} | stringa separata da virgole, elementi attualmente visibili in tutti i canali di riproduzione a sequenza (multipli in caso di layout a più zone) |
| isDefaultContent {boolean} | true se il canale di riproduzione è considerato un canale predefinito o di fallback (ovvero, ha priorità 1 e nessuna pianificazione) |
| hasContentChanged {boolean} | true se il contenuto è cambiato negli ultimi 5 minuti, false in caso contrario |
| lastContentChange {string} | timestamp dell’ultima modifica del contenuto |

>[!NOTE]
>Facoltativamente, è possibile abilitare una proprietà più avanzata dalle preferenze del lettore (Abilita monitoraggio riproduzione), ovvero:
>|Proprietà|Descrizione|
>|—|—|
>|isContentRendering {boolean}|true se la GPU può confermare che sta riproducendo il contenuto effettivo (in base all&#39;analisi dei pixel)|

### Limitazioni  {#limitations}

Di seguito sono elencate alcune limitazioni al monitoraggio della riproduzione di base:

* Il lettore segnala il proprio stato di riproduzione al server, quindi richiede una connessione attiva.

* La proprietà `isContentRendering` che controlla che la GPU sia attualmente troppo intensa di risorse per essere abilitata per impostazione predefinita e richiede un esplicito consenso dalle preferenze del lettore. Si consiglia di non utilizzarlo insieme ai video in produzione.

* Questa funzione è supportata solo per i canali di sequenza e non copre ancora il caso d’uso dei canali interattivi (SPA).

* Le metriche non sono ancora completamente esposte ai nostri clienti, stiamo lavorando sodo per abilitare un meccanismo di reporting e avvisi simile a dashboard in un futuro prossimo.

### Risorse aggiuntive {#additional-resources}

Per ulteriori informazioni, consulta i seguenti argomenti:

* Per scaricare Android Player, visita **Google Play**. Per informazioni sull&#39;implementazione di Android Watchdog, consulta [Implementazione di Android player](implementing-android-player.md).

* Per implementare Chrome OS Player, fai riferimento a [Chrome Management Console](implementing-chrome-os-player.md) per ulteriori informazioni.

* Per configurare AEM Screens Windows Player, consulta [Implementazione di Windows Player](implementing-windows-player.md).
