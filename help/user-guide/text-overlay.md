---
title: Sovrapposizione testo
seo-title: Text Overlay
description: La sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposta su un’immagine. Per ulteriori informazioni, segui questa pagina.
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# Sovrapposizione testo {#text-overlay}

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Utilizzo della sovrapposizione testo**
* **Informazioni sulle proprietà di sovrapposizione testo**
* **Utilizzo dei valori ContextHub nella sovrapposizione testo**

>[!CAUTION]
>
>Il **Sovrapposizione testo** Questa funzione è disponibile solo se è stato installato il Feature Pack 5 di AEM 6.3 o il Feature Pack 3 di AEM 6.4.

## Panoramica {#overview}

La sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposta su un’immagine.

Per informazioni su come creare un componente personalizzato, consulta **Estensione di un componente AEM Screens**.

In questa sezione viene illustrato solo come utilizzare e applicare il componente poster in un progetto AEM Screens e utilizzarlo come sovrapposizione di testo in uno dei canali della sequenza.

## Utilizzo della sovrapposizione testo {#using-text-overlay}

La sezione seguente descrive l’utilizzo della sovrapposizione di testo in un progetto AEM Screens.

**Prerequisiti**

Prima di iniziare a implementare questa funzionalità, assicurati di aver impostato un progetto come prerequisito per iniziare a implementare la sovrapposizione di testo. Ad esempio:

* Crea un progetto AEM Screens (in questo esempio, **DemoSovrapposizioneTesto**)

* Crea un canale di sequenza denominato **TextSample** in **Canali** cartella

* Aggiungi contenuto al tuo **TextSample** Canale

L&#39;immagine seguente mostra **DemoSovrapposizioneTesto** progetto con **TextSample** channel in **Canali** cartella.

![screen_shot_2018-12-16alle75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Per utilizzare la sovrapposizione di testo in un canale AEM Screens, effettua le seguenti operazioni:

1. Accedi a **DemoSovrapposizioneTesto** —> **Canali** —> **TextSample** e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor.

   ![screen_shot_2018-12-16alle80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Seleziona l’immagine e fai clic su **Configura** (icona a forma di chiave inglese) per aprire la finestra di dialogo proprietà.

   ![screen_shot_2018-12-16alle80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Seleziona la **Sovrapposizione testo** nella barra di navigazione della finestra di dialogo, come illustrato nella figura riportata di seguito.

   ![screen_shot_2018-12-16alle80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Informazioni sulle proprietà di sovrapposizione testo {#understanding-text-overlay-properties}

Utilizzando le proprietà Sovrapposizione testo è possibile aggiungere testo a qualsiasi componente del progetto Schermi. La sezione seguente fornisce una panoramica delle proprietà disponibili in Sovrapposizione testo:

![testo](assets/text.gif)

È possibile aggiungere un testo alla casella di testo e aggiungere enfasi tipografiche quali grassetto, corsivo e sottolineato.

**Variante colore** Questa opzione consente di impostare il testo come Scuro (testo in nero) o Chiaro (testo in bianco).

**Dimensioni e posizionamento** Questa opzione consente all’utente di allineare il testo orizzontalmente o verticalmente oppure di utilizzare strumenti a grana fine per l’allineamento del testo.

>[!NOTE]
>
>Per utilizzare correttamente gli strumenti granulari, assicurati di identificare la posizione corretta in pixel utilizzando (px) come suffisso, ad esempio 200 px. Il risultato di questa espressione è di 200 pixel dal punto iniziale.

## Utilizzo dei valori ContextHub nella sovrapposizione testo {#using-text-overlay-context-hub}

La sezione seguente descrive l’utilizzo di valori provenienti da un archivio dati, ad esempio i fogli di google nel componente di sovrapposizione testo.

**Prerequisiti**

Configura le configurazioni ContextHub per il progetto AEM Screens.

Per informazioni su come impostare e gestire le modifiche delle risorse basate sui dati utilizzando un archivio dati, consulta [Configurazione di ContextHub in AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Dopo aver impostato le configurazioni richieste per il progetto, segui i passaggi seguenti per utilizzare i valori dei fogli di Google:

1. Accedi a **DemoSovrapposizioneTesto** —> **Canali** —> **TextSample** e fai clic su **Proprietà** dalla barra delle azioni.

1. Seleziona la **Personalizzazione** per configurare le configurazioni ContextHub.

   1. Seleziona la **Percorso ContextHub** as **libs** > **impostazioni** > **impostazioni cloud** > **predefinito** > **Configurazioni ContextHub** e fai clic su **Seleziona**.

   1. Seleziona la **Percorso segmenti** as **conf** > **schermi** > **impostazioni** > **wcm** > **segmenti** e fai clic su **Seleziona**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      >
      >Utilizza ContextHub e il percorso Segmenti, dove hai inizialmente salvato le configurazioni e i segmenti dell’hub di contesto.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Accedi a **DemoSovrapposizioneTesto** —> **Canali** —> **TextSample** e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Aggiungi un componente di sovrapposizione immagine e testo all’immagine, come descritto in [Utilizzo della sovrapposizione testo](/help/user-guide/text-overlay.md#using-text-overlay) sezione di questa pagina.

1. Fai clic su **Configura** (icona chiave inglese) per aprire **Immagine** .

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Accedi a **ContextHub** scheda da **Immagine** . Clic **Aggiungi**.

   >[!NOTE]
   >Se non hai configurato le configurazioni ContextHub, questa opzione è disabilitata per il progetto.

1. Invio **Valore** nel **Segnaposto** campo. Selezionare la riga in cui si desidera ottenere il valore dal foglio Google in **Variabile ContextHub**. In questo caso, il valore viene recuperato dalla riga 2 e dalla colonna 1 dai fogli di Google. Ora immetti il **Valore predefinito** as **20**, come illustrato nella figura seguente. Al termine, fai clic sul segno di spunta.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Per riferimento, l&#39;immagine seguente mostra il valore recuperato dai fogli di Google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Torna a **Sovrapposizione testo** dalla finestra di dialogo Immagine e aggiungere il testo *Temperatura corrente {Value}*, come illustrato nella figura seguente.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Fai clic su **Anteprima** per visualizzare l&#39;output desiderato.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
