---
title: Canale di acquisizione perpetuo
seo-title: Canale di acquisizione perpetuo
description: Segui questo caso d’uso per creare un canale TakeOver permanente.
seo-description: Segui questo caso d’uso per configurare un progetto che crea un canale Perpetual TakeOver che viene riprodotto continuamente per un giorno e un’ora specifici.
contentOwner: jsyal
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 1%

---


# Canale di acquisizione perpetuo {#perpetual-takeover-channel}

Nella pagina seguente viene illustrato un caso d’uso che mette in evidenza l’impostazione di un progetto su come creare un canale Perpetual TakeOver che viene riprodotto continuamente per un giorno e un’ora specifici.

## Descrizione di un caso d’uso {#use-case-description}

Questo caso d&#39;uso spiega come creare un canale che *prende il controllo di* dal canale di riproduzione normale per una visualizzazione o un gruppo di display. L&#39;acquisizione avverrà per un giorno e un&#39;ora specifici in modo permanente.
Ad esempio, c&#39;è un canale Perpetual TakeOver che riproduce ogni venerdì dalle 9 alle 10. Durante questo periodo, nessun altro canale dovrebbe giocare. L&#39;esempio seguente mostra la creazione di un canale di acquisizione perpetuo che riproduce consente la riproduzione dei contenuti ogni mercoledì per 2 ore dalle 2:00 alle 16:00.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di comprendere come:

* **[Creare e gestire i canali](managing-channels.md)**
* **[Creare e gestire posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Configurazione del progetto {#setting-up-the-project}

Per impostare un progetto, effettua le seguenti operazioni:

**Impostazione dei canali e della visualizzazione**

1. Crea un progetto AEM Screens denominato **PerpetualTakeOver**, come illustrato di seguito.

   ![risorsa](assets/p_usecase1.png)

1. Crea un **MainAdChannel** nella cartella **Canali**.

   ![risorsa](assets/p_usecase2.png)

1. Seleziona il **MainAdChannel** e fai clic su **Modifica** nella barra delle azioni. Trascina alcune risorse (immagini, video, sequenze incorporate) sul tuo canale.

   ![risorsa](assets/p_usecase3.png)


   >[!NOTE]
   >In questo esempio **MainAdChannel** viene mostrato un canale per sequenza che riproduce continuamente il contenuto.

1. Crea un canale **TakeOver** che acquisisca il contenuto in **MainAdChannel** e riprodurrà ogni mercoledì dalle 2:00 alle 4:00.

1. Seleziona il **TakeOver** e fai clic su **Modifica** nella barra delle azioni. Trascina alcune risorse sul tuo canale. L’esempio seguente mostra un’immagine a una singola zona aggiunta al canale.

   ![risorsa](assets/p_usecase4.png)

1. Imposta una posizione e una visualizzazione per i tuoi canali. Per questo progetto, ad esempio, è impostata la seguente posizione **MainLobby** e la seguente visualizzazione **MainLobbyDisplay**.

   ![risorsa](assets/p_usecase5.png)

**Assegnazione di canali a una visualizzazione**

1. Selezionare il display **MainLobbyDisplay** dalla cartella **Locations**. Fai clic su **Assegna canale** nella barra delle azioni per aprire la finestra di dialogo **Assegnazione canale**.

   >[!NOTE]
   >Per scoprire come assegnare un canale a una visualizzazione, fai riferimento a **[Assegnazione canale](channel-assignment.md)**.

1. Compila i campi (**Percorso canale**, **Priorità** e **Eventi supportati**) dalla finestra di dialogo **Assegnazione canale** e fai clic su **Salva** per assegnare il **MainAdChannel** alla visualizzazione .

   * **Percorso** canale: Seleziona il percorso del canale  **** MainAdChannel
   * **Priorità**: Imposta la priorità del canale su 1.
   * **Eventi** supportati: Seleziona la  **schermata** Caricamento iniziale e  **Inattivo**.

   ![risorsa](assets/p_usecase6.png)

1. Seleziona la visualizzazione **TakeOver** dalla cartella **Posizioni**. Fai clic su **Assegna canale** dalla barra delle azioni per assegnare il canale di acquisizione.

1. Per assegnare il canale **TakeOver** alla visualizzazione in un momento pianificato e compilare i campi seguenti dalla finestra di dialogo **Assegnazione canale** e fare clic su **Salva**:

   * **Percorso** canale: Selezionare il percorso del  **** TakeOverchannel
   * **Priorità**: Imposta la priorità di questo canale maggiore di  **MainAdChannel**. Ad esempio, la priorità impostata in questo esempio è 8.
   * **Eventi** supportati: Selezionare  **Idle** Screenand  **Timer**.
   * **Pianificazione**: Immettere il testo per la pianificazione che si desidera che il canale esegua la visualizzazione. Il testo in **Schedule** menzionato in questo esempio è *il mercoledì dopo le 14:00 e prima delle 16:00*.

      >[!NOTE]
      >Per ulteriori informazioni sulle espressioni che puoi aggiungere alla sezione **Pianificazione**, consulta la sezione [Espressioni di esempio](#example-expressions) riportata di seguito.
   * **attivo da**: Data e ora di inizio.
   * **attivo fino** a: Data e ora di fine.

      Ad esempio, il testo in **Pianificazione** e **attivo da** e **attivo fino a** data e ora qui consente la riproduzione del contenuto ogni mercoledì dalle 2:00 alle 16:00.


      ![risorsa](assets/p_usecase7.png)

      Passa alla visualizzazione da **TakeOver** —> **Posizioni** —> **MainLobby** —> **MainLobbyDisplay** e fai clic su **Dashboard** nella barra delle azioni per visualizzare i canali assegnati con le relative priorità, come mostrato di seguito.

      >[!NOTE]
      >È obbligatorio impostare la priorità del canale di acquisizione come la più alta.

      ![](assets/p_usecase8.png)
assetNow,  **** TakeOverchannel sostituirà  **** MainAdChannelat 2:00 per due ore fino alle 16:00 ogni mercoledì e riprodurrà i propri contenuti dal 09 gennaio 2020 al 31 gennaio 2020.

## Espressioni di esempio {#example-expressions}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| prima delle 8:00 | il canale suona prima delle 8:00 ogni giorno |
| dopo le 14:00 | il canale gioca dopo le 2:00 pm ogni giorno |
| dopo le 12:15 e prima delle 12:45 | il canale gioca dopo le 12:15 ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | il canale gioca prima 12:15 ogni giorno e poi anche dopo 12:45 pm |
| il 1° gennaio dopo le 14.00 anche il 2° giorno di gennaio anche il 3° giorno di gennaio prima delle 3.00 | il canale inizia a giocare dopo le 2:00 del 1° gennaio, continua a giocare per tutta la giornata del 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 gennaio dopo le 2:00 del pomeriggio anche il 2-3 di gennaio prima delle 3:00 | il canale avvia il lettore dopo le 2:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 pm e continua a giocare fino alle 3:00 del 3 gennaio |

>[!NOTE]
>
>È inoltre possibile utilizzare la notazione _tempo militare_ (ovvero, 14:00) invece della notazione *am/pm* (ovvero 2:00 pm).
