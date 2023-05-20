---
title: Canale TakeOver permanente
seo-title: Perpetual TakeOver Channel
description: Segui questo caso d’uso per creare un canale di acquisizione permanente.
seo-description: Follow this Use Case on setting up a project that creates a Perpetual TakeOver channel that plays for a specific time day and time continuously.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 1%

---

# Canale TakeOver permanente {#perpetual-takeover-channel}

La pagina seguente presenta un caso d’uso con particolare attenzione alla configurazione di un progetto e spiega come creare un canale di acquisizione permanente che viene riprodotto continuamente per un giorno e un’ora specifici.

## Descrizione del caso d’uso {#use-case-description}

Questo caso d’uso spiega come creare un canale che *subentra* dal canale di riproduzione normale per uno schermo o un gruppo di schermi. L&#39;acquisizione avverrà perennemente per un giorno e un&#39;ora specifici.
Ad esempio, esiste un canale TakeOver permanente che viene riprodotto ogni venerdì dalle 9 alle 10. Durante questo periodo, nessun altro canale dovrebbe essere riprodotto. L’esempio seguente mostra la creazione di un canale di acquisizione perpetuo che viene riprodotto e consente di riprodurre i contenuti ogni mercoledì per 2 ore, dalle 14:00 alle 16:00.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di aver compreso come:

* **[Creare e gestire i canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire gli Schedules](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Configurazione del progetto {#setting-up-the-project}

Per impostare un progetto, segui i passaggi seguenti:

**Impostazione dei canali e della visualizzazione**

1. Creare un progetto AEM Screens con titolo **PerpetualTakeOver**, come illustrato di seguito.

   ![risorsa](assets/p_usecase1.png)

1. Creare un **MainAdChannel** nel **Canali** cartella.

   ![risorsa](assets/p_usecase2.png)

1. Seleziona la **MainAdChannel** e fai clic su **Modifica** dalla barra delle azioni. Trascina alcune risorse (immagini, video, sequenze incorporate) sul canale.

   ![risorsa](assets/p_usecase3.png)


   >[!NOTE]
   >Il **MainAdChannel** in questo esempio viene illustrato un canale di sequenza che riproduce il contenuto in modo continuo.

1. Creare un **TakeOver** canale che assume il controllo dei contenuti in **MainAdChannel** e verrà eseguito ogni mercoledì dalle 2:00 alle 16:00.

1. Seleziona la **TakeOver** e fai clic su **Modifica** dalla barra delle azioni. Trascina alcune risorse sul tuo canale. L’esempio seguente mostra un’immagine di una singola zona aggiunta a questo canale.

   ![risorsa](assets/p_usecase4.png)

1. Imposta una posizione e una visualizzazione per i canali. Ad esempio, la seguente posizione **LobbyPrincipale** e visualizzazione **MainLobbyDisplay** è configurato per questo progetto.

   ![risorsa](assets/p_usecase5.png)

**Assegnazione di canali a una visualizzazione**

1. Seleziona la visualizzazione **MainLobbyDisplay** dal **Posizioni** cartella. Clic **Assegna canale** dalla barra delle azioni per aprire **Assegnazione canale** .

   >[!NOTE]
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta **[Assegnazione canale](channel-assignment.md)**.

1. Compila i campi (**Percorso canale**, **Priorità**, e **Eventi supportati**) dalla **Assegnazione canale** e fare clic su **Salva** per assegnare **MainAdChannel** sul display.

   * **Percorso canale**: seleziona il percorso del file **MainAdChannel** channel
   * **Priorità**: imposta la priorità di questo canale su 1.
   * **Eventi supportati**: seleziona la **Caricamento iniziale** e **Schermata di inattività**.

   ![risorsa](assets/p_usecase6.png)

1. Seleziona la visualizzazione **TakeOver** dal **Posizioni** cartella. Clic **Assegna canale** dalla barra delle azioni per assegnare il canale di acquisizione.

1. Per assegnare **TakeOver** canale per la visualizzazione a un orario pianificato e compila i campi seguenti dal **Assegnazione canale** e fare clic su **Salva**:

   * **Percorso canale**: seleziona il percorso del file **TakeOver** channel
   * **Priorità**: imposta la priorità di questo canale su un valore maggiore di **MainAdChannel**. Ad esempio, la priorità impostata in questo esempio è 8.
   * **Eventi supportati**: seleziona la **Schermata di inattività** e **Timer**.
   * **Pianificazione**: immetti il testo per la pianificazione in base alla quale il canale deve eseguire la visualizzazione. Il testo nella **Pianificazione** menzionato in questo esempio è *il mercoledì dopo le 14:00 e prima delle 16:00*.

      >[!NOTE]
      >Per ulteriori informazioni sulle espressioni puoi aggiungere al **Pianificazione**, fare riferimento a [Espressioni di esempio](#example-expressions) sezione successiva.
   * **attivo da**: data e ora di inizio.
   * **attivo fino a**: data e ora di fine.

      Ad esempio, il testo in **Pianificazione** e **attivo da** e **attivo fino a** La data e l’ora consentono di riprodurre il contenuto ogni mercoledì dalle 14:00 alle 16:00.


      ![risorsa](assets/p_usecase7.png)

      Passa alla visualizzazione da **TakeOver** —> **Posizioni** —> **LobbyPrincipale** —> **MainLobbyDisplay** e fai clic su **Dashboard** dalla barra delle azioni per visualizzare i canali assegnati con le relative priorità, come illustrato di seguito.

      >[!NOTE]
      >È obbligatorio impostare come massima la priorità del canale di acquisizione.

      ![risorsa](assets/p_usecase8.png)
Ora, il **TakeOver** canale prenderà il controllo della **MainAdChannel** alle 14:00 per due ore fino alle 16:00 ogni mercoledì e riprodurre il contenuto dal 9 gennaio 2020 al 31 gennaio 2020.

## Espressioni di esempio {#example-expressions}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| prima delle 08:00 | il canale viene riprodotto ogni giorno prima delle 8:00 |
| dopo le 2:00 | il canale viene riprodotto ogni giorno dopo le 14:00 |
| dopo le 12:15 e prima delle 12:45 | il canale viene riprodotto ogni giorno dopo le 12:15 per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | il canale viene riprodotto ogni giorno prima delle 12:15 e poi anche dopo le 12:45 |
| il 1° gennaio dopo le 14:00 anche il 2 gennaio anche il 3 gennaio prima delle 03:00 | il canale inizia la riproduzione dopo le 14:00 del 1° gennaio e continua per l’intera giornata del 2 gennaio fino alle 03:00 del 3 gennaio |
| l&#39;1-2 giorno di gennaio dopo le 14:00 anche il 2-3 giorno di gennaio prima delle 3:00 | il canale avvia il lettore dopo le 14:00 del 1° gennaio, continua la riproduzione fino alle 03:00 del 2 gennaio, quindi ricomincia il 2 gennaio alle 14:00 e continua fino alle 03:00 del 3 gennaio |

>[!NOTE]
>
>Puoi anche utilizzare _ora militare_ notazione (ovvero 14:00) invece di *am/pm* notazione (ovvero, 14:00).
