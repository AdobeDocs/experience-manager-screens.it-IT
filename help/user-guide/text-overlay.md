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
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '767'
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
>Il **Sovrapposizione testo** Questa funzione è disponibile solo se è stato installato il Feature Pack 5 di AEM 6.3 o il Feature Pack 3 di AEM 6.4.

## Panoramica {#overview}

La sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposta su un’immagine.

Per informazioni su come creare un componente personalizzato, consulta **Estensione di un componente AEM Screens**.

In questa sezione viene illustrato solo come utilizzare e applicare il componente poster in un progetto AEM Screens e utilizzarlo come sovrapposizione di testo in uno dei canali della sequenza.

## Utilizzo della sovrapposizione testo {#using-text-overlay}

La sezione seguente descrive l’utilizzo della sovrapposizione di testo in un progetto AEM Screens.

**Prerequisiti**

Prima di implementare questa funzionalità, accertati di aver impostato un progetto come prerequisito per iniziare a implementare la sovrapposizione di testo. Ad esempio:

* Crea un progetto AEM Screens (in questo esempio, **DemoSovrapposizioneTesto**)

* Crea un canale di sequenza denominato **TextSample** in **Canali** cartella

* Aggiungi contenuto al tuo **TextSample** Canale

L&#39;immagine seguente mostra **DemoSovrapposizioneTesto** progetto con **TextSample** channel in **Canali** cartella.

![screen_shot_2018-12-16alle75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Per utilizzare la sovrapposizione di testo in un canale AEM Screens, effettua le seguenti operazioni:

1. Accedi a **DemoSovrapposizioneTesto** > **Canali** > **TextSample** e seleziona **Modifica** dalla barra delle azioni.

   ![screen_shot_2018-12-16alle80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Seleziona l’immagine e seleziona **Configura** (icona a forma di chiave inglese) per aprire la finestra di dialogo proprietà.

   ![screen_shot_2018-12-16alle80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Seleziona la **Sovrapposizione testo** nella barra di navigazione della finestra di dialogo, come illustrato nella figura riportata di seguito.

   ![screen_shot_2018-12-16alle80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Informazioni sulle proprietà di sovrapposizione testo {#understanding-text-overlay-properties}

Utilizzando le proprietà Sovrapposizione testo è possibile aggiungere testo a qualsiasi componente del progetto Schermi. La sezione seguente fornisce una panoramica delle proprietà disponibili in Sovrapposizione testo:

![text](assets/text.gif)

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

Per scoprire come impostare e gestire le modifiche delle risorse basate sui dati utilizzando un archivio dati, consulta [Configurazione di ContextHub in AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

Dopo aver impostato le configurazioni richieste per il progetto, segui i passaggi seguenti per utilizzare i valori dei fogli di Google:

1. Accedi a **DemoSovrapposizioneTesto** > **Canali** > **TextSample** e seleziona **Proprietà** dalla barra delle azioni.

1. Seleziona la **Personalizzazione** in modo da poter impostare le configurazioni ContextHub.

   1. Seleziona la **Percorso ContextHub** as **libs** > **impostazioni** > **impostazioni cloud** > **predefinito** > **Configurazioni ContextHub** e seleziona **Seleziona**.

   1. Seleziona la **Percorso segmenti** as **conf** > **schermi** > **impostazioni** > **wcm** > **segmenti** e seleziona **Seleziona**.

   1. Seleziona **Salva e chiudi**.

      >[!NOTE]
      >
      >Utilizza ContextHub e il percorso Segmenti, dove hai inizialmente salvato le configurazioni e i segmenti dell’hub di contesto.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Accedi a **DemoSovrapposizioneTesto** > **Canali** > **TextSample** e seleziona **Modifica** dalla barra delle azioni.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Aggiungi un componente di sovrapposizione immagine e testo all’immagine, come descritto in [Utilizzo della sovrapposizione testo](/help/user-guide/text-overlay.md#using-text-overlay) sezione di questa pagina.

1. Seleziona il **Configura** (icona chiave inglese) per aprire **Immagine** .

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Accedi a **ContextHub** scheda da **Immagine** . Seleziona **Aggiungi**.

   >[!NOTE]
   >Se non hai configurato la configurazione ContextHub, questa opzione è disabilitata per il progetto.

1. Invio **Valore** nel **Segnaposto** campo. Selezionare la riga in cui si desidera ottenere il valore dal foglio Google in **Variabile ContextHub**. In questo caso, il valore viene recuperato dalla riga 2 e dalla colonna 1 dai fogli di Google. Ora immetti il **Valore predefinito** as **20**, come illustrato nella figura seguente. Al termine, seleziona il segno di spunta.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Per riferimento, l’immagine seguente mostra il valore recuperato dai fogli di Google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Torna a **Sovrapposizione testo** dalla finestra di dialogo Immagine e aggiungere il testo *Temperatura corrente {Value}*, come illustrato nella figura seguente.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Seleziona **Anteprima**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
