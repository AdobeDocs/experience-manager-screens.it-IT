---
title: Uso della Sequenza dinamica incorporata
seo-title: Uso della Sequenza dinamica incorporata
description: Segui questa pagina per apprendere come implementare le sequenze incorporate dinamiche nel progetto AEM Screens .
seo-description: Segui questa pagina per apprendere come implementare le sequenze incorporate dinamiche nel progetto AEM Screens .
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '2535'
ht-degree: 3%

---


# Uso della Sequenza dinamica incorporata {#using-dynamic-embedded-sequence}

L&#39;utilizzo di sequenze incorporate dinamiche illustra i seguenti argomenti:

* **Panoramica**
* **Utilizzo dell&#39;esperienza integrata dinamica in  AEM Screens**
* **Visualizzazione dei risultati**
* **Limitazione degli utenti e modifica degli ACL**

## Panoramica {#overview}

***Le*** sequenze incorporate dinamiche vengono create per progetti di grandi dimensioni che seguono la gerarchia figlio principale, in cui viene fatto riferimento all&#39;elemento secondario in una cartella di posizione e non in una cartella di canale. Consente all&#39;utente di incorporare una sequenza all&#39;interno di un canale tramite ***Channel Role***. Consente all&#39;utente di definire segnaposto specifici per la posizione per uffici diversi utilizzando una sequenza incorporata all&#39;interno di un canale principale.

Quando si assegna un canale a uno schermo, è possibile specificare il percorso del display o il ruolo del canale che verrà risolto su un canale effettivo in base al contesto.

Per utilizzare la sequenza incorporata dinamica, è possibile assegnare un canale tramite ***Ruolo canale***. Ruolo canale definisce il contesto della visualizzazione. Il ruolo è mirato da diverse azioni ed è indipendente dal canale effettivo che svolge il ruolo. Questa sezione descrive un esempio di utilizzo che definisce i canali secondo il ruolo e il modo in cui puoi sfruttare tali contenuti per un canale globale. Potete anche considerare il ruolo come un identificatore per l&#39;assegnazione, o un alias per il canale nel contesto di.

### Vantaggi dell&#39;utilizzo di sequenze incorporate dinamiche {#benefits-of-using-dynamic-embedded-sequences}

Il vantaggio principale di inserire un canale di sequenza all’interno di una posizione invece che nella cartella dei canali è quello di consentire agli autori locali o regionali di modificare i contenuti ad essi pertinenti, limitando al contempo la possibilità di modificare i canali in alto nella gerarchia.

Facendo riferimento a un *Canale per ruolo*, potete creare una versione locale di un canale, al fine di risolvere in modo dinamico il contenuto specifico per la posizione e anche creare un canale globale che sfrutta il contenuto per i canali specifici per la posizione.

>[!NOTE]
>
>**Sequenze incorporate e sequenze incorporate dinamiche**
>
>Una sequenza incorporata dinamica è simile a una sequenza incorporata, ma consente all’utente di seguire una gerarchia in cui le modifiche o gli aggiornamenti effettuati su un canale vengono propagati a un altro in relazione. Segue la gerarchia padre-figlio e include anche risorse come immagini o video.
>
>***Le*** sequenze incorporate dinamiche consentono di visualizzare contenuto specifico per la posizione, mentre le  ***sequenze*** incorporate visualizzano solo una presentazione generale del contenuto. Inoltre, durante l&#39;impostazione di sequenze incorporate dinamiche, è necessario configurare il canale utilizzando il ruolo e il nome del canale. Fare riferimento ai passaggi indicati di seguito per l&#39;implementazione pratica.
>
>Per ulteriori informazioni sull&#39;implementazione di sequenze incorporate, consultare [Sequenze incorporate](embedded-sequences.md) in  AEM Screens.

L&#39;esempio seguente fornisce una soluzione concentrandosi sui seguenti termini chiave:

* a ***canale di sequenza principale*** per la sequenza globale
* ***componenti di*** sequenza incorporati dinamici per ciascuna parte della sequenza personalizzabile localmente
* ***le singole sequenze*** canali nelle rispettive posizioni con un  ** ruolo che corrisponde al  **ruolo *del componente della sequenza incorporata*dinamica.**

>[!NOTE]
>
>Per ulteriori informazioni sull&#39;assegnazione dei canali, vedere **[Assegnazione dei canali](channel-assignment.md)** nella sezione Authoring della documentazione  AEM Screens.

## Uso della Sequenza dinamica incorporata {#using-dynamic-embedded-sequence-2}

Nella sezione seguente viene illustrata la creazione di una sequenza incorporata dinamica in un canale AEM Screens .

### Prerequisiti {#prerequisites}

Prima di iniziare ad implementare questa funzionalità, accertatevi di disporre dei seguenti prerequisiti per iniziare a implementare le sequenze incorporate dinamiche:

* Creare un progetto AEM Screens  (in questo esempio, **Demo**)

* Creare un canale come **Global** nella cartella **Channels**

* Aggiungere contenuto al canale **Globale** (*Controllare **Resources.zip**per le risorse pertinenti*

L&#39;immagine seguente mostra il progetto **Demo** con il canale **Global** nella cartella **Channels**.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Riferimenti {#resources}

Potete scaricare le risorse seguenti (immagini e aggiungerle alle risorse) e utilizzarle ulteriormente come contenuti per canali a scopo dimostrativo.

[Ottieni file](assets/resources.zip)

>[!NOTE]
>
>Per ulteriori informazioni su come creare un progetto e come creare un canale di sequenza, consulta le risorse seguenti:
>
>* **[Creazione e gestione di progetti](creating-a-screens-project.md)**
>* **[Gestione di un canale](managing-channels.md)**

>



L’implementazione di sequenze incorporate dinamiche in un progetto AEM Screens  comporta tre attività principali:

1. **Impostazione della tassonomia del progetto, inclusi canali, posizioni e display**
1. **Creare una pianificazione**
1. **Assegnazione di Schedule a ogni visualizzazione**

Per implementare la funzionalità, effettuate le operazioni seguenti:

>[!CAUTION]
>
>Durante l&#39;implementazione delle sequenze incorporate dinamiche, prestate attenzione ai campi **Name** e **Title** durante la creazione di canali in ogni posizione. Seguire attentamente le istruzioni sulla nomenclatura.

1. **Create due cartelle di posizioni.**

   Andate alla cartella **Locations** nel progetto AEM Screens  e create due cartelle di posizioni come **Region A** e **Region B**.

   >[!NOTE]
   >
   >Durante la creazione della cartella di posizione **Regione A**, assicurarsi di inserire il campo **Titolo** come **Regione A** e di lasciare vuoto il campo **Nome**, in modo che venga scelto automaticamente il nome **regione-a**.
   >
   >Analogamente, è il caso per la creazione della cartella di posizione **Regione B**, come illustrato di seguito:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Per informazioni su come creare una posizione, fare riferimento a **[Creazione e gestione di posizioni](managing-locations.md)**.

1. **Create due posizioni e un canale sotto ogni cartella di posizione.**

   1. Passare a **Demo** —> **Locations** —> **Region A**.
   1. Selezionare **Regione A** e fare clic su **+ Crea** dalla barra delle azioni.
   1. Selezionare **Location** dalla procedura guidata con **Title** come **Store 1**. Analogamente, create un&#39;altra posizione dalla procedura guidata denominata **Store 2** con **Title** come **Store 2**. È possibile lasciare vuoto il campo **Name** durante la creazione di **Store 1** e **Store 2**.
   1. Ripetere il passaggio (b) e ora selezionare **Canale sequenza** dalla procedura guidata. Immettere il **Titolo** come **Regione A** e **Nome** come **regione** per questo canale.

   >[!CAUTION]
   >
   >Assicurarsi che durante la creazione del canale **Regione A**, inserire il **Titolo** come **Regione A** e il **Nome** come **regione**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Allo stesso modo, create due posizioni in **Regione B** con titolo **Store 3** e **Store 4**. Inoltre, create un **Canale sequenza** con **Titolo** come **Regione B** e **Nome** come **regione**.

   >[!CAUTION]
   >
   >Assicurarsi di poter utilizzare lo stesso nome per i canali creati in **Regione A** e **Regione B** come **regione**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Crea display e canale sotto ogni posizione.**

   1. Passare a **Demo** —> **Locations** —> **Region A** —> **Store 1**.
   1. Selezionare **Store 1** e fare clic su **+ Crea** dalla barra delle azioni.
   1. Selezionare **Display** dalla procedura guidata e creare **Store1Display.**
   1. Ripetere il passaggio b) e selezionare **Canale sequenza** dalla procedura guidata. Immettete il **Titolo** come **Store1Channel** e il **Nome** come **store**.

   >[!CAUTION]
   >
   >È importante quando si crea un canale di sequenza, il **Titolo** del canale può essere uguale alle esigenze, ma il **Nome** deve essere lo stesso in tutti i canali locali.
   >In questo esempio, i canali sotto **Regione A** e **Regione B** condividono lo stesso **Nome** come **regione** e i canali sotto **Store 1**, **Store 2**, **Store 3** e **Store 4** condividono lo stesso **Name** come **store**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Allo stesso modo, create un display come **Store2Display** e un canale **Store2Channel** in **Store 2** (con nome come **store**).

   >[!NOTE]
   >Assicurarsi di poter utilizzare lo stesso nome per i canali creati in **Store 1** e **Store 2** come **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Seguire i passaggi precedenti per creare un canale e visualizzarlo in **Store 3** e **Store 4** in **Regione B**. Di nuovo, accertatevi di utilizzare lo stesso **Nome** come **store** durante la creazione del canale **Store3Channel** e **Store4Channel** rispettivamente.

   L&#39;immagine seguente mostra la visualizzazione e il canale in **Store 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   L&#39;immagine seguente mostra la visualizzazione e il canale in **Store 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Aggiungere contenuti ai canali nelle rispettive posizioni.**

   Andate alla **Demo** -> **Locations** -> **Region A** -> **Region A** e fate clic su **Edit** dalla barra delle azioni. Trascinate e rilasciate le risorse che desiderate aggiungere al canale.

   >[!NOTE]
   >Potete utilizzare il file ***Resources.zip*** dalla sezione **Risorse** qui sopra, per utilizzare le immagini come risorse per il contenuto del canale.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Allo stesso modo, andate alla **Demo** -> **Locations** -> **Region B** -> **Region B** e fate clic su **Edit** dalla barra delle azioni per trascinare e rilasciare le risorse sul canale, come illustrato di seguito:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Seguite i passaggi precedenti e le risorse per aggiungere contenuti ai seguenti canali:

   * **Store1 Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **Creare una pianificazione**

   Individuate e selezionate la cartella **Pianificazioni** nel progetto AEM Screens , quindi fate clic su **Crea** nella barra delle azioni per creare una nuova pianificazione.

   L&#39;immagine seguente mostra la **AdSchedule** creata nel progetto **Demo**.

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Assegnazione di canali a una pianificazione**

   1. Andate a **Demo** —> **Pianificazioni** —> **AdSchedule** e fate clic su **Dashboard** dalla barra delle azioni.
   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI** per aprire la finestra di dialogo **Assegnazione canale**.
   1. Selezionare **Canale di riferimento**. per percorso.
   1. Selezionare il percorso **Canale** come **Demo** —> ***Canali*** —> ***Globale***.
   1. Immettere il **ruolo canale** come **GlobalAdSegment**.
   1. Selezionare **Eventi supportati** come **Carico iniziale**, **Schermo inattivo** e **Interazione utente**.
   1. Fai clic su **Salva**.

   **Assegna canale per ruolo per regione:**

   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI** per aprire la finestra di dialogo **Assegnazione canale**.
   1. Selezionare **Canale di riferimento**. per nome.
   1. Immettere il **Nome canale** come **regione***.
   1. Immettete il **ruolo canale** come **segmentoRegioneAdSegment**.
   1. Fai clic su **Salva**.

   **Assegna canale per ruolo per store:**

   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI** per aprire la finestra di dialogo **Assegnazione canale**.
   1. Selezionare **Canale di riferimento**. per nome.
   1. Immettere il **Nome canale** come **store**.
   1. Immettere il **ruolo canale** come **StoreAdSegment**.
   1. Fai clic su **Salva**.

   L&#39;immagine seguente mostra i canali assegnati per percorso e per ruolo.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configurazione della sequenza incorporata dinamica nel canale globale.**

   Andate al canale **Globale** creato inizialmente nel progetto **Demo**.

   Fare clic su **Modifica** dall&#39;azione per aprire l&#39;editor.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Trascinate e rilasciate due componenti **Sequenza incorporata dinamica** nell&#39;editor canale.

   Aprite le proprietà di uno dei componenti e immettete il **Ruolo assegnazione canale** come **RegioneAdSegment**.

   Allo stesso modo, selezionare l&#39;altro componente e aprire le proprietà per inserire il **Ruolo assegnazione canale** come **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Assegnazione di Schedule a ogni display**

   1. Passare a ciascun display, ad esempio **Demo** —> **Locations** —> **Region A** —>**Store 1** —>**Store1Display**.
   1. Fare clic su **Dashboard** dall&#39;azione per aprire il dashboard di visualizzazione.
   1. Fare clic su **...** dal pannello **CANALI ASSEGNATI &amp; PROGRAMMI**, quindi fare clic su **+Assegna pianificazione**.
   1. Selezionare il percorso della programmazione (ad esempio, qui, **Demo** —> **Pianificazioni** —>**AdSchedule**).
   1. Fai clic su **Salva**.

## Visualizzazione dei risultati {#viewing-the-results}

Una volta impostata la visualizzazione dei canali e dei canali, avviate il lettore AEM Screens  per visualizzare il contenuto.

>[!NOTE]
>
>Per ulteriori informazioni su AEM riproduttore dello schermo, fare riferimento alle seguenti risorse:
>
>* [Download del lettore AEM Screens ](https://download.macromedia.com/screens/)
>* [Utilizzo di  AEM Screens Player](working-with-screens-player.md)



Il seguente output conferma il contenuto del canale in  lettore AEM Screens, a seconda del percorso di visualizzazione.

**Scenario 1**:

Se si assegna il percorso di visualizzazione come **Demo** —> **Locations** —> **Region A** —> **Store 1** —> **Store1Display**, sul lettore AEM Screens  verrà visualizzato il seguente contenuto:

![channeldisplay1](assets/channeldisplay1.gif)

**Scenario 1**:

Se si assegna il percorso di visualizzazione come **Demo** —> **Locations** —> **Region B** —> **Store 3** —> **Store3Display**, sul lettore AEM Screens  verrà visualizzato il contenuto seguente.

![channeldisplay2](assets/channeldisplay2.gif)

## Limitazione degli utenti e modifica degli ACL {#restricting-users-and-modifying-the-acls}

Potete creare autori globali, regionali o locali per modificare i contenuti ad essi pertinenti e allo stesso tempo limitare l’accesso ai canali di modifica più in alto nella gerarchia.

È necessario modificare gli ACL per limitare l&#39;accesso degli utenti al contenuto in base alla loro posizione.

### Esempio di utilizzo {#example-use-case}

L&#39;esempio seguente consente di creare tre utenti per il progetto Demo sopraindicato.

I privilegi sono assegnati a ciascun gruppo nel modo seguente:

**Gruppi**:

* **Global-Author**: È costituito da utenti che hanno accesso a tutte le posizioni e i canali nel  **** progetto Demoproject e dispongono di tutte le autorizzazioni di lettura, scrittura e modifica.

* **Autore** regione: È costituito da utenti che dispongono di autorizzazioni di lettura, scrittura e modifica per  **Area** e  **Regione B**.

* **Store-Author**: È costituito da utenti che dispongono di autorizzazioni di lettura, scrittura e modifica solo per  **Store 1**,  **Store 2**,  **Store 3** e  **Store 4**.

#### Passaggi per la creazione di gruppi di utenti, utenti e la configurazione di ACL {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Per informazioni dettagliate su come separare i progetti utilizzando ACL in modo che ogni singolo o team gestisca il proprio progetto, fare riferimento a **Impostazione di ACL**.

Per creare gruppi, utenti e modificare gli ACL in base alle autorizzazioni, effettuate le operazioni seguenti:

1. **Crea gruppi**

   1. Passare a **Adobe Experience Manager**.
   1. Fare clic su **Strumenti** —> **Protezione** —> **Gruppi**.
   1. Fare clic su **Crea gruppo** e immettere **Global-Author** in **ID**.
   1. Fai clic su **Salva e chiudi**.

   Allo stesso modo, create altri due gruppi come **Region-Author** e **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Creazione di utenti e aggiunta di utenti ai gruppi**

   1. Passare a **Adobe Experience Manager**.
   1. Fare clic su **Strumenti** —> **Protezione** —> **Utenti**.
   1. Fare clic su **Crea utente** e immettere **Global-User** in **ID**.
   1. Immettere **Password** e confermare la password per l&#39;utente.
   1. Fare clic sulla scheda **Gruppi** e inserire il nome del gruppo in **Seleziona gruppo**, ad esempio, immettere **Global-Author** per aggiungere **Global-User** a tale gruppo specifico.
   1. Fai clic su **Salva e chiudi**.

   Allo stesso modo, create altri due utenti come **Region-User** e **Store-User** e aggiungeteli rispettivamente a **Region-Author** e **Store-Author**.

   >[!NOTE]
   >È consigliabile aggiungere utenti in un gruppo e quindi assegnare le autorizzazioni a ciascun gruppo specifico di utenti.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Aggiungi tutti i gruppi ai collaboratori**

   1. Passare a **Adobe Experience Manager**.
   1. Fare clic su **Strumenti** —> **Protezione** —> **Gruppi**.
   1. Selezionare **Collaboratori** dall&#39;elenco e selezionare la scheda **Membri**.
   1. Selezionate il **gruppo**, ad esempio **Global-Author**, **Region-Author,** e **Store-Author** ai collaboratori.
   1. Fai clic su **Salva e chiudi**.

1. **Accesso alle autorizzazioni per ogni gruppo**

   1. Andate a *User admin* e utilizzate questa interfaccia per modificare le autorizzazioni per i diversi gruppi.
   1. Cercate **Global-Author** e fate clic sulla scheda **Autorizzazioni**, come illustrato nella figura riportata di seguito.
   1. Allo stesso modo, potete accedere alle autorizzazioni per **Region-Author** e **Store-Author**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modifica delle autorizzazioni per ogni gruppo**

   **Per Global-Author:**

   1. Passare alla scheda **Autorizzazioni**
   1. Andate a ***/content/screens/demo*** e verificate tutte le autorizzazioni
   1. Andate a ***/content/screens/demo/locations*** e verificate tutte le autorizzazioni
   1. Andate a ***/content/screens/demo/locations/region-a*** e controllate tutte le autorizzazioni. Analogamente, controllare le autorizzazioni per **region-b**.

   Fare riferimento alla figura seguente per comprendere i passaggi:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   L&#39;immagine seguente mostra che ora il **Global-User** ha accesso al **Canale Globale** e sia alla **Regione A** che alla **Regione B** con tutti e quattro i negozi, ovvero **Store 1**, **Store 2&lt;a1/>,** Store 3 **e** Store 4 **.**

   ![globale](assets/global.gif)

   **Per l’autore di un’area geografica:**

   1. Passate alla scheda **Autorizzazioni**.
   1. Accedete a ***/content/screens/demo*** e controllate solo le autorizzazioni **Leggi**.
   1. Andate a ***/content/screens/demo/locations*** e controllate solo le autorizzazioni **Leggi**.
   1. Andate a ***/content/screens/demo/channel*** e deselezionate le autorizzazioni per il canale **Global**.
   1. Andate a ***/content/screens/demo/locations***/***region-a*** e controllate tutte le autorizzazioni. Analogamente, controllare le autorizzazioni per **region-b**.

   Fare riferimento alla figura seguente per comprendere i passaggi:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   L&#39;immagine seguente mostra che ora l&#39;utente della regione ha accesso sia alla **Regione A** che alla **Regione B** con tutti e quattro i negozi: **Store 1**, **Store 2**, **Store 3** e **Store 4&lt;a7 1/> ma non ha accesso al canale** Global **.**

   ![regione](assets/region.gif)

   **Per Store-Author:**

   1. Passate alla scheda **Autorizzazioni**.
   1. Accedete a ***/content/screens/demo*** e controllate solo le autorizzazioni **Leggi**.
   1. Andate a ***/content/screens/demo/locations*** e controllate solo le autorizzazioni **Leggi**.
   1. Andate a ***/content/screens/demo/channel*** e deselezionate le autorizzazioni per il canale **Global**.
   1. Andate a ***/content/screens/demo/locations/region-a*** e controllate solo le autorizzazioni **Leggi**. Analogamente, controllare solo le autorizzazioni **Leggi** per **region-b**.
   1. Andate a ***/content/screens/demo/locations***/***region-a /store-1*** e controllate tutte le autorizzazioni. Analogamente, controllare le autorizzazioni per **store-2, store-3,** e **store-4**.

   Fare riferimento alla figura seguente per comprendere i passaggi:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   L&#39;immagine seguente mostra che ora il **Store-User** ha accesso solo ai quattro store, ovvero **Store 1**, **Store 2**, **Store 3** e **Store 4** ma non dispone delle autorizzazioni per accedere al **Global&lt;a 11/> o i canali della regione (** Regione A **e** Regione B **).**

   ![store](assets/store.gif)

>[!NOTE]
>
>Per informazioni dettagliate sulla configurazione delle autorizzazioni, fare riferimento a [Impostazione di ACL](setting-up-acls.md).

