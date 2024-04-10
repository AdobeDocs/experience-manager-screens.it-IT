---
title: Canale TakeOver monouso
description: Segui questo caso d’uso per creare un canale TakeOver monouso.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# Canale TakeOver per singolo utilizzo {#single-use-takeover-channel}

Nella pagina seguente viene illustrato un caso d’uso che pone l’accento sulla configurazione di un progetto per la creazione di un singolo canale TakeOver che viene riprodotto una volta per un periodo di tempo specifico.


## Descrizione del caso d’uso {#use-case-description}

Questo caso d’uso spiega come creare un canale che *subentra* dal canale di riproduzione normale per un display o un gruppo di display. L&#39;acquisizione avviene una sola volta e per un periodo di tempo specifico.

Ad esempio, esiste un canale Single TakeOver che viene riprodotto da venerdì 9:00 a mezzanotte. Durante questo periodo, nessun altro canale dovrebbe essere riprodotto. Prima e dopo questo periodo di tempo, il canale Single Use Takeover non viene riprodotto. L’esempio seguente illustra la creazione di un singolo canale di acquisizione che consente la riproduzione del contenuto per 2 minuti prima delle 00:00 del 31 dicembre fino alle 00:01.

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

1. Creare un progetto AEM Screens con titolo **SingleUseTakeOver**, come illustrato di seguito.

   ![risorsa](assets/single-takeover1.png)

1. Creare un **MainAdChannel** nel **Canali** cartella.

   ![risorsa](assets/single-takeover2.png)

1. Seleziona la **MainAdChannel** e fai clic su **Modifica** dalla barra delle azioni. Trascina alcune risorse (immagini, video, sequenze incorporate) sul canale.

   ![risorsa](assets/single-takeover2.png)


   >[!NOTE]
   >Il **MainAdChannel** in questo esempio viene illustrato un canale di sequenza che riproduce il contenuto in modo continuo.

   ![risorsa](assets/single-takeover3.png)

1. Creare un **TakeOver** canale che assume il controllo dei contenuti in **MainAdChannel** e viene riprodotto solo per un giorno e un’ora specifici.

1. Seleziona la **TakeOver** e fai clic su **Modifica** dalla barra delle azioni. Trascina alcune risorse nel canale. L’esempio seguente mostra un’immagine di una singola zona aggiunta a questo canale.

   ![risorsa](assets/single-takeover4.png)

1. Imposta una posizione e una visualizzazione per i canali. Ad esempio, i seguenti **Lobby** posizione e  **MainLobbyDisplay** sono impostati per questo progetto.

   ![risorsa](assets/single-takeover5.png)

**Assegnazione di canali a una visualizzazione**

1. Seleziona la visualizzazione **MainLobbyDisplay** dal **Posizioni** cartella. Clic **Assegna canale** dalla barra delle azioni.

   ![risorsa](assets/single-takeover6.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta **[Assegnazione canale](channel-assignment.md)**.

1. Compila i campi (**Percorso canale**, **Priorità**, e **Eventi supportati**) dalla **Assegnazione canale** e fare clic su **Salva**. Ora hai assegnato il **MainAdChannel** sul display.

   ![risorsa](assets/single-takeover7.png)

1. Seleziona la visualizzazione **TakeOver** dal **Posizioni** cartella. Clic **Assegna canale** dalla barra delle azioni, in modo da poter assegnare il canale di acquisizione monouso.

1. Assegna la **TakeOver** canale per la visualizzazione a un orario pianificato e compila i campi seguenti dal **Assegnazione canale** e fare clic su **Salva**:

   * **Percorso canale**: seleziona il percorso del canale TakeOver
   * **Priorità**: imposta la priorità di questo canale su un valore maggiore di **MainAdChannel**. Ad esempio, la priorità impostata in questo esempio è 8.

     >[!NOTE]
     >Priorità può essere qualsiasi valore superiore al valore di priorità del canale di riproduzione normale.
   * **Eventi supportati**: seleziona la **Schermata di inattività** e **Timer**.
   * **Pianificazione**: immetti il testo per la pianificazione in base alla quale il canale deve eseguire la visualizzazione. Ad esempio, il testo qui consente la riproduzione del contenuto 2 minuti prima delle 00:00 del 31 dicembre fino alle 00:01 Il testo nella **Pianificazione** menzionato in questo esempio è *il 31 dicembre dopo le 23:58 e anche il 1° gennaio prima delle 00.01*.

     ![risorsa](assets/single-takeover8.png)

     Passa alla visualizzazione da **SingleUseTakeOver** > **Posizioni** > **Lobby** > **MainLobbyDisplay** e fai clic su **Dashboard** dalla barra delle azioni, in modo da poter visualizzare i canali assegnati con le relative priorità, come illustrato di seguito.

     >[!NOTE]
     >È obbligatorio impostare come massima la priorità del canale di acquisizione.

     ![risorsa](assets/single-takeover9.png)

>[!NOTE]
>
>È consigliabile eliminare il canale TakeOver monouso, una volta riprodotto.
