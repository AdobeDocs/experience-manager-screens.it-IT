---
title: 'Estensione di un componente AEM Screens '
seo-title: 'Estensione di un componente AEM Screens '
description: L'esercitazione seguente illustra i passaggi e le procedure ottimali per l'estensione dei componenti  AEM Screens. Il componente Immagine viene esteso per aggiungere una sovrapposizione di testo modificabile.
seo-description: L'esercitazione seguente illustra i passaggi e le procedure ottimali per l'estensione dei componenti  AEM Screens. Il componente Immagine viene esteso per aggiungere una sovrapposizione di testo modificabile.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ec8324ead3789a6cd5dde35a932c89e916709f70
workflow-type: tm+mt
source-wordcount: '1852'
ht-degree: 0%

---


# Estensione di un componente AEM Screens  {#extending-an-aem-screens-component}

L&#39;esercitazione seguente illustra i passaggi e le procedure ottimali per l&#39;estensione dei componenti  AEM Screens. Il componente Immagine viene esteso per aggiungere una sovrapposizione di testo modificabile.

## Panoramica {#overview}

Questa esercitazione è destinata agli sviluppatori che hanno familiarità con  AEM Screens. In questa esercitazione, il componente Immagine schermate viene esteso per creare un componente Poster. Titolo, descrizione e logo sono sovrapposti a un’immagine per creare un’esperienza coinvolgente in un canale di sequenza.

>[!NOTE]
>
>Prima di avviare questa esercitazione, è consigliabile completare l&#39;esercitazione: [Sviluppo di un componente personalizzato per  AEM Screens](developing-custom-component-tutorial-develop.md).

![Personalizzato, componente Poster](assets/2018-05-07_at_4_09pm.png)

Il componente Poster personalizzato viene creato estendendo il componente Immagine.

## Prerequisiti {#prerequisites}

Per completare questa esercitazione, è necessario effettuare le seguenti operazioni:

1. [AEM 6.4 ](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/release-notes.html) o  [AEM 6.3](https://helpx.adobe.com/it/experience-manager/6-3/release-notes.html) + Ultimi pacchetti di funzioni per schermi
1. [Lettore AEM Screens](/help/user-guide/aem-screens-introduction.md)
1. Ambiente di sviluppo locale

I passaggi dell&#39;esercitazione e le schermate vengono eseguiti utilizzando CRXDE-Lite. [Per completare l&#39;esercitazione è inoltre possibile utilizzare ](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) Eclipseor  [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) IntelliJIDE. Ulteriori informazioni sull&#39;utilizzo di un IDE per [sviluppare con AEM sono disponibili qui](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide).

## Configurazione del progetto {#project-setup}

Il codice sorgente di un progetto Screens viene generalmente gestito come progetto Maven multi-modulo. Per accelerare l&#39;esercitazione, un progetto è stato pre-generato utilizzando il [AEM Project Archetype 13](https://github.com/adobe/aem-project-archetype). Maggiori dettagli sulla [creazione di un progetto con Maven AEM Project Archetype sono disponibili qui](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule).

1. Scaricare e installare i pacchetti seguenti utilizzando **CRX package manage** `http://localhost:4502/crx/packmgr/index.jsp)r:`

   [Ottieni file](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Ottieni file](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Facoltativamente,** se lavorate con Eclipse o un altro IDE, scaricate il pacchetto sorgente riportato di seguito. Distribuite il progetto in un&#39;istanza AEM locale utilizzando il comando Paradiso:

   **`mvn -PautoInstallPackage clean install`**

   SRC Start Screens We.Retail Run Project

   [Ottieni file](assets/start-poster-screens-weretail-run.zip)

1. In **CRX Package Manager** `http://localhost:4502/crx/packmgr/index.jsp` sono installati i due pacchetti seguenti:

   1. **screens-weretail-run.ui.co-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Schermi I.Retail Run I pacchetti Ui.Apps e Ui.Content installati tramite CRX Package Manager](assets/crx-packages.png)

   Schermi I.Retail Run I pacchetti Ui.Apps e Ui.Content installati tramite CRX Package Manager

## Creare il componente Poster {#poster-cmp}

Il componente Poster estende il componente Immagine fuori dalla casella. Un meccanismo Sling, `sling:resourceSuperType`, viene utilizzato per ereditare le funzionalità core del componente Immagine senza dover copiare e incollare. Ulteriori informazioni sulle nozioni di base di [Sling Request Processing (Elaborazione delle richieste Sling) sono disponibili qui.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

Il componente Poster viene riprodotto a schermo intero in modalità di anteprima/produzione. In modalità di modifica, è importante eseguire il rendering del componente in modo diverso per facilitare l’authoring del canale della sequenza.

1. In **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (o IDE di scelta) sotto a `/apps/weretail-run/components/content`creare un nuovo `cq:Component` denominato `poster`.

   Aggiungete le seguenti proprietà al componente `poster`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![Proprietà per /apps/weretail-run/components/content/poster](assets/poster.png)

   Proprietà per /apps/weretail-run/components/content/poster

   Impostando la proprietà `sling:resourceSuperType`uguale a `screens/core/components/content/image`, il componente Poster eredita tutte le funzionalità del componente Immagine. I nodi e i file equivalenti trovati sotto `screens/core/components/content/image` possono essere aggiunti sotto il componente `poster` per sovrascrivere e ampliare la funzionalità.

1. Copiare il nodo `cq:editConfig` sotto `/libs/screens/core/components/content/image.`Incollare il `cq:editConfig` sotto il componente `/apps/weretail-run/components/content/poster`.

   Sul nodo `cq:editConfig/cq:dropTargets/image/parameters` aggiornare la proprietà `sling:resourceType` in modo che sia uguale a `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   Rappresentazione XML di cq:editConfig rappresentata di seguito:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. Copiare la finestra di dialogo WCM Foundation `image` da utilizzare per il componente `poster`.

   È più semplice iniziare da una finestra di dialogo esistente e apportare quindi modifiche.

   1. Copiate la finestra di dialogo da: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Incolla la finestra di dialogo sotto `/apps/weretail-run/components/content/poster`

   ![Finestra di dialogo copiata da /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   Finestra di dialogo copiata da /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster

   Il componente Screens `image` è sovrapposto al componente WCM Foundation `image`. Di conseguenza, il componente `poster` eredita le funzionalità da entrambi. La finestra di dialogo per il componente poster è composta da una combinazione di finestre di dialogo e fondazioni. Le funzioni di **Sling Resource Merger** vengono utilizzate per nascondere i campi e le schede di dialogo irrilevanti ereditati dai componenti superati.

1. Aggiornate la finestra di dialogo cq:dialog sotto `/apps/weretail-run/components/content/poster` con le seguenti modifiche rappresentate in XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   La proprietà `sling:hideChildren`= `"[linkURL,size]`&quot; viene utilizzata sul nodo `items` per garantire che i campi **linkURL** e **size** siano nascosti dalla finestra di dialogo. La rimozione di questi nodi dalla finestra di dialogo poster non è sufficiente. La proprietà `sling:hideResource="{Boolean}true"` nella scheda di accessibilità viene utilizzata per nascondere l&#39;intera scheda.

   Due campi selezionati vengono aggiunti alla finestra di dialogo per consentire agli autori di controllare la posizione del testo e il colore del titolo e della descrizione.

   ![Poster - Struttura finestra di dialogo finale](assets/2018-05-03_at_4_49pm.png)

   Poster - Struttura finestra di dialogo finale

   A questo punto è possibile aggiungere un&#39;istanza del componente `poster` alla pagina **Canale inattivo** nel progetto We.Retail Run: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Campi finestra di dialogo miniatura](assets/poster-dialog-full.png)

   Campi finestra di dialogo miniatura

1. Creare un file sotto `/apps/weretail-run/components/content/poster` denominato `production.html.`

   Compilate il file con le seguenti opzioni:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   Sopra è riportata la marcatura di produzione per il componente Poster. Lo script HTL ha la priorità su `screens/core/components/content/image/production.html`. `image.js` è uno script sul lato server che crea un oggetto Immagine simile a POJO. L&#39;oggetto Image può quindi essere chiamato per eseguire il rendering di `src` come immagine di sfondo in linea.

   `The h1` e i tag h2 aggiunti visualizzano il Titolo e la Descrizione in base alle proprietà del componente:  `${properties.jcr:title}` e  `${properties.jcr:description}`.

   La posizione intorno ai tag `h1` e `h2` è un wrapper div con tre classi CSS con varianti di &quot; `cmp-poster__text`&quot;. Il valore delle proprietà `textPosition` e `textColor` viene utilizzato per modificare la classe CSS rappresentata in base alla selezione di dialogo dell&#39;autore. Nella sezione successiva vengono scritti CSS dalle librerie client per attivare la visualizzazione di tali modifiche.

   Un logo è incluso anche come sovrapposizione nel componente. In questo esempio, il percorso del logo We.Retail è codificato in DAM. A seconda del caso d’uso potrebbe essere più utile creare un nuovo campo di dialogo per rendere il percorso del logo un valore popolato in modo dinamico.

   Inoltre, con il componente viene utilizzata la notazione BEM (Modificatore elemento blocco). BEM è una convenzione di codifica CSS che semplifica la creazione di componenti riutilizzabili. BEM è la notazione utilizzata da [AEM componenti core](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions). Maggiori informazioni sono disponibili all&#39;indirizzo: [https://getbem.com/](https://getbem.com/)

1. Creare un file sotto `/apps/weretail-run/components/content/poster` denominato `edit.html.`

   Compilate il file con le seguenti opzioni:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   Sopra è riportata la marcatura **edit** per il componente Poster. Lo script HTL ha la priorità su `/libs/screens/core/components/content/image/edit.html`. La marcatura è simile alla marcatura `production.html` e visualizza il titolo e la descrizione sopra l&#39;immagine.

   Viene aggiunto `aem-Screens-editWrapper`in modo che il componente non esegua il rendering a schermo intero nell&#39;editor. L&#39;attributo `data-emptytext` assicura che venga visualizzato un segnaposto quando non è stata compilata alcuna immagine o contenuto.

## Creare librerie lato client {#clientlibs}

Le librerie lato client forniscono un meccanismo per organizzare e gestire i file CSS e JavaScript necessari per un&#39;implementazione AEM. Ulteriori informazioni sull&#39;utilizzo delle [librerie lato client sono disponibili qui.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

 i componenti AEM Screens vengono sottoposti a rendering in modo diverso in modalità Modifica rispetto alla modalità Anteprima/Produzione. Vengono creati due set di librerie client, uno per la modalità di modifica e uno per l’anteprima/produzione.

1. Creare una cartella per le librerie lato client per il componente Poster.

   Sotto `/apps/weretail-run/components/content/poster,`creare una nuova cartella denominata `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Sotto la cartella `clientlibs` create un nuovo nodo denominato `shared` di tipo `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. Aggiungete le seguenti proprietà alla libreria client condivisa:

   * `allowProxy` | Booleano | `true`
   * `categories` | Stringa[] |  `cq.screens.components`

   ![Proprietà per /apps/weretail-run/components/content/poster/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Proprietà per /apps/weretail-run/components/content/poster/clientlibs/shared

   La proprietà `categories` è una stringa che identifica la libreria client. La categoria `cq.screens.components` viene utilizzata sia in modalità Modifica che in modalità Anteprima/Produzione. Pertanto, qualsiasi CSS/JS definito nella clientlib `shared` viene caricato in tutte le modalità.

   È consigliabile non esporre mai alcun percorso direttamente alle /app in un ambiente di produzione. La proprietà `allowProxy` garantisce che la libreria client faccia riferimento a CSS e JS tramite un prefisso `/etc.clientlibs`. Ulteriori informazioni sulla proprietà [allowProxy sono disponibili qui.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. Create un file denominato `css.txt` sotto la cartella condivisa.

   Compilate il file con le seguenti opzioni:

   ```
   #base=css
   
   styles.less
   ```

1. Create una cartella denominata `css` sotto la cartella `shared`. Aggiungete un file denominato `style.less` sotto la cartella `css`. La struttura delle librerie client deve ora essere simile alla seguente:

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   Invece di scrivere CSS direttamente, questa esercitazione utilizza LESS. [](https://lesscss.org/) LESS è un popolare precompilatore CSS che supporta variabili, mixin e funzioni CSS. AEM librerie client supportano in modo nativo la compilazione LESS. Sass o altri precompilatori possono essere utilizzati ma devono essere compilati al di fuori di AEM.

1. Compilare `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` con i seguenti elementi:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >I font Web Google vengono utilizzati per le famiglie di font. I font Web richiedono la connettività Internet e non tutte le implementazioni delle schermate avranno una connessione affidabile. La pianificazione della modalità offline è un aspetto importante per le distribuzioni di schermi.

1. Copiate la cartella della libreria client `shared`. Incollatela come elemento di pari livello e rinominatela in `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. Aggiornare la proprietà `categories` della clientlibrary di produzione affinché sia `cq.screens.components.production.`

   La categoria `cq.screens.components.production` garantisce che gli stili vengano caricati solo in modalità Anteprima/Produzione.

   ![Proprietà per /apps/weretail-run/components/content/poster/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Proprietà per /apps/weretail-run/components/content/poster/clientlibs/production

1. Compilare `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` con i seguenti elementi:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   Gli stili di cui sopra mostrano il Titolo e la Descrizione in posizione assoluta sullo schermo. Il titolo verrà visualizzato in modo molto più grande della descrizione. La notazione BEM del componente semplifica notevolmente l’ambito degli stili all’interno della classe cmp-poster.

Una terza categoria di clientlibrary: È possibile utilizzare `cq.screens.components.edit` per aggiungere al componente solo stili specifici di Edit.

| Categoria Clientlib | Utilizzo |
|---|---|
| `cq.screens.components` | Stili e script condivisi tra modalità di modifica e produzione |
| `cq.screens.components.edit` | Stili e script utilizzati solo in modalità di modifica |
| `cq.screens.components.production` | Stili e script utilizzati solo in modalità di produzione |

## Aggiungi componente poster a un canale di sequenza {#add-sequence-channel}

Il componente Poster deve essere utilizzato su un canale sequenza. Il pacchetto di avvio per questa esercitazione includeva un canale inattivo. Il canale inattivo è preconfigurato per consentire ai componenti del gruppo **We.Retail Run - Content**. Il gruppo del componente Poster è impostato su `We.Retail Run - Content` ed è disponibile per l&#39;aggiunta al canale.

1. Aprite il canale inattivo dal progetto We.Retail Run: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Trascinare + rilasciare una nuova istanza del componente **Poster** dalla barra laterale alla pagina.

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. Modificate la finestra di dialogo del componente Poster per aggiungere un’immagine, un titolo e una descrizione. Usate le opzioni Posizione testo e Colore testo per garantire che Titolo/Descrizione sia leggibile sull’immagine.

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. Ripetete i passaggi indicati sopra per aggiungere alcuni componenti Poster. Aggiungere transizioni tra i componenti.

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## Mettere tutto insieme {#putting-it-all-together}

Il video seguente mostra il componente finito e come può essere aggiunto a un canale Sequenza. Il canale viene quindi aggiunto alla visualizzazione Posizione e, in ultima istanza, assegnato a un lettore Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## Codice finito {#finished-code}

Di seguito è riportato il codice finale dell&#39;esercitazione. I **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** e **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** sono i pacchetti AEM compilati. Il **SRC-screens-weretail-run-0.0.1.zip **è il codice sorgente non compilato che può essere distribuito con Maven.

[Ottieni file](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Ottieni file](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final Screens We.Retail Run Project

[Ottieni file](assets/src-screens-weretail-run-001.zip)
