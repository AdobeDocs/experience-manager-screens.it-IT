---
title: Installazione di Screens Player
description: Scopri come installare correttamente un lettore AEM Screens.
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# Installazione di AEM Screens Player {#installing-player}

Questa pagina descrive come installare AEM Screens Player.

## Lettore Screens disponibile {#available-players}

AEM Screens Player è disponibile per Android™, Chrome OS e Windows.

Per scaricare **AEM Screens Player**, visita la pagina [Download di AEM 6.5 Player](https://download.macromedia.com/screens/).

>[!NOTE]
>
>Dopo aver scaricato l&#39;ultimo lettore (*.exe*), eseguire la procedura sul lettore per completare l&#39;installazione ad hoc:
>
>1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
>1. Passa a **Configurazione** dal menu Azioni a sinistra e immetti l&#39;indirizzo del percorso dell&#39;istanza di AEM in **Server**, quindi fai clic su **Salva**.
>1. Fai clic sul collegamento **Registrazione** dal menu Azioni a sinistra e sui passaggi seguenti per completare il processo di registrazione del dispositivo.

## Monitoraggio della riproduzione di base {#playback-monitoring}

Il lettore riporta diverse metriche di riproduzione per ogni `ping` per impostazione predefinita, 30 secondi. In base a queste metriche, è in grado di rilevare vari casi limite, come esperienza bloccata, schermata vuota e problemi di pianificazione. Ci consente di comprendere e risolvere i problemi sul dispositivo, e quindi accelera un&#39;indagine e misure correttive per voi.

Il monitoraggio della riproduzione di base in un lettore AEM Screens consente di effettuare le seguenti operazioni:

* Monitora in remoto se un lettore riproduce correttamente il contenuto.

* Migliora la reattività a schermate vuote o esperienze bloccate nel campo.

* Riduce il rischio di mostrare all’utente finale un’esperienza non funzionante.

### Informazioni sulle proprietà {#understand-properties}

In ogni `ping` sono incluse le seguenti proprietà:

| Proprietà | Descrizione |
|---|---|
| id {string} | l’identificatore del lettore |
| activeChannel {string} | percorso del canale attualmente in riproduzione o null se non è pianificato nulla |
| activeElements {string} | stringhe separate da virgola, elementi attualmente visibili in tutti i canali della sequenza di riproduzione (più in è presente un layout multizona) |
| isDefaultContent {boolean} | true se il canale di riproduzione è considerato un canale predefinito o di fallback (ovvero, ha priorità 1 e nessuna pianificazione) |
| hasContentChanged {boolean} | true se il contenuto è cambiato negli ultimi 5 minuti, false in caso contrario |
| lastContentChange {string} | timestamp dell’ultima modifica al contenuto |

>[!NOTE]
>
>Facoltativamente, è possibile abilitare una proprietà più avanzata dalle preferenze del lettore (Abilita monitoraggio della riproduzione), ovvero:
>
>| Proprietà | Descrizione |
>|---|---|
>| isContentRendering {boolean} | true se la GPU può confermare che sta riproducendo il contenuto effettivo (in base all&#39;analisi dei pixel) |

### Limitazioni {#limitations}

Di seguito sono elencate alcune limitazioni al monitoraggio di base della riproduzione:

* Il lettore segnala il proprio stato di riproduzione al server, pertanto richiede una connessione attiva.

* La proprietà `isContentRendering` che controlla la GPU richiede molte più risorse per essere abilitata per impostazione predefinita e richiede il consenso esplicito dalle preferenze del lettore. Adobe consiglia di non utilizzarlo con i video in produzione.

* Questa funzione è supportata solo per i canali di sequenza e non copre ancora il caso di utilizzo dei canali interattivi (SPA).

* Le metriche non sono ancora completamente esposte ai clienti, ma Adobe sta lavorando per abilitare presto meccanismi di reporting e di avviso simili a quelli delle dashboard.

### Altre risorse {#additional-resources}

Per informazioni dettagliate, consulta i seguenti argomenti:

* Per scaricare Android™ Player, visita **Google Play**. Per informazioni sull&#39;implementazione di Android™ Watchdog, consulta [Implementazione di Android™ player](implementing-android-player.md).

* Per implementare Chrome OS Player, vedere [Chrome Management Console](implementing-chrome-os-player.md) per ulteriori informazioni.

* Per configurare AEM Screens Windows Player, vedere [Implementazione di Windows Player](implementing-windows-player.md).
