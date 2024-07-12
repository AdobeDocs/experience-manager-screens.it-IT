---
title: Applicazione di branding e stile personalizzati per le sovrapposizioni di testo
description: Scopri come applicare il branding e lo stile personalizzati per le sovrapposizioni di testo applicate alle risorse in un canale AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---

# Personalizza branding e stile per sovrapposizioni testo {#creating-custom-branding-styling}

Scopri come applicare il branding e lo stile personalizzati per le sovrapposizioni di testo applicate alle risorse in un canale AEM Screens.

## Creazione di branding e stili personalizzati per le sovrapposizioni di testo {#steps-custom-branding}

Per creare un marchio e uno stile personalizzati per le sovrapposizioni di testo, effettua le seguenti operazioni:

1. Crea un progetto AEM Screens. In questo esempio vengono illustrate le funzionalità mediante la creazione di un progetto denominato **`customstyle`** e di un canale denominato **DemoBrand**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dall’editor, trascina e rilascia un’immagine e aggiungi una sovrapposizione di testo alla risorsa.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Per informazioni su come aggiungere una sovrapposizione di testo alla risorsa in un editor di canali, consulta [Sovrapposizione di testo](/help/user-guide/text-overlay.md).

1. Passa a CRXDE Lite dalla tua istanza AEM > Strumenti > **CRXDE Liti**.

1. Creare una progettazione personalizzata in `/apps/settings/wcm/designs/<your-project>/`. In questo caso, ad esempio, passare a `/apps/settings/wcm/designs/customstyle/`

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Crea un file *static.css* e imposta le seguenti regole css. Anche mostrato come esempio nella figura sotto le regole css.

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

1. Copiare il percorso nel progetto. In questo caso, il percorso è `/apps/settings/wcm/designs/customstyle`.

1. Passa al canale con titolo **DemoBrand** (creato nel passaggio(1)) e fai clic su **Proprietà** nella barra delle azioni dopo aver selezionato il canale.

1. Passa alla scheda **Avanzate** e controlla il campo **Progettazione**.
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Per impostazione predefinita, il campo **Progettazione** mostra il percorso che punta alle progettazioni nella cartella libs.

1. Aggiorna il campo **Progettazione** con il percorso della cartella del progetto. In questo caso, è `/apps/settings/wcm/designs/customstyle`.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Fai clic su **Salva e chiudi** per aggiornare il percorso di progettazione.

   >[!IMPORTANT]
   >Facoltativamente, puoi sovrapporre i modelli Screens esistenti per inserire le progettazioni personalizzate per impostazione predefinita o creare completamente un modello personalizzato. Per ulteriori informazioni, consulta i passaggi seguenti.

1. Per sovrapporre i modelli Screens esistenti per inserire le proprie progettazioni per impostazione predefinita:

   1. Sovrapposizione di `/libs/screens/core/templates/sequencechannel` in `/apps/screens/core/templates/sequencechannel`.
   1. Modificare la proprietà *`cq:designPath`* in `/apps/screens/core/templates/sequencechannel/jcr:content` in modo che punti alla nuova struttura.

1. Per creare completamente un modello personalizzato:
   1. Copia `/libs/screens/core/templates/sequencechannel` in `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modificare la proprietà *`cq:designPath`* in `/apps/customstyle/templates/styled-sequencechannel/jcr:content` in modo che punti alla nuova struttura.


### Aggiornamento degli ACL {#updating-acls}

Aggiorna gli ACL per queste progettazioni in modo che il lettore possa scaricarle.

1. Passare all&#39;amministratore utenti, scegliere `screens-<project>-devices group` e concedere l&#39;autorizzazione di lettura per il percorso di progettazione personalizzato.

1. Fornire al gruppo `screens-<project>-administrators` le autorizzazioni di lettura e modifica per questo percorso.

## Visualizzazione del risultato {#viewing-the-result}

Dopo aver completato i passaggi precedenti, puoi aggiornare il file *statis.css* da **CRXDE Liti** e quindi visualizzare l&#39;aggiornamento alla sovrimpressione di testo già aggiunto alla risorsa.

Per visualizzare la progettazione aggiornata in sovrapposizione testo, attenersi alla procedura descritta di seguito.

1. Passa al progetto AEM Screens con titolo **`customstyle`** > **Canali** > **DemoBrand**. Fai clic sul canale e fai clic su **Modifica** nella barra delle azioni.

1. Poiché hai aggiunto la progettazione al campo **Progettazioni**, come indicato in precedenza, fai clic su **Anteprima** per visualizzare lo stile corrente dell&#39;immagine con sovrapposizione di testo.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Passa al file *static.css* in CRXDE Lite e aggiungi al file il tipo di carattere `font-family: "Lucida Console", Courier, monospace;`, come illustrato di seguito.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Quando salvi le modifiche e ricarichi l’anteprima, viene visualizzato un aggiornamento del font di sovrapposizione del testo, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. È inoltre possibile rimuovere gli ultimi due blocchi di codice dal file *static.css* per rimuovere lo stile del riquadro attorno alla sovrapposizione di testo.

![immagine](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Visualizza la modifica aggiornata nell’anteprima in cui la sovrapposizione di testo viene aggiunta all’immagine.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Ora puoi aggiornare il brand e lo stile personalizzato per le sovrapposizioni di testo aggiunte alle risorse.
