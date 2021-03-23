---
title: Creazione di modelli personalizzati nei layout MultiZone
seo-title: Creazione di modelli personalizzati nei layout MultiZone
description: Segui questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
seo-description: Segui questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
contentOwner: Jyotika Syal
feature: Sviluppo di schermi
role: Developer (Sviluppatore)
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---


# Creazione di modelli personalizzati per layout multi-zone {#creating-custom-templates-multizone}

In questa pagina viene illustrato come creare un modello personalizzato per un layout con più aree.

## Considerazioni importanti {#considerations}

È necessario tenere presenti due importanti considerazioni prima di creare un modello personalizzato nel layout a più aree:

1. **Dimensioni o percentuali** fisse dei pixel:

   È necessario decidere se utilizzare le dimensioni dei pixel fisse per aree diverse per il layout personalizzato o se si desidera creare un layout personalizzato utilizzando le percentuali.

   >[!NOTE]
   >Il vantaggio dell’utilizzo della percentuale per impostare le aree per il layout personalizzato consente di riutilizzare il modello in diverse dimensioni dello schermo.

1. **Convenzione** di denominazione:

   Prima di comprendere come creare modelli di aree multiple personalizzati da utilizzare in un progetto AEM Screens, è consigliabile conoscere la versione dei modelli da creare.

   | **Nome layout** | **Descrizione** |
   |---|---|
   | Left20-LandscapeHD3Zone | Si riferisce a un layout orizzontale a 3 zone che consente di creare 3 zone con zona 1 come 20% dello schermo orizzontale e verticale da sinistra, zona 2 come 80% dello schermo orizzontale e 20% dello schermo verticale giustificato, zona 3 come 100% dello schermo orizzontale e 80% dello schermo verticale con rapporto di formato di 16:9 |
   | Upper20-PortraitHD2Zone | Si riferisce a un modello per ritratti a 2 zone che copre il 20% dello schermo dalla parte superiore, con rapporto di formato di 16:9 |
   | Right20-LandscapeSD3Zone | Si riferisce a un modello a 3 zone che copre il 20% dello schermo da destra, con rapporto di formato di 4:3 |

   >[!IMPORTANT]
   >Le aree definite all’interno del layout personalizzato potrebbero non corrispondere alle proporzioni complessive dell’intero layout. La convenzione di denominazione seguita in questo documento specifica le proporzioni del layout personalizzato nel suo insieme.

## Esempio di utilizzo Case Left20-LandscapeHD3Zone Layout {#custom-template-one}

Segui la sezione seguente per creare un modello personalizzato *Left20-LandscapeHD3Zone* con la seguente configurazione:

* **Left20** fa riferimento alla zona superiore a sinistra che copre il 20% delle dimensioni dello schermo orizzontale e verticale.
* **** Fasce di destinazione per l’orientamento dello schermo
* **** HD: rapporto di formato 16:9
* **3** Zonerefers a tre zone del display

## Rappresentazione visiva del layout MultiZone {#multi-layout-visual-one}

Il layout Left20-LandscapeHD3Zone consente di creare nel progetto il seguente layout a più aree:

![immagine](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Creazione di un layout Left20-LandscapeHD3Zone {#landscape-layout-one}

Per creare un layout Left20-LandscapeHD3Zone per un progetto AEM Screens, effettua le seguenti operazioni:

1. Crea un progetto AEM Screens denominato **customtemplate**.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Passa a **CRXDE Lite** dalla tua istanza AEM —> Strumenti —> **CRXDE Lite**.

1. Crea una cartella in **apps** con titolo **customtemplate**. Allo stesso modo, crea un&#39;altra cartella denominata **template** in **customtemplate**, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >È consigliabile fare clic su **Salva tutto** nella barra delle azioni di CRXDE Lite ogni volta che si creano, modificano o copia contenuti in uno dei nodi, altrimenti non sarà possibile eseguire il commit degli aggiornamenti.

1. Copia il modello a sinistra della barra da `/libs/screens/core/templates/splitscreenchannel/lbar-left` a `/apps/customtemplate/template`.

1. Rinomina il **lbar-left** (`/apps/customtemplate/template`) copiato in **my-custom-layout**.
   ![immagine](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Passa a `/apps/customtemplate/template/my-custom-layout` e aggiorna le proprietà **jcr:description** a *Modello per Left20-LandscapeHD3Zone* e **jcr:title** a *Left20-LandscapeHD3Zone*.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Passa al nodo **offline-config** da `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` e aggiorna il **jcr:title** a *Left20-LandscapeHD3Zone*.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Passa alla proprietà *jcr:content* di **my-custom-template** da `/apps/customtemplate/template/my-custom-layout/jcr:content` e aggiorna la proprietà **cq:cssClass** su **aem-Layout my-custom-layout**.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. Facendo riferimento al passaggio (4), in cui hai copiato il modello a sinistra della barra, potrai visualizzare 3 griglie reattive in `my-custom-layout/jcr:content`. Aggiungi una classe css personalizzata a ciascuna griglia reattiva nella proprietà *cq:cssClass* , ad esempio *my-custom-layout—in alto a sinistra* per il nodo *r1c1*.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Allo stesso modo, aggiungi *my-custom-layout—top-right* per *r1c2* e, *my-custom-layout—bottom* per il nodo *r2c1*.

   >[!NOTE]
   >Queste classi personalizzate verranno utilizzate nel css per impostare la larghezza/altezza per queste griglie reattive.

   >[!NOTE]
   >È possibile aggiungere o rimuovere le griglie reattive in base al numero di griglie totali desiderate. In questo esempio, mostriamo 2 griglie nella prima riga e 1 griglia nella seconda riga, quindi ci sono un totale di 3 griglie reattive (r1c1, r1c2, r2c1).

1. Copia `/libs/settings/wcm/designs/screens` in `/apps/settings/wcm/designs/` e rinomina la progettazione copiata come **custom-template-designs**.

1. Passa a `/apps/settings/wcm/designs/custom-template-designs` e aggiorna la proprietà *jcr:title* di **custom-template-designs** a **customtemplate-design**.

1. Passa a `/apps/settings/wcm/designs/custom-template-designs` e crea un file static.css.

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
   >Puoi aggiornare le percentuali in modo che corrispondano ai requisiti per il modello personalizzato.

1. Passa a `/apps/<project>/templates/my-custom-layout/jcr:content` e aggiorna la proprietà *cq:designPath* a `/apps/settings/wcm/designs/customtemplate-designs` per caricare gli stili configurati in static.css

   >[!NOTE]
   >È consigliabile digitare tutti gli stili anziché copiare o incollare, in modo da causare problemi di stile CSS.

## Visualizzazione del risultato {#viewing-result}

Segui i passaggi riportati di seguito per utilizzare il modello personalizzato sopra indicato nel tuo progetto AEM Screens:

1. Passa al progetto Screens creato al passaggio (1) e seleziona la cartella **Canali** .

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Fai clic su **Crea** nella barra delle azioni e seleziona il modello **Left20-LandscapeHD3Zone** dalla procedura guidata **Crea** .

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Dopo aver creato un canale con il modello personalizzato, puoi aggiungere risorse al canale dall’editor. L’anteprima seguente mostra le immagini in un modello personalizzato.

   ![immagine](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserimento di un’immagine come livello di sfondo {#inserting-image}

Potete inserire un’immagine come livello di sfondo nel layout:

Puoi regolare la regola CSS per utilizzare ciò che viene chiamato &quot;data-uri&quot; e inline direttamente l&#39;immagine (codificata Base64) nel file CSS, creato in (passaggio 13), *static.css*.

Ciò avviene nel modo seguente:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Oppure, puoi seguire i passaggi seguenti:

1. Assicurati che l&#39;immagine sia in qualche modo inclusa nella configurazione offline del canale
1. Utilizza un collegamento diretto all’immagine nel CSS precedente, invece della variante &quot;data-uri&quot;


## Aggiornamento del colore di sfondo {#updating-color}

Per modificare il colore di sfondo, aggiungi il seguente codice al file xml (passaggio 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



