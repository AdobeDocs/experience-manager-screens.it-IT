---
title: Canale di emergenza
seo-title: Emergency Channel
description: Segui questo esempio di caso d’uso per scoprire come creare e gestire un canale di emergenza che l’autore del contenuto può passare da un canale di sequenza in caso di una precondizione.
seo-description: Follow this use case example to learn about creating and managing an emergency channel that the content author can switch from a sequence channel in case of a precondition.
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 1%

---

# Canale di emergenza {#emergency-channel}

## Descrizione del caso d’uso {#use-case-description}

Questa sezione descrive un esempio di caso d’uso che pone l’accento sulla creazione e la gestione di un canale di emergenza che l’autore del contenuto può passare da un canale di sequenza in caso di una precondizione.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di aver compreso come:

* **[Creare e gestire i canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire gli Schedules](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Flusso di base: configurazione del progetto {#basic-flow-setting-up-the-project}

Per impostare un canale di emergenza, procedere come segue:

1. Creare un progetto AEM Screens denominato come **EmergencyChannel**, come illustrato di seguito.

   >[!NOTE]
   >Per ulteriori informazioni sulla creazione e la gestione di progetti in AEM Screens, consulta Creazione di un progetto.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Creazione di un canale sequenza**

   1. Seleziona la **Canali** cartella e fai clic su **Crea** per aprire la procedura guidata per creare un canale.

   1. Seleziona **Canale sequenza** dalla procedura guidata e crea il canale con titolo **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Aggiunta di contenuto al canale della sequenza**

   1. Seleziona il canale (**MainAdChannel**).
   1. Clic **Modifica** dalla barra delle azioni per aprire l’editor. Trascina alcune risorse sul tuo canale.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Creazione di un canale di emergenza**

   1. Seleziona la **Canali** cartella.
   1. Fai clic su **Crea** per aprire la procedura guidata per creare un canale.
   1. Seleziona **Canale sequenza** dalla procedura guidata e crea il canale con titolo **EmergencyChannel**.

   >[!NOTE]
   >
   >Normalmente, il canale di emergenza viene aggiunto al progetto di produzione preesistente.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Aggiunta di contenuto al canale di emergenza**

   1. Seleziona il canale (**Canale di emergenza)**.
   1. Clic **Modifica** dalla barra delle azioni per aprire l’editor. Trascina nel canale la risorsa da eseguire in caso di emergenza.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Creazione di una posizione**

   1. Accedi a **Posizioni** cartella.
   1. Clic **Crea** dalla barra delle azioni e crea una posizione denominata **Archivia** dalla procedura guidata.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Creazione di visualizzazioni nella tua posizione**

   Passa alla tua posizione (**Archivia**) e fai clic su **Crea** dalla barra delle azioni. Segui la procedura guidata per creare due **Display** con titolo **StoreFront** e **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Creazione di una pianificazione**

   1. Accedi al tuo **Schedules** cartella.
   1. Clic **Crea** dalla barra delle azioni. Segui la procedura guidata per creare una pianificazione con titolo **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Assegnare entrambe le visualizzazioni alla pianificazione e impostare le priorità

   1. Seleziona la pianificazione **(StoreSchedule)** e fai clic su **Dashboard** dalla barra delle azioni.

   1. Clic **+ Assegna canale** dal **CANALI ASSEGNATI** pannello.

   1. Dalla sezione **Assegnazione canale** finestra di dialogo:

      1. Seleziona il percorso per **MainAdChannel**
      1. Imposta il **Priorità** as 2
      1. Imposta gli eventi supportati come **Caricamento iniziale** e **Schermata di inattività**.
      1. Fai clic su **Salva**

      Allo stesso modo, dovrai seguire di nuovo gli stessi passaggi per assegnare il **EmergencyChannel** e impostarne **Priorità**.
   >[!NOTE]
   >
   >La priorità viene utilizzata per ordinare le assegnazioni nel caso in cui più corrispondano ai criteri di riproduzione. Quello con il valore più alto avrà sempre la precedenza sui valori più bassi.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Clic **+ Assegna canale** dal **CANALI ASSEGNATI** pannello.

1. Dalla sezione **Assegnazione canale** finestra di dialogo:

   1. Seleziona il percorso per **EmergencyChannel**
   1. Imposta il **Priorità** as 1

   1. Imposta gli eventi supportati come **Caricamento iniziale**, **Schermata di inattività**, e **Interazione utente**

   1. Fai clic su **Salva**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Puoi visualizzare i canali assegnati dalla sezione **StoreSchedule** dashboard.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Assegnazione della pianificazione a ogni visualizzazione**

   1. Passa a ogni visualizzazione, ad esempio **EmergencyChannel** —> **Posizioni** —> **Archivia** —>**StoreFront**.

   1. Clic **Dashboard** dall&#39;azione per aprire il dashboard di visualizzazione.
   1. Clic **...** dal **CANALI E PIANIFICAZIONI ASSEGNATI** e fai clic su **+Assegna pianificazione**.

   1. Seleziona il percorso della pianificazione (ad esempio, qui, **EmergencyChannel** —> **Schedules** —>**StoreSchedule**).

   1. Fai clic su **Salva**.

   È possibile visualizzare la programmazione assegnata dalla **StoreSchedule** dashboard.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registrazione dispositivo**

   Completa il processo di registrazione del dispositivo e, una volta effettuata la registrazione, visualizzerai il seguente output sul lettore AEM Screens.

   ![new30](assets/new30.gif)

## Passaggio al canale di emergenza {#switching-to-emergency-channel}

In caso di emergenza, effettuare le seguenti operazioni:

1. Accedi a **EmergencyChannel** —> **Schedules** —> **StoreSchedule** e seleziona **Dashboard** dalla barra delle azioni.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Seleziona la **EmergencyChannel** dal **StoreSchedule** dashboard e fai clic su **Modifica assegnazione**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Aggiornare il **Priorità** del **EmergencyChannel** a **3** dal **Assegnazione canale** e fare clic su **Salva**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Non appena viene aggiornata la priorità del canale, tutto il lettore AEM Screens visualizzerà **EmergencyChannel** come mostrato di seguito.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusione {#conclusion}

Il **EmergencyChannel** continuerà a visualizzarne il contenuto fino a quando l’autore del contenuto non reimposta il valore di priorità su 1.

Una volta che l’autore del contenuto riceve le istruzioni per l’eliminazione dell’emergenza, deve aggiornare la priorità della **MainAdChannel** che riprenderà la riproduzione normale.
