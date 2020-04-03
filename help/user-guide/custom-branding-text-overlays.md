---
title: Applicazione del marchio personalizzato e dello stile per le sovrapposizioni di testo
seo-title: Applicazione del marchio personalizzato e dello stile per le sovrapposizioni di testo
description: Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo.
seo-description: Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# Personalizzazione e stile per le sovrapposizioni di testo {#creating-custom-branding-styling}

Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo.

## Creazione di stili e marchi personalizzati per le sovrapposizioni di testo {#steps-custom-branding}

Per creare un marchio e uno stile personalizzati per le sovrapposizioni di testo, effettuate le seguenti operazioni:

1. Create un progetto AEM Screens intitolato come stile **** personalizzato e un canale denominato **DemoBrand**, come illustrato nella figura riportata di seguito.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dall’editor trascinate un’immagine e aggiungete una sovrapposizione di testo alla risorsa.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Per informazioni su come aggiungere una sovrapposizione di testo alla risorsa in un editor canale, consultate Sovrapposizione [testo](/help/user-guide/text-overlay.md).

1. Passa a CRXDE Lite dall’istanza di AEM —> Strumenti —> **CRXDE Lite**.

1. È necessario creare una progettazione personalizzata, ad esempio in `/apps/settings/wcm/designs/<your-project>/`questo caso

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Andate al file static.css e impostate le seguenti regole css. Anche mostrato nella figura seguente.

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copiate il percorso del progetto, in questo caso il percorso sarà `/apps/settings/wcm/designs/customstyle`.

1. Andate al canale denominato con titolo **DemoBrand** (creato nel passaggio 1)) e fate clic su **Proprietà** dalla barra delle azioni dopo aver selezionato il canale.

1. Passare alla scheda **Avanzate** e selezionare il campo **Progettazione** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Per impostazione predefinita, il campo **Progettazione** mostra il percorso che punta alle strutture nella cartella libs.

1. Aggiornate il campo **Progettazione** con il percorso della cartella del progetto. In questo caso, sarà, `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Fate clic su **Salva e chiudi** per aggiornare il percorso di progettazione.


## Visualizzazione del risultato {#viewing-the-result}

Una volta completati i passaggi precedenti, puoi aggiornare il file *statis.css* da **CRXDE Lite** e visualizzare di conseguenza l’aggiornamento al layout di testo aggiunto alla risorsa.

Per visualizzare la progettazione aggiornata al layout di testo, effettuate le seguenti operazioni:

1. Andate al progetto AEM Screens intitolato come stile **** personalizzato e un canale denominato **DemoBrand** , quindi fate clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.

1. Poiché la progettazione è stata aggiunta al campo **Progettazione** , come indicato sopra, fate clic su **Anteprima** per visualizzare lo stile corrente sull&#39;immagine con sovrapposizione di testo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Andate al file static.css in CRXDE Lite, ad esempio, aggiungete il font.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Dopo aver salvato le modifiche e ricaricato l’anteprima, viene visualizzato un aggiornamento del font della sovrapposizione di testo, come illustrato nella figura riportata di seguito.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Inoltre, potete rimuovere gli ultimi due blocchi di codice dal file static.css per rimuovere lo stile &quot;box&quot; intorno alla sovrapposizione di testo.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. La modifica aggiornata verrà visualizzata nell’anteprima in cui la sovrapposizione di testo viene aggiunta all’immagine, come illustrato di seguito.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

Di conseguenza, seguendo i passaggi descritti nelle sezioni precedenti, potete aggiornare il marchio e lo stile personalizzato per le sovrapposizioni di testo aggiunte alle risorse.









