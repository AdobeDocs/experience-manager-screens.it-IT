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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Attivazione A Livello Di Canale - Riproduzione A Singolo Evento {#channel-level-activation-single-event-playback}

L'utilizzo dell'attivazione a livello di canale illustra i seguenti argomenti:

* Panoramica
* Utilizzo dell'attivazione a livello di canale come riproduzione di un singolo evento

## Panoramica {#overview}

***Attivazione*** a livello di canale consente ai canali di passare a una determinata pianificazione. Il singolo canale evento sostituisce il canale principale dopo una programmazione impostata e viene riprodotto per un particolare momento, fino a quando il canale principale non riproduce il contenuto.

L'esempio seguente fornisce una soluzione concentrandosi sui seguenti termini chiave:

* un canale ***di sequenza*** principale per la sequenza globale
* un canale ***evento*** singolo che viene eseguito una sola volta alla volta
* una pianificazione ***impostata e una priorità*** per l'evento di riproduzione singola che si verifica all'interno del canale della sequenza principale

## Utilizzo dell'attivazione a livello di canale {#using-channel-level-activation}

La sezione seguente illustra la creazione di un singolo evento riprodotto all’interno di un canale per un progetto AEM Screens.

### Prerequisiti {#prerequisites}

Prima di iniziare ad implementare questa funzionalità, accertatevi di disporre dei seguenti prerequisiti per iniziare a implementare l'attivazione a livello di canale:

* Crea un progetto AEM Screens, in questo esempio, Attivazione a livello di **canale**

* Crea un canale come **MainAdChannel** nella cartella **Channels (Canali** )

* Crea un altro canale come **TargetingSinglePlay** nella cartella **Channels (Canali** )

* Aggiunta di risorse rilevanti a entrambi i canali

L'immagine seguente mostra il progetto Attivazione **a livello di** canale con canali **MainAdChannel** e **TargetingSinglePlay** nella cartella **Channels** .

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

   1. Andate a Attivazione **a livello di** canale &gt; **Posizioni** &gt; **Regione**.
   1. Selezionate **Regione** e fate clic su **+ Crea** dalla barra delle azioni.
   1. Selezionate **Visualizza** dalla procedura guidata e create una visualizzazione con titolo **Visualizzazione area.**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Assegna canali da visualizzare**

   Per **MainAdChannel:**

   1. Andate a Attivazione **a livello di** canale &gt; **Posizioni** &gt; **Regione** &gt; Visualizzazione **a livello di canale e fate clic su** Assegna canale **** dalla barra delle azioni.
   1. **Viene visualizzata la finestra di dialogo Assegnazione** canale.
   1. Select **Reference Channel**.. by path.
   1. Selezionate il percorso **del** canale come Attivazione **a livello di** canale &gt; ***Canali*** &gt; ***MainAdChannel***.
   1. Il ruolo **** canale viene popolato come canale **principale**.
   1. Selezionate la **priorità** come **1**.
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Fai clic su **Salva**.
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Potete anche assegnare il canale dal pannello di visualizzazione accedendo a Attivazione **a livello di** canale &gt; **Posizioni** &gt; **Regione** &gt; **Visualizzazione** area e facendo clic su **Dashboard** dalla barra delle azioni. Fate clic su **+ Assegna canale** dal pannello CANALI E PIANIFICAZIONI **ASSEGNATI** .

   Analogamente, assegna canale **TargetingSinglePlay** per display**:

   1. Andate a Attivazione **a livello di** canale —&gt; **Posizioni** —&gt; **Regione** —&gt; **Visualizzazione** a livello di canale e fate clic su **Assegna canale** dalla barra delle azioni.
   1. **Viene visualizzata la finestra di dialogo Assegnazione** canale.
   1. Select **Reference Channel**.. by path.
   1. Selezionate Percorso **** canale come Attivazione **a livello di** canale* —&gt; ***Canali*** —&gt; ***TargetingSinglePlay***.
   1. Il ruolo **** del canale viene popolato come **mirato per singola** riproduzione.
   1. Impostate la **priorità** su **2**.
   1. Selezionate gli eventi **** supportati come Carico **** iniziale, Schermo **inattivo e** Timer ****, *come mostrato nella figura seguente.
   1. Scegli la data in **attivo dal** 27 novembre 2018 11:59 pm e in **attivo fino** al 28 novembre 2018 12:05 am.
   1. Fai clic su **Salva**.
   >[!CAUTION]
   È necessario impostare la priorità per il canale **TargetingSinglePlay** più alto del canale **MainAdSegment** .

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Per scegliere lo stesso giorno, è necessario selezionare il giorno successivo e modificare manualmente la data nello stesso giorno, ma per un'ora successiva. Questo impedisce all'utente di selezionare una data precedente. Fare riferimento all'esempio seguente:

   ![new1](assets/new1.gif)

## Visualizzazione dei risultati {#viewing-the-results}

Una volta impostata la visualizzazione dei canali, avvia il lettore AEM Screens per visualizzare il contenuto.

Il lettore visualizza il contenuto di **MainAdChannel** ed esattamente alle 11:59 (come impostato nella pianificazione), il canale **TargetingSinglePlay** visualizzerà il contenuto fino alle 12:05 e il canale **MainAdChannel** riprenderà a riprodurlo.

>[!NOTE]
Per informazioni su AEM Screen Player, consulta le risorse seguenti:
* [Download di AEM Screens Player](https://download.macromedia.com/screens/)
* [Utilizzo di AEM Screens Player](working-with-screens-player.md)

