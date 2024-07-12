---
title: Creazione di modelli personalizzati in layout multisito
description: Scopri come creare modelli personalizzati nei layout MultiZone per AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 1%

---

# Creazione di modelli personalizzati per i layout multizona {#creating-custom-templates-multizone}

In questa pagina viene illustrato come creare un modello personalizzato per un layout multizona.

## Considerazioni importanti {#considerations}

Prima di creare un modello personalizzato in un layout multizona è necessario tenere presenti due considerazioni importanti:

1. **Dimensioni pixel fisse o percentuali**:

   Decidi se utilizzare dimensioni pixel fisse per aree diverse per il layout personalizzato o se desideri creare un layout personalizzato utilizzando le percentuali.

   >[!NOTE]
   >L’utilizzo della percentuale per impostare le zone per il layout personalizzato consente di riutilizzare il modello su schermi di varie dimensioni.

1. **Convenzione di denominazione**:

   Consente di comprendere come creare modelli personalizzati per più aree da utilizzare in un progetto AEM Screens. Ma prima di tutto, devi capire il limite dei modelli che vuoi creare.

   | **Nome layout** | **Descrizione** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | Layout orizzontale a tre zone che consente di creare tre zone:<br>* Zona 1 come 20% dello schermo orizzontale e verticale da sinistra<br>* Zona 2 come 80% dello schermo orizzontale e 20% dello schermo verticale giustificato a destra<br>* Zona 3 come 100% dello schermo orizzontale e 80% dello schermo verticale. Il rapporto di formato è 16:9 |
   | `Upper20-PortraitHD2Zone` | Modello di ritratto in due zone che copre il 20% dello schermo dalla parte superiore, con proporzioni di 16:9 |
   | `Right20-LandscapeSD3Zone` | Modello a tre aree che copre il 20% dello schermo da destra, con proporzioni di 4:3 |

   >[!IMPORTANT]
   >Le aree definite nel layout personalizzato potrebbero non corrispondere alle proporzioni complessive dell&#39;intero layout. La convenzione di denominazione utilizzata in questo documento specifica le proporzioni del layout personalizzato nel suo complesso.

## Esempio di utilizzo del caso `Left20-LandscapeHD3Zone` Layout {#custom-template-one}

Seguire la sezione seguente per creare un modello personalizzato *`Left20-LandscapeHD3Zone`* con la seguente configurazione:

* **`Left20`** - La zona superiore a sinistra copre il 20% delle dimensioni dello schermo orizzontale e verticale.
* **`Landscape`** - Orientamento dello schermo.
* **`HD`** - Proporzioni 16:9.
* **`3Zone`** - Tre aree della visualizzazione.

## Rappresentazione visiva del layout MultiZone {#multi-layout-visual-one}

Il layout `Left20-LandscapeHD3Zone` consente di creare il seguente layout multizona nel progetto:

![immagine](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Creazione di un layout `Left20-LandscapeHD3Zone` {#landscape-layout-one}

Per creare un layout `Left20-LandscapeHD3Zone` per un progetto AEM Screens, eseguire la procedura seguente.

1. Creare un progetto AEM Screens con titolo **`customtemplate`**.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Passa a **CRXDE Liti** dalla tua istanza AEM > Strumenti > **CRXDE Liti**.

1. Crea una cartella in **app** con titolo **`customtemplate`**. Analogamente, creare un&#39;altra cartella con titolo **modello** in **`customtemplate`**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Fare clic su **Salva tutto** nella barra delle azioni di CRXDE Lite ogni volta che si crea, si modifica o si copia contenuto in uno dei nodi. In caso contrario, non è possibile eseguire il commit degli aggiornamenti.

1. Copia il modello a sinistra della barra da `/libs/screens/core/templates/splitscreenchannel/lbar-left` a `/apps/customtemplate/template`.

1. Rinomina **lbar-left** (`/apps/customtemplate/template`) copiato in **my-custom-layout**.
   ![immagine](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Passare a `/apps/customtemplate/template/my-custom-layout` e aggiornare le proprietà **`jcr:description`** a *Modello per`Left20-LandscapeHD3Zone`* e **`jcr:title`** a *`Left20-LandscapeHD3Zone`*.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Passare al nodo **`offline-config`** da `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` e aggiornare **`jcr:title`** a *`Left20-LandscapeHD3Zone`*.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Passa alla proprietà *`jcr:content`* di **my-custom-template** da `/apps/customtemplate/template/my-custom-layout/jcr:content` e aggiorna la proprietà **`cq:cssClass`** per poter utilizzare **aem-Layout my-custom-layout**.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. Con riferimento al passaggio (4) in cui è stato copiato il modello barra a sinistra, è possibile visualizzare tre griglie reattive in `my-custom-layout/jcr:content`. Aggiungi una classe CSS personalizzata a ciascuna griglia reattiva nella proprietà *`cq:cssClass`*, ad esempio *my-custom-layout-top-left* per il nodo *r1c1*.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Allo stesso modo, aggiungi *my-custom-layout-top-right* per *r1c2* e *my-custom-layout-bottom* per il nodo *r2c1*.

   >[!NOTE]
   >Queste classi personalizzate vengono utilizzate nel CSS per impostare la larghezza/altezza di queste griglie reattive.

   >[!NOTE]
   >È possibile aggiungere o rimuovere le griglie reattive in base al numero di griglie totali desiderate. In questo esempio vengono visualizzate due griglie nella prima riga e una nella seconda riga, in modo da ottenere un totale di tre griglie reattive (r1c1, r1c2, r2c1).

1. Copiare `/libs/settings/wcm/designs/screens` in `/apps/settings/wcm/designs/` e rinominare la progettazione copiata come **custom-template-designs**.

1. Passa a `/apps/settings/wcm/designs/custom-template-designs` e aggiorna la proprietà *`jcr:title`* di **custom-template-designs** in **customtemplate-design**.

1. Passare a `/apps/settings/wcm/designs/custom-template-designs` e creare un file static.css.

1. Copia il contenuto nel file `static.css`:

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >Puoi aggiornare le percentuali in base ai requisiti del modello personalizzato.

1. Passare a `/apps/<project>/templates/my-custom-layout/jcr:content` e aggiornare la proprietà *`cq:designPath`* a `/apps/settings/wcm/designs/customtemplate-designs` in modo da poter caricare gli stili configurati in static.css.

   >[!NOTE]
   >Digita tutti gli stili invece di copiare o incollare, il che può causare spazi bianchi che causano problemi di stile CSS.

## Visualizzazione del risultato {#viewing-result}

Segui i passaggi seguenti per utilizzare il modello personalizzato di cui sopra nel tuo progetto AEM Screens:

1. Passa al progetto Screens creato al passaggio 1 e fai clic sulla cartella **Canali**.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Fare clic su **Crea** nella barra delle azioni e fare clic sul modello **`Left20-LandscapeHD3Zone`** nella procedura guidata **Crea**.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Dopo aver creato un canale con il modello personalizzato, puoi aggiungere risorse al canale dall’editor. L’anteprima seguente mostra le immagini in un modello personalizzato.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserimento di un&#39;immagine come livello di sfondo {#inserting-image}

Potete inserire un&#39;immagine come livello di sfondo nel layout:

È possibile regolare la regola CSS per utilizzare &quot;data-uri&quot; e allineare direttamente l&#39;immagine (`Base64` codificata) nel file CSS creato in (passaggio 13), *static.css*.

Questa disposizione viene eseguita come segue:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Oppure, puoi seguire i passaggi seguenti:

1. Assicurati che l’immagine sia inclusa in qualche modo nella configurazione offline per il canale.
1. Utilizza un collegamento diretto all’immagine nel CSS qui sopra, invece della variante &quot;data-uri&quot;.


## Aggiornamento del colore di sfondo {#updating-color}

Per modificare il colore di sfondo, aggiungere il codice seguente al file xml (passaggio 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
