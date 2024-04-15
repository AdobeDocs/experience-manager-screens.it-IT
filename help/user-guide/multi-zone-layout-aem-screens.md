---
title: Layout multizona
description: Scopri come creare contenuti per più aree e utilizzare varie risorse come video, immagini e testo che possono essere combinati in una singola schermata in AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# Layout multizona {#multi-zone-layout}

La pagina seguente descrive l&#39;utilizzo del layout multizona e tratta i seguenti argomenti:

* Panoramica
* Creazione di un layout multizona
* Prerequisiti
* Utilizzo di risorse singole in una o più aree
* Utilizzo di contenuti in sequenza in una o più aree

## Panoramica {#overview}

***Layout multizona*** consente di creare contenuti per più aree e utilizzare varie risorse, come video, immagini e testo, che possono essere combinati in un’unica schermata. Puoi richiamare immagini, video e testo per unire le diverse caratteristiche e creare un’esperienza digitale intuitiva.

In base alle esigenze del progetto, a volte è necessario disporre di più zone in un canale e modificarle come un&#39;unica unità completa. Ad esempio, una sequenza di prodotto con un feed di social media correlato che viene eseguita in tre aree separate su un singolo canale.

>[!NOTE]
>Nei canali multizona, la pianificazione a livello di risorsa non è consigliata a causa di potenziali conflitti e comportamenti non desiderati. Se è necessaria una pianificazione a livello di risorsa, si consiglia di creare un canale di sequenza separato e di applicare una logica di pianificazione all’interno di tale canale. Quindi, incorpora il canale della sequenza nel canale multizona.

### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, assicurati di disporre delle conoscenze concettuali su:

* [Creazione di un progetto AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [Creazione di una visualizzazione](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [Assegnazione di un canale a una visualizzazione](/help/user-guide/channel-assignment.md)

## Creazione di un layout multizona {#creating-multi-zone-layout}

Durante la creazione di un canale, puoi utilizzare diversi modelli per creare zone nel canale. Puoi aggiungere una singola immagine, un video o un canale incorporato per visualizzare più risorse in una sequenza.

**Creazione di un canale**

1. Seleziona il collegamento Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. In alternativa, puoi passare direttamente a: `http://localhost:4502/screens.html/content/screens`.
1. Accedi a **Canali** cartella e seleziona **Crea** dalla barra delle azioni.

1. Seleziona **Canale schermo diviso 1x2** dal **Crea** procedura guidata.

1. Seleziona **Successivo** e immetti **titolo** as **ZonaMultipla**.

1. Seleziona **Crea** per completare la creazione del canale.

### Utilizzo di risorse singole in una o più aree {#using-single-assets-in-one-or-more-zones}

Puoi utilizzare risorse singole, come un’immagine o un video, in tutte le singole aree. Per l’implementazione, segui i passaggi seguenti:

1. **Aggiunta di contenuto al canale**

   1. Accedi a **Zone** > **Canali**> **ZonaMultipla**.
   1. Seleziona la **ZonaMultipla** channel e select **Modifica** dalla barra delle azioni.

1. **Aggiunta di immagini al canale**

   Per riprodurre una singola immagine o un video in due zone, è sufficiente trascinare un’immagine in ciascuna zona dell’editor canali, come illustrato nella figura seguente:

   ![immagine](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Utilizzo di contenuti in sequenza in una o più aree {#using-sequenced-content-in-one-or-more-zones}

Se desideri che le aree visualizzino la sequenza di immagini e un video nelle diverse aree, segui i passaggi riportati di seguito per i dettagli.

1. **Creazione di una cartella canali**

   1. Accedi a **Zone** > **ZonaMultipla** > **Canali** e seleziona **Crea** dalla barra delle azioni.
   1. Seleziona **Cartella canali** dal **Crea** procedura guidata e seleziona **Successivo**.
   1. Inserisci il titolo come **EmbeddedChannels** e seleziona **Crea**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Aggiunta di altri due canali alla cartella canali**

   1. Accedi a **Zone** > **Canali** > **EmbeddedChannels** e seleziona **Crea** dalla barra delle azioni.
   1. Seleziona **Canale sequenza** dal **Crea** creazione guidata di un canale con titolo **`Zone1`**.
   1. Seleziona **`Zone1`** e seleziona **Modifica** dalla barra delle azioni.
   1. Trascina alcune immagini su questo canale.
   1. Allo stesso modo, crea un altro canale di sequenza denominato **`Zone2`** in **EmbeddedChannels** cartella.
   1. Trascina un video su questo canale.

   Nella figura seguente vengono illustrati i canali **`Zone1`** e **`Zone2`**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Le immagini aggiunte all’editor di **`Zone1`** di seguito sono riportati i canali di sequenza:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Il video aggiunto all’editor di **`Zone2`** di seguito è riportato un canale di sequenza:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Aggiunta di sequenze incorporate (componente) al canale principale (MultiZone)**

   1. Accedi a **Zone** > **Canali** > **ZonaMultipla**.
   1. Seleziona **Modifica** dalla barra delle azioni.
   1. Trascina la **Sequenza incorporata** in entrambe le zone.
   1. Selezionate la sequenza incorporata in una delle zone.
   1. Seleziona la **Configura** (chiave inglese) a una delle sequenze incorporate nell’editor.
   1. Seleziona il percorso del canale come **Zone** > **Canali** > **EmbeddedChannels** > **`Zone1`**, come illustrato nella figura seguente.
   1. Analogamente, aggiungi **`Zone2`** a un altro componente di sequenza incorporato nell’editor.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creazione di una posizione e di una visualizzazione {#creating-location}

Crea una posizione e una visualizzazione per visualizzare il contenuto nel lettore AEM Screens.

1. **Creazione di una posizione**

   1. Accedi a **Zone** > **Posizioni** cartella.
   1. Seleziona la **Posizioni** cartella e seleziona **Crea** dalla barra delle azioni.
   1. Seleziona **Posizione** dal **Crea** procedura guidata e seleziona **Successivo**.
   1. Inserisci il **Titolo** as **SanJose** e seleziona **Crea**.

1. **Creazione di una visualizzazione**

   1. Accedi a **Zone** > **Posizioni** cartella.
   1. Seleziona la **SanJose** posizione e selezione **Crea** dalla barra delle azioni.
   1. Seleziona **Visualizzazione** dal **Crea** procedura guidata e seleziona **Successivo**.
   1. Inserisci il **Titolo** as **Lobby** e seleziona **Crea**.

### Assegnazione di canali alla visualizzazione {#channel-channel}

Assegna i canali alla visualizzazione per visualizzare il contenuto. Per assegnare il canale al display, segui la procedura riportata di seguito.

1. **Assegnazione del canale alla visualizzazione**

   1. Accedi a **Zone** > **Posizioni** > **SanJose**> **Lobby**.
   1. Seleziona la **Lobby** visualizza e seleziona **Assegna canale** dalla barra delle azioni.
   1. Inserisci il percorso del **ZonaMultipla** channel in **Percorso canale**.
   1. Imposta il **Eventi supportati** as **Caricamento iniziale**, **Schermata di inattività**, e **Timer**.
   1. Seleziona **Salva**.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Allo stesso modo, assegna gli altri due canali incorporati (**`Zone1`** e **`Zone2`**) a questo display.
   1. Dopo aver assegnato tutti e tre i canali a **Lobby** visualizzazione, dovresti essere in grado di visualizzare i canali assegnati dal dashboard di visualizzazione.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >Dopo aver assegnato il canale principale (in questo caso, **ZonaMultipla**) al display, è necessario assegnare gli altri due canali incorporati **`Zone1`** e **`Zone2`** anche sullo stesso display.

### Registrazione del dispositivo {#registering-device}

Dopo aver impostato una posizione e uno schermo, attenersi alla procedura riportata di seguito per registrare il dispositivo e assegnargli uno schermo.

1. **Registrazione del dispositivo**

   1. Accedi a **Zone** > **Dispositivi** cartella.
   1. Seleziona la **Dispositivi** cartella e seleziona **Gestione dispositivi** dalla barra delle azioni.
   1. Seleziona **Registrazione dispositivo** e selezionare il dispositivo in sospeso dall&#39;elenco.

      >[!NOTE]
      > Il titolo del dispositivo deve corrispondere al token del dispositivo (**Token** ) visualizzato nel **Registrazione dispositivo** scheda.

   1. Se il titolo corrisponde al token del dispositivo, seleziona il dispositivo e seleziona **Registra dispositivo** dalla barra delle azioni.
   1. Se il codice di registrazione corrisponde al codice presente nel lettore Screens **Registrazione dispositivo** , seleziona **Convalida** dalla barra delle azioni.
      ![immagine](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Inserisci il **Titolo** as **`Chrome-Device1`** e seleziona **Registrati**.
   1. Seleziona **Assegna visualizzazione** e selezionare il percorso della configurazione del dispositivo.

   >[!NOTE]
   >Se stai tentando di visualizzare il contenuto in Screens player, assicurati di selezionare **Aggiorna contenuto offline** dal dashboard dei canali per ciascuno dei canali assegnati alla visualizzazione.

### Visualizzazione del risultato {#viewing-the-result}

Quando si implementano layout multizona utilizzando i passaggi precedenti, viene visualizzato il seguente output.

Controlla il lettore Screens in modo da poter visualizzare l’output che mostra il contenuto in due aree diverse. Le zone sinistra e destra (entrambe utilizzano una sequenza incorporata come componente).

La zona sinistra è un canale di sequenza e la zona destra include un video.

![nuovo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
