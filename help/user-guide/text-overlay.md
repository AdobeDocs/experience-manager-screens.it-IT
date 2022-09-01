---
title: Sovrapposizione testo
seo-title: Text Overlay
description: Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza avvincente in un Canale per sequenza fornendo un titolo o una descrizione sovrapposti a un’immagine. Segui questa pagina per ulteriori informazioni.
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
* **Informazioni sulle proprietà della sovrapposizione testo**
* **Utilizzo dei valori ContextHub nella sovrapposizione del testo**

>[!CAUTION]
>
>La **Sovrapposizione testo** Questa funzione è disponibile solo se è stato installato AEM Feature Pack 5 o AEM 6.4 Feature Pack 3 di 6.3.

## Panoramica {#overview}

Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un’esperienza avvincente in un Canale per sequenza fornendo un titolo o una descrizione sovrapposti a un’immagine.

Per informazioni su come creare un componente personalizzato, consulta **Estensione di un componente AEM Screens**.

Questa sezione mostra solo come utilizzare e applicare il componente poster in un progetto AEM Screens e utilizzarlo come sovrapposizione di testo in uno dei canali di sequenza.

## Utilizzo della sovrapposizione testo {#using-text-overlay}

La sezione seguente descrive l’utilizzo della sovrapposizione testo in un progetto AEM Screens.

**Prerequisiti**

Prima di iniziare a implementare questa funzionalità, assicurati di aver impostato un progetto come prerequisito per iniziare a implementare la sovrapposizione di testo. Ad esempio:

* Crea un progetto AEM Screens (in questo esempio, **TextOverlayDemo**)

* Crea un canale per sequenza denominato come **TextSample** sotto **Canali** cartella

* Aggiungi contenuto al tuo **TextSample** Canale

L’immagine seguente mostra la **TextOverlayDemo** progetto con **TextSample** ingresso canale **Canali** cartella.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Segui i passaggi seguenti per utilizzare la sovrapposizione di testo in un canale AEM Screens:

1. Passa a **TextOverlayDemo** —> **Canali** —> **TextSample** e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Seleziona l’immagine e fai clic su **Configura** (icona a forma di chiave inglese) per aprire la finestra di dialogo delle proprietà.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Seleziona la **Sovrapposizione testo** nella barra di navigazione della finestra di dialogo, come illustrato nella figura riportata di seguito.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Informazioni sulle proprietà della sovrapposizione testo {#understanding-text-overlay-properties}

Utilizzando le proprietà Sovrapposizione testo , puoi aggiungere testo a qualsiasi componente del progetto Screens. La sezione seguente fornisce una panoramica delle proprietà disponibili in Sovrapposizione testo:

![text](assets/text.gif)

È possibile aggiungere un testo alla casella di testo e un’enfasi tipografica, ad esempio grassetto, corsivo e sottolineato.

**Variante colore** Questa opzione consente al testo di essere scuro (testo con colore nero) o chiaro (testo con colore bianco).

**Dimensioni e posizionamento** Questa opzione consente all’utente di allineare il testo orizzontalmente o verticalmente oppure di utilizzare strumenti a grana fine per l’allineamento del testo.

>[!NOTE]
>
>Per utilizzare correttamente gli strumenti a grana fine, accertati di identificare la posizione corretta in pixel utilizzando (px) come suffisso, ad esempio 200 px. Il risultato di questa espressione è di 200 pixel dal punto iniziale.

## Utilizzo dei valori ContextHub nella sovrapposizione del testo {#using-text-overlay-context-hub}

La sezione seguente descrive l&#39;utilizzo dei valori da un archivio dati, ad esempio, google sheet nel componente sovrapposizione testo.

**Prerequisiti**

Imposta le configurazioni ContextHub per il progetto AEM Screens.

Per informazioni su come impostare e gestire le modifiche delle risorse basate sui dati utilizzando un archivio dati, consulta [Configurazione di ContextHub in AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Una volta configurate le configurazioni richieste per il progetto, segui i passaggi seguenti per utilizzare i valori dei fogli di Google:

1. Passa a **TextOverlayDemo** —> **Canali** —> **TextSample** e fai clic su **Proprietà** dalla barra delle azioni.

1. Seleziona la **Personalizzazione** scheda per configurare le configurazioni di ContextHub.

   1. Seleziona la **Percorso ContextHub** come **libs** > **impostazioni** > **impostazioni cloud** > **default** > **Configurazioni ContextHub** e fai clic su **Seleziona**.

   1. Seleziona la **Percorso segmenti** come **conf** > **schermate** > **impostazioni** > **wcm** > **segmenti** e fai clic su **Seleziona**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      >
      >Utilizza ContextHub e il percorso Segmenti, in cui hai inizialmente salvato le configurazioni e i segmenti dell&#39;hub di contesto.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Passa a **TextOverlayDemo** —> **Canali** —> **TextSample** e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Aggiungi all’immagine un componente immagine e sovrapposizione testo come descritto in [Utilizzo della sovrapposizione testo](/help/user-guide/text-overlay.md#using-text-overlay) di questa pagina.

1. Fai clic su **Configura** (icona a forma di chiave inglese) per aprire **Immagine** finestra di dialogo.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Passa a **ContextHub** dalla scheda **Immagine** finestra di dialogo. Fate clic su **Aggiungi**.

   >[!NOTE]
   >Se non hai impostato le configurazioni di ContextHub, questa opzione è disabilitata per il progetto.

1. Invio **Valore** in **Segnaposto** campo . Selezionare la riga che si desidera ottenere il valore dal foglio Google in **Variabile ContextHub**. In questo caso, il valore viene recuperato dai fogli Google della riga 2 e della colonna 1. Ora inserisci il **Valore predefinito** come **20**, come illustrato nella figura riportata di seguito. Al termine, fai clic sul segno di spunta.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Per riferimento, l&#39;immagine seguente mostra il valore recuperato dai fogli di Google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Torna alla pagina **Sovrapposizione testo** scheda dalla finestra di dialogo Immagine e aggiungi il testo *Temperatura corrente {Value}*, come illustrato nella figura seguente.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Fai clic su **Anteprima** per visualizzare l&#39;output desiderato.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
