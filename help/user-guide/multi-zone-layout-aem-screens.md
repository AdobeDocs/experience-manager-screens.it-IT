---
title: Layout con più aree
seo-title: Layout con più aree
description: Layout con più aree consente di creare contenuti con più aree e di usare una serie di risorse quali video, immagini e testo che possono essere combinati in un unico schermo. Segui questa pagina per saperne di più.
seo-description: Layout con più aree consente di creare contenuti con più aree e di usare una serie di risorse quali video, immagini e testo che possono essere combinati in un unico schermo. Segui questa pagina per saperne di più.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 6%

---


# Layout multi-zona {#multi-zone-layout}

La pagina seguente descrive l’utilizzo del layout a più zone e illustra i seguenti argomenti:

* Panoramica
* Creazione di un layout con più aree
* Prerequisiti
* Utilizzo di risorse singole in una o più aree
* Utilizzo del contenuto sequenziale in una o più aree

## Panoramica {#overview}

***Layout con più aree*** consente di creare contenuti con più aree e di usare una serie di risorse quali video, immagini e testo che possono essere combinati in un unico schermo. Potete inserire immagini, video e testo per fonderli e creare un&#39;esperienza digitale intuitiva.

In base ai requisiti del progetto, talvolta è necessario disporre di più aree in un canale e modificarle come un’unica unità. Ad esempio, una sequenza del prodotto con il relativo feed social media in esecuzione in tre aree distinte su un singolo canale.


### Prerequisiti {#prerequisites}

Prima di iniziare ad implementare questa funzionalità, accertatevi di disporre delle conoscenze concettuali su:

* [Creazione di un progetto AEM Screens ](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Creazione di una visualizzazione](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Assegnazione di un canale a uno schermo](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## Creazione di un layout con più zone {#creating-multi-zone-layout}

Durante la creazione di un canale, potete usare diversi modelli per creare aree nel vostro canale. Potete aggiungere una singola immagine, un video o un canale incorporato che consenta la visualizzazione di più risorse in una sequenza.

**Creazione di un canale**

1. Seleziona il collegamento all’Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. In alternativa, puoi accedere direttamente a: `http://localhost:4502/screens.html/content/screens`.
1. Andate alla cartella **Channels** e fate clic su **Create** dalla barra delle azioni.

1. Selezionare **1x2 Split Screen Channel** dalla procedura guidata **Create**.

1. Fare clic su **Next** e inserire il **title** come **MultiZone**.

1. Fare clic su **Crea** per completare la creazione del canale.

### Utilizzo di risorse singole in una o più aree {#using-single-assets-in-one-or-more-zones}

Potete usare singole risorse, ad esempio un’immagine o un video, in tutte le singole aree. Seguite i passaggi indicati di seguito per l&#39;implementazione:

1. **Aggiunta di contenuti al canale**

   1. Passare a **Zone** —> **Canali**—> **MultiZone**.
   1. Selezionate il canale **MultiZone** e fate clic su **Edit** dalla barra delle azioni per aprire l&#39;editor.

1. **Aggiunta di immagini al canale**

   Per riprodurre una singola immagine o un video in due aree, è sufficiente trascinare un’immagine in ciascuna area dell’editor canale, come illustrato nella figura seguente:

   ![immagine](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Utilizzo del contenuto sequenziale in una o più aree {#using-sequenced-content-in-one-or-more-zones}

Per visualizzare la sequenza di immagini e video nelle diverse aree, effettuate le operazioni seguenti per ulteriori dettagli.

1. **Creazione di una cartella canale**

   1. Andate alle **aree** —> **MultiZone** —> **Canali** e fate clic su **Crea** dalla barra delle azioni.
   1. Selezionare **Cartella canali** dalla procedura guidata **Crea** e fare clic su **Avanti**.
   1. Immettete il titolo come **EmbeddedChannels** e fate clic su **Create**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Aggiunta di altri due canali alla cartella Canale**

   1. Andate alle **aree** —> **Canali** —> **EmbeddedChannels** e fate clic su **Create** dalla barra delle azioni.
   1. Selezionare **Sequenza canale** dalla procedura guidata **Crea** per creare un canale denominato **Zona1**.
   1. Selezionare **Zone1** e fare clic su **Edit** dalla barra delle azioni per aprire l&#39;editor.
   1. Trascinate alcune immagini su questo canale.
   1. Allo stesso modo, create un altro canale di sequenza denominato **Zone2** nella cartella **EmbeddedChannels**.
   1. Trascinate e rilasciate un video su questo canale.

   La figura seguente mostra i canali **Zone1** e **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Le immagini aggiunte all&#39;editor del canale di sequenza **Zone1** sono mostrate di seguito:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Il video aggiunto all&#39;editor del canale di sequenza **Zone2** è riportato di seguito:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Aggiunta di sequenze incorporate (componente) al canale principale (MultiZone)**

   1. Passare a **Zone** —> **Canali** —> **MultiZone**.
   1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.
   1. Trascinare il componente **Sequenza incorporata** in entrambe le aree.
   1. Selezionare la sequenza incorporata in una delle zone.
   1. Fate clic sull&#39;icona **Configura** (chiave inglese) per passare a una delle sequenze incorporate nell&#39;editor.
   1. Selezionare il percorso del canale come **Zone** —> **Canali** —> **EmbeddedChannels** —> **Zone1**, come illustrato nella figura seguente.
   1. Allo stesso modo, aggiungete **Zone2** a un altro componente della sequenza incorporata nell&#39;editor.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creazione di una posizione e di un display {#creating-location}

È necessario creare una posizione e una visualizzazione per visualizzare il contenuto nel lettore Screens. Per creare una posizione e una visualizzazione, effettuate le operazioni seguenti.

1. **Creazione di una posizione** 

   1. Passare alla cartella **Zone** —> **Posizioni**.
   1. Selezionare la cartella **Locations** e fare clic su **Create** dalla barra delle azioni.
   1. Selezionare **Posizione** dalla procedura guidata **Crea** e fare clic su **Avanti**.
   1. Immettete il **Titolo** come **SanJose** e fate clic su **Crea**.

1. **Creazione di una visualizzazione**

   1. Passare alla cartella **Zone** —> **Posizioni**.
   1. Selezionare la posizione **SanJose** e fare clic su **Crea** dalla barra delle azioni.
   1. Selezionare **Display** dalla procedura guidata **Crea** e fare clic su **Next**.
   1. Immettete il **Titolo** come **Sala d&#39;attesa** e fate clic su **Crea**.

### Assegnazione di canali al display {#channel-channel}

Per visualizzare il contenuto, dovete assegnare i canali al display. Seguite i passaggi indicati di seguito per assegnare il canale al display.

1. **Assegnazione del canale al display**

   1. Passare alle **aree** —> **posizioni** —> **SanJose**—> **Sala d&#39;attesa**.
   1. Selezionate il display **Lobby** e fate clic su **Assegna canale** dalla barra delle azioni.
   1. Immettere il percorso del canale **MultiZone** in **Percorso canale**.
   1. Impostare gli **Eventi supportati** come **Carico iniziale**, **Schermo inattivo** e **Timer**.
   1. Fai clic su **Salva**.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Allo stesso modo, è necessario assegnare gli altri due canali incorporati (**Zone1** e **Zone2**) a questo display.
   1. Dopo aver assegnato tutti e tre i canali al display **Lobby**, è necessario essere in grado di visualizzare i canali assegnati dal pannello di visualizzazione.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Dopo aver assegnato il canale principale (in questo caso, **MultiZone**) al display, è obbligatorio assegnare gli altri due canali incorporati **Zone1** e **Zone2** allo stesso display.

### Registrazione del dispositivo {#registering-device}

Una volta impostata una posizione e uno schermo, seguite i passaggi indicati di seguito per registrare il dispositivo e assegnare lo schermo al dispositivo.

1. **Registrazione del dispositivo**

   1. Andate alla cartella **Zone** —> **Dispositivi**.
   1. Selezionate la cartella **Devices** e fate clic su **Device Manager** dalla barra delle azioni.
   1. Fare clic su **Registrazione dispositivo** e selezionare il dispositivo in sospeso dall&#39;elenco.

      >[!NOTE]
      > Il titolo del dispositivo deve corrispondere al token dispositivo (**Token** campo) visualizzato nella scheda **Registrazione dispositivo**.
   1. Se il titolo corrisponde al token dispositivo, selezionare il dispositivo e fare clic su **Registra dispositivo** nella barra delle azioni.
   1. Se il codice di registrazione corrisponde al codice del lettore Screens **Registrazione dispositivo**, fare clic su **Validate** nella barra delle azioni.
      ![immagine](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Immettere il **Titolo** come **Chrome-Device1** e fare clic su **Register**.
   1. Selezionare **Assegna display** e selezionare il percorso della configurazione del dispositivo.

   >[!NOTE]
   >Se state tentando di visualizzare il contenuto nel lettore Screens, accertatevi di fare clic su **Aggiorna contenuto offline** nel dashboard del canale per ciascuno dei canali assegnati al display.

### Visualizzazione del risultato {#viewing-the-result}

Una volta implementati i layout con più aree utilizzando i passaggi precedenti, viene visualizzato il seguente output.

Controllare il lettore Screens per visualizzare l&#39;output che mostra il contenuto in due aree diverse. Le aree sinistra e destra (entrambe utilizzano la sequenza incorporata come componente).

La zona sinistra è un canale di sequenza e la zona destra include un video.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


