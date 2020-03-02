---
title: Creazione di modelli personalizzati in layout MultiZone
seo-title: Creazione di modelli personalizzati in layout MultiZone
description: Seguite questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
seo-description: Seguite questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 90d3d91f127432d8783748f00440bc6949262826

---


# Creazione di modelli personalizzati per layout multi-zona {#creating-custom-templates-multizone}

In questa pagina viene illustrato come creare un modello personalizzato per un layout con più aree.

## Considerazioni importanti {#considerations}

Prima di creare un modello personalizzato in un layout con più aree è importante tenere presenti due considerazioni importanti:

1. **Dimensioni o percentuali** fisse in pixel:

   È necessario decidere se utilizzare la dimensione in pixel fissa per aree diverse per il layout personalizzato o se creare un layout personalizzato utilizzando le percentuali.

   > [!NOTE]
   > Il vantaggio derivante dall’utilizzo della percentuale per impostare le aree per il layout personalizzato consente di riutilizzare il modello in diverse dimensioni di schermo.

1. **Convenzione** di denominazione:

   Prima di comprendere come creare modelli personalizzati per più aree da utilizzare in un progetto AEM Screens, è consigliabile conoscere la versione dei modelli da creare.

   | **Nome layout** | **Descrizione** |
   |---|---|
   | Left20-LandscapeHD3Zone | Si riferisce a un layout orizzontale a 3 zone che consente di creare 3 zone con la zona 1 come 20% dello schermo orizzontale e verticale da sinistra, la zona 2 come 80% dello schermo orizzontale e il 20% dello schermo verticale giustificato, la zona 3 come 100% dello schermo orizzontale e l&#39;80% dello schermo verticale con proporzioni pari a 16:9 |
   | Upper20-PortraitHD2Zone | Si riferisce a un modello verticale a 2 zone che copre il 20% dello schermo dalla parte superiore, con proporzioni pari a 16:9 |
   | Right20-LandscapeSD3Zone | Si riferisce a un modello a 3 zone che copre il 20% dello schermo da destra, con proporzioni pari a 4:3 |

   > [!IMPORTANT]
   > Le aree definite all&#39;interno del layout personalizzato potrebbero non corrispondere alle proporzioni complessive dell&#39;intero layout. La convenzione di denominazione seguita in questo documento specifica le proporzioni dell&#39;intero layout personalizzato.

## Esempio di utilizzo Case Left20-LandscapeLayout HD3Zone {#custom-template-one}

Seguite la sezione seguente per creare un modello personalizzato *Left20-LandscapeHD3Zone* con la seguente configurazione:

* **Left20** fa riferimento alla zona superiore sinistra che copre il 20% delle dimensioni orizzontali e verticali dello schermo.
* **Orizzontale** si riferisce all&#39;orientamento dello schermo
* **HD** indica le proporzioni 16:9
* **3Zone** si riferisce a tre zone del display

## Rappresentazione visiva del layout MultiZone {#multi-layout-visual-one}

Il layout Left20-LandscapeHD3Zone consente di creare nel progetto il seguente layout a più zone:

![image](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Creazione di un layout Left20-LandscapeHD3Zone {#landscape-layout-one}

Per creare un layout Left20-LandscapeHD3Zone per un progetto AEM Screens, effettuate le seguenti operazioni:

1. Crea un progetto AEM Screens denominato **modello** personalizzato.

   ![image](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Andate a **CRXDE Lite** dall’istanza di AEM —> Strumenti —> **CRXDE Lite**.

1. Create una cartella nelle **app** con titolo come modello **** personalizzato. Analogamente, create un’altra cartella denominata **template** in **custom template**, come illustrato nella figura riportata di seguito.

   ![image](/help/user-guide/assets/custom-multizone/custom-template1.png)

   > [!NOTE]
   > È consigliabile fare clic su **Save all** from the action bar in CRXDE Lite ogni volta che si crea, modifica o copia contenuto in uno dei nodi, altrimenti non sarà possibile eseguire il commit degli aggiornamenti.

1. Copiate il modello da barra a sinistra da `/libs/screens/core/templates/splitscreenchannel/lbar-left` a `/apps/customtemplate/template`.

1. Rinominare la **barra a sinistra** copiata (`/apps/customtemplate/template`) in **layout**personalizzato.
   ![image](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Andate a `/apps/customtemplate/template/my-custom-layout` e aggiornate le proprietà **jcr:description** in *Template for Left20-LandscapeHD3Zone* and **jcr:title** to *Left20-LandscapeHD3Zone*(Modello per Left20-Landscape).

   ![image](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Andate al nodo **offline-config** da `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` e aggiornate **jcr:title** a *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Andate alla proprietà *jcr:content* di **my-custom-template** da `/apps/customtemplate/template/my-custom-layout/jcr:content` e aggiornate la proprietà **cq:cssClass** su **aem-Layout my-custom-layout**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. Facendo riferimento al passaggio (4), in cui avete copiato il modello a sinistra, potrete visualizzare 3 griglie reattive sotto `my-custom-layout/jcr:content`. Aggiungi classe css personalizzata a ciascuna griglia reattiva nella proprietà *cq:cssClass* , ad esempio, *my-custom-layout—in alto a sinistra* per il nodo *r1c1* .

   ![image](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Allo stesso modo, aggiungete *il layout personalizzato (in alto a destra* per *r1c2* e *il layout personalizzato) in basso* per il nodo *r2c1* .

   >[!NOTE]
   >Queste classi personalizzate verranno utilizzate nel css per impostare larghezza/altezza per queste griglie reattive.

   >[!NOTE]
   > Potete aggiungere o rimuovere le griglie reattive in base al numero totale di griglie desiderato. In questo esempio, vengono mostrate 2 griglie nella prima riga e 1 griglia nella seconda riga, quindi ci sono un totale di 3 griglie reattive (r1c1, r1c2, r2c1).

1. Copiate `/libs/settings/wcm/designs/screens` in `/apps/settings/wcm/designs/` e rinominate la progettazione copiata come progettazioni **di modelli** personalizzati.

1. Andate a `/apps/settings/wcm/designs/custom-template-designs` e aggiornate la proprietà *jcr:title* della struttura **custom-template-designs** alla progettazione **di modelli** personalizzati.

1. Individuare `/apps/settings/wcm/designs/custom-template-designs` e creare un file static.css.

1. Copiate il contenuto in un file static.css:

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
   > Potete aggiornare le percentuali in modo che corrispondano ai requisiti per il modello personalizzato.

1. Individuare `/apps/<project>/templates/my-custom-layout/jcr:content` e aggiornare la proprietà *cq:designPath* per `/apps/settings/wcm/designs/customtemplate-designs` caricare gli stili configurati in static.css

   >[!NOTE]
   > Si consiglia di digitare tutti gli stili invece di copiare o incollare, il che può causare problemi di stile CSS causati da spazi bianchi.

## Visualizzazione del risultato {#viewing-result}

Segui i passaggi indicati di seguito per utilizzare il modello personalizzato riportato sopra nel progetto AEM Screens:

1. Andate al progetto Screens che avete creato nel passaggio (1) e selezionate la cartella **Channels (Canali** ).

   ![image](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Fate clic su **Crea** nella barra delle azioni e selezionate il modello **Left20-LandscapeHD3Zone** dalla **procedura guidata Crea** .

   ![image](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Dopo aver creato un canale con il modello personalizzato, potete aggiungere risorse al canale dall’editor. La seguente anteprima mostra le immagini in un modello personalizzato.

   ![image](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserimento di un’immagine come livello di sfondo {#inserting-image}

Potete inserire nel layout un’immagine come livello di sfondo:

Potete regolare la regola CSS in modo da usare ciò che viene chiamato &quot;data-uri&quot; e direttamente in linea l&#39;immagine (con codifica Base64) nel file CSS creato in (passaggio 13), *static.css*.

Tale operazione è effettuata come segue:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

In alternativa, puoi seguire i passaggi seguenti:

1. Accertatevi che l&#39;immagine sia in qualche modo inclusa nella configurazione offline per il canale
1. Utilizzate un collegamento diretto all&#39;immagine nel CSS precedente, invece della variante &quot;data-uri&quot;


## Aggiornamento colore di sfondo {#updating-color}

Per modificare il colore di sfondo, aggiungete il codice seguente al file xml (passaggio 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



