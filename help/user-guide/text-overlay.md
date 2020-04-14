---
title: Sovrapposizione testo
seo-title: Sovrapposizione testo
description: Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un'esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposto a un'immagine. Segui questa pagina per saperne di più.
seo-description: Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un'esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposto a un'immagine. Segui questa pagina per saperne di più.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: 651627223e1b9bd0f650b010d2b92f004b9e2ea2

---


# Sovrapposizione testo {#text-overlay}

Questa sezione illustra i seguenti argomenti:

* **Panoramica**
* **Utilizzo della sovrapposizione testo**
* **Informazioni sulle proprietà delle sovrapposizioni di testo**
* **Utilizzo dei valori ContextHub in sovrapposizione testo**

>[!CAUTION]
>
>La funzione Sovrapposizione **** testo è disponibile solo se avete installato AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

## Panoramica {#overview}

Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un&#39;esperienza coinvolgente in un canale di sequenza fornendo un titolo o una descrizione sovrapposto a un&#39;immagine.

Per informazioni su come creare un componente personalizzato, consultate **Estensione di un componente** AEM Screens.

Questa sezione mostra solo come usare e usare il componente poster in un progetto AEM Screens e utilizzarlo come sovrapposizione di testo in uno dei canali della sequenza.

## Utilizzo della sovrapposizione testo {#using-text-overlay}

La sezione seguente descrive l&#39;utilizzo della sovrapposizione di testo in un progetto AEM Screens.

**Prerequisiti**

Prima di iniziare ad implementare questa funzionalità, accertatevi di aver configurato un progetto come prerequisito per iniziare ad implementare la sovrapposizione di testo. Esempio,

* Creare un progetto AEM Screens (in questo esempio, **TextOverlayDemo**)

* Creare un canale di sequenza denominato **TextSample** nella cartella **Channels (Canali** )

* Aggiungere contenuto al canale **TextSample**

L&#39;immagine seguente mostra il progetto **TextOverlayDemo** con il canale **TextSample** nella cartella **Channels** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Per utilizzare la sovrapposizione di testo in un canale AEM Screens, effettuate le operazioni seguenti:

1. Andate a **TextOverlayDemo** —> **Canali** —> **TextSample** e fate clic su **Modifica** dalla barra delle azioni per aprire l&#39;editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Selezionate l’immagine e fate clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Selezionate l’opzione Sovrapposizione **** testo dalla barra di navigazione della finestra di dialogo, come illustrato nella figura riportata di seguito.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Informazioni sulle proprietà delle sovrapposizioni di testo {#understanding-text-overlay-properties}

Utilizzando le proprietà Sovrapposizione testo, potete aggiungere del testo a qualsiasi componente del progetto Screens. La sezione seguente fornisce una panoramica delle proprietà disponibili in Sovrapposizione testo:

![Testo](assets/text.gif)

È possibile aggiungere un testo alla casella di testo e evidenziare elementi tipografici quali grassetto, corsivo, sottolineato e così via.

**Variante** colore Questa opzione consente al testo di essere scuro (testo con colore nero) o chiaro (testo con colore bianco).

**Ridimensionamento e posizionamento** Questa opzione consente all’utente di allineare il testo in orizzontale o in verticale oppure di utilizzare strumenti con granulometria fine per l’allineamento del testo.

>[!NOTE]
>
>Per utilizzare correttamente gli strumenti a grana fine, accertatevi di identificare la posizione corretta in pixel usando (px) come suffisso, ad esempio 200px. Il risultato di questa espressione sarà di 200 pixel dal punto iniziale.

## Utilizzo dei valori ContextHub in sovrapposizione testo {#using-text-overlay-context-hub}

La sezione seguente descrive l’uso dei valori da un archivio dati, ad esempio, fogli google nel componente per sovrapposizione testo.

**Prerequisiti**

Devi configurare le configurazioni ContextHub per il progetto AEM Screens.

Per informazioni su come impostare e gestire le modifiche delle risorse basate sui dati utilizzando un archivio dati, consultate [Configurazione di ContextHub in AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Una volta configurate le configurazioni richieste per il progetto, seguite i passaggi seguenti per utilizzare i valori dei fogli di Google:

1. Andate a **TextOverlayDemo** —> **Canali** —> **TextSample** e fate clic su **Proprietà** dalla barra delle azioni.

1. Selezionate la scheda **Personalizzazione** per impostare le configurazioni ContextHub.

   1. Selezionate **ContextHub Path** come **libs** > **settings** > **cloud settings** > **default** **** ****>ContextHub Configurations, quindi fate clic suSelect.

   1. Selezionare Percorso **** segmenti come **conf** > **schermate** > **impostazioni** > **wcm** **** ****> Segmentidi segmenti, quindi fare clic su Seleziona.

   1. Fate clic su **Salva e chiudi**.

      >[!NOTE]
      >
      >Usa ContextHub e il percorso Segments, dove hai salvato inizialmente le configurazioni e i segmenti dell&#39;hub di contesto.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Andate a **TextOverlayDemo** —> **Canali** —> **TextSample** e fate clic su **Modifica** dalla barra delle azioni per aprire l&#39;editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Aggiungete all’immagine un componente di immagine e sovrapposizione di testo come descritto nella sezione [Utilizzo della sovrapposizione](/help/user-guide/text-overlay.md#using-text-overlay) di testo di questa pagina.

1. Fate clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo **Immagine** .

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Passare alla scheda **ContextHub** dalla finestra di dialogo **Immagine** . Fate clic su **Aggiungi**.

   >[!NOTE]
   >Se non hai impostato le configurazioni ContextHub, questa opzione sarà disabilitata per il progetto.

1. Immettere **Valore** nel campo **Segnaposto** , selezionare la riga che si desidera ottenere dal foglio di Google nella variabile **** ContextHub (in questo caso, il valore viene recuperato dalla riga 2 e dalla colonna 1 dai fogli di Google) e immettere il valore **** Predefinito come **20**, come illustrato nella figura seguente. Dopo aver fatto clic sul segno di spunta.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Per riferimento, la seguente immagine mostra il valore recuperato dai fogli di Google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Tornate alla scheda Sovrapposizione **** testo dalla finestra di dialogo Immagine e aggiungete il testo Temperatura *corrente {Valore}*, come illustrato nella figura seguente.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Fate clic su **Anteprima** per visualizzare l’output desiderato.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)















