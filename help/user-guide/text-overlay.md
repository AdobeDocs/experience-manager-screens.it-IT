---
title: Sovrapposizione testo
description: Scopri la sovrapposizione di testo in AEM Screens che consente di creare un’esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposta su un’immagine.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 1%

---

# Sovrapposizione testo {#text-overlay}

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Utilizzo della sovrapposizione testo**
* **Informazioni sulle proprietà di sovrapposizione testo**
* **Utilizzo dei valori ContextHub nella sovrapposizione testo**

>[!CAUTION]
>
>La funzionalità **Sovrapposizione testo** è disponibile solo se è stato installato AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

## Panoramica {#overview}

La sovrapposizione testo è una funzione disponibile in AEM Screens. Ti consente di creare un’esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposta su un’immagine.

Per informazioni su come creare un componente personalizzato, consulta **Estensione di un componente AEM Screens**.

In questa sezione viene illustrato solo come utilizzare e applicare il componente poster in un progetto AEM Screens. Mostra anche come utilizzarlo come sovrapposizione di testo in uno dei canali della sequenza.

## Utilizzo della sovrapposizione testo {#using-text-overlay}

La sezione seguente descrive l’utilizzo della sovrapposizione di testo in un progetto AEM Screens.

**Prerequisiti**

Prima di implementare questa funzionalità, accertati di aver impostato un progetto come prerequisito per iniziare a implementare la sovrapposizione di testo. Ad esempio:

* Crea un progetto AEM Screens (in questo esempio, **TextOverlayDemo**)

* Crea un canale di sequenza con titolo **TextSample** nella cartella **Channels**

* Aggiungi contenuto al tuo canale **TextSample**

L&#39;immagine seguente mostra il progetto **TextOverlayDemo** con il canale **TextSample** nella cartella **Channels**.

![schermata_shot_2018-12-16alle75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Per utilizzare la sovrapposizione di testo in un canale AEM Screens, effettua le seguenti operazioni:

1. Passa a **TextOverlayDemo** > **Canali** > **TextSample** e fai clic su **Modifica** nella barra delle azioni.

   ![schermata_shot_2018-12-16alle80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Fai clic sull&#39;immagine e fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

   ![schermata_shot_2018-12-16alle80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Fare clic sull&#39;opzione **Sovrapposizione testo** nella barra di navigazione della finestra di dialogo, come illustrato nella figura riportata di seguito.

   ![schermata_shot_2018-12-16alle80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Informazioni sulle proprietà di sovrapposizione testo {#understanding-text-overlay-properties}

Utilizzando le proprietà Sovrapposizione testo, puoi aggiungere testo a qualsiasi componente del progetto Screens. La sezione seguente fornisce una panoramica delle proprietà disponibili in Sovrapposizione testo:

![testo](assets/text.gif)

È possibile aggiungere un testo alla casella di testo e aggiungere enfasi tipografiche quali grassetto, corsivo e sottolineato.

**Variante colore** Questa opzione consente di impostare il testo come Scuro (testo in nero) o Chiaro (testo in bianco).

**Ridimensionamento e posizionamento** Questa opzione consente all&#39;utente di allineare il testo orizzontalmente o verticalmente oppure di utilizzare strumenti granulari per l&#39;allineamento del testo.

>[!NOTE]
>
>Quando si utilizzano strumenti granulari, assicurarsi di identificare la posizione corretta in pixel utilizzando (px) come suffisso, ad esempio 200 px. Il risultato di questa espressione è di 200 pixel dal punto iniziale.

## Utilizzo dei valori ContextHub nella sovrapposizione testo {#using-text-overlay-context-hub}

La sezione seguente descrive l’utilizzo di valori provenienti da un archivio dati, ad esempio i fogli Google nel componente di sovrapposizione testo.

**Prerequisiti**

Configura le configurazioni ContextHub per il progetto AEM Screens.

Per informazioni su come impostare e gestire le modifiche delle risorse basate sui dati utilizzando un archivio dati, consulta [Configurazione di ContextHub in AEM Screens](https://experienceleague.adobe.com/it/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

Dopo aver impostato le configurazioni richieste per il progetto, segui i passaggi seguenti per utilizzare i valori dei fogli di Google:

1. Passa a **TextOverlayDemo** > **Canali** > **TextSample** e fai clic su **Proprietà** nella barra delle azioni.

1. Fai clic sulla scheda **Personalization** per configurare le configurazioni di ContextHub.

   1. Fai clic sul percorso **ContextHub** come **libs** > **settings** > **cloudsettings** > **default** > **Configurazioni ContextHub** e fai clic su **Select**.

   1. Fai clic su **Percorso segmenti** come **conf** > **schermate** > **impostazioni** > **wcm** > **segmenti** e fai clic su **Seleziona**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      >
      >Utilizza ContextHub e il percorso Segmenti, dove hai inizialmente salvato le configurazioni e i segmenti dell’hub di contesto.

      ![immagine1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Passa a **TextOverlayDemo** > **Canali** > **TextSample** e fai clic su **Modifica** nella barra delle azioni.

   ![immagine1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Aggiungi un componente di sovrapposizione immagine e testo all&#39;immagine come descritto nella sezione [Utilizzo della sovrapposizione testo](/help/user-guide/text-overlay.md#using-text-overlay) di questa pagina.

1. Fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo **Immagine**.

   ![immagine1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Dalla finestra di dialogo **Immagine**, accedi alla scheda **ContextHub**. Fare clic su **Aggiungi**.

   >[!NOTE]
   >Se non hai configurato la configurazione ContextHub, questa opzione è disabilitata per il progetto.

1. Immetti **Valore** nel campo **Segnaposto**. Fare clic sulla riga per ottenere il valore dal foglio Google in **Variabile ContextHub**. In questo caso, il valore viene recuperato dalla riga 2 e dalla colonna 1 dai fogli di Google. Immetti il **valore predefinito** come **20**, come illustrato nella figura seguente. Al termine, fai clic sul segno di spunta.

   ![immagine1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Per riferimento, l’immagine seguente mostra il valore recuperato dai fogli di Google:

   ![immagine1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Tornare alla scheda **Sovrapposizione testo** dalla finestra di dialogo Immagine e aggiungere il testo *Temperatura corrente {Value}*, come illustrato nella figura seguente.

   ![immagine1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Fare clic su **Anteprima**.

   ![immagine1](/help/user-guide/assets/text-overlay/text-overlay10.png)
