---
title: Sovrapposizione testo
seo-title: Sovrapposizione testo
description: Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un'esperienza coinvolgente in un canale sequenza fornendo un titolo o una descrizione sovrapposto a un'immagine. Segui questa pagina per saperne di più.
seo-description: Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un'esperienza coinvolgente in un canale sequenza fornendo un titolo o una descrizione sovrapposto a un'immagine. Segui questa pagina per saperne di più.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Sovrapposizione testo {#text-overlay}

Questa sezione illustra i seguenti argomenti:

* **Panoramica**
* **Utilizzo della sovrapposizione testo**
* **Prerequisiti**
* **Informazioni sulle proprietà delle sovrapposizioni di testo**

>[!CAUTION]
>
>La funzione Sovrapposizione **** testo è disponibile solo se avete installato AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

## Panoramica {#overview}

Sovrapposizione testo è una funzione disponibile in AEM Screens che consente di creare un'esperienza coinvolgente in un canale sequenza fornendo un titolo o una descrizione sovrapposto a un'immagine.

Per informazioni su come creare un componente personalizzato, consultate **Estensione di un componente** AEM Screens.

Questa sezione mostra solo come usare e usare il componente poster in un progetto AEM Screens e utilizzarlo come sovrapposizione di testo in uno dei canali della sequenza.

## Utilizzo della sovrapposizione testo {#using-text-overlay}

La sezione seguente descrive l'utilizzo della sovrapposizione di testo in un progetto AEM Screens.

### Prerequisiti {#prerequisites}

Prima di iniziare ad implementare questa funzionalità, accertatevi di aver configurato un progetto come prerequisito per iniziare ad implementare la sovrapposizione di testo. Esempio,

* Creare un progetto AEM Screens (in questo esempio, **TextOverlayDemo**)

* Crea un canale come **TextSample** nella cartella **Canali**

* Aggiungere contenuto al canale **TextSample**

L'immagine seguente mostra il progetto **TextOverlayDemo** con il canale **TextSample** nella cartella **Channels** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. Andate a **TextOverlayDemo** —&gt; **Canali** —&gt; **TextSample** e fate clic su **Modifica** dalla barra delle azioni per aprire l'editor.

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

