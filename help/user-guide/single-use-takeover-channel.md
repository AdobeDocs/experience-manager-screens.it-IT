---
title: Canale TakeOver monouso
description: Segui questo caso d’uso per creare un canale di acquisizione monouso.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Canale TakeOver per singolo utilizzo {#single-use-takeover-channel}

Nella pagina seguente viene illustrato un caso d’uso che pone l’accento sulla configurazione di un progetto per la creazione di un singolo canale TakeOver che viene riprodotto una volta per un periodo di tempo specifico.

## Descrizione del caso d’uso {#use-case-description}

In questo caso d&#39;uso viene illustrato come creare un canale che *rileva* dal normale canale di riproduzione per una visualizzazione o un gruppo di visualizzazioni. L&#39;acquisizione avviene una sola volta e per un periodo di tempo specifico.

Ad esempio, esiste un canale Single TakeOver che viene riprodotto da venerdì 9:00 a mezzanotte. Durante questo periodo, nessun altro canale dovrebbe essere riprodotto. Prima e dopo questo periodo di tempo, il canale Single Use Takeover non viene riprodotto. L’esempio seguente illustra la creazione di un singolo canale di acquisizione che consente la riproduzione del contenuto per 2 minuti prima delle 00:00 del 31 dicembre fino alle 00:01.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di aver compreso come:

* **[Crea e gestisci canali](managing-channels.md)**
* **[Crea e gestisci posizioni](managing-locations.md)**
* **[Crea e gestisci pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Configurazione del progetto {#setting-up-the-project}

Per impostare un progetto, segui i passaggi seguenti:

**Configurazione di canali e visualizzazione**

1. Crea un progetto AEM Screens con titolo **SingleUseTakeOver**, come illustrato di seguito.

   ![risorsa](assets/single-takeover1.png)

1. Crea un **MainAdChannel** nella cartella **Channels**.

   ![risorsa](assets/single-takeover2.png)

1. Fai clic su **MainAdChannel** e fai clic su **Modifica** nella barra delle azioni. Trascina alcune risorse (immagini, video, sequenze incorporate) sul canale.

   ![risorsa](assets/single-takeover2.png)


   >[!NOTE]
   >**MainAdChannel** in questo esempio illustra un canale di sequenza che riproduce il contenuto in modo continuo.

   ![risorsa](assets/single-takeover3.png)

1. Crea un canale **TakeOver** che assume il contenuto in **MainAdChannel** e viene riprodotto solo per un giorno e un&#39;ora specifici.

1. Fai clic su **TakeOver** e fai clic su **Modifica** nella barra delle azioni. Trascina alcune risorse nel canale. L’esempio seguente mostra un’immagine di una singola zona aggiunta a questo canale.

   ![risorsa](assets/single-takeover4.png)

1. Imposta una posizione e una visualizzazione per i canali. Ad esempio, per questo progetto sono configurate la seguente posizione **Lobby** e la seguente visualizzazione **MainLobbyDisplay**.

   ![risorsa](assets/single-takeover5.png)

**Assegnazione di canali a una visualizzazione**

1. Fare clic sulla visualizzazione **MainLobbyDisplay** dalla cartella **Locations**. Fare clic su **Assegna canale** nella barra delle azioni.

   ![risorsa](assets/single-takeover6.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta **[Assegnazione canale](channel-assignment.md)**.

1. Compilare i campi (**Percorso canale**, **Priorità** e **Eventi supportati**) dalla finestra di dialogo **Assegnazione canale** e fare clic su **Salva**. Hai assegnato **MainAdChannel** alla tua visualizzazione.

   ![risorsa](assets/single-takeover7.png)

1. Fai clic sulla cartella **Percorsi** per visualizzare **Acquisisci**. Fai clic su **Assegna canale** dalla barra delle azioni per assegnare il canale di acquisizione monouso.

1. Assegna il canale **TakeOver** alla visualizzazione in un orario pianificato e popola i campi seguenti dalla finestra di dialogo **Assegnazione canale** e fai clic su **Salva**:

   * **Percorso canale**: fare clic sul percorso del canale TakeOver
   * **Priorità**: imposta la priorità di questo canale maggiore di **MainAdChannel**. Ad esempio, la priorità impostata in questo esempio è 8.

     >[!NOTE]
     >Priorità può essere qualsiasi valore superiore al valore di priorità del canale di riproduzione normale.
   * **Eventi supportati**: fare clic sulla **schermata di inattività** e **Timer**.
   * **Pianificazione**: immettere il testo per la pianificazione che si desidera venga eseguita sul display da questo canale. Ad esempio, il testo qui consente la riproduzione del contenuto 2 minuti prima delle 00:00 del 31 dicembre fino alle 00:01
Il testo nella **Pianificazione** menzionata in questo esempio è *del 31 dicembre dopo le 23:58 e anche del 1° gennaio prima delle 00.01*.

     ![risorsa](assets/single-takeover8.png)

     Passa alla visualizzazione da **SingleUseTakeOver** > **Percorsi** > **Lobby** > **MainLobbyDisplay**. Fai clic su **Dashboard** nella barra delle azioni per visualizzare i canali assegnati con le relative priorità, come illustrato di seguito.

     >[!NOTE]
     >È obbligatorio impostare come massima la priorità del canale di acquisizione.

     ![risorsa](assets/single-takeover9.png)

>[!NOTE]
>
>È consigliabile eliminare il canale TakeOver monouso, una volta riprodotto.
