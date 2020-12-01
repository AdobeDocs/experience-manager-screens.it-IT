---
title: Applicazione del marchio personalizzato e dello stile per le sovrapposizioni di testo
seo-title: Applicazione del marchio personalizzato e dello stile per le sovrapposizioni di testo
description: Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo.
seo-description: Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 099000dea848810c7ab12a32f0235ca478c0d5dd
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 1%

---


# Personalizzazione e stile per le sovrapposizioni di testo {#creating-custom-branding-styling}

Seguite questa pagina per apprendere come applicare un marchio e uno stile personalizzati per le sovrapposizioni di testo applicate alle risorse in un canale AEM Screens .

## Creazione di un marchio personalizzato e stile per le sovrapposizioni di testo {#steps-custom-branding}

Per creare un marchio e uno stile personalizzati per le sovrapposizioni di testo, effettuate le seguenti operazioni:

1. Creare un progetto AEM Screens . Questo esempio mostra la funzionalità creando un progetto denominato **customstyle** e un canale denominato **DemoBrand**, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dall’editor trascinate un’immagine e aggiungete una sovrapposizione di testo alla risorsa.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Per informazioni su come aggiungere una sovrapposizione di testo alla risorsa in un editor canale, consultate [Text Overlay](/help/user-guide/text-overlay.md).

1. Andate al CRXDE Lite dall&#39;istanza AEM —> strumenti —> **CRXDE Lite**.

1. È necessario creare una progettazione personalizzata in `/apps/settings/wcm/designs/<your-project>/`, ad esempio in questo caso andate a `/apps/settings/wcm/designs/customstyle/`

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Create il file *static.css* e impostate le seguenti regole css. Anche mostrato come esempio nella figura sotto le regole css.

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

1. Copiate il percorso del progetto, in questo caso il percorso sarà `/apps/settings/wcm/designs/customstyle`.

1. Andate al canale denominato **DemoBrand** (creato al punto 1)) e fate clic su **Properties** dalla barra delle azioni dopo aver selezionato il canale.

1. Passare alla scheda **Avanzate** e controllare il campo **Progettazione**.
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Per impostazione predefinita, il campo **Design** mostra il percorso che punta alle strutture nella cartella libs.

1. Aggiornate il campo **Design** con il percorso della cartella del progetto. In questo caso, sarà `/apps/settings/wcm/designs/customstyle`.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Fare clic su **Salva e chiudi** per aggiornare il percorso di progettazione.

   >[!IMPORTANT]
   >È possibile sovrapporre i modelli esistenti di Screens per inserire i propri design per impostazione predefinita o creare un modello personalizzato. Per ulteriori informazioni, fare riferimento ai passaggi descritti di seguito.

1. Per sovrapporre i modelli Screens esistenti per inserire i propri design per impostazione predefinita:

   1. Sovrapposizione `/libs/screens/core/templates/sequencechannel` in `/apps/screens/core/templates/sequencechannel`.
   1. Modificate la proprietà *cq:designPath* in `/apps/screens/core/templates/sequencechannel/jcr:content` per puntare alla nuova progettazione.

1. Per creare un modello personalizzato:
   1. Copiare `/libs/screens/core/templates/sequencechannel` in `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modificate la proprietà *cq:designPath* in `/apps/customstyle/templates/styled-sequencechannel/jcr:content` per puntare alla nuova progettazione.


### Aggiornamento di ACL {#updating-acls}

È necessario aggiornare gli ACL per queste progettazioni in modo che possano essere scaricati dal lettore.

1. Passate all&#39;amministratore utente e scegliete `screens-<project>-devices group` e assegnategli l&#39;autorizzazione di lettura per il percorso di progettazione personalizzato.

1. Specifica le autorizzazioni di lettura e modifica del gruppo `screens-<project>-administrators` per questo percorso.

## Visualizzazione del risultato {#viewing-the-result}

Una volta completati i passaggi precedenti, potete aggiornare il file *statis.css* da **CRXDE Lite** e visualizzare di conseguenza l&#39;aggiornamento alla sovrapposizione di testo già aggiunta alla risorsa.

Per visualizzare la struttura aggiornata alla sovrapposizione di testo, effettuate le seguenti operazioni:

1. Andate al progetto AEM Screens  denominato **customstyle** —> **Channels** —> **DemoBrand**. Selezionate il canale e fate clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.

1. Poiché la progettazione è stata aggiunta al campo **Progettazione**, come indicato sopra, fare clic su **Anteprima** per visualizzare lo stile corrente sull&#39;immagine con sovrapposizione testo.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Individuate il file *static.css* nel CRXDE Lite e aggiungete il font `font-family: "Lucida Console", Courier, monospace;` al file, come illustrato di seguito.
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Dopo aver salvato le modifiche e ricaricato l&#39;anteprima, viene visualizzato un aggiornamento al font della sovrapposizione di testo, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Inoltre, potete rimuovere gli ultimi due blocchi di codice dal file *static.css* per rimuovere lo stile &quot;boxed&quot; intorno alla sovrapposizione di testo.
   ![immagine](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Nell’anteprima verrà visualizzata la modifica aggiornata in cui la sovrapposizione di testo viene aggiunta all’immagine.

   ![immagine](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Ora è possibile aggiornare il marchio e lo stile personalizzato per le sovrapposizioni di testo aggiunte alle risorse.









