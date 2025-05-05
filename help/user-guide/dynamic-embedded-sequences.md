---
title: Utilizzo della sequenza dinamica incorporata
description: Scopri come implementare le sequenze Dynamic Embedded nel progetto AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3208d058-0812-44e1-83e3-b727b384876a
source-git-commit: 8a914d4b0237c327b7954c936c84a2c1aa719603
workflow-type: tm+mt
source-wordcount: '2451'
ht-degree: 1%

---

# Utilizzo della sequenza dinamica incorporata {#using-dynamic-embedded-sequence}

L’utilizzo delle sequenze dinamiche incorporate tratta i seguenti argomenti:

* **Panoramica**
* **Utilizzo dell&#39;esperienza dinamica incorporata in AEM Screens**
* **Visualizzazione dei risultati**
* **Limitazione degli utenti e modifica degli ACL**

## Panoramica {#overview}

***Le sequenze incorporate dinamiche*** vengono create per progetti di grandi dimensioni che seguono una gerarchia padre-figlio, in cui all&#39;elemento figlio viene fatto riferimento all&#39;interno di una cartella di percorso e non in una cartella di canale. Consente all&#39;utente di incorporare una sequenza in un canale da ***Ruolo canale***. Consente all&#39;utente di definire segnaposto specifici per la posizione per uffici diversi utilizzando una sequenza incorporata all&#39;interno di un canale principale.

Quando si assegna un canale a una visualizzazione, è possibile specificare il percorso della visualizzazione. In alternativa, puoi specificare il ruolo del canale che viene risolto in un canale effettivo in base al contesto.

Per utilizzare la sequenza dinamica incorporata, assegnare un canale in base a ***Ruolo canale***. Ruolo canale definisce il contesto della visualizzazione. Il ruolo esegue il targeting di varie azioni ed è indipendente dal canale effettivo che svolge il ruolo. Questa sezione descrive un caso d’uso che definisce i canali in base al ruolo e come applicarli a un canale globale. Puoi anche considerare il ruolo come un identificatore per l’assegnazione o un alias per il canale nel contesto di.

### Vantaggi dell’utilizzo di sequenze dinamiche incorporate {#benefits-of-using-dynamic-embedded-sequences}

Posizionare un canale di sequenza all&#39;interno di una posizione invece che nella cartella dei canali consente agli autori locali o regionali di modificare i contenuti di loro interesse. Consente inoltre di non effettuare l&#39;editing dei canali nella parte superiore della gerarchia.

Facendo riferimento a un *canale per ruolo*, puoi creare una versione locale di un canale. In questo modo viene risolto in modo dinamico il contenuto specifico della posizione e viene creato un canale globale che utilizza il contenuto per i canali specifici della posizione.

>[!NOTE]
>
>**Sequenze incorporate rispetto alle sequenze incorporate dinamiche**
>
>Una sequenza incorporata dinamica è simile a una sequenza incorporata, ma consente all’utente di seguire una gerarchia in cui le modifiche e gli aggiornamenti apportati a un canale vengono propagati a un altro in relazione. Segue una gerarchia genitore-figlio e include anche risorse come immagini o video.
>
>***Sequenze incorporate dinamiche*** consente di visualizzare contenuto specifico della posizione, mentre ***Sequenze incorporate*** visualizza solo la presentazione generale del contenuto. Inoltre, durante l’impostazione delle sequenze dinamiche incorporate, configura il canale utilizzando il ruolo e il nome del canale. Per informazioni sull’implementazione pratica, consulta i passaggi seguenti.
>
>Per ulteriori informazioni sull&#39;implementazione di sequenze incorporate, vedere [Sequenze incorporate](embedded-sequences.md) in AEM Screens.

L’esempio seguente fornisce una soluzione concentrandosi sui seguenti termini chiave:

* un ***canale sequenza principale*** per la sequenza globale.
* ***componenti di sequenza incorporata dinamica*** per ogni parte della sequenza personalizzabile localmente.
* ***singoli canali di sequenza*** nelle rispettive posizioni con un *ruolo* nella visualizzazione corrispondente al *ruolo&#x200B;*** del componente sequenza incorporato dinamico &#x200B;**.

>[!NOTE]
>
>Per ulteriori informazioni sull&#39;assegnazione dei canali, consulta **[Assegnazione canale](channel-assignment.md)** nella sezione Authoring della documentazione di AEM Screens.

## Utilizzo della sequenza dinamica incorporata {#using-dynamic-embedded-sequence-2}

La sezione seguente spiega la creazione di una sequenza dinamica incorporata in un canale AEM Screens.

### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, accertati di disporre dei seguenti prerequisiti per iniziare a implementare sequenze integrate dinamiche:

* Crea un progetto AEM Screens (in questo esempio, **Demo**).
* Crea un canale **Global** nella cartella **Channels**.
* Aggiungi contenuto al tuo canale **Global** (*Controlla **Resources.zip**&#x200B;per le risorse rilevanti*).

L&#39;immagine seguente mostra il progetto **Demo** con il canale **Global** nella cartella **Channels**.
![schermata_shot_2018-09-07alle21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Riferimenti {#resources}

Puoi scaricare le seguenti risorse (immagini e aggiungerle alle risorse) e utilizzarle ulteriormente come contenuto di canale a scopo dimostrativo.

[Ottieni file](assets/resources.zip)

>[!NOTE]
>
>Per ulteriori informazioni su come creare un progetto e un canale di sequenza, consulta le risorse seguenti:
>
>* **[Creazione e gestione di progetti](creating-a-screens-project.md)**
>* **[Gestione di un canale](managing-channels.md)**
>

L’implementazione di Dynamic Embedded Sequence in un progetto AEM Screens comporta tre attività principali:

1. **Impostazione della tassonomia del progetto, inclusi canali, posizioni e visualizzazioni**
1. **Creazione di una pianificazione**
1. **Assegnazione della pianificazione a ogni visualizzazione**

Per implementare la funzionalità, segui i passaggi seguenti:

>[!CAUTION]
>
>Durante l&#39;implementazione delle sequenze Dynamic Embedded, fai attenzione ai campi **Nome** e **Titolo** durante la creazione dei canali in ogni posizione. Seguire attentamente le istruzioni relative alla nomenclatura.

1. **Crea due percorsi cartella.**

   Passa alla cartella **Percorsi** nel progetto AEM Screens e crea due cartelle dei percorsi come **Area A** e **Area B**.

   >[!NOTE]
   >
   >Durante la creazione della cartella di percorso **Area A**, assicurati di immettere il **Titolo** come **Area A** e di poter lasciare vuoto il campo **Nome**, in modo che venga automaticamente scelto il nome **area-a**.
   >
   >Analogamente, è possibile creare la cartella di percorso **Area B**, come illustrato di seguito:

   ![schermata_shot_2018-09-13alle23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Per informazioni su come creare un percorso, vedere **[Creazione e gestione di percorsi](managing-locations.md)**.

1. **Creare due percorsi e un canale in ogni cartella di percorsi.**

   1. Passa a **Demo** > **Percorsi** > **Area A**.
   1. Fare clic su **Area A** e su **+ Crea** nella barra delle azioni.
   1. Fare clic su **Posizione** della procedura guidata con **Titolo** come **Archivio 1**. Analogamente, creare un altro percorso dalla procedura guidata con titolo **Archivio 2** e **Titolo** come **Archivio 2**. È possibile lasciare vuoto il campo **Nome** durante la creazione di **Archivio 1** e **Archivio 2**.
   1. Ripetere il passaggio b) e fare clic su **Canale sequenza** dalla procedura guidata. Immetti **Titolo** come **Area A** e **Nome** come **Area** per questo canale.

   >[!CAUTION]
   >
   >Assicurati che durante la creazione del canale **Area A**, immetti **Titolo** come **Area A** e **Nome** come **Area**.

   ![schermata_shot_2018-09-13alle22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Analogamente, creare due percorsi in **Area B** con titolo **Archivio 3** e **Archivio 4**. Creare inoltre un **canale sequenza** con **titolo** come **area B** e **nome** come **area**.

   >[!CAUTION]
   >
   >Assicurarsi di poter utilizzare lo stesso nome per i canali creati in **Area A** e **Area B** come **Area**.

   ![schermata_shot_2018-09-13alle24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Crea visualizzazione e canale sotto ogni posizione.**

   1. Passa a **Demo** > **Percorsi** > **Area A** > **Archivio 1**.
   1. Fai clic su **Store 1** e fai clic su **+ Crea** nella barra delle azioni.
   1. Fare clic su **Visualizza** dalla procedura guidata e creare **`Store1Display`**.
   1. Ripeti il passaggio b) e questa volta fai clic su **Canale sequenza** dalla procedura guidata. Immetti **Titolo** come **`Store1Channel`** e **Nome** come **Archivio**.

   >[!CAUTION]
   >
   >È importante quando crei un canale di sequenza, il **Titolo** del canale può essere come requisito, ma il **Nome** deve essere lo stesso in tutti i canali locali.
   >In questo esempio, i canali dell&#39;area **A** e dell&#39;area **B** condividono **Name** come **region** e i canali dell&#39;area **`Store 1`**, **`Store 2`**, **`Store 3`** e **`Store 4`** condividono **Name** come **store**.

   ![schermata_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Analogamente, creare una visualizzazione come **`Store2Display`** e un canale **`Store2Channel`** in **`Store `2** (con nome come **store**).

   >[!NOTE]
   >Assicurarsi di utilizzare lo stesso nome per i canali creati in **`Store 1`** e **`Store 2`** come **store**.

   ![schermata_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Segui i passaggi precedenti per creare un canale e visualizzarlo in **`Store 3`** e **`Store 4`** in **Area B**. Di nuovo, assicurati di utilizzare lo stesso **Nome** come **archivio** durante la creazione del canale **`Store3Channel`** e **`Store4Channel`** rispettivamente.

   L&#39;immagine seguente mostra la visualizzazione e il canale in **`Store 3`**.

   ![schermata_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   L&#39;immagine seguente mostra la visualizzazione e il canale in **`Store 4`**.

   ![schermata_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Aggiungi contenuto ai canali nelle rispettive posizioni.**

   Passa a **Demo** > **Percorsi** > **Area A** > **Area A** e fai clic su **Modifica** nella barra delle azioni. Trascina e rilascia le risorse da aggiungere al canale.

   >[!NOTE]
   >Puoi utilizzare il file ***Resources.zip*** dalla sezione **Resources** sopra, per utilizzare le immagini come risorse per il contenuto del canale.

   ![schermata_shot_2018-09-12alle12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Analogamente, passa a **Demo** > **Percorsi** > **Area B** > **Area B** e fai clic su **Modifica** dalla barra delle azioni per trascinare e rilasciare le risorse sul tuo canale, come illustrato di seguito:

   ![schermata_shot_2018-09-12alle13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Segui i passaggi precedenti e le risorse per aggiungere contenuti ai seguenti canali:

   * **`Store1Channel`**
   * **`Store2Channel`**
   * **`Store3Channel`**
   * **`Store4Channel`**

1. **Crea una pianificazione**

   Passa alla cartella **Schedules** del progetto AEM Screens e fai clic su di essa. Quindi fai clic su **Crea** nella barra delle azioni.

   L&#39;immagine seguente mostra l&#39;**AdSchedule** creato nel progetto **Demo**.

   ![schermata_shot_2018-09-13alle33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Assegna canali a una pianificazione**

   1. Passa a **Demo** > **Pianificazioni** > **AdSchedule** e fai clic su **Dashboard** nella barra delle azioni.
   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI** per aprire la finestra di dialogo **Assegnazione canale**.
   1. Fai clic su **Canale di riferimento** per percorso.
   1. Fai clic sul **percorso canale**, esattamente come **demo** > ***canali*** > ***globale***.
   1. Immetti il **Ruolo canale**, esattamente come **GlobalAdSegment**.
   1. Fai clic su **Eventi supportati**, come **Caricamento iniziale**, **Schermata di inattività** e **Interazione utente**.
   1. Fai clic su **Salva**.

   **Assegna canale per ruolo per regione:**

   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI**.
   1. Nella finestra di dialogo Assegnazione canale fare clic su **Canale di riferimento** per nome.
   1. Immetti **Nome canale** come **area***.
   1. Immetti **Ruolo canale** come **RegionAdSegment**.
   1. Fai clic su **Salva**.

   **Assegna canale per ruolo per archivio:**

   1. Fare clic su **+ Assegna canale** dal pannello **CANALI ASSEGNATI**.
   1. Nella finestra di dialogo Assegnazione canale fare clic su **Canale di riferimento** per nome.
   1. Immetti **Nome canale** come **archivio**.
   1. Immetti **Ruolo canale** come **StoreAdSegment**.
   1. Fai clic su **Salva**.

   L’immagine seguente mostra i canali assegnati in base al percorso e al ruolo.

   ![schermata_shot_2018-09-12alle21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configurazione della sequenza dinamica incorporata nel canale globale.**

   Passa al canale **Global** creato inizialmente nel progetto **Demo**.

   Fai clic su **Modifica** nella barra delle azioni.

   ![schermata_shot_2018-09-13alle52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Nell&#39;editor, trascina e rilascia due componenti **Dynamic Embedded Sequence** nell&#39;editor canali.

   Apri le proprietà da uno dei componenti e immetti **Ruolo assegnazione canale** come **RegionAdSegment**.

   Allo stesso modo, fai clic sugli altri componenti e apri le proprietà per immettere **Ruolo assegnazione canale** come **StoreAdSegment**.

   ![canalovisualizzazione4](assets/channeldisplay4.gif)

1. **Assegnazione della pianificazione a ogni visualizzazione**

   1. Passa a ogni visualizzazione, ad esempio **Demo** > **Percorsi** > **Area A** >**Archivio 1** >**`Store1Display`**.
   1. Fai clic su **Dashboard** nella barra delle azioni.
   1. Nel dashboard, fare clic su **...** dal pannello **SCHEDULES E CANALI ASSEGNATI**, quindi fare clic su **+Assegna Schedule**.
   1. Fai clic sul percorso della pianificazione (ad esempio, qui **Demo** > **Pianificazioni** > **AdSchedule**).
   1. Fai clic su **Salva**.

## Visualizzazione dei risultati {#viewing-the-results}

Una volta completata la configurazione dei canali e della visualizzazione, avvia AEM Screens Player per visualizzare il contenuto.

>[!NOTE]
>
>Per informazioni su AEM Screens Player, consulta le risorse seguenti:
>
>* [Scarica AEM Screens Player](https://download.macromedia.com/screens/)
>* [Utilizzo di AEM Screens Player](working-with-screens-player.md)


L’output seguente conferma il contenuto del canale in AEM Screens Player, a seconda del percorso di visualizzazione.

**Esempio 1**:

Se assegni il percorso di visualizzazione come **Demo** > **Percorsi** > **Area A** > **Archivio 1** > **`Store1Display`**, il seguente contenuto viene visualizzato nel lettore AEM Screens.

![canalovisualizzazione1](assets/channeldisplay1.gif)

**Esempio 1**:

Se assegni il percorso di visualizzazione come **Demo** > **Percorsi** > **Area B** > **Archivio 3** > **`Store3Display`**, il seguente contenuto viene visualizzato nel lettore AEM Screens.

![visualizzazionecanale2](assets/channeldisplay2.gif)

## Limitazione degli utenti e modifica degli ACL {#restricting-users-and-modifying-the-acls}

Puoi creare autori globali, regionali o locali per modificare contenuti di loro interesse mentre è loro impedito di modificare i canali più in alto nella gerarchia.

Modifica gli ACL in modo da poter limitare l’accesso dell’utente al contenuto in base alla sua posizione.

### Caso d’uso di esempio {#example-use-case}

L’esempio seguente consente di creare tre utenti per il progetto demo indicato sopra.

I privilegi sono assegnati a ciascun gruppo come segue:

**Gruppi**:

* **Autore globale**: è costituito da utenti che hanno accesso a tutte le posizioni e i canali del progetto **Demo** e dispongono di tutte le autorizzazioni di lettura, scrittura e modifica.

* **Autore area**: è costituito da utenti con autorizzazioni di lettura, scrittura e modifica per **Area A** e **Area B**.

* **Store-Author**: utenti con autorizzazioni di lettura, scrittura e modifica solo per **Store 1**, **Store 2**, **Store 3** e **Store 4**.

#### Passaggi per creare gruppi di utenti, utenti e configurare ACL {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Per informazioni dettagliate su come separare i progetti utilizzando gli ACL in modo che ogni singolo utente o team gestisca il proprio progetto, vedere **Configurazione degli ACL**.

Segui i passaggi seguenti per creare gruppi, utenti e modificare gli ACL in base alle autorizzazioni:

1. **Crea gruppi**

   1. Passa a **Adobe Experience Manager**.
   1. Fai clic su **Strumenti** > **Sicurezza** > **Gruppi**.
   1. Fai clic su **Crea gruppo** e immetti **Autore globale** in **ID**.
   1. Fai clic su **Salva e chiudi**.

   Allo stesso modo, crea altri due gruppi come **Autore-Regione** e **Autore-Archivio**.

   ![schermata_shot_2018-09-17alle34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Crea utenti e aggiungi utenti ai gruppi**

   1. Passa a **Adobe Experience Manager**.
   1. Fai clic su **Strumenti** > **Protezione** > **Utenti**.
   1. Fai clic su **Crea utente** e immetti **Utente globale** in **ID**.
   1. Immetti **Password** e conferma la password per questo utente.
   1. Fai clic sulla scheda **Gruppi** e immetti il nome del gruppo in **Fai clic su Gruppo**. Ad esempio, immetti **Global-Author** per aggiungere **Global-User** a quel gruppo specifico.
   1. Fai clic su **Salva e chiudi**.

   Allo stesso modo, crea altri due utenti come **Utente-Regione** e **Utente-Archivio** e aggiungili rispettivamente a **Autore-Regione** e **Autore-Archivio**.

   >[!NOTE]
   >È consigliabile aggiungere utenti in un gruppo e quindi assegnare le autorizzazioni a ciascun gruppo di utenti specifico.

   ![schermata_shot_2018-09-17alle34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Aggiungi tutti i gruppi ai collaboratori**

   1. Passa a **Adobe Experience Manager**.
   1. Fai clic su **Strumenti** > **Sicurezza** > **Gruppi**.
   1. Fare clic su **Collaboratori** dall&#39;elenco e quindi sulla scheda **Membri**.
   1. Fare clic su **Gruppo**, ad esempio **Autore-globale**, **Autore-regione,** e **Autore-store**, per i collaboratori.
   1. Fai clic su **Salva e chiudi**.

1. **Accesso alle autorizzazioni per ogni gruppo**

   1. Passa a *Amministratore utenti* e utilizza questa interfaccia utente per modificare le autorizzazioni per i diversi gruppi.
   1. Cerca **Global-Author** e fai clic sulla scheda **Autorizzazioni**, come illustrato nella figura seguente.
   1. Allo stesso modo, puoi accedere alle autorizzazioni per **Autore-Regione** e **Autore-Archivio**.

   ![schermata_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modifica delle autorizzazioni per ogni gruppo**

   **Per Global-Author:**

   1. Passa alla scheda **Autorizzazioni**
   1. Passa a ***/content/screens/demo*** e controlla tutte le autorizzazioni
   1. Passa a ***/content/screens/demo/locations*** e controlla tutte le autorizzazioni
   1. Passa a ***/content/screens/demo/locations/region-a*** e controlla tutte le autorizzazioni. Analogamente, controllare le autorizzazioni per **`region-b`**.

   Per comprendere i passaggi, vedere la figura riportata di seguito.
   ![schermata_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   Di seguito viene illustrato che **Global-User** ha accesso al **Global Channel**. Accesso a **Area A** e **Area B** con tutti e quattro gli archivi: **Archivio 1**, **Archivio 2**, **Archivio 3** e **Archivio 4**.

   ![globale](assets/global.gif)

   **Per Autore Area Geografica:**

   1. Passa alla scheda **Autorizzazioni**.
   1. Passa a ***/content/screens/demo*** e controlla solo le autorizzazioni **Read**.
   1. Passa a ***/content/screens/demo/locations*** e controlla solo le autorizzazioni **Read**.
   1. Passa a ***/content/screens/demo/channels*** e deseleziona le autorizzazioni per il canale **Global**.
   1. Passa a ***/content/screens/demo/locations***/***region-a*** e controlla tutte le autorizzazioni. Analogamente, controllare le autorizzazioni per **`region-b`**.

   Consulta l’immagine seguente per comprendere i passaggi:

   ![schermata_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   Di seguito viene illustrato che l&#39;utente dell&#39;area ha accesso sia all&#39;**Area A** che all&#39;**Area B**. Accesso a tutti e quattro gli archivi, ovvero **Store 1**, **Store 2**, **Store 3** e **Store 4**, ma non al canale **Global**.

   ![area](assets/region.gif)

   **Per Store-Author:**

   1. Passa alla scheda **Autorizzazioni**.
   1. Passa a ***/content/screens/demo*** e controlla solo le autorizzazioni **Read**.
   1. Passa a ***/content/screens/demo/locations*** e controlla solo le autorizzazioni **Read**.
   1. Passa a ***/content/screens/demo/channels*** e deseleziona le autorizzazioni per il canale **Global**.
   1. Passa a ***/content/screens/demo/locations/region-a*** e controlla solo le autorizzazioni **Read**. Analogamente, controllare solo le autorizzazioni **Lettura** per **`region-b`**.
   1. Passa a ***/content/screens/demo/locations***/***region-a /store-1*** e controlla tutte le autorizzazioni. Analogamente, controllare le autorizzazioni per **store-2, store-3,** e **store-4**.

   Consulta l’immagine seguente per comprendere i passaggi:

   ![schermata_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   Di seguito viene mostrato che l&#39;**Utente-Store** ha accesso solo a **Store 1**, **Store 2**, **Store 3** e **Store 4**. Tuttavia, non dispone delle autorizzazioni per accedere ai canali **Global** o area (**Region A** e **Region B**).

   ![archivio](assets/store.gif)

>[!NOTE]
>
>Per informazioni dettagliate sulla configurazione delle autorizzazioni, vedere [Configurazione di ACL](setting-up-acls.md).
