---
title: Attivazione a livello di canale - Riproduzione a evento singolo
description: Scopri l’attivazione a livello di canale tramite la riproduzione di un singolo evento.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1769'
ht-degree: 0%

---

# Attivazione a livello di canale {#channel-level-activation-single-event-playback}

Questa pagina descrive l’attivazione a livello di canale per le risorse utilizzate nei canali.

In questa sezione vengono trattati i seguenti argomenti:

* Panoramica
* Finestra di attivazione
* Utilizzo dell’attivazione a livello di canale come riproduzione di un singolo evento
* Gestione della ricorrenza per le risorse in un canale
   * DayParting
   * WeekParting
   * MonthParting
   * Combinazione di partizioni
* Utilizzo dell’attivazione a livello di canale come riproduzione di un singolo evento

## Panoramica {#overview}

***Attivazione a livello di canale*** consente ai canali di passare dopo una determinata pianificazione. Il canale singolo dell’evento sostituisce il canale principale dopo un programma impostato e viene riprodotto per un momento particolare, fino a quando il canale principale non riproduce nuovamente il suo contenuto.

L’esempio seguente fornisce una soluzione concentrandosi sui seguenti termini chiave:

* a ***canale sequenza principale*** per la sequenza globale
* a ***canale evento singolo*** che viene eseguito una sola volta alla volta
* a ***imposta pianificazione e priorità*** per il singolo evento di riproduzione che si verifica all’interno del canale della sequenza principale

## Finestra di attivazione {#using-channel-level-activation}

La sezione seguente spiega la creazione di una riproduzione di un singolo evento all’interno di un canale per un progetto AEM Screens.

### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, assicurati di disporre dei seguenti prerequisiti per iniziare a implementare l’attivazione a livello di canale:

* Crea un progetto AEM Screens, in questo esempio, **Attivazione a livello di canale**

* Crea un canale come **MainAdChannel** in **Canali** cartella

* Crea un altro canale come **TargetedSinglePlay** in **Canali** cartella

* Aggiungere risorse rilevanti a entrambi i canali

L&#39;immagine seguente mostra **Attivazione a livello di canale** progetto con **MainAdChannel** e **TargetedSinglePlay** canali in **Canali** cartella.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Per ulteriori informazioni su come creare un progetto e un canale di sequenza, consulta le risorse seguenti:
>
>* [Creazione e gestione di progetti](creating-a-screens-project.md)
>
>* [Gestione di un canale](managing-channels.md)
>

### Implementazione {#implementation}

L’implementazione dell’attivazione a livello di canale in un progetto AEM Screens prevede tre attività principali:

1. **Impostazione della tassonomia del progetto, inclusi canali, posizioni e visualizzazioni**
1. **Assegnazione di canali alla visualizzazione**
1. **Impostazione di una pianificazione e di una priorità**

Per implementare la funzionalità, segui i passaggi seguenti:

1. **Creare una posizione**

   Accedi al tuo **Posizioni** cartella nel progetto AEM Screens e crea un percorso come **Regione**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Per informazioni su come creare una posizione, consulta **[Creazione e gestione delle posizioni](managing-locations.md)**.

1. **Crea visualizzazione in Posizione**

   1. Accedi a **Attivazione a livello di canale** > **Posizioni** > **Regione**.
   1. Seleziona **Regione** e seleziona **+ Crea** dalla barra delle azioni.
   1. Seleziona **Visualizzazione** dalla procedura guidata e crea una visualizzazione con titolo **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Assegna canali da visualizzare**

   Per **MainAdChannel:**

   1. Accedi a **Attivazione a livello di canale** > **Posizioni** > **Regione** > **RegionDisplay** e seleziona **Assegna canale** dalla barra delle azioni.
   1. **Assegnazione canale** viene visualizzata.
   1. Seleziona **Canale di riferimento** in base al percorso.
   1. Seleziona la **Percorso canale** as **Attivazione a livello di canale** > ***Canali*** > ***MainAdChannel***.
   1. Il **Ruolo canale** viene compilato come **mainadchannel**.
   1. Seleziona la **Priorità** as **1**.
   1. Seleziona la **Eventi supportati** as **Caricamento iniziale** e **Schermata di inattività**.
   1. Seleziona **Salva**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >È inoltre possibile assegnare un canale dal dashboard di visualizzazione passando a **Attivazione a livello di canale** > **Posizioni** > **Regione** > **RegionDisplay** e selezione **Dashboard** dalla barra delle azioni. Seleziona **+ Assegna canale** dal **CANALI E PIANIFICAZIONI ASSEGNATI** pannello.

   Analogamente, assegna canale **TargetedSinglePlay** per la visualizzazione**:

   1. Accedi a **Attivazione a livello di canale** > **Posizioni** > **Regione** > **RegionDisplay** e seleziona **Assegna canale** dalla barra delle azioni.
   1. **Assegnazione canale** viene visualizzata.
   1. Seleziona **Canale di riferimento** in base al percorso.
   1. Seleziona la **Percorso canale** as **Attivazione a livello di canale*** > ***Canali*** > ***TargetedSinglePlay***.
   1. Il **Ruolo canale** viene compilato come **targetedsingleplay**.
   1. Imposta il **Priorità** as **2**.
   1. Seleziona la **Eventi supportati** as **Caricamento iniziale**, **Schermata di inattività**, e **Timer**, come illustrato nella figura seguente.
   1. Scegli la data in **attivo da** come 27 novembre 2018 23:59 e in **attivo fino a** come 28 novembre 2018 12:05 A.M.
   1. Seleziona **Salva**.

   >[!CAUTION]
   >
   >Imposta la priorità per **TargetedSinglePlay** canale superiore al **MainAdSegment** canale.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Per scegliere lo stesso giorno, seleziona il giorno successivo, quindi modifica manualmente la data impostandola sullo stesso giorno ma per un’ora successiva. In questo modo si impedisce all’utente di selezionare una data passata. Vedi l’esempio seguente:

   ![nuovo1](assets/new1.gif)

## Visualizzazione dei risultati {#viewing-the-results}

Una volta completata la configurazione dei canali e della visualizzazione, avvia il lettore AEM Screens per visualizzare il contenuto.

Il lettore visualizza il contenuto di **MainAdChannel** ed esattamente alle 23:59 (come indicato nella pianificazione), **TargetedSinglePlay** canale visualizza il contenuto fino alle 00:05 e quindi il **MainAdChannel** riprende la riproduzione del contenuto.

>[!NOTE]
>
>Per informazioni sul lettore di schermo dell’AEM, consulta le seguenti risorse:
>[Download di AEM Screens Player](https://download.macromedia.com/screens/)
>[Utilizzo di AEM Screens Player](working-with-screens-player.md)


## Gestione della ricorrenza per le risorse in un canale {#handling-recurrence-in-assets}

Puoi pianificare le risorse in un canale in modo che ricorrano a determinati intervalli su base giornaliera, settimanale o mensile, anche in base alle tue esigenze.

Si supponga di voler visualizzare il contenuto di un canale solo il venerdì dalle 13.00 alle 22.00. È possibile utilizzare **Attivazione** per impostare l’intervallo ricorrente desiderato per la risorsa.

### Ripartizione giornaliera {#day-parting}

1. Seleziona il canale, quindi seleziona **Dashboard** dalla barra delle azioni.

1. Dopo aver inserito la data/ora di inizio e la data/ora di fine dalla **Assegnazione canale** è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione di ricorrenza.

   >[!NOTE]
   >
   >Puoi saltare o includere **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Schedules, in base alle tue esigenze.

1. Immetti l’espressione nel file **Pianificazione** e la risorsa viene visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la suddivisione dei giorni {#example-one}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| prima delle 08:00 | la risorsa nel canale viene riprodotta prima delle 8.00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 14:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa nel canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | la risorsa nel canale viene riprodotta ogni giorno prima delle 12:15 e poi anche dopo le 12:45. |
| Lun, Mar, Mer o Mon-Wed | la risorsa viene riprodotta nel canale da lunedì a mercoledì |
| il primo giorno di gennaio dopo le 14:00 anche il secondo giorno di gennaio anche il terzo giorno di gennaio prima delle 03:00. | la risorsa nel canale inizia a essere riprodotta dopo le 2:00 del 1° gennaio e continua a essere riprodotta per l’intera giornata del 2 gennaio fino alle 3:00 del 3 gennaio |
| nei 1-2 giorni di gennaio dopo le 2:00 anche nei 2-3 giorni di gennaio prima delle 3:00. | la risorsa nel canale avvia il lettore dopo le 2:00 del 1° gennaio, continua a essere riprodotta fino alle 3:00 del 2 gennaio, quindi riparte il 2 gennaio alle 2:00 e continua a essere riprodotta fino alle 3:00 del 3 gennaio |

>[!NOTE]
>
>Puoi anche utilizzare _ora militare_ notazione (14:00) invece di *A.M./P.M.* (14.00).

### WeekParting {#week-parting}

1. Seleziona il canale, quindi seleziona **Dashboard** dalla barra delle azioni.

1. Dopo aver inserito la data/ora di inizio e la data/ora di fine dalla **Assegnazione canale** è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione di ricorrenza.

   >[!NOTE]
   >
   >Puoi saltare o includere **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Schedules, in base alle tue esigenze.

1. Immetti l’espressione nel file **Pianificazione** e la risorsa viene visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per WeekParting {#example-two}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| Lun, Mar, Mer o Mon-Wed | la risorsa viene riprodotta nel canale da lunedì a mercoledì |
| prima delle 08:00 | la risorsa nel canale viene riprodotta prima delle 8.00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 14:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa nel canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | il canale viene riprodotto ogni giorno prima delle 12:15 e poi anche dopo le 12:45. |

>[!NOTE]
>
>Puoi anche utilizzare _ora militare_ notazione (14:00) invece di *A.M./P.M.* (14.00).


### MonthParting {#month-parting}

1. Seleziona il canale, quindi seleziona **Dashboard** dalla barra delle azioni.

1. Dopo aver inserito la data/ora di inizio e la data/ora di fine dalla **Assegnazione canale** è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione di ricorrenza.

   >[!NOTE]
   >
   >Puoi saltare o includere **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Schedules, in base alle tue esigenze.

1. Immetti l’espressione nel file **Pianificazione** e la risorsa viene visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per MonthParting {#example-three}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| di `February,May,August,November` | la risorsa viene riprodotta nel canale in febbraio, maggio, agosto e novembre |

>[!NOTE]
>
>Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le notazioni a breve termine che quelle con nome completo, ad esempio lunedì/lunedì e gennaio/gennaio.

>[!NOTE]
>
>Puoi anche utilizzare _ora militare_ notazione (14:00) invece di *A.M./P.M.* (14.00).

### Combinazione di partizioni {#combined-parting}

1. Seleziona il canale, quindi seleziona **Dashboard** dalla barra delle azioni.

1. Dopo aver inserito la data/ora di inizio e la data/ora di fine dalla **Assegnazione canale** è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione di ricorrenza.

   >[!NOTE]
   >
   >Puoi saltare o includere **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Schedules, in base alle tue esigenze.

1. Immetti l’espressione nel file **Pianificazione** e la risorsa viene visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la combinazione di partizioni {#example-four}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| dopo le 6:00 e prima delle 18:00 di lunedì, mercoledì di gennaio-marzo | la risorsa viene riprodotta nel canale tra le 6 e le 18 il lunedì e il mercoledì da gennaio a fine marzo |
| il primo giorno di gennaio dopo le 14:00 anche il secondo giorno di gennaio anche il terzo giorno di gennaio prima delle 03:00. | la risorsa nel canale inizia a essere riprodotta dopo le 2:00 del 1° gennaio e continua a essere riprodotta per l’intera giornata del 2 gennaio fino alle 3:00 del 3 gennaio |
| nei 1-2 giorni di gennaio dopo le 2:00 anche nei 2-3 giorni di gennaio prima delle 3:00. | la risorsa nel canale avvia il lettore dopo le 2:00 del 1° gennaio, continua a essere riprodotta fino alle 3:00 del 2 gennaio, quindi riparte il 2 gennaio alle 2:00 e continua a essere riprodotta fino alle 3:00 del 3 gennaio |

>[!NOTE]
>
>Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le notazioni a breve termine che quelle con nome completo, come lunedì/lunedì e gennaio/gennaio. Inoltre, puoi anche utilizzare _ora militare_ notazione (14:00) invece di *A.M./P.M.* (14.00).
