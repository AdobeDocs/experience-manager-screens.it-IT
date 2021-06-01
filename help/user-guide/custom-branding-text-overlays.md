---
title: Applicazione di branding e stile personalizzati per le sovrapposizioni di testo
seo-title: Applicazione di branding e stile personalizzati per le sovrapposizioni di testo
description: Segui questa pagina per scoprire come applicare branding e stile personalizzati per le sovrapposizioni di testo.
seo-description: Segui questa pagina per scoprire come applicare branding e stile personalizzati per le sovrapposizioni di testo.
contentOwner: Jyotika Syal
feature: Sviluppo di schermi
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---


# Branding personalizzato e stile per sovrapposizioni testo {#creating-custom-branding-styling}

Segui questa pagina per scoprire come applicare branding e stile personalizzati per le sovrapposizioni di testo applicate alle risorse in un canale AEM Screens.

## Creazione di branding e stili personalizzati per le sovrapposizioni di testo {#steps-custom-branding}

Segui i passaggi riportati di seguito per creare branding e stile personalizzati per le sovrapposizioni di testo:

1. Crea un progetto AEM Screens. Questo esempio illustra la funzionalità creando un progetto denominato **customstyle** e un canale denominato **DemoBrand** , come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dall’editor trascina e rilascia un’immagine e aggiungi sovrapposizione testo alla risorsa.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Per scoprire come aggiungere una sovrapposizione di testo alla risorsa in un editor di canali, consulta [Sovrapposizione di testo](/help/user-guide/text-overlay.md).

1. Passa a CRXDE Lite dalla tua istanza AEM —> strumenti —> **CRXDE Lite**.

1. È necessario creare una progettazione personalizzata in `/apps/settings/wcm/designs/<your-project>/`, ad esempio, in questo caso, accedi a `/apps/settings/wcm/designs/customstyle/`

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Crea il file *static.css* e imposta le seguenti regole css. Anche mostrato come esempio nella figura sotto le regole css.

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copia il percorso del progetto. In questo caso, il percorso sarà `/apps/settings/wcm/designs/customstyle`.

1. Passa al canale denominato **DemoBrand** (creato nel passaggio(1))) e fai clic su **Proprietà** nella barra delle azioni dopo aver selezionato il canale.

1. Passa alla scheda **Avanzate** e controlla il campo **Progettazione** .
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Per impostazione predefinita, il campo **Progettazione** mostra il percorso che punta alle progettazioni nella cartella libs.

1. Aggiorna il campo **Progettazione** con il percorso della cartella del progetto. In questo caso, sarà, `/apps/settings/wcm/designs/customstyle`.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Fai clic su **Salva e chiudi** per aggiornare il percorso di progettazione.

   >[!IMPORTANT]
   >Puoi sovrapporre i modelli Screens esistenti per inserire i tuoi progetti per impostazione predefinita o creare un modello tutto tuo. Per ulteriori informazioni, fai riferimento ai passaggi seguenti.

1. Per sovrapporre i modelli Screens esistenti per inserire le proprie progettazioni per impostazione predefinita:

   1. Sovrapponi `/libs/screens/core/templates/sequencechannel` in `/apps/screens/core/templates/sequencechannel`.
   1. Modifica la proprietà *cq:designPath* in `/apps/screens/core/templates/sequencechannel/jcr:content` per puntare alla nuova progettazione.

1. Per creare un modello personalizzato:
   1. Copia `/libs/screens/core/templates/sequencechannel` in `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifica la proprietà *cq:designPath* in `/apps/customstyle/templates/styled-sequencechannel/jcr:content` per puntare alla nuova progettazione.


### Aggiornamento delle ACL {#updating-acls}

Devi aggiornare le ACL per queste progettazioni in modo che possano essere scaricate dal lettore.

1. Passa all&#39;amministratore utente e scegli il `screens-<project>-devices group` e concedi ad esso l&#39;autorizzazione di lettura per il percorso di progettazione personalizzato.

1. Fornisci al gruppo `screens-<project>-administrators` le autorizzazioni di lettura e modifica per questo percorso.

## Visualizzazione del risultato {#viewing-the-result}

Una volta completati i passaggi precedenti, puoi aggiornare il file *statis.css* da **CRXDE Lite** e quindi visualizzare l’aggiornamento della sovrapposizione di testo già aggiunta alla risorsa.

Segui i passaggi riportati di seguito per visualizzare la progettazione aggiornata alla sovrapposizione del testo:

1. Passa al progetto AEM Screens denominato **customstyle** —> **Canali** —> **DemoBrand**. Seleziona il canale e fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.

1. Poiché hai aggiunto la progettazione al campo **Progettazioni**, come indicato in precedenza, fai clic su **Anteprima** per visualizzare lo stile corrente sull&#39;immagine con sovrapposizione testo.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Passa al file *static.css* in CRXDE Lite e aggiungi il font `font-family: "Lucida Console", Courier, monospace;` a questo file, come illustrato di seguito.
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Una volta salvate le modifiche e ricaricate l&#39;anteprima, verrà visualizzato un aggiornamento del font sovrapposto testo, come mostrato nella figura seguente.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Inoltre, è possibile rimuovere gli ultimi due blocchi di codice dal file *static.css* per rimuovere lo stile in box intorno alla sovrapposizione di testo.
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Nella tua anteprima verrà visualizzata la modifica aggiornata in cui la sovrapposizione testo viene aggiunta all&#39;immagine.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Ora è possibile aggiornare il marchio e lo stile personalizzato per le sovrapposizioni di testo aggiunte alle risorse.









