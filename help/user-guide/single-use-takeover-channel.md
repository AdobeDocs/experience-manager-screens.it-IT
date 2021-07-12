---
title: Canale TakeOver per uso singolo
seo-title: Canale TakeOver per uso singolo
description: Segui questo caso d’uso per creare un singolo canale TakeOver.
seo-description: Segui questo caso d’uso per creare un singolo canale TakeOver.
contentOwner: jsyal
feature: Creazione di esperienze in Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 2%

---

# Canale TakeOver per uso singolo {#single-use-takeover-channel}

Nella pagina seguente viene illustrato un caso d’uso che mette in evidenza l’impostazione di un progetto su come creare un singolo canale TakeOver che viene riprodotto una sola volta per un momento specifico.


## Descrizione di un caso d’uso {#use-case-description}

Questo caso d&#39;uso spiega come creare un canale che *prende il controllo di* dal canale di riproduzione normale per una visualizzazione o un gruppo di display. L&#39;acquisizione avverrà solo una volta e per un momento specifico.
Ad esempio, esiste un singolo canale TakeOver che viene riprodotto il venerdì dalle 9 alle 10. Durante questo periodo, nessun altro canale dovrebbe giocare. Prima e dopo questo periodo, il canale di acquisizione a uso singolo non verrà riprodotto. L’esempio seguente mostra la creazione di un singolo canale di acquisizione riprodotto che consente la riproduzione dei contenuti per 2 minuti prima delle ore 12:00 del 31 dicembre fino alle ore 12:01.

### Condizioni preliminari {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di comprendere come:

* **[Creare e gestire i canali](managing-channels.md)**
* **[Creare e gestire posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori primari {#primary-actors}

Autori di contenuti

## Impostazione del progetto {#setting-up-the-project}

Per impostare un progetto, effettua le seguenti operazioni:

**Impostazione dei canali e della visualizzazione**

1. Crea un progetto AEM Screens denominato **SingleUseTakeOver**, come illustrato di seguito.

   ![risorsa](assets/single-takeover1.png)

1. Crea un **MainAdChannel** nella cartella **Canali**.

   ![risorsa](assets/single-takeover2.png)

1. Seleziona il **MainAdChannel** e fai clic su **Modifica** nella barra delle azioni. Trascina alcune risorse (immagini, video, sequenze incorporate) sul tuo canale.

   ![risorsa](assets/single-takeover2.png)


   >[!NOTE]
   >In questo esempio **MainAdChannel** viene mostrato un canale per sequenza che riproduce continuamente il contenuto.

   ![risorsa](assets/single-takeover3.png)

1. Crea un canale **TakeOver** che acquisisce il contenuto in **MainAdChannel** e lo riproduce solo per un giorno e un&#39;ora specifici.

1. Seleziona il **TakeOver** e fai clic su **Modifica** nella barra delle azioni. Trascina alcune risorse sul tuo canale. L’esempio seguente mostra un’immagine a una singola zona aggiunta al canale.

   ![risorsa](assets/single-takeover4.png)

1. Imposta una posizione e una visualizzazione per i tuoi canali. Ad esempio, per questo progetto è impostata la seguente posizione **Lobby** e la seguente visualizzazione **MainLobbyDisplay**.

   ![risorsa](assets/single-takeover5.png)

**Assegnazione di canali a una visualizzazione**

1. Selezionare il display **MainLobbyDisplay** dalla cartella **Locations**. Fai clic su **Assegna canale** dalla barra delle azioni.

   ![risorsa](assets/single-takeover6.png)

   >[!NOTE]
   >Per scoprire come assegnare un canale a una visualizzazione, fai riferimento a **[Assegnazione canale](channel-assignment.md)**.

1. Compila i campi (**Percorso canale**, **Priorità** e **Eventi supportati**) nella finestra di dialogo **Assegnazione canale** e fai clic su **Salva**. Ora hai assegnato il **MainAdChannel** al tuo display.

   ![risorsa](assets/single-takeover7.png)

1. Seleziona la visualizzazione **TakeOver** dalla cartella **Posizioni**. Fai clic su **Assegna canale** dalla barra delle azioni per assegnare il canale di acquisizione a uso singolo.

1. Per assegnare il canale **TakeOver** alla visualizzazione in un momento pianificato e compilare i campi seguenti dalla finestra di dialogo **Assegnazione canale** e fare clic su **Salva**:

   * **Percorso** canale: Selezionare il percorso del canale TakeOver
   * **Priorità**: Imposta la priorità di questo canale maggiore di  **MainAdChannel**. Ad esempio, la priorità impostata in questo esempio è 8.

      >[!NOTE]
      >La priorità può essere qualsiasi valore superiore al valore di priorità del canale normalmente in esecuzione.
   * **Eventi** supportati: Selezionare  **Idle** Screenand  **Timer**.
   * **Pianificazione**: Immettere il testo per la pianificazione che si desidera che il canale esegua la visualizzazione. Ad esempio, il testo qui consente la riproduzione del contenuto 2 minuti prima delle 12:00 del 31 dicembre fino alle 12:01.
Il testo nel **Programma** menzionato in questo esempio è *il 31 dicembre dopo le 23:58 e anche il 1° gennaio prima delle 00.01*.

      ![risorsa](assets/single-takeover8.png)

      Passa alla visualizzazione da **SingleUseTakeOver** —> **Posizioni** —> **Lobby** —> **MainLobbyDisplay** e fai clic su **Dashboard** dalla barra delle azioni per visualizzare i canali assegnati con le relative priorità, come mostrato di seguito.

      >[!NOTE]
      >È obbligatorio impostare la priorità del canale di acquisizione come la più alta.

      ![risorsa](assets/single-takeover9.png)

>[!NOTE]
>
>È consigliabile eliminare il canale TakeOver per uso singolo una volta riprodotto.
