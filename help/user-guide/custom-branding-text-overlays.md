---
title: Applicazione del marchio personalizzato e dello stile per le sovrapposizioni di testo
seo-title: Applicazione del marchio personalizzato e dello stile per le sovrapposizioni di testo
description: Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo.
seo-description: Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 04639198c5220e01af5945b8032c5fd86dc27499
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 1%

---


# Personalizzazione e stile per le sovrapposizioni di testo {#creating-custom-branding-styling}

Seguite questa pagina per apprendere come applicare il marchio e lo stile personalizzati per le sovrapposizioni di testo applicate alle risorse in un canale Screens.

## Creazione di stili e marchi personalizzati per le sovrapposizioni di testo {#steps-custom-branding}

Per creare un marchio e uno stile personalizzati per le sovrapposizioni di testo, effettuate le seguenti operazioni:

1. Crea un progetto AEM Screens. Questo esempio mostra la funzionalità creando un progetto denominato **customstyle** e un canale denominato **DemoBrand** , come illustrato nella figura riportata di seguito.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dall’editor trascinate un’immagine e aggiungete una sovrapposizione di testo alla risorsa.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Per informazioni su come aggiungere una sovrapposizione di testo alla risorsa in un editor canale, consultate Sovrapposizione [](/help/user-guide/text-overlay.md)testo.

1. Passa a CRXDE Lite dall’istanza di AEM —> Strumenti —> **CRXDE Lite**.

1. È necessario creare una progettazione personalizzata in `/apps/settings/wcm/designs/<your-project>/`, ad esempio, in questo caso, passare a `/apps/settings/wcm/designs/customstyle/`

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Create un file *static.css* e impostate le seguenti regole css. Anche mostrato come esempio nella figura sotto le regole css.

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

   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copiate il percorso del progetto, in questo caso il percorso sarà `/apps/settings/wcm/designs/customstyle`.

1. Andate al canale denominato **DemoBrand** (creato al punto 1)) e fate clic su **Proprietà** dalla barra delle azioni dopo aver selezionato il canale.

1. Passare alla scheda **Avanzate** e selezionare il campo **Progettazione** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Per impostazione predefinita, il campo **Progettazione** mostra il percorso che punta alle strutture nella cartella libs.

1. Aggiornate il campo **Progettazione** con il percorso della cartella del progetto. In questo caso, sarà, `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Fate clic su **Salva e chiudi** per aggiornare il percorso di progettazione.

>[!IMPORTANT]
> È possibile sovrapporre i modelli esistenti di Screens per inserire i propri design per impostazione predefinita o creare un modello personalizzato. Per ulteriori informazioni, fare riferimento ai passaggi descritti di seguito.

1. Per sovrapporre i modelli Screens esistenti per inserire i propri design per impostazione predefinita:

   1. Sovrapposizione `/libs/screens/core/templates/sequencechannel` in `/apps/screens/core/templates/sequencechannel`.
   1. Modificate la proprietà *cq:designPath* in `/apps/screens/core/templates/sequencechannel/jcr:content` modo da puntare alla nuova progettazione.

1. Per creare un modello personalizzato:
   1. Copia `/libs/screens/core/templates/sequencechannel` in `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modificate la proprietà *cq:designPath* in `/apps/customstyle/templates/styled-sequencechannel/jcr:content` modo da puntare alla nuova progettazione.


### Aggiornamento degli ACL {#updating-acls}

È necessario aggiornare gli ACL per queste progettazioni in modo che possano essere scaricati dal lettore.

1. Andate a useradmin e scegliete il percorso `screens-<project>-devices group` e assegnategli l&#39;autorizzazione di lettura per il percorso di progettazione personalizzato.

1. Specifica le autorizzazioni di lettura e modifica del `screens-<project>-administrators` gruppo per questo percorso.

## Visualizzazione del risultato {#viewing-the-result}

Una volta completati i passaggi precedenti, potete aggiornare il file *statis.css* da **CRXDE Lite** e visualizzare di conseguenza l’aggiornamento alla sovrapposizione di testo già aggiunta alla risorsa.

Per visualizzare la struttura aggiornata alla sovrapposizione di testo, effettuate le seguenti operazioni:

1. Passa al progetto AEM Screens denominato **custom style** —> **Channels** —> **DemoBrand**. Select the channel and click **Edit** from the action bar to open the editor.

1. Poiché la progettazione è stata aggiunta al campo **Progettazione** , come indicato sopra, fate clic su **Anteprima** per visualizzare lo stile corrente sull&#39;immagine con sovrapposizione di testo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Individuate il file *static.css* in CRXDE Lite e aggiungete il font, ad esempio, `font-family: "Lucida Console", Courier, monospace;` a questo file, come illustrato di seguito.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Dopo aver salvato le modifiche e ricaricato l&#39;anteprima, viene visualizzato un aggiornamento al font della sovrapposizione di testo, come illustrato nella figura riportata di seguito.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Inoltre, potete rimuovere gli ultimi due blocchi di codice dal file *static.css* per rimuovere lo stile &quot;in box&quot; intorno alla sovrapposizione di testo.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Nell’anteprima verrà visualizzata la modifica aggiornata in cui la sovrapposizione di testo viene aggiunta all’immagine.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

Con riferimento all’esercitazione, ora potete aggiornare il vostro marchio e lo stile personalizzato per le sovrapposizioni di testo aggiunte alle risorse.









