---
title: Layout multizona
seo-title: Multi-zone Layout
description: Il layout multizona consente di creare contenuti per più aree e utilizzare varie risorse, come video, immagini e testo, che possono essere combinati in un’unica schermata. Per ulteriori informazioni, segui questa pagina.
seo-description: Multi-zone Layout allows you to create multiple zone content and use a variety of assets such as videos, images and text that can be combined in a single screen. Follow this page to learn more.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1129'
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


### Prerequisiti {#prerequisites}

Prima di iniziare a implementare questa funzionalità, assicurati di disporre delle conoscenze concettuali per:

* [Creazione di un progetto AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Creazione di una visualizzazione](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Assegnazione di un canale a una visualizzazione](/help/user-guide/channel-assignment.md)

## Creazione di un layout multizona {#creating-multi-zone-layout}

Durante la creazione di un canale, puoi utilizzare diversi modelli per creare zone nel canale. Puoi aggiungere una singola immagine, un video o un canale incorporato per visualizzare più risorse in una sequenza.

**Creazione di un canale**

1. Seleziona il collegamento Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. In alternativa, puoi passare direttamente a: `http://localhost:4502/screens.html/content/screens`.
1. Accedi a **Canali** cartella e fai clic su **Crea** dalla barra delle azioni.

1. Seleziona **Canale schermo diviso 1x2** dal **Crea** procedura guidata.

1. Clic **Successivo** e immetti **titolo** as **ZonaMultipla**.

1. Clic **Crea** per completare la creazione del canale.

### Utilizzo di risorse singole in una o più aree {#using-single-assets-in-one-or-more-zones}

Puoi utilizzare risorse singole, come un’immagine o un video, in tutte le singole aree. Per l’implementazione, segui i passaggi seguenti:

1. **Aggiunta di contenuto al canale**

   1. Accedi a **Zone** —> **Canali**—> **ZonaMultipla**.
   1. Seleziona la **ZonaMultipla** channel e click **Modifica** dalla barra delle azioni per aprire l’editor.

1. **Aggiunta di immagini al canale**

   Per riprodurre una singola immagine o un video in due zone, è sufficiente trascinare un’immagine in ciascuna zona dell’editor canali, come illustrato nella figura seguente:

   ![immagine](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Utilizzo di contenuti in sequenza in una o più aree {#using-sequenced-content-in-one-or-more-zones}

Se desideri che le aree visualizzino la sequenza di immagini e un video nelle diverse aree, segui i passaggi riportati di seguito per i dettagli.

1. **Creazione di una cartella canali**

   1. Accedi a **Zone** —> **ZonaMultipla** —> **Canali** e fai clic su **Crea** dalla barra delle azioni.
   1. Seleziona **Cartella canali** dal **Crea** e fai clic su **Successivo**.
   1. Inserisci il titolo come **EmbeddedChannels** e fai clic su **Crea**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Aggiunta di altri due canali alla cartella canali**

   1. Accedi a **Zone** —> **Canali** —> **EmbeddedChannels** e fai clic su **Crea** dalla barra delle azioni.
   1. Seleziona **Canale sequenza** dal **Crea** creazione guidata di un canale con titolo **Zona1**.
   1. Seleziona **Zona1** e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor.
   1. Trascina alcune immagini su questo canale.
   1. Allo stesso modo, crea un altro canale di sequenza denominato **Zona2** in **EmbeddedChannels** cartella.
   1. Trascina un video su questo canale.

   Nella figura seguente vengono illustrati i canali **Zona1** e **Zona2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Le immagini aggiunte all’editor di **Zona1** di seguito sono riportati i canali di sequenza:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   Il video aggiunto all’editor di **Zona2** di seguito è riportato un canale di sequenza:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Aggiunta di sequenze incorporate (componente) al canale principale (MultiZone)**

   1. Accedi a **Zone** —> **Canali** —> **ZonaMultipla**.
   1. Clic **Modifica** dalla barra delle azioni per aprire l’editor.
   1. Trascina la **Sequenza incorporata** in entrambe le zone.
   1. Selezionate la sequenza incorporata in una delle zone.
   1. Fai clic su **Configura** (chiave inglese) a una delle sequenze incorporate nell’editor.
   1. Seleziona il percorso del canale come **Zone** —> **Canali** —> **EmbeddedChannels** —> **Zona1**, come illustrato nella figura seguente.
   1. Analogamente, aggiungi **Zona2** a un altro componente di sequenza incorporato nell’editor.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-3.png)

### Creazione di una posizione e di una visualizzazione {#creating-location}

Crea una posizione e una visualizzazione per visualizzare il contenuto in Screens player.

1. **Creazione di una posizione**

   1. Accedi a **Zone** —> **Posizioni** cartella.
   1. Seleziona la **Posizioni** cartella e fai clic su **Crea** dalla barra delle azioni.
   1. Seleziona **Posizione** dal **Crea** e fai clic su **Successivo**.
   1. Inserisci il **Titolo** as **SanJose** e fai clic su **Crea**.

1. **Creazione di una visualizzazione**

   1. Accedi a **Zone** —> **Posizioni** cartella.
   1. Seleziona la **SanJose** posizione e clic **Crea** dalla barra delle azioni.
   1. Seleziona **Visualizzazione** dal **Crea** e fai clic su **Successivo**.
   1. Inserisci il **Titolo** as **Lobby** e fai clic su **Crea**.

### Assegnazione di canali alla visualizzazione {#channel-channel}

Assegna i canali alla visualizzazione per visualizzare il contenuto. Per assegnare il canale al display, segui la procedura riportata di seguito.

1. **Assegnazione del canale alla visualizzazione**

   1. Accedi a **Zone** —> **Posizioni** —> **SanJose**—> **Lobby**.
   1. Seleziona la **Lobby** visualizzare e fare clic su **Assegna canale** dalla barra delle azioni.
   1. Inserisci il percorso del **ZonaMultipla** channel in **Percorso canale**.
   1. Imposta il **Eventi supportati** as **Caricamento iniziale**, **Schermata di inattività**, e **Timer**.
   1. Fai clic su **Salva**.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Analogamente, è necessario assegnare gli altri due canali incorporati (**Zona1** e **Zona2**) a questo display.
   1. Dopo aver assegnato tutti e tre i canali a **Lobby** visualizzazione, dovresti essere in grado di visualizzare i canali assegnati dal dashboard di visualizzazione.

      ![immagine](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Una volta assegnato il canale principale (in questo caso, **ZonaMultipla**) al display, è necessario assegnare gli altri due canali incorporati **Zona1** e **Zona2** anche sullo stesso display.

### Registrazione del dispositivo {#registering-device}

Dopo aver impostato una posizione e uno schermo, attenersi alla procedura riportata di seguito per registrare il dispositivo e assegnargli uno schermo.

1. **Registrazione del dispositivo**

   1. Accedi a **Zone** —> **Dispositivi** cartella.
   1. Seleziona la **Dispositivi** cartella e fai clic su **Gestione dispositivi** dalla barra delle azioni.
   1. Clic **Registrazione dispositivo** e selezionare il dispositivo in sospeso dall&#39;elenco.

      >[!NOTE]
      > Il titolo del dispositivo deve corrispondere al token del dispositivo (**Token** ) visualizzato nel **Registrazione dispositivo** scheda.
   1. Se il titolo corrisponde al token del dispositivo, seleziona il dispositivo e fai clic su **Registra dispositivo** dalla barra delle azioni.
   1. Se il codice di registrazione corrisponde al codice presente nel lettore Screens **Registrazione dispositivo** , fare clic su **Convalida** dalla barra delle azioni.
      ![immagine](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Inserisci il **Titolo** as **Chrome-Device1** e fai clic su **Registrati**.
   1. Seleziona **Assegna visualizzazione** e selezionare il percorso della configurazione del dispositivo.

   >[!NOTE]
   >Se stai tentando di visualizzare il contenuto in Screens player, assicurati di fare clic su **Aggiorna contenuto offline** dal dashboard dei canali per ciascuno dei canali assegnati alla visualizzazione.

### Visualizzazione del risultato {#viewing-the-result}

Dopo aver implementato i layout multizona utilizzando i passaggi precedenti, viene visualizzato il seguente output.

Controlla il lettore Screens per visualizzare l’output che mostra il contenuto in due diverse aree. Le zone sinistra e destra (entrambe utilizzano una sequenza incorporata come componente).

La zona sinistra è un canale di sequenza e la zona destra include un video.

![nuovo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
