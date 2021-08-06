---
title: Attivazione a livello di canale - Riproduzione di eventi singoli
seo-title: Attivazione a livello di canale - Riproduzione di eventi singoli
description: Segui questa guida per comprendere l’attivazione a livello di canale utilizzando la riproduzione di un singolo evento.
topic-tags: authoring
feature: Creazione di schermi, Attivazione a livello di canale
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: 72352b9ece8fde2d02b9fa0ccd25c6dfd7d602fd
workflow-type: tm+mt
source-wordcount: '1795'
ht-degree: 0%

---

# Attivazione a livello di canale {#channel-level-activation-single-event-playback}

Questa pagina descrive l’attivazione a livello di canale per le risorse utilizzate in Canali.

I seguenti argomenti sono trattati in questa sezione:

* Panoramica
* Finestra di attivazione
* Utilizzo di Attivazione a livello di canale come riproduzione di un singolo evento
* Gestione della ricorrenza per le risorse in un canale
   * DayParting
   * WeekParting
   * MonthParting
   * Combinazione di partizioni
* Utilizzo di Attivazione a livello di canale come riproduzione di un singolo evento

## Panoramica {#overview}

***Channel Level*** Activationconsente ai canali di passare dopo una determinata pianificazione. Il canale evento singolo sostituisce il canale principale dopo una pianificazione impostata e viene riprodotto per un particolare momento, fino a quando il canale principale riproduce di nuovo il contenuto.

L&#39;esempio seguente fornisce una soluzione concentrandosi sui seguenti termini chiave:

* a ***canale sequenza principale*** per la sequenza globale
* a ***singolo canale evento*** che viene eseguito una sola volta a un&#39;ora impostata
* a ***impostare la pianificazione e la priorità*** per l&#39;evento di riproduzione singola che si verifica all&#39;interno del canale della sequenza principale

## Finestra di attivazione {#using-channel-level-activation}

La sezione seguente spiega la creazione di un singolo evento di riproduzione all’interno di un canale per un progetto AEM Screens.

### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, assicurati di disporre dei seguenti prerequisiti per iniziare a implementare l’attivazione a livello di canale:

* Crea un progetto AEM Screens, in questo esempio, **Attivazione a livello di canale**

* Crea un canale come **MainAdChannel** nella cartella **Canali**

* Crea un altro canale come **TargetedSinglePlay** nella cartella **Canali**

* Aggiungere risorse rilevanti a entrambi i canali

L&#39;immagine seguente mostra il progetto **Attivazione a livello di canale** con canali **MainAdChannel** e **TargetSinglePlay** nella cartella **Canali**.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Per ulteriori informazioni su come creare un progetto e come creare un canale per sequenza, consulta le risorse seguenti:
>
>* [Creazione e gestione di progetti](creating-a-screens-project.md)

* [Gestione di un canale](managing-channels.md)



### Implementazione {#implementation}

L’implementazione dell’attivazione a livello di canale in un progetto AEM Screens prevede tre attività principali:

1. **Impostazione della tassonomia del progetto, compresi canali, posizioni e visualizzazioni**
1. **Assegnazione dei canali da visualizzare**
1. **Impostazione di una pianificazione e di una priorità**

Per implementare la funzionalità , effettua le seguenti operazioni:

1. **Creare una posizione**

   Passa alla cartella **Posizioni** nel progetto AEM Screens e crea una posizione come **Regione**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   Per informazioni su come creare una posizione, consulta **[Creazione e gestione di posizioni](managing-locations.md)**.

1. **Crea visualizzazione in posizione**

   1. Passa a **Attivazione a livello di canale** > **Posizioni** > **Regione**.
   1. Seleziona **Regione** e fai clic su **+ Crea** dalla barra delle azioni.
   1. Seleziona **Display** dalla procedura guidata e crea una visualizzazione dal titolo **Visualizzazione regioni.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Assegna canali da visualizzare**

   Per **MainAdChannel:**

   1. Passa a **Attivazione a livello di canale** > **Posizioni** > **Regione** > **Visualizzazione a livello di canale** e fai clic su **Assegna canale** dalla barra delle azioni.
   1. **Viene visualizzata la finestra** di dialogo Assegnazione canale .
   1. Seleziona **Canale di riferimento**.. per percorso.
   1. Seleziona il **Percorso canale** come **Attivazione livello canale** —> ***Canali*** —> ***MainAdChannel***.
   1. Il **Ruolo canale** viene popolato come **canale principale**.
   1. Seleziona la **Priorità** come **1**.
   1. Seleziona **Eventi supportati** come **Caricamento iniziale** e **Schermo di inattività**.
   1. Fai clic su **Salva**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   Puoi anche assegnare il canale dal dashboard di visualizzazione passando a **Attivazione a livello di canale** —> **Posizioni** —> **Regione** —> **Visualizzazione a livello di canale** e facendo clic su **Dashboard** dalla barra delle azioni. Fai clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI E PIANIFICAZIONI**.

   Allo stesso modo, assegna il canale **TargetedSinglePlay** per la visualizzazione**:

   1. Passa a **Attivazione a livello di canale** —> **Posizioni** —> **Regione** —> **Visualizzazione a livello di canale** e fai clic su **Assegna canale** dalla barra delle azioni.
   1. **Viene visualizzata la finestra** di dialogo Assegnazione canale .
   1. Seleziona **Canale di riferimento**.. per percorso.
   1. Seleziona il **Percorso canale** come **Attivazione livello canale*** —> ***Canali*** —> ***TargetedSinglePlay***.
   1. Il **Ruolo canale** viene popolato come **targetedsingleplay**.
   1. Imposta la **Priorità** come **2**.
   1. Seleziona gli **Eventi supportati** come **Caricamento iniziale**, **Schermo di inattività** e **Timer**, *come mostrato nella figura seguente.
   1. Scegli la data in **attivo da** come 27 novembre 2018 11:59 pm e in **attivo fino a** come 28 novembre 2018 12:05 am.
   1. Fai clic su **Salva**.

   >[!CAUTION]
   È necessario impostare la priorità per il canale **TargetedSinglePlay** superiore al canale **MainAdSegment**.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Per scegliere lo stesso giorno, è necessario selezionare il giorno successivo e modificare manualmente la data nello stesso giorno, ma per un’ora successiva. In questo modo l’utente non può selezionare una data passata. Fai riferimento all&#39;esempio seguente:

   ![new1](assets/new1.gif)

## Visualizzazione dei risultati {#viewing-the-results}

Una volta completata la configurazione dei canali e la visualizzazione, avvia il lettore AEM Screens per visualizzare il contenuto.

Il lettore visualizza il contenuto di **MainAdChannel** ed esattamente alle 11:59 (come impostato nella pianificazione), il canale **TargetedSinglePlay** visualizza il contenuto fino alle 12:05 e il canale **MainAdChannel** riprenderà a riprodurre nuovamente il contenuto.

>[!NOTE]
Per informazioni su AEM Screen Player, consulta le seguenti risorse:
[Download di AEM Screens Player](https://download.macromedia.com/screens/)
[Utilizzo di AEM Screens Player](working-with-screens-player.md)


## Gestione della ricorrenza per le risorse in un canale {#handling-recurrence-in-assets}

Puoi pianificare le risorse in un canale in modo che ricorrano a determinati intervalli giornalieri, settimanali o mensili, in base alle tue esigenze.

Supponiamo di voler visualizzare il contenuto di un canale solo il venerdì dalle 13:00 alle 10:00. Puoi utilizzare la scheda **Activation** per impostare l’intervallo ricorrente desiderato per la risorsa.

### Ripartizione giornaliera {#day-parting}

1. Seleziona il canale e fai clic su **Dashboard** nella barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/ora di inizio e l&#39;ora di fine/data dalla finestra di dialogo **Assegnazione canale**, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per ripartizione giornaliera {#example-one}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| prima delle 8:00 | la risorsa del canale viene riprodotta prima delle 8:00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 2:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa del canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | la risorsa nel canale viene riprodotta prima delle 12:15 di ogni giorno e poi anche dopo le 12:45 di sera |
| Luna, mar, Wed o Mon-Wed | la risorsa viene riprodotta nella risorsa del canale da lunedì a mercoledì |
| il 1° gennaio dopo le 14.00 anche il 2° giorno di gennaio anche il 3° giorno di gennaio prima delle 3.00 | la risorsa del canale inizia a giocare dopo le 2:00 del 1° gennaio, continua a giocare per tutta la giornata del 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 gennaio dopo le 2:00 del pomeriggio anche il 2-3 di gennaio prima delle 3:00 | la risorsa del canale inizia il lettore dopo le 2:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 pm e continua a giocare fino alle 3:00 del 3 gennaio |

>[!NOTE]
È inoltre possibile utilizzare la notazione _tempo militare_ (ovvero, 14:00) invece della notazione *am/pm* (ovvero 2:00 pm).

### WeekParting {#week-parting}

1. Seleziona il canale e fai clic su **Dashboard** nella barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/ora di inizio e l&#39;ora di fine/data dalla finestra di dialogo **Assegnazione canale**, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per WeekParting {#example-two}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| Luna, mar, Wed o Mon-Wed | la risorsa viene riprodotta nella risorsa del canale da lunedì a mercoledì |
| prima delle 8:00 | la risorsa del canale viene riprodotta prima delle 8:00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 2:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa del canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | il canale gioca prima 12:15 ogni giorno e poi anche dopo 12:45 pm |

>[!NOTE]
È inoltre possibile utilizzare la notazione _tempo militare_ (ovvero, 14:00) invece della notazione *am/pm* (ovvero 2:00 pm).


### MonthParting {#month-parting}

1. Seleziona il canale e fai clic su **Dashboard** nella barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/ora di inizio e l&#39;ora di fine/data dalla finestra di dialogo **Assegnazione canale**, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per MonthParting {#example-three}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| di febbraio,maggio,agosto,novembre | la risorsa viene riprodotta nel canale in febbraio, maggio, agosto, novembre |

>[!NOTE]
Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le note a mano breve che a nome completo, ad esempio, lunedì/lunedì e gennaio/gennaio.

>[!NOTE]
È inoltre possibile utilizzare la notazione _tempo militare_ (ovvero, 14:00) invece della notazione *am/pm* (ovvero 2:00 pm).

### Combinazione di partizioni {#combined-parting}

1. Seleziona il canale e fai clic su **Dashboard** nella barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/ora di inizio e l&#39;ora di fine/data dalla finestra di dialogo **Assegnazione canale**, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la combinazione di partizioni {#example-four}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| dopo le 6:00 e prima delle 18:00 su lun,Wed di gen-mar | il asset gioca nel canale tra le 6 del mattino e le 18 del pomeriggio del lunedì e del mercoledì da gennaio a fine marzo |
| il 1° gennaio dopo le 14.00 anche il 2° giorno di gennaio anche il 3° giorno di gennaio prima delle 3.00 | la risorsa del canale inizia a giocare dopo le 2:00 del 1° gennaio, continua a giocare per tutta la giornata del 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 gennaio dopo le 2:00 del pomeriggio anche il 2-3 di gennaio prima delle 3:00 | la risorsa del canale inizia il lettore dopo le 2:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 pm e continua a giocare fino alle 3:00 del 3 gennaio |

>[!NOTE]
Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le note a mano breve che a nome completo, ad esempio, lunedì/lunedì e gennaio/gennaio.  Inoltre, è possibile utilizzare la notazione _tempo militare_ (ovvero, 14:00) invece della notazione *am/pm* (ovvero 2:00 pm).
