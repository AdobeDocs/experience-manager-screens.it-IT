---
title: Sovrapposizione testo
seo-title: Sovrapposizione testo
description: Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza avvincente in un Canale per sequenza fornendo un titolo o una descrizione sovrapposti a un’immagine. Segui questa pagina per ulteriori informazioni.
seo-description: Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza avvincente in un Canale per sequenza fornendo un titolo o una descrizione sovrapposti a un’immagine. Segui questa pagina per ulteriori informazioni.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Creazione di esperienze in Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 3%

---


# Sovrapposizione testo {#text-overlay}

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Utilizzo della sovrapposizione testo**
* **Informazioni sulle proprietà della sovrapposizione testo**
* **Utilizzo dei valori ContextHub nella sovrapposizione del testo**

>[!CAUTION]
>
>La funzione **Sovrapposizione testo** è disponibile solo se è stato installato AEM Feature Pack 5 6.3 o AEM 6.4 Feature Pack 3.

## Panoramica {#overview}

Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza avvincente in un Canale per sequenza fornendo un titolo o una descrizione sovrapposti a un’immagine.

Per informazioni su come creare un componente personalizzato, consulta **Estensione di un componente AEM Screens**.

Questa sezione mostra solo come utilizzare e sfruttare il componente poster in un progetto AEM Screens e utilizzarlo come sovrapposizione di testo in uno dei canali di sequenza.

## Utilizzo della sovrapposizione testo {#using-text-overlay}

La sezione seguente descrive l’utilizzo della sovrapposizione testo in un progetto AEM Screens.

**Prerequisiti**

Prima di iniziare a implementare questa funzionalità, assicurati di aver impostato un progetto come prerequisito per iniziare a implementare la sovrapposizione di testo. Esempio,

* Crea un progetto AEM Screens (in questo esempio, **TextOverlayDemo**)

* Crea un canale di sequenza denominato **TextSample** nella cartella **Canali**

* Aggiungi contenuto al tuo canale **TextSample**

L&#39;immagine seguente mostra il progetto **TextOverlayDemo** con il canale **TextSample** nella cartella **Canali** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Segui i passaggi seguenti per utilizzare la sovrapposizione di testo in un canale AEM Screens:

1. Passa a **TextOverlayDemo** —> **Canali** —> **TextSample** e fai clic su **Modifica** dalla barra delle azioni per aprire l&#39;editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Seleziona l&#39;immagine e fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Seleziona l’opzione **Sovrapposizione testo** dalla barra di navigazione della finestra di dialogo, come illustrato nella figura riportata di seguito.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Proprietà di sovrapposizione testo {#understanding-text-overlay-properties}

Utilizzando le proprietà Sovrapposizione testo , puoi aggiungere testo a qualsiasi componente del progetto Screens. La sezione seguente fornisce una panoramica delle proprietà disponibili in Sovrapposizione testo:

![Testo](assets/text.gif)

È possibile aggiungere un testo alla casella di testo e l’enfasi tipografica, ad esempio grassetto, corsivo, sottolineato e così via.

**Colore** VariantQuesta opzione consente al testo di essere scuro (testo a colori neri) o chiaro (testo a colori bianchi).

**Ridimensionamento e** posizionamentoQuesta opzione consente all’utente di allineare il testo in orizzontale o verticale o di utilizzare strumenti a grana fine per l’allineamento del testo.

>[!NOTE]
>
>Per utilizzare correttamente gli strumenti a grana fine, accertati di identificare la posizione corretta in pixel utilizzando (px) come suffisso, ad esempio 200px. Il risultato di questa espressione sarà di 200 pixel dal punto iniziale.

## Utilizzo dei valori ContextHub nella sovrapposizione testo {#using-text-overlay-context-hub}

La sezione seguente descrive l&#39;utilizzo dei valori da un archivio dati, ad esempio, google sheet nel componente sovrapposizione testo.

**Prerequisiti**

Devi configurare le configurazioni ContextHub per il progetto AEM Screens.

Per informazioni su come impostare e gestire le modifiche alle risorse basate su dati utilizzando un archivio dati, consulta [Configurazione di ContextHub in AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Una volta configurate le configurazioni richieste per il progetto, segui i passaggi seguenti per utilizzare i valori dei fogli di Google:

1. Passa a **TextOverlayDemo** —> **Canali** —> **TextSample** e fai clic su **Proprietà** dalla barra delle azioni.

1. Seleziona la scheda **Personalizzazione** per impostare le configurazioni di ContextHub.

   1. Seleziona il **Percorso ContextHub** come **libs** > **impostazioni** > **impostazioni cloud** > **predefinito** > **Configurazioni ContextHub** e fai clic su **Predefinito Seleziona**.

   1. Seleziona il **Percorso segmenti** come **conf** > **screens** > **impostazioni** > **wcm** > **segmenti** e fai clic su **Seleziona**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      >
      >Utilizza ContextHub e il percorso Segmenti, in cui hai inizialmente salvato le configurazioni e i segmenti dell&#39;hub di contesto.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Passa a **TextOverlayDemo** —> **Canali** —> **TextSample** e fai clic su **Modifica** dalla barra delle azioni per aprire l&#39;editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Aggiungi un componente immagine e sovrapposizione testo all&#39;immagine come descritto nella sezione [Utilizzo della sovrapposizione testo](/help/user-guide/text-overlay.md#using-text-overlay) di questa pagina.

1. Fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo **Immagine**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Passa alla scheda **ContextHub** dalla finestra di dialogo **Immagine**. Fate clic su **Aggiungi**.

   >[!NOTE]
   >Se non hai configurato le configurazioni di ContextHub, questa opzione sarà disabilitata per il progetto.

1. Immetti **Valore** nel campo **Segnaposto**, seleziona la riga che desideri ottenere il valore dal tuo foglio google in **Variabile ContextHub** (in questo caso, il valore viene recuperato dalla riga 2 e dalla colonna 1 dai fogli google) e immetti il **Valore predefinito** come **20**, come mostrato nella figura seguente. Una volta fatto, fai clic sul segno di spunta.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Per riferimento, l&#39;immagine seguente mostra il valore recuperato dai fogli di Google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Torna alla scheda **Sovrapposizione testo** dalla finestra di dialogo Immagine e aggiungi il testo *Temperatura corrente {Value}*, come illustrato nella figura riportata di seguito.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Fai clic su **Anteprima** per visualizzare l&#39;output desiderato.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)















