---
title: Applicazione di branding e stile personalizzati per le sovrapposizioni di testo
description: Scopri come applicare il branding e lo stile personalizzati per le sovrapposizioni di testo applicate alle risorse in un canale AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---

# Personalizza branding e stile per sovrapposizioni testo {#creating-custom-branding-styling}

Scopri come applicare il branding e lo stile personalizzati per le sovrapposizioni di testo applicate alle risorse in un canale AEM Screens.

## Creazione di branding e stili personalizzati per le sovrapposizioni di testo {#steps-custom-branding}

Per creare un marchio e uno stile personalizzati per le sovrapposizioni di testo, effettua le seguenti operazioni:

1. Crea un progetto AEM Screens. Questo esempio mostra la funzionalità creando un progetto denominato **`customstyle`** e un canale con titolo **DemoBrand** , come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dall’editor, trascina e rilascia un’immagine e aggiungi sovrapposizione testo alla risorsa.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Per informazioni su come aggiungere una sovrapposizione di testo alla risorsa in un editor di canali, consulta [Sovrapposizione testo](/help/user-guide/text-overlay.md).

1. Passa a CRXDE Liti dall’istanza AEM > Strumenti > **CRXDE Liti**.

1. Creare una progettazione personalizzata in `/apps/settings/wcm/designs/<your-project>/`, ad esempio, in questo caso, passa a `/apps/settings/wcm/designs/customstyle/`

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Crea *static.css* e imposta le seguenti regole css. Anche mostrato come esempio nella figura sotto le regole css.

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

1. Copia il percorso nel progetto; in questo caso, il percorso è `/apps/settings/wcm/designs/customstyle`.

1. Passa al canale con titolo **DemoBrand** (creato nel passaggio 1) e fare clic su **Proprietà** dalla barra delle azioni dopo aver selezionato il canale.

1. Accedi a **Avanzate** e controllare la **Progettazione** campo.
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Per impostazione predefinita, **Progettazione** mostra il percorso che punta alle progettazioni nella cartella libs.

1. Aggiornare il **Progettazione** con il percorso della cartella del progetto. In questo caso, è `/apps/settings/wcm/designs/customstyle`.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Clic **Salva e chiudi** per aggiornare il percorso di progettazione.

   >[!IMPORTANT]
   >Facoltativamente, puoi sovrapporre i modelli di Screens esistenti per inserire le progettazioni personalizzate per impostazione predefinita o creare completamente un modello personalizzato. Per ulteriori informazioni, consulta i passaggi seguenti.

1. Per sovrapporre i modelli Screens esistenti per inserire le proprie progettazioni per impostazione predefinita:

   1. Sovrapposizione `/libs/screens/core/templates/sequencechannel` in `/apps/screens/core/templates/sequencechannel`.
   1. Modifica il *`cq:designPath`* proprietà in `/apps/screens/core/templates/sequencechannel/jcr:content` in modo che punti al nuovo design.

1. Per creare completamente un modello personalizzato:
   1. Copia `/libs/screens/core/templates/sequencechannel` a `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifica il *`cq:designPath`* proprietà in `/apps/customstyle/templates/styled-sequencechannel/jcr:content` in modo che punti al nuovo design.


### Aggiornamento degli ACL {#updating-acls}

Aggiorna gli ACL per queste progettazioni in modo che possano essere scaricati dal lettore.

1. Accedi all’amministratore utenti e scegli il `screens-<project>-devices group` e concedergli l&#39;autorizzazione di lettura per il percorso di progettazione personalizzato.

1. Fornire `screens-<project>-administrators` autorizzazioni di lettura e modifica di gruppo per questo percorso.

## Visualizzazione del risultato {#viewing-the-result}

Una volta completati i passaggi precedenti, puoi aggiornare *statis.css* file da **CRXDE Liti** e quindi visualizza l’aggiornamento della sovrapposizione di testo già aggiunto alla risorsa.

Per visualizzare la progettazione aggiornata in sovrapposizione testo, attenersi alla procedura descritta di seguito.

1. Passa al progetto AEM Screens con titolo **`customstyle`** > **Canali** > **DemoBrand**. Fai clic sul canale e fai clic su **Modifica** dalla barra delle azioni.

1. Poiché ora hai aggiunto il design al tuo **Progettazioni** come indicato in precedenza, fai clic su **Anteprima** per visualizzare lo stile corrente dell&#39;immagine con sovrapposizione testo.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Accedi al tuo *static.css* file in CRXDE Liti e aggiungi il font, ad esempio, `font-family: "Lucida Console", Courier, monospace;` a questo file, come illustrato di seguito.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Quando salvi le modifiche e ricarichi l’anteprima, viene visualizzato un aggiornamento del font di sovrapposizione del testo, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Inoltre, puoi rimuovere gli ultimi due blocchi di codice da *static.css* per rimuovere lo stile del riquadro attorno alla sovrapposizione di testo.

![immagine](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Visualizza la modifica aggiornata nell’anteprima in cui la sovrapposizione di testo viene aggiunta all’immagine.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Ora puoi aggiornare il brand e lo stile personalizzato per le sovrapposizioni di testo aggiunte alle risorse.
