---
title: Sviluppo di un componente personalizzato per AEM Screens
seo-title: Sviluppo di un componente personalizzato per AEM Screens
description: L’esercitazione seguente illustra i passaggi necessari per creare un componente personalizzato per AEM Screens. AEM Screens riutilizza molti modelli di progettazione e tecnologie esistenti di altri prodotti AEM. L’esercitazione evidenzia differenze e considerazioni speciali durante lo sviluppo per AEM Screens.
seo-description: Un tutorial introduttivo per creare un semplice componente "Hello World" per AEM Screens. AEM Screens riutilizza molti modelli di progettazione e tecnologie esistenti di altri prodotti AEM. L’esercitazione seguente intende evidenziare le differenze e le considerazioni specifiche durante lo sviluppo per AEM Screens.
uuid: 8ec8be5a-6348-48f2-9cb7-75b2bad555a6
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 24eb937f-ab51-4883-8236-8ebe6243f6e3
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '2190'
ht-degree: 2%

---


# Sviluppo di un componente personalizzato per AEM Screens {#developing-a-custom-component-for-aem-screens}

L’esercitazione seguente illustra i passaggi necessari per creare un componente personalizzato per AEM Screens. AEM Screens riutilizza molti modelli di progettazione e tecnologie esistenti di altri prodotti AEM. L’esercitazione evidenzia differenze e considerazioni speciali durante lo sviluppo per AEM Screens.

## Panoramica {#overview}

Questa esercitazione è destinata agli sviluppatori che hanno poca esperienza con AEM Screens. In questa esercitazione viene creato un semplice componente &quot;Hello World&quot; per un canale Sequenza in AEM Screens. Una finestra di dialogo consente agli autori di aggiornare il testo visualizzato.

![capogruppo](assets/overviewhellow.png)

## Prerequisiti {#prerequisites}

Per completare questa esercitazione è necessario quanto segue:

1. [Feature Pack di AEM 6.5](https://helpx.adobe.com/it/experience-manager/6-4/release-notes.html) o  [AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + ultimo Screens

1. [Lettore AEM Screens](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-screens-introduction.html)
1. Ambiente di sviluppo locale

I passaggi del tutorial e le schermate vengono eseguiti utilizzando **CRXDE-Lite**. Gli IDE possono anche essere utilizzati per completare l’esercitazione. Ulteriori informazioni sull&#39;utilizzo di un IDE per sviluppare [con AEM sono disponibili qui.](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#eclipse-ide)


## Configurazione del progetto {#project-setup}

Il codice sorgente di un progetto Screens viene generalmente gestito come progetto Maven con più moduli. Per accelerare l’esercitazione, un progetto è stato generato in precedenza utilizzando il [AEM Project Archetype 13](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype). Ulteriori dettagli sulla [creazione di un progetto con Maven AEM Project Archetype sono disponibili qui](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#maven-multimodule).

1. Scarica e installa i seguenti pacchetti utilizzando [CRX package manager](http://localhost:4502/crx/packmgr/index.jsp):

   [Ottieni file](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [Ottieni file](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **** Se si lavora con Eclipse o un altro IDE, è possibile scaricare il pacchetto sorgente seguente. Distribuisci il progetto in un’istanza AEM locale utilizzando il comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Avvia progetto di esecuzione di We.Retail di HelloWorld SRC Screens

   [Ottieni file](assets/src-screens-weretail-run.zip)

1. In [CRX Package Manager](http://localhost:4502/crx/packmgr/index.jsp) verifica che siano installati i due pacchetti seguenti:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Schermi I.Retail Esegui pacchetti Ui.Apps e Ui.Content installati tramite CRX Package Manager](assets/crx-packages.png)

   Schermi I.Retail Esegui pacchetti Ui.Apps e Ui.Content installati tramite CRX Package Manager

1. Il pacchetto **screens-weretail-run.ui.apps** installa il codice sotto `/apps/weretail-run`.

   Questo pacchetto contiene il codice responsabile del rendering dei componenti personalizzati per il progetto. Questo pacchetto include il codice del componente ed eventuali codice JavaScript o CSS necessari. Questo pacchetto incorpora anche **screens-weretail-run.core-0.0.1-SNAPSHOT.jar** , che contiene eventuali codici Java necessari per il progetto.

   >[!NOTE]
   >
   >In questa esercitazione non viene scritto alcun codice Java. Se è necessaria una logica di business più complessa, puoi creare e distribuire Java back-end utilizzando il bundle Java core.

   ![Rappresentazione del codice ui.apps in CRXDE Lite](assets/uipps-contents.png)

   Rappresentazione del codice ui.apps in CRXDE Lite

   Il componente **helloworld** è attualmente solo un segnaposto. Nel corso dell’esercitazione, verrà aggiunta una funzionalità che consente all’autore di aggiornare il messaggio visualizzato dal componente.

1. Il pacchetto **screens-weretail-run.ui.content** installa il codice sotto:

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   Questo pacchetto contiene il contenuto iniziale e la struttura di configurazione necessarie per il progetto. **`/conf/we-retail-run`** contiene tutte le configurazioni per il progetto We.Retail Run. **`/content/dam/we-retail-run`** include l&#39;avvio di risorse digitali per il progetto. **`/content/screens/we-retail-run`** contiene la struttura del contenuto Screens. Il contenuto sotto tutti questi percorsi viene aggiornato principalmente in AEM. Per promuovere la coerenza tra gli ambienti (locale, sviluppatore, stage, Prod) spesso nel controllo del codice sorgente viene salvata una struttura di contenuto di base.

1. **Passa al progetto AEM Screens > Esegui We.Retail:**

   Dal menu di avvio AEM > Fai clic su Screens sull&#39;icona. Verifica che il progetto di esecuzione We.Retail possa essere visualizzato.

   ![we-retaiul-run-starter](assets/we-retaiul-run-starter.png)

## Crea il componente &quot;Hello World&quot; {#hello-world-cmp}

Il componente Hello World è un componente semplice che consente all’utente di inserire un messaggio da visualizzare sullo schermo. Il componente si basa sul modello di componente [AEM Screens: https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

AEM Screens presenta alcuni vincoli interessanti che non sono necessariamente veri per i componenti WCM Sites tradizionali.

* La maggior parte dei componenti Screens deve essere eseguita a schermo intero sui dispositivi di digital signage di destinazione
* La maggior parte dei componenti Screens deve essere incorporabile nei canali della sequenza per generare slideshow
* L’authoring dovrebbe consentire la modifica di singoli componenti in un canale per sequenza, pertanto il rendering a schermo intero non è più una questione

1. In **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (o IDE selezionati) passa a `/apps/weretail-run/components/content/helloworld.`

   Aggiungi le seguenti proprietà al componente `helloworld` :

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![Proprietà per /apps/weretail-run/components/content/helloworld](assets/2018-04-28_at_4_23pm.png)

   Proprietà per /apps/weretail-run/components/content/helloworld

   Il componente **helloworld** estende il componente **foundation/components/parbase** in modo che possa essere utilizzato correttamente all&#39;interno di un canale per sequenza.

1. Crea un file sotto `/apps/weretail-run/components/content/helloworld` denominato `helloworld.html.`

   Compila il file con le seguenti caratteristiche:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   I componenti Screens richiedono due rendering diversi a seconda della modalità di authoring [che viene utilizzata:](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/author-environment-tools.html#PageModes)

   1. **Produzione**: Modalità Anteprima o Pubblicazione (wcmmode=disabled)
   1. **Modifica**: utilizzato per tutte le altre modalità di authoring, ad esempio modifica, progettazione, scaffolding, sviluppatore...

   `helloworld.html`funge da switch, controllando quale modalità di authoring è attualmente attiva e reindirizzando a un altro script HTL. Una convenzione comune utilizzata dai componenti screens consiste nell’avere uno script `edit.html` per la modalità Modifica e uno script `production.html` per la modalità Produzione.

1. Crea un file sotto `/apps/weretail-run/components/content/helloworld` denominato `production.html.`

   Compila il file con le seguenti caratteristiche:

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   Qui sopra è riportato il markup di produzione per il componente Hello World. È incluso un attributo `data-duration` poiché il componente viene utilizzato su un canale Sequenza. L&#39;attributo `data-duration` viene utilizzato dal canale della sequenza per sapere per quanto tempo deve essere visualizzato un elemento della sequenza.

   Il componente esegue il rendering di un tag `div` e di un tag `h1` con testo. `${properties.message}` è una parte dello script HTL che restituisce il contenuto di una proprietà JCR denominata  `message`. In seguito viene creata una finestra di dialogo che consente all’utente di immettere un valore per il testo della proprietà `message`.

   Inoltre, con il componente viene utilizzata la notazione BEM (modificatore elemento di blocco). BEM è una convenzione di codifica CSS che facilita la creazione di componenti riutilizzabili. BEM è la notazione utilizzata da [AEM Componenti core](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions). Maggiori informazioni sono disponibili all&#39;indirizzo: [https://getbem.com/](https://getbem.com/)

1. Crea un file sotto `/apps/weretail-run/components/content/helloworld` denominato `edit.html.`

   Compila il file con le seguenti caratteristiche:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   Sopra è riportata la marcatura per la modifica del componente Hello World. Il primo blocco visualizza una versione di modifica del componente se il messaggio di dialogo è stato compilato.

   Viene eseguito il rendering del secondo blocco se non è stato inserito alcun messaggio di dialogo. In tal caso, le `cq-placeholder` e `data-emptytext` eseguono il rendering dell&#39;etichetta ***Hello World*** come segnaposto. La stringa per l’etichetta può essere internazionalizzata utilizzando i18n per supportare l’authoring in più impostazioni internazionali.

1. **Copia schermata Finestra di dialogo immagine da utilizzare per il componente Hello World.**

   È più semplice iniziare da una finestra di dialogo esistente e quindi apportare modifiche.

   1. Copia la finestra di dialogo da: `/libs/screens/core/components/content/image/cq:dialog`
   1. Incolla la finestra di dialogo sotto `/apps/weretail-run/components/content/helloworld`

   ![copia-immagine-finestra di dialogo](assets/copy-image-dialog.gif)

1. **Aggiorna la finestra di dialogo Hello World per includere una scheda per il messaggio.**

   Aggiorna la finestra di dialogo in modo che corrisponda a quanto segue. La struttura del nodo JCR della finestra di dialogo finale è presentata di seguito in XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image will be shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   Il campo di testo per il messaggio verrà salvato in una proprietà denominata `message` e il campo numerico per la durata verrà salvato in una proprietà denominata `duration`. A entrambe queste proprietà viene fatto riferimento in `/apps/weretail-run/components/content/helloworld/production.html` da HTL come `${properties.message}` e `${properties.duration}`.

   ![Hello World - finestra di dialogo completata](assets/2018-04-29_at_5_21pm.png)

   Hello World - finestra di dialogo completata

## Creare librerie lato client {#clientlibs}

Le librerie lato client forniscono un meccanismo per organizzare e gestire i file CSS e JavaScript necessari per un’implementazione AEM.

Il rendering dei componenti AEM Screens avviene in modo diverso in modalità Modifica rispetto alla modalità Anteprima/Produzione. Verranno create due librerie client, una per la modalità Modifica e una per l’anteprima/produzione.

1. Crea una cartella per le librerie lato client per il componente Hello World.

   Sotto `/apps/weretail-run/components/content/helloworld`crea una nuova cartella denominata `clientlibs`.

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. Sotto la cartella `clientlibs` crea un nuovo nodo denominato `shared` di tipo `cq:ClientLibraryFolder.`

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. Aggiungi le seguenti proprietà alla libreria client condivisa:

   * `allowProxy` | Booleano | `true`

   * `categories`| Stringa[] |  `cq.screens.components`

   ![Proprietà per /apps/weretail-run/components/content/helloworld/clientlibs/shared](assets/2018-05-03_at_1026pm.png)

   Proprietà per /apps/weretail-run/components/content/helloworld/clientlibs/shared

   La proprietà categories è una stringa che identifica la libreria client. La categoria cq.screens.component viene utilizzata sia in modalità Modifica che in modalità Anteprima/Produzione. Pertanto, qualsiasi CSS/JS definito in sharedclientlib viene caricato in tutte le modalità.

   È consigliabile non esporre mai alcun percorso direttamente a /apps in un ambiente di produzione. La proprietà allowProxy assicura che la libreria client CSS e JS siano referenziati tramite un prefisso of/etc.clientlibs.

1. Crea un file denominato `css.txt` sotto la cartella condivisa.

   Compila il file con le seguenti caratteristiche:

   ```
   #base=css
   
   styles.less
   ```

1. Crea una cartella denominata `css` sotto la cartella `shared`. Aggiungi un file denominato `style.less` sotto la cartella `css` . La struttura delle librerie client dovrebbe ora essere simile alla seguente:

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   Invece di scrivere CSS direttamente, questa esercitazione utilizza LESS. [](https://lesscss.org/) LESSè un popolare precompilatore CSS che supporta variabili, mixin e funzioni CSS. AEM librerie client supportano in modo nativo la compilazione LESS. Sass o altri pre-compilatori possono essere utilizzati ma devono essere compilati al di fuori di AEM.

1. Popolare `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` con quanto segue:

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. Copia e incolla la cartella della libreria client `shared` per creare una nuova libreria client denominata `production`.

   ![Copia la libreria client condivisa per creare una nuova libreria client di produzione](assets/copy-clientlib.gif)

   Copia la libreria client condivisa per creare una nuova libreria client di produzione

1. Aggiorna la proprietà `categories` della libreria client di produzione in modo che sia `cq.screens.components.production.`

   In questo modo gli stili vengono caricati solo in modalità Anteprima/Produzione.

   ![Proprietà per /apps/weretail-run/components/content/helloworld/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Proprietà per /apps/weretail-run/components/content/helloworld/clientlibs/production

1. Popolare `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` con quanto segue:

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   Gli stili di cui sopra visualizzano il messaggio centrato al centro dello schermo, ma solo in modalità di produzione.

Una terza categoria di clientlibrary: `cq.screens.components.edit` può essere utilizzato per aggiungere al componente stili specifici per la modifica.

| Categoria clientlib | Utilizzo |
|---|---|
| `cq.screens.components` | Stili e script condivisi tra le modalità di modifica e di produzione |
| `cq.screens.components.edit` | Stili e script utilizzati solo in modalità di modifica |
| `cq.screens.components.production` | Stili e script utilizzati solo in modalità di produzione |

## Creare una pagina di progettazione {#design-page}

AEM Screens utilizza [modelli di pagina statici](https://helpx.adobe.com/it/experience-manager/6-5/sites/developing/using/page-templates-static.html) e [configurazioni di progettazione](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/default-components-designmode.html) per le modifiche globali. Le configurazioni di progettazione vengono spesso utilizzate per configurare i componenti consentiti per Parsys su un canale. Una best practice consiste nell’archiviare queste configurazioni in un modo specifico per l’app.

Di seguito viene creata una pagina di progettazione di esecuzione We.Retail che memorizzerà tutte le configurazioni specifiche per il progetto di esecuzione We.Retail.

1. In **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs` vai a `/apps/settings/wcm/designs`
1. Crea un nuovo nodo sotto la cartella delle progettazioni, denominato `we-retail-run` con un tipo di `cq:Page`.
1. Sotto la pagina `we-retail-run`, aggiungi un altro nodo denominato `jcr:content` di tipo `nt:unstructured`. Aggiungi le seguenti proprietà al nodo `jcr:content` :

   | Nome | Tipo | Valore |
   |---|---|---|
   | jcr:title | Stringa | Esecuzione We.Retail |
   | sling:resourceType | Stringa | wcm/core/components/designer |
   | cq:doctype | Stringa | html_5 |

   ![Pagina di progettazione in /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   Pagina di progettazione in /apps/settings/wcm/designs/we-retail-run

## Creare un canale per sequenza {#create-sequence-channel}

Il componente Hello World è destinato all’utilizzo su un canale per sequenza. Per testare il componente, viene creato un nuovo Canale per sequenza.

1. Dal menu di avvio AEM, passa a **Schermi** > **We.Retail Ru** n > e seleziona **Canali**.

1. Fai clic sul pulsante **Crea**

   1. Scegli **Crea entità**

   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. Nella procedura guidata Crea :

1. Passaggio modello: scegli **Canale sequenza**

   1. Passaggio Proprietà
   * Scheda di base > Titolo = **Canale inattivo**
   * Scheda Canale > controlla **Rendi il canale online**

   ![canale inattivo](assets/idle-channel.gif)

1. Apri le proprietà della pagina per il Canale inattivo. Aggiorna il campo Progettazione in modo che punti a `/apps/settings/wcm/designs/we-retail-run,`la pagina di progettazione creata nella sezione precedente.

   ![Configurazione di progettazione /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   Configurazione di progettazione che punta a /apps/settings/wcm/designs/we-retail-run

1. Modifica il Canale inattivo appena creato per aprirlo.

1. Passa alla modalità pagina in modalità **Progettazione**

   1. Fai clic sull&#39;icona **chiave inglese** in Parsys per configurare i componenti consentiti

   1. Seleziona il gruppo **Screens** e il gruppo **We.Retail Run - Content** .

   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. Passa alla modalità pagina su **Modifica**. È ora possibile aggiungere alla pagina il componente Ciao mondo e combinarlo con altri componenti del canale per sequenza.

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. In **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par` passa a `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`. Nota che la proprietà `components` ora include `group:Screens`, `group:We.Retail Run - Content`.

   ![Configurazione della progettazione in /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1_14pm.png)

   Configurazione della progettazione in /apps/settings/wcm/designs/we-retail-run

## Modello per gestori personalizzati {#custom-handlers}

Nel caso in cui il componente personalizzato utilizzi risorse esterne come risorse (immagini, video, font, icone, ecc.), rappresentazioni di risorse specifiche o librerie lato client (css, js, ecc.), queste non vengono aggiunte automaticamente alla configurazione offline in quanto aggreghiamo solo il markup HTML per impostazione predefinita.

Per personalizzare e ottimizzare le risorse esatte scaricate sul lettore, offriamo un meccanismo di estensione per i componenti personalizzati per esporre le loro dipendenze alla logica di caching offline in Screens.

La sezione seguente illustra il modello per i gestori di risorse offline personalizzati e i requisiti minimi in `pom.xml` per quel progetto specifico.

```java
package …;

import javax.annotation.Nonnull;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceUtil;
import org.apache.sling.api.resource.ValueMap;

import com.adobe.cq.screens.visitor.OfflineResourceHandler;

@Service(value = OfflineResourceHandler.class)
@Component(immediate = true)
public class MyCustomHandler extends AbstractResourceHandler {

 @Reference
 private …; // OSGi services injection

 /**
  * The resource types that are handled by the handler.
  * @return the handled resource types
  */
 @Nonnull
 @Override
 public String[] getSupportedResourceTypes() {
     return new String[] { … };
 }

 /**
  * Accept the provided resource, visit and traverse it as needed.
  * @param resource The resource to accept
  */
 @Override
 public void accept(@Nonnull Resource resource) {
     ValueMap properties = ResourceUtil.getValueMap(resource);
     
     /* You can directly add explicit paths for offline caching using the `visit`
        method of the visitor. */
     
     // retrieve a custom property from the component
     String myCustomRenditionUrl = properties.get("myCustomRenditionUrl", String.class);
     // adding that exact asset/rendition/path to the offline manifest
     this.visitor.visit(myCustomRenditionUrl);
     
     
     /* You can delegate handling for dependent resources so they are also added to
        the offline cache using the `accept` method of the visitor. */
     
     // retrieve a referenced dependent resource
     String referencedResourcePath = properties.get("myOtherResource", String.class);
     ResourceResolver resolver = resource.getResourceResolver();
     Resource referencedResource = resolver.getResource(referencedResourcePath);
     // let the handler for that resource handle it
     if (referencedResource != null) {
         this.visitor.accept(referencedResource);
     }
   }
}
```

Il codice seguente fornisce i requisiti minimi in `pom.xml` per quel progetto specifico:

```css
   <dependencies>
        …
        <!-- Felix annotations -->
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.9.0</version>
            <scope>provided</scope>
        </dependency>

        <!-- Screens core bundle with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.cq.screens</groupId>
            <artifactId>com.adobe.cq.screens</artifactId>
            <version>1.5.90</version>
            <scope>provided</scope>
        </dependency>
        …
      </dependencies>
```

## Mettere tutto insieme {#putting-it-all-together}

Il video seguente mostra il componente finito e come può essere aggiunto a un canale Sequenza. Il canale viene quindi aggiunto a una visualizzazione Posizione e infine assegnato a un lettore Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## Codice finito {#finished-code}

Di seguito è riportato il codice finito dell&#39;esercitazione. I **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** e **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** sono i pacchetti AEM compilati. Il **SRC-screens-weretail-run-0.0.1.zip **è il codice sorgente non compilato che può essere distribuito utilizzando Maven.

[Ottieni file](assets/screens-weretail-runuiapps-001-snapshot.zip)

[Ottieni file](assets/screens-weretail-runuicontent-001-snapshot.zip)

[Ottieni file](assets/screens-weretail-run.zip)
