---
title: Canale TakeOver per uso singolo
seo-title: Canale TakeOver per uso singolo
description: Seguite questo esempio per creare un canale TakeOver per un singolo utilizzo.
seo-description: Seguite questo esempio per creare un canale TakeOver per un singolo utilizzo.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 2%

---


# Canale TakeOver singolo {#single-use-takeover-channel}

Nella pagina seguente viene illustrato un esempio di utilizzo che mette in evidenza l’impostazione di un progetto per la creazione di un singolo canale TakeOver da riprodurre una sola volta per un’ora specifica.


## Descrizione di un caso d’uso {#use-case-description}

Questo caso d&#39;uso spiega come creare un canale che *prende il posto di* dal canale di riproduzione normale per uno schermo o un gruppo di display. L&#39;acquisizione avverrà solo una volta e per un periodo di tempo determinato.
Ad esempio, esiste un canale TakeOver singolo che viene riprodotto il venerdì dalle 9 alle 10. Durante questo periodo, nessun altro canale dovrebbe essere riprodotto. Prima e dopo questo periodo, il canale di singola acquisizione non verrà riprodotto. L&#39;esempio seguente mostra la creazione di un singolo canale di acquisizione che consente la riproduzione dei contenuti per 2 minuti prima delle 12:00 del 31 dicembre fino alle 12:01.

### Precondizioni {#preconditions}

Prima di iniziare questo caso di utilizzo, accertatevi di comprendere come:

* **[Creazione e gestione di canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori primari {#primary-actors}

Autori contenuto

## Impostazione del progetto {#setting-up-the-project}

Per impostare un progetto, effettuate le seguenti operazioni:

**Impostazione dei canali e della visualizzazione**

1. Create un progetto AEM Screens  denominato **SingleUseTakeOver**, come illustrato di seguito.

   ![risorsa](assets/single-takeover1.png)

1. Create un **MainAdChannel** nella cartella **Channels**.

   ![risorsa](assets/single-takeover2.png)

1. Selezionare **MainAdChannel** e fare clic su **Edit** dalla barra delle azioni. Trascinate alcune risorse (immagini, video, sequenze incorporate) sul canale.

   ![risorsa](assets/single-takeover2.png)


   >[!NOTE]
   >In questo esempio, **MainAdChannel** mostra un canale di sequenza che riproduce continuamente il contenuto.

   ![risorsa](assets/single-takeover3.png)

1. Create un canale **TakeOver** che occupi il contenuto in **MainAdChannel** e che verrà riprodotto solo per un giorno e un&#39;ora specifici.

1. Selezionare il **TakeOver** e fare clic su **Edit** dalla barra delle azioni. Trascinate alcune risorse sul canale. L&#39;esempio seguente mostra un&#39;immagine a zona singola aggiunta a questo canale.

   ![risorsa](assets/single-takeover4.png)

1. Configurate una posizione e una visualizzazione per i canali. Ad esempio, per questo progetto è impostata la posizione seguente **Lobby** e la visualizzazione **MainLobbyDisplay**.

   ![risorsa](assets/single-takeover5.png)

**Assegnazione di canali a una visualizzazione**

1. Selezionare il display **MainLobbyDisplay** dalla cartella **Locations**. Fare clic su **Assegna canale** dalla barra delle azioni.

   ![risorsa](assets/single-takeover6.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a **[Assegnazione canale](channel-assignment.md)**.

1. Compilare i campi (**Percorso canale**, **Priorità** e **Eventi supportati**) dalla finestra di dialogo **Assegnazione canale** e fare clic su **Salva**. È stato assegnato il **MainAdChannel** al display.

   ![risorsa](assets/single-takeover7.png)

1. Selezionare il display **TakeOver** dalla cartella **Locations**. Fate clic su **Assegna canale** dalla barra delle azioni per assegnare il canale di acquisizione a uso singolo.

1. Per assegnare il canale **TakeOver** al display in un momento programmato e compilare i campi seguenti dalla finestra di dialogo **Assegnazione canale**, quindi fare clic su **Salva**:

   * **Percorso** canale: Selezionare il percorso del canale TakeOver
   * **Priorità**: Impostate la priorità di questo canale maggiore di  **MainAdChannel**. Ad esempio, la priorità impostata in questo esempio è 8.

      >[!NOTE]
      >Priorità può essere qualsiasi valore superiore al valore di priorità del canale di riproduzione normale.
   * **Eventi** supportati: Selezionate  **Idle** Screenand  **Timer** (Schermata inattiva e Timer).
   * **Pianificazione**: Immettere il testo per la pianificazione che si desidera che il canale esegua la visualizzazione. Ad esempio, il testo qui consente la riproduzione del contenuto 2 minuti prima delle 12:00 del 31 dicembre fino alle 12:01.
Il testo nella **Schedule** citata in questo esempio è *il 31 dicembre dopo le 23:58 e anche il 1 giorno di gennaio prima delle 00.01*.

      ![risorsa](assets/single-takeover8.png)

      Andate alla visualizzazione da **SingleUseTakeOver** —> **Locations** —> **Lobby** —> **MainLobbyDisplay** e fate clic su **Dashboard** dalla barra delle azioni per visualizzare i canali assegnati con le relative priorità, come mostrato di seguito.

      >[!NOTE]
      >È obbligatorio impostare la priorità del canale di acquisizione come massima.

      ![risorsa](assets/single-takeover9.png)

>[!NOTE]
>
>È consigliabile eliminare il canale One Use TakeOver una volta riprodotto.