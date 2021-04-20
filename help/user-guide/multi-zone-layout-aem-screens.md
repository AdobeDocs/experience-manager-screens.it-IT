---
title: Layout a più zone
seo-title: Layout a più zone
description: Il layout a più aree consente di creare più contenuti di zona e utilizzare una varietà di risorse, come video, immagini e testo che possono essere combinate in un unico schermo. Segui questa pagina per ulteriori informazioni.
seo-description: Il layout a più aree consente di creare più contenuti di zona e utilizzare una varietà di risorse, come video, immagini e testo che possono essere combinate in un unico schermo. Segui questa pagina per ulteriori informazioni.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 6%

---


# Layout a più zone {#multi-zone-layout}

La pagina seguente descrive l’utilizzo del layout a più aree e illustra i seguenti argomenti:

* Panoramica
* Creazione di un layout a più zone
* Prerequisiti
* Utilizzo di risorse singole in una o più aree
* Utilizzo del contenuto sequenziale in una o più aree

## Panoramica {#overview}

***I*** layout a più aree consentono di creare più contenuti di zona e di utilizzare una varietà di risorse, quali video, immagini e testo che possono essere combinate in un’unica schermata. È possibile inserire immagini, video e testo per combinarli e creare un&#39;esperienza digitale intuitiva.

In base ai requisiti del progetto, talvolta è necessario disporre di più aree in un canale e modificarle come un’unica unità. Ad esempio, una sequenza del prodotto con il relativo feed social media in esecuzione in tre aree distinte su un singolo canale.


### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, assicurati di disporre delle conoscenze concettuali su:

* [Creazione di un progetto AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Creazione di una visualizzazione](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Assegnazione di un canale a una visualizzazione](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## Creazione di un layout a più zone {#creating-multi-zone-layout}

Durante la creazione di un canale, puoi utilizzare diversi modelli per creare aree nel canale. È possibile aggiungere un&#39;immagine singola, un video o un canale incorporato che consente la visualizzazione di più risorse in una sequenza.

**Creazione di un canale**

1. Seleziona il collegamento all’Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. In alternativa, puoi passare direttamente a: `http://localhost:4502/screens.html/content/screens`.
1. Passa alla cartella **Canali** e fai clic su **Crea** dalla barra delle azioni.

1. Seleziona **1x2 Split Screen Channel** dalla procedura guidata **Crea**.

1. Fai clic su **Avanti** e immetti il **titolo** come **MultiZone**.

1. Fai clic su **Crea** per completare la creazione del canale.

### Utilizzo di risorse singole in una o più aree {#using-single-assets-in-one-or-more-zones}

È possibile utilizzare risorse singole, ad esempio un’immagine o un video, in tutte le singole aree. Per l’implementazione, segui i passaggi seguenti:

1. **Aggiunta di contenuto al canale**

   1. Passa a **Zone** —> **Canali** —> **AreaMultipla**.
   1. Seleziona il canale **MultiZone** e fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.

1. **Aggiunta di immagini al canale**

   Per riprodurre un’immagine singola o un video in due aree, è sufficiente trascinare un’immagine in ciascuna zona nell’editor canali, come illustrato nella figura seguente:

   ![immagine](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Utilizzo del contenuto sequenziale in una o più aree {#using-sequenced-content-in-one-or-more-zones}

Per visualizzare la sequenza di immagini e un video nelle diverse aree, segui i passaggi riportati di seguito per ulteriori dettagli.

1. **Creazione di una cartella di canali**

   1. Passa a **Zone** —> **MultiZone** —> **Canali** e fai clic su **Crea** dalla barra delle azioni.
   1. Seleziona **Cartella canali** dalla procedura guidata **Crea** e fai clic su **Avanti**.
   1. Inserisci il titolo **EmbeddedChannels** e fai clic su **Crea**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Aggiunta di altri due canali alla cartella Canale**

   1. Passa a **Zone** —> **Canali** —> **Canali incorporati** e fai clic su **Crea** dalla barra delle azioni.
   1. Seleziona **Canale sequenza** dalla procedura guidata **Crea** per creare un canale denominato **Zona1**.
   1. Seleziona **Zona1** e fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.
   1. Trascina e rilascia alcune immagini su questo canale.
   1. Allo stesso modo, crea un altro canale di sequenza denominato **Zone2** nella cartella **EmbeddedChannels** .
   1. Trascina e rilascia un video su questo canale.

   La figura seguente mostra i canali **Zone1** e **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Le immagini aggiunte all&#39;editor del canale di sequenza **Zone1** sono mostrate di seguito:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Il video aggiunto all&#39;editor del canale di sequenza **Zone2** è mostrato di seguito:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Aggiunta di sequenze incorporate (componenti) al canale principale (MultiZone)**

   1. Passa a **Zone** —> **Canali** —> **MultiZone**.
   1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.
   1. Trascina il componente **Sequenza incorporata** in entrambe le aree.
   1. Selezionare la sequenza incorporata in una delle zone.
   1. Fai clic sull&#39;icona **Configura** (chiave inglese) in una delle sequenze incorporate nell&#39;editor.
   1. Seleziona il percorso del canale come **Zone** —> **Canali** —> **Canali incorporati** —> **Zona1**, come illustrato nella figura riportata di seguito.
   1. Allo stesso modo, aggiungi **Zone2** a un altro componente di sequenza incorporato nell&#39;editor.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creazione di una posizione e di una visualizzazione {#creating-location}

È necessario creare una posizione e una visualizzazione per visualizzare il contenuto nel lettore Screens. Segui i passaggi riportati di seguito per creare una posizione e una visualizzazione.

1. **Creazione di una posizione** 

   1. Passa alla cartella **Zone** —> **Posizioni** .
   1. Seleziona la cartella **Posizioni** e fai clic su **Crea** dalla barra delle azioni.
   1. Seleziona **Posizione** dalla procedura guidata **Crea** e fai clic su **Avanti**.
   1. Inserisci il **Titolo** come **SanJose** e fai clic su **Crea**.

1. **Creazione di una visualizzazione**

   1. Passa alla cartella **Zone** —> **Posizioni** .
   1. Seleziona la posizione **SanJose** e fai clic su **Crea** dalla barra delle azioni.
   1. Seleziona **Display** dalla procedura guidata **Crea** e fai clic su **Avanti**.
   1. Inserisci il **Titolo** come **Lobby** e fai clic su **Crea**.

### Assegnazione di canali alla visualizzazione {#channel-channel}

Per visualizzare il contenuto, è necessario assegnare i canali alla visualizzazione. Segui i passaggi riportati di seguito per assegnare il canale alla visualizzazione.

1. **Assegnazione del canale alla visualizzazione**

   1. Passa a **Zone** —> **Posizioni** —> **SanJose**—> **Lobby**.
   1. Seleziona la visualizzazione **Lobby** e fai clic su **Assegna canale** dalla barra delle azioni.
   1. Immetti il percorso del canale **MultiZone** in **Percorso del canale**.
   1. Imposta gli **Eventi supportati** come **Caricamento iniziale**, **Schermo inattivo** e **Timer**.
   1. Fai clic su **Salva**.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Allo stesso modo, è necessario assegnare gli altri due canali incorporati (**Zona1** e **Zona2**) a questa visualizzazione.
   1. Dopo aver assegnato tutti e tre i canali alla visualizzazione **Lobby**, è necessario essere in grado di visualizzare i canali assegnati dal dashboard di visualizzazione.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Dopo aver assegnato il canale principale (in questo caso, **MultiZone**) alla visualizzazione, è obbligatorio assegnare allo stesso display anche gli altri due canali incorporati **Zone1** e **Zone2**.

### Registrazione del dispositivo {#registering-device}

Una volta impostata una posizione e una visualizzazione, segui i passaggi seguenti per registrare il dispositivo e assegnare la visualizzazione al dispositivo.

1. **Registrazione del dispositivo**

   1. Passa alla cartella **Zone** —> **Dispositivi** .
   1. Seleziona la cartella **Dispositivi** e fai clic su **Gestione dispositivi** nella barra delle azioni.
   1. Fare clic su **Registrazione dispositivo** e selezionare il dispositivo in sospeso dall&#39;elenco.

      >[!NOTE]
      > Il titolo del dispositivo deve corrispondere al token dispositivo (**Token** ) visualizzato nella scheda **Registrazione dispositivo** .
   1. Se il titolo corrisponde al token del dispositivo, seleziona il dispositivo e fai clic su **Registra dispositivo** nella barra delle azioni.
   1. Se il codice di registrazione corrisponde al codice presente nella scheda Screens Player **Registrazione dispositivo** , fai clic su **Convalida** nella barra delle azioni.
      ![immagine](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Inserisci il **Titolo** come **Chrome-Device1** e fai clic su **Registra**.
   1. Seleziona **Assegna visualizzazione** e seleziona il percorso della configurazione del dispositivo.

   >[!NOTE]
   >Se stai tentando di visualizzare il contenuto nel lettore Screens, assicurati di fare clic su **Aggiorna contenuto offline** nel dashboard del canale per ciascuno dei canali assegnati alla visualizzazione.

### Visualizzazione del risultato {#viewing-the-result}

Una volta implementati i layout con più aree utilizzando i passaggi precedenti, viene visualizzato il seguente output.

Controlla il lettore Screens per visualizzare l&#39;output che mostra il contenuto in due aree diverse. Le zone sinistra e destra (entrambe utilizzano la sequenza incorporata come componente).

La zona a sinistra è un canale per sequenza e la zona a destra include un video.

![nuovo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


