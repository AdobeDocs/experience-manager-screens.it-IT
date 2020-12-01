---
title: Canale di emergenza
seo-title: Canale di emergenza
description: Per informazioni sulla creazione e la gestione di un canale di emergenza, l’autore del contenuto può passare da un canale di sequenza in caso di prerequisito, seguite questo esempio.
seo-description: Per informazioni sulla creazione e la gestione di un canale di emergenza, l’autore del contenuto può passare da un canale di sequenza in caso di prerequisito, seguite questo esempio.
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 9%

---


# Canale di emergenza {#emergency-channel}

## Descrizione di un caso d’uso {#use-case-description}

In questa sezione viene illustrato un esempio di esempio che mette in evidenza la creazione e la gestione di un canale di emergenza per consentire all’autore del contenuto di passare da un canale di sequenza in caso di pre-condizione.

### Precondizioni {#preconditions}

Prima di iniziare questo caso di utilizzo, accertatevi di comprendere come:

* **[Creazione e gestione di canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori primari {#primary-actors}

Autori contenuto

## Flusso di base: Impostazione del progetto {#basic-flow-setting-up-the-project}

Per impostare un canale di emergenza, effettuate le seguenti operazioni:

1. Create un progetto AEM Screens  denominato **EmergencyChannel**, come illustrato di seguito.

   >[!NOTE]
   >Per ulteriori informazioni sulla creazione e la gestione di progetti in  AEM Screens, vedere Creazione di un progetto.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Creazione di un canale di sequenza**

   1. Selezionate la cartella **Channels** e fate clic su **Create** per aprire la procedura guidata per creare un canale.

   1. Selezionare **Sequenza canale** dalla procedura guidata e creare il canale denominato **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Aggiunta di contenuto al canale della sequenza**

   1. Selezionare il canale (**MainAdChannel**).
   1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor. Trascinate alcune risorse sul canale.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Creazione di un canale di emergenza**

   1. Selezionare la cartella **Channels**.
   1. Fare clic su **Crea** per aprire la procedura guidata per creare un canale.
   1. Selezionare **Sequenza canale** dalla procedura guidata e creare il canale denominato **EmergencyChannel**.

   >[!NOTE]
   >
   >Normalmente, il canale di emergenza viene aggiunto al progetto di produzione preesistente.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Aggiunta di contenuto al canale di emergenza**

   1. Selezionare il canale (**Canale di emergenza)**.
   1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor. Trascina sul canale la risorsa da eseguire durante un’emergenza.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Creazione di una posizione** 

   1. Andate alla cartella **Locations**.
   1. Fare clic su **Crea** dalla barra delle azioni e creare un percorso denominato **Store** dalla procedura guidata.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Creazione di display nella posizione**

   Andate alla posizione (**Store**) e fate clic su **Crea** dalla barra delle azioni. Seguire la procedura guidata per creare due **Display** denominati **StoreFront** e **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Creare una pianificazione**

   1. Andate alla cartella **Pianificazioni**.
   1. Fai clic su **Crea** nella barra delle azioni. Seguire la procedura guidata per creare una pianificazione denominata **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Assegnare i display alla pianificazione e impostare le priorità

   1. Selezionare la pianificazione **(StoreSchedule)** e fare clic su **Dashboard** dalla barra delle azioni.

   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI**.

   1. Dalla finestra di dialogo **Assegnazione canale**:

      1. Selezionare il percorso del **MainAdChannel**
      1. Impostare **Priority** su 2
      1. Impostate gli eventi supportati come **Carico iniziale** e **Schermo inattivo**.
      1. Fai clic su **Salva**

      Allo stesso modo, sarà necessario seguire di nuovo gli stessi passaggi per assegnare il **EmergencyChannel** e impostare la relativa **Priority**.
   >[!NOTE]
   >
   >La priorità viene usata per ordinare le assegnazioni nel caso in cui più utenti corrispondano ai criteri di riproduzione. Quella con il valore più alto avrà sempre la precedenza su quella con i valori più bassi.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI**.

1. Dalla finestra di dialogo **Assegnazione canale**:

   1. Selezionare il percorso del **canale di emergenza**
   1. Impostare **Priority** su 1

   1. Impostare gli eventi supportati come **Carico iniziale**, **Schermo inattivo** e **Interazione utente**

   1. Fai clic su **Salva**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   È possibile visualizzare i canali assegnati dal dashboard **StoreSchedule**.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Assegnazione di Schedule a ogni display**

   1. Passare a ciascun display, ad esempio **EmergencyChannel** —> **Locations** —> **Store** —>**StoreFront**.

   1. Fare clic su **Dashboard** dall&#39;azione per aprire il dashboard di visualizzazione.
   1. Fare clic su **...** dal pannello **CANALI ASSEGNATI &amp; PROGRAMMI**, quindi fare clic su **+Assegna pianificazione**.

   1. Selezionare il percorso della programmazione (ad esempio, qui, **EmergencyChannel** —> **Schedules** —>**StoreSchedule**).

   1. Fai clic su **Salva**.

   È possibile visualizzare la pianificazione assegnata al display dal dashboard **StoreSchedule**.
   ![screen_shot_2019-03-04at122003 pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registrazione dispositivo**

   Completare il processo di registrazione del dispositivo e dopo aver effettuato la registrazione sarà visualizzato il seguente output sul lettore AEM Screens .

   ![new30](assets/new30.gif)

## Passaggio al canale di emergenza {#switching-to-emergency-channel}

In caso di emergenza, effettuare le seguenti operazioni:

1. Andate a **EmergencyChannel** —> **Schedules** —> **StoreSchedule** e selezionate **Dashboard** dalla barra delle azioni.

   ![screen_shot_2019-02-25at10112 pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Selezionare **EmergencyChannel** dal dashboard **StoreSchedule** e fare clic su **Edit Assignment**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Aggiornare la **Priorità** del **canale di emergenza** a **3** dalla finestra di dialogo **Assegnazione canale** e fare clic su **Salva**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Non appena la priorità del canale viene aggiornata, tutto il lettore AEM Screens  visualizzerà il contenuto **EmergencyChannel**, come mostrato di seguito.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusione {#conclusion}

**EmergencyChannel** continuerà a visualizzare il contenuto fino a quando l&#39;autore del contenuto non reimposta il valore Priority su 1.

Dopo che l&#39;autore del contenuto ha ricevuto le istruzioni per l&#39;eliminazione dell&#39;emergenza, deve aggiornare la priorità di **MainAdChannel**, causando la ripresa della riproduzione normale.
