---
title: Canale di emergenza
description: Scopri come creare e gestire un canale di emergenza che l’autore del contenuto può cambiare da un canale di sequenza, se esiste una precondizione.
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Canale di emergenza {#emergency-channel}

## Descrizione del caso d’uso {#use-case-description}

Questa sezione descrive un esempio di caso d’uso. Sottolinea l’importanza di creare e gestire un canale di emergenza che l’autore del contenuto può cambiare da un canale di sequenza, se esiste una precondizione.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di aver compreso come:

* **[Crea e gestisci canali](managing-channels.md)**
* **[Crea e gestisci posizioni](managing-locations.md)**
* **[Crea e gestisci pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Flusso di base: configurazione del progetto {#basic-flow-setting-up-the-project}

Per impostare un canale di emergenza, procedere come segue:

1. Crea un progetto AEM Screens denominato **EmergencyChannel**, come illustrato di seguito.

   >[!NOTE]
   >Per ulteriori informazioni sulla creazione e la gestione di progetti in AEM Screens, consulta Creazione di un progetto.

   ![schermata_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Creazione di un canale di sequenza**

   1. Fai clic sulla cartella **Canali** e fai clic su **Crea**.

   1. Fai clic su **Canale sequenza** dalla procedura guidata e crea il canale con titolo **MainAdChannel**.

   ![schermata_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Aggiunta di contenuto al canale di sequenza**

   1. Fai clic sul canale (**MainAdChannel**).
   1. Fai clic su **Modifica** nella barra delle azioni.
   1. Trascina alcune risorse sul tuo canale.

   ![schermata_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Creazione di un canale di emergenza**

   1. Fare clic sulla cartella **Canali**.
   1. Fai clic su **Crea**.
   1. Fai clic su **Canale sequenza** dalla procedura guidata e crea il canale con titolo **Canale di emergenza**.

   >[!NOTE]
   >
   >Normalmente, il canale di emergenza viene aggiunto al progetto di produzione preesistente.

   ![schermata_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Aggiunta di contenuto al canale di emergenza**

   1. Fare clic sul canale (**Canale di emergenza)**.
   1. Fai clic su **Modifica** nella barra delle azioni.
   1. Trascina nel canale la risorsa da eseguire in caso di emergenza.

   ![schermata_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Creazione di un percorso**

   1. Passa alla cartella **Percorsi**.
   1. Fai clic su **Crea** nella barra delle azioni e crea un percorso con titolo **Archivia** dalla procedura guidata.

   ![schermata_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Creazione di visualizzazioni nel percorso**

   Passa alla tua posizione (**Archivio**) e fai clic su **Crea** nella barra delle azioni. Al termine della procedura guidata, crea due **Visualizzazioni** con titolo **StoreFront** e **StoreRear**.

   ![schermata_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Creazione di una pianificazione**

   1. Passa alla cartella **Schedules**.
   1. Fai clic su **Crea** nella barra delle azioni.
   1. Al termine della procedura guidata, crea una pianificazione denominata **StoreSchedule**.

   ![schermata_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Assegnare entrambe le visualizzazioni alla pianificazione e impostare le priorità

   1. Fai clic sulla pianificazione **(StoreSchedule)** e fai clic su **Dashboard** nella barra delle azioni.

   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI**.

   1. Dalla finestra di dialogo **Assegnazione canale**:

      1. Fai clic sul percorso per **MainAdChannel**
      1. Imposta **Priorità** come 2
      1. Impostare gli eventi supportati come **Caricamento iniziale** e **Schermata di inattività**.
      1. Fai clic su **Salva**

      Analogamente, eseguire nuovamente gli stessi passaggi per assegnare **EmergencyChannel** e impostarne **Priority**.

   >[!NOTE]
   >
   >La priorità viene utilizzata per ordinare le assegnazioni nel caso in cui più corrispondano ai criteri di riproduzione. Quello con il valore più alto ha sempre la precedenza sui valori più bassi.

   ![schermata_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI**.

1. Dalla finestra di dialogo **Assegnazione canale**:

   1. Fai clic sul percorso per **EmergencyChannel**
   1. Imposta **Priorità** come 1

   1. Imposta gli eventi supportati come **Caricamento iniziale**, **Schermata di inattività** e **Interazione utente**

   1. Fai clic su **Salva**

   ![schermata_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Puoi visualizzare i canali assegnati dal dashboard **StoreSchedule**.

   ![schermata_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Assegnazione della pianificazione a ogni visualizzazione**

   1. Passa a ogni visualizzazione, ad esempio **EmergencyChannel** > **Percorsi** > **Store** >**StoreFront**.

   1. Fai clic su **Dashboard** nella barra delle azioni.
   1. Fai clic su **...** dal pannello **SCHEDULES E CANALI ASSEGNATI**, quindi fai clic su **+Assegna pianificazione**.

   1. Fai clic sul percorso della pianificazione (ad esempio, qui **EmergencyChannel** > **Schedules** >**StoreSchedule**).

   1. Fai clic su **Salva**.

   Puoi visualizzare la pianificazione assegnata alla visualizzazione dal dashboard **StoreSchedule**.
   ![schermata_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registrazione dispositivo**

   Completa il processo di registrazione del dispositivo. Dopo la registrazione, puoi visualizzare il seguente output su AEM Screens Player.

   ![nuovo30](assets/new30.gif)

## Passaggio al canale di emergenza {#switching-to-emergency-channel}

In caso di emergenza, effettuare le seguenti operazioni:

1. Passa a **EmergencyChannel** > **Schedules** > **StoreSchedule** e fai clic su **Dashboard** nella barra delle azioni.

   ![schermata_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Fai clic su **EmergencyChannel** dal dashboard **StoreSchedule** e fai clic su **Modifica assegnazione**.

   ![schermata_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Aggiorna **Priorità** di **EmergencyChannel** in **3** dalla finestra di dialogo **Assegnazione canale** e fai clic su **Salva**.

   ![schermata_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Quando la priorità del canale viene aggiornata, tutto AEM Screens Player visualizza il contenuto **EmergencyChannel**.

   ![schermata_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusione {#conclusion}

**EmergencyChannel** continua a visualizzarne il contenuto fino a quando l&#39;autore del contenuto non reimposta il valore di priorità su 1.

Quando l&#39;autore del contenuto riceve le istruzioni per l&#39;eliminazione dell&#39;emergenza, deve aggiornare la priorità di **MainAdChannel**. In questo modo la riproduzione normale riprende.
