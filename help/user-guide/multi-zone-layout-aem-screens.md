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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Layout con più aree {#multi-zone-layout}

La pagina seguente descrive l’utilizzo del layout a più zone e illustra i seguenti argomenti:

* Panoramica
* Creazione di un layout con più aree
* Prerequisiti
* Utilizzo di risorse singole in una o più aree
* Utilizzo del contenuto sequenziale in una o più aree

## Panoramica {#overview}

***Layout*** con più aree consente di creare contenuti con più aree e di utilizzare una varietà di risorse come video, immagini e testo che possono essere combinati in un unico schermo. Potete inserire immagini, video e testo per fonderli e creare un'esperienza digitale intuitiva.

In base ai requisiti del progetto, talvolta è necessario disporre di più aree in un canale e modificarle come un’unica unità. Ad esempio, una sequenza del prodotto con il relativo feed social media in esecuzione in tre aree distinte su un singolo canale.

## Creazione di un layout con più aree {#creating-multi-zone-layout}

Durante la creazione di un canale, potete usare diversi modelli per creare aree nel vostro canale. Potete aggiungere una singola immagine, un video o un canale incorporato che consenta la visualizzazione di più risorse in una sequenza.

### Prerequisiti {#prerequisites}

Prima di iniziare ad implementare questa funzionalità, assicuratevi di disporre di un progetto pronto come prerequisito per iniziare a implementare il layout multizona. Esempio,

* Creare un progetto AEM Screens denominato **AEM Screens**
* Creare una visualizzazione in **Posizioni** denominate **MultiZoneDisplay**

Create un canale denominato **MultiZone** nel progetto **Zone** . Effettuate le seguenti operazioni:

**Creazione del canale**

1. Seleziona il collegamento all’Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. Andate alla cartella **Canali** e fate clic su **Crea** dalla barra delle azioni.

1. Selezionate **Barra L a sinistra Dividi canale** schermo dalla procedura guidata **Crea** .

1. Fate clic su **Avanti** e immettete il **titolo** come **MultiZone**.

1. Fate clic su **Crea** per completare la creazione del canale.

![screen_shot_2018-12-07at120026pm](assets/screen_shot_2018-12-07at120026pm.png)

### Utilizzo di risorse singole in una o più aree {#using-single-assets-in-one-or-more-zones}

Potete usare singole risorse, ad esempio un’immagine o un video, in tutte e tre le aree. Seguite i passaggi indicati di seguito per l'implementazione:

1. **Aggiunta di contenuti al canale**

   1. Passare a **Aree** —&gt; **Canali**—&gt;**Zonamultipla**.
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.
   ![screen_shot_2018-12-07at14917pm](assets/screen_shot_2018-12-07at14917pm.png)

1. **Aggiunta di immagini al canale**

   Per riprodurre una singola immagine o un video in tutte e tre le aree, trascinate e rilasciate l’immagine nell’editor canale, come mostrato di seguito.

   ![new1-1](assets/new1-1.gif)

### Utilizzo del contenuto sequenziale in una o più aree {#using-sequenced-content-in-one-or-more-zones}

Se desiderate che nelle aree venga visualizzata una sequenza di immagini o contenuti e un'immagine statica in tre aree diverse, seguite i passaggi indicati di seguito per ulteriori dettagli.

1. **Creazione di una cartella canale**

   1. Passate alle **aree** —&gt; **MultiZone** —&gt; **Canali** e fate clic su **Crea** dalla barra delle azioni.
   1. Select **Channels Folder** from the **Create** wizard and click **Next**.
   1. Enter the title as **EmbeddedChannels** and click **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Aggiunta di altri due canali alla cartella Canale**

   1. Andate a **Aree** —&gt; **Canali** —&gt; **Canali** incorporati e fate clic su **Crea** dalla barra delle azioni.
   1. Selezionate Canale **** sequenza dalla procedura guidata **Crea** per creare un canale denominato** Zone1*.
   1. Select **Zone1** and click **Edit** from the action bar to open the editor.
   1. Trascinate alcune immagini su questo canale.
   Analogamente, create un altro canale di sequenza denominato **Zone2** nella cartella **EmbeddedChannels** .

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

1. **Aggiunta di sequenze/componenti incorporati al canale principale (MultiZone)**

   1. Passare a **Aree** —&gt; **Canali** —&gt; **Zona** multipla.
   1. Fai clic su **Modifica** nella barra delle azioni per aprire l'editor.
   1. Trascinate e rilasciate il componente Sequenza **** incorporata in due delle zone, come illustrato nella figura riportata di seguito.
   ![nuovo](assets/new.gif)

1. **Aggiungere contenuto a tutte e tre le aree**

   1. Passare a **Aree** —&gt; **Canali** —&gt; **Zona** multipla.
   1. Selezionare la sequenza incorporata in una delle zone.
   1. Fate clic sull'icona **Configura** (chiave inglese) per passare a una delle sequenze incorporate nell'editor.
   1. Selezionate il percorso del canale come **Aree** —&gt; **Canali** —&gt; **IncorporatiCanali** —&gt; **Zona1**, come illustrato nella figura seguente.
   Allo stesso modo, aggiungete la **Zona2** a un altro componente della sequenza incorporata nell’editor. Inoltre, aggiungete un’immagine alla terza zona in basso, come illustrato di seguito.

   ![new2-1](assets/new2-1.gif)

#### Visualizzazione del risultato {#viewing-the-result}

Una volta implementati i layout con più aree utilizzando i passaggi precedenti, viene visualizzato il seguente output, come illustrato nella figura riportata di seguito.

Il seguente output in Screens Player visualizza il contenuto in tre aree diverse. Nelle zone a sinistra e a destra (entrambe utilizzano la sequenza incorporata come componente) viene visualizzata una sequenza di immagini e nella zona sottostante viene visualizzata un’immagine statica.

![new2-2](assets/new2-2.gif)
