---
title: Attivazione A Livello Di Canale - Riproduzione A Singolo Evento
seo-title: Attivazione A Livello Di Canale - Riproduzione A Singolo Evento
description: Seguite questa guida per comprendere meglio l'attivazione a livello di canale con la riproduzione di un singolo evento.
seo-description: Seguite questa guida per comprendere meglio l'attivazione a livello di canale con la riproduzione di un singolo evento.
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: af244dc18aa4eb526978ab9ced60e8b818f6201e

---


# Attivazione a livello di canale {#channel-level-activation-single-event-playback}

Questa pagina descrive l’attivazione a livello di canale per le risorse utilizzate in Canali.

Gli argomenti seguenti sono trattati in questa sezione:

* Panoramica
* Finestra Attivazione
* Utilizzo dell&#39;attivazione a livello di canale come riproduzione di un singolo evento
* Gestione della ricorrenza per le risorse in un canale
   * Frazionamento del giorno
   * Scomposizione Settimana
   * Mese di suddivisione
   * Combinazione di partizioni
* Utilizzo dell&#39;attivazione a livello di canale come riproduzione di un singolo evento

## Panoramica {#overview}

***Attivazione*** a livello di canale consente ai canali di passare a una determinata pianificazione. Il singolo canale evento sostituisce il canale principale dopo una programmazione impostata e viene riprodotto per un particolare momento, fino a quando il canale principale non riproduce il contenuto.

L&#39;esempio seguente fornisce una soluzione concentrandosi sui seguenti termini chiave:

* un canale ***di sequenza*** principale per la sequenza globale
* un canale ***evento*** singolo che viene eseguito una sola volta alla volta
* una pianificazione ***impostata e una priorità*** per l&#39;evento di riproduzione singola che si verifica all&#39;interno del canale della sequenza principale

## Finestra Attivazione {#using-channel-level-activation}

La sezione seguente illustra la creazione di un singolo evento riprodotto all’interno di un canale per un progetto AEM Screens.

### Prerequisiti {#prerequisites}

Prima di iniziare ad implementare questa funzionalità, accertatevi di disporre dei seguenti prerequisiti per iniziare a implementare l&#39;attivazione a livello di canale:

* Crea un progetto AEM Screens, in questo esempio, Attivazione a livello di **canale**

* Crea un canale come **MainAdChannel** nella cartella **Channels (Canali** )

* Crea un altro canale come **TargetingSinglePlay** nella cartella **Channels (Canali** )

* Aggiunta di risorse rilevanti a entrambi i canali

L&#39;immagine seguente mostra il progetto Attivazione **a livello di** canale con canali **MainAdChannel** e **TargetingSinglePlay** nella cartella **Channels** .

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Per ulteriori informazioni su come creare un progetto e come creare un canale di sequenza, consulta le risorse seguenti:
>
>* [Creazione e gestione di progetti](creating-a-screens-project.md)
   >
   >
* [Gestione di un canale](managing-channels.md)
>



### Implementazione {#implementation}

L’implementazione dell’attivazione a livello di canale in un progetto AEM Screens implica tre attività principali:

1. **Impostazione della tassonomia del progetto, inclusi canali, posizioni e display**
1. **Assegnazione di canali da visualizzare**
1. **Impostazione di una pianificazione e di una priorità**

Per implementare la funzionalità, effettuate le operazioni seguenti:

1. **Creare una posizione**

   Andate alla cartella **Locations** (Posizioni) nel progetto AEM Screens e create una posizione come **Regione**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un percorso, consultate **[Creazione e gestione di posizioni](managing-locations.md)**.

1. **Crea visualizzazione in posizione**

   1. Andate a Attivazione **a livello di** canale > **Posizioni** > **Regione**.
   1. Selezionate **Regione** e fate clic su **+ Crea** dalla barra delle azioni.
   1. Selezionate **Visualizza** dalla procedura guidata e create una visualizzazione con titolo **Visualizzazione area.**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Assegna canali da visualizzare**

   Per **MainAdChannel:**

   1. Andate a Attivazione **a livello di** canale > **Posizioni** > **Regione** > **Visualizzazione** a livello di canale e fate clic su **Assegna canale** dalla barra delle azioni.
   1. **Viene visualizzata la finestra di dialogo Assegnazione** canale.
   1. Select **Reference Channel**.. by path.
   1. Selezionate il percorso **del** canale come Attivazione **a livello di** canale > ***Canali*** > ***MainAdChannel***.
   1. Il ruolo **** canale viene popolato come canale **principale**.
   1. Selezionate la **priorità** come **1**.
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Fai clic su **Salva**.
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Potete anche assegnare il canale dal pannello di visualizzazione accedendo a Attivazione **a livello di** canale > **Posizioni** > **Regione** > **Visualizzazione** area e facendo clic su **Dashboard** dalla barra delle azioni. Fate clic su **+ Assegna canale** dal pannello CANALI E PIANIFICAZIONI **ASSEGNATI** .

   Analogamente, assegna canale **TargetingSinglePlay** per display**:

   1. Andate a Attivazione **a livello di** canale —> **Posizioni** —> **Regione** —> **Visualizzazione** a livello di canale e fate clic su **Assegna canale** dalla barra delle azioni.
   1. **Viene visualizzata la finestra di dialogo Assegnazione** canale.
   1. Select **Reference Channel**.. by path.
   1. Selezionate il percorso **del** canale come attivazione **a livello di** canale* —> ***Canali*** —> ***TargetingSinglePlay***.
   1. Il ruolo **** del canale viene popolato come **mirato per singola** riproduzione.
   1. Impostate la **priorità** su **2**.
   1. Selezionate gli eventi **** supportati come Carico **** iniziale, Schermo **inattivo e** Timer ****, *come mostrato nella figura seguente.
   1. Scegli la data in **attivo dal** 27 novembre 2018 11:59 pm e in **attivo fino** al 28 novembre 2018 12:05 am.
   1. Fai clic su **Salva**.
   >[!CAUTION]
   È necessario impostare la priorità per il canale **TargetingSinglePlay** più alto del canale **MainAdSegment** .

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Per scegliere lo stesso giorno, è necessario selezionare il giorno successivo e modificare manualmente la data nello stesso giorno, ma per un&#39;ora successiva. Questo impedisce all&#39;utente di selezionare una data precedente. Fare riferimento all&#39;esempio seguente:

   ![new1](assets/new1.gif)

## Visualizzazione dei risultati {#viewing-the-results}

Una volta impostata la visualizzazione dei canali, avvia il lettore AEM Screens per visualizzare il contenuto.

Il lettore visualizza il contenuto di **MainAdChannel** ed esattamente alle 11:59 (come impostato nella pianificazione), il canale **TargetingSinglePlay** visualizzerà il contenuto fino alle 12:05 e il canale **MainAdChannel** riprenderà a riprodurlo.

>[!NOTE]
Per informazioni su AEM Screen Player, consulta le risorse seguenti:
* [Download di AEM Screens Player](https://download.macromedia.com/screens/)
* [Utilizzo di AEM Screens Player](working-with-screens-player.md)



## Gestione della ricorrenza per le risorse in un canale{#handling-recurrence-in-assets}

Potete pianificare le risorse in un canale in modo che si ripetano a determinati intervalli su base giornaliera, settimanale o mensile, in base alle vostre esigenze.

Supponete di voler visualizzare il contenuto di un canale solo il venerdì dall&#39;1:00 fino alle 10:00. Potete utilizzare la scheda **Attivazione** per impostare l&#39;intervallo periodico desiderato per la risorsa.

### Frazionamento del giorno {#day-parting}

1. Selezionate il canale e fate clic sul **dashboard** dalla barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/l&#39;ora di inizio e di fine/data dalla finestra di dialogo Assegnazione **** canale, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare il programma di ricorrenza.

   >[!NOTE]
Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la suddivisione del giorno {#example-one}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| prima delle 8:00 | la risorsa nel canale viene riprodotta prima delle 8:00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 14:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa nel canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | la risorsa nel canale viene riprodotta prima delle 12:15 di ogni giorno e poi anche dopo le 12:45 di sera |
| Lun,Tue,Wed o Luna-Wed | la risorsa viene riprodotta nella risorsa nel canale da lunedì a mercoledì |
| il 1° gennaio dopo le 14:00 anche il 2° giorno di gennaio anche il 3 gennaio prima delle 3:00 | la risorsa nel canale inizia a giocare dopo le 14:00 del 1° gennaio, continua a giocare per l&#39;intera giornata il 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 giorno di gennaio dopo le 2:00 pm anche il 2-3 giorno di gennaio prima delle 3:00 | la risorsa nel canale avvia il lettore dopo le 14:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 del pomeriggio e continua a giocare fino alle 3:00 del 3 gennaio |

>[!NOTE]
È inoltre possibile utilizzare la notazione _militare dell&#39;ora_ (ovvero, 14:00) invece della notazione *AM/pm* (ovvero, 2:00 pm).

### Scomposizione Settimana {#week-parting}

1. Selezionate il canale e fate clic sul **dashboard** dalla barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/l&#39;ora di inizio e di fine/data dalla finestra di dialogo Assegnazione **** canale, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare il programma di ricorrenza.

   >[!NOTE]
Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la suddivisione settimanale {#example-two}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| Lun,Tue,Wed o Luna-Wed | la risorsa viene riprodotta nella risorsa nel canale da lunedì a mercoledì |
| prima delle 8:00 | la risorsa nel canale viene riprodotta prima delle 8:00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 14:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa nel canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | il canale gioca prima delle 12:15 pm ogni giorno e poi anche dopo 12:45 pm |

>[!NOTE]
È inoltre possibile utilizzare la notazione _militare dell&#39;ora_ (ovvero, 14:00) invece della notazione *AM/pm* (ovvero, 2:00 pm).


### Mese di suddivisione {#month-parting}

1. Selezionate il canale e fate clic sul **dashboard** dalla barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/l&#39;ora di inizio e di fine/data dalla finestra di dialogo Assegnazione **** canale, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare il programma di ricorrenza.

   >[!NOTE]
Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la suddivisione del mese {#example-three}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| di febbraio,maggio,agosto,novembre | la risorsa viene riprodotta nel canale in febbraio, maggio, agosto, novembre |

>[!NOTE]
Quando definite i giorni della settimana e dei mesi, potete utilizzare sia le note a mano breve che quelle a nome intero, ad esempio, Luna/Lunedì e Gen/Gennaio.

>[!NOTE]
È inoltre possibile utilizzare la notazione _militare dell&#39;ora_ (ovvero, 14:00) invece della notazione *AM/pm* (ovvero, 2:00 pm).

### Combinazione di partizioni {#combined-parting}

1. Selezionate il canale e fate clic sul **dashboard** dalla barra delle azioni per aprire il dashboard del canale.

1. Dopo aver immesso la data/l&#39;ora di inizio e di fine/data dalla finestra di dialogo Assegnazione **** canale, è possibile utilizzare un&#39;espressione o una versione di testo naturale per specificare il programma di ricorrenza.

   >[!NOTE]
Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la combinazione di partizioni {#example-four}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| dopo le 6:00 e prima delle 18:00 il lun,Wed di gen-mar | la risorsa viene riprodotta nel canale tra le 6 del mattino e le 6 del pomeriggio del lunedì e del mercoledì da gennaio a fine marzo |
| il 1° gennaio dopo le 14:00 anche il 2° giorno di gennaio anche il 3 gennaio prima delle 3:00 | la risorsa nel canale inizia a giocare dopo le 14:00 del 1° gennaio, continua a giocare per l&#39;intera giornata il 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 giorno di gennaio dopo le 2:00 pm anche il 2-3 giorno di gennaio prima delle 3:00 | la risorsa nel canale avvia il lettore dopo le 14:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 del pomeriggio e continua a giocare fino alle 3:00 del 3 gennaio |

>[!NOTE]
Quando definite i giorni della settimana e dei mesi, potete utilizzare sia le note a mano breve che quelle a nome intero, ad esempio, Luna/Lunedì e Gen/Gennaio.  Inoltre, è possibile utilizzare la notazione _militare dell&#39;ora_ (ovvero, 14:00) invece della notazione *AM/pm* (ovvero, 2:00 pm).

