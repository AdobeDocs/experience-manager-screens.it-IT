---
title: Estensione di un componente AEM Screens
seo-title: Extending an AEM Screens Component
description: L’esercitazione seguente illustra i passaggi e le best practice per l’estensione dei componenti predefiniti di AEM Screens. Il componente Immagine viene esteso per aggiungere una sovrapposizione di testo modificabile.
seo-description: The following tutorial walks through the steps and best practices for extending out of the box AEM Screens components. The Image component is extended to add an authorable text overlay.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: e316614f-2d40-4b62-a1e5-f30817def742
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1786'
ht-degree: 2%

---

# Estensione di un componente AEM Screens {#extending-an-aem-screens-component}

L’esercitazione seguente illustra i passaggi e le best practice per l’estensione dei componenti predefiniti di AEM Screens. Il componente Immagine viene esteso per aggiungere una sovrapposizione di testo modificabile.

## Panoramica {#overview}

Questa esercitazione è destinata agli sviluppatori che hanno poca esperienza con AEM Screens. In questa esercitazione, il componente Immagine Screens viene esteso per creare un componente Poster. Titolo, descrizione e logo vengono sovrapposti su un’immagine per creare un’esperienza coinvolgente in un Canale per sequenza.

>[!NOTE]
>
>Prima di avviare questa esercitazione, è consigliabile completare l&#39;esercitazione: [Sviluppo di un componente personalizzato per AEM Screens](developing-custom-component-tutorial-develop.md).

![Componente Poster personalizzato](assets/2018-05-07_at_4_09pm.png)

Il componente Poster personalizzato viene creato estendendo il componente Immagine .

## Prerequisiti {#prerequisites}

Per completare questa esercitazione, è necessario quanto segue:

1. [AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/release-notes.html?lang=it) o [AEM 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=it) + Feature Pack degli schermi più recenti
1. [Lettore AEM Screens](/help/user-guide/aem-screens-introduction.md)
1. Ambiente di sviluppo locale

I passaggi del tutorial e le schermate vengono eseguiti utilizzando CRXDE-Lite. [Eclipse](https://experienceleague.adobe.com/docs/experience-manager-64/developing/devtools/aem-eclipse.html) o [IntelliJ](https://experienceleague.adobe.com/docs/experience-manager-64/developing/devtools/ht-intellij.html) Gli IDE possono anche essere utilizzati per completare l’esercitazione. Ulteriori informazioni sull’utilizzo di un IDE per [sviluppare con AEM si trova qui](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

## Configurazione del progetto {#project-setup}

Il codice sorgente di un progetto Screens viene generalmente gestito come progetto Maven con più moduli. Per accelerare l’esercitazione, è stato pregenerato un progetto utilizzando [Archetipo di progetto AEM 13](https://github.com/adobe/aem-project-archetype). Maggiori dettagli su [la creazione di un progetto con Maven AEM Project Archetype si trova qui](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

1. Scarica e installa i seguenti pacchetti utilizzando **Gestione pacchetti CRX** `http://localhost:4502/crx/packmgr/index.jsp)r:`

[Ottieni file](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Ottieni file](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Facoltativamente,** se lavori con Eclipse o un altro IDE, scarica il pacchetto sorgente seguente. Distribuisci il progetto in un’istanza AEM locale utilizzando il comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Progetto di esecuzione We.Retail di SRC Start Screens

[Ottieni file](assets/start-poster-screens-weretail-run.zip)

1. In **Gestione pacchetti CRX** `http://localhost:4502/crx/packmgr/index.jsp` sono installati i due pacchetti seguenti:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Schermi I.Retail Esegui pacchetti Ui.Apps e Ui.Content installati tramite CRX Package Manager](assets/crx-packages.png)

   Schermi I.Retail Esegui pacchetti Ui.Apps e Ui.Content installati tramite CRX Package Manager

## Creare il componente Poster {#poster-cmp}

Il componente Poster estende il componente Immagine della schermata predefinita. Meccanismo di Sling, `sling:resourceSuperType`, viene utilizzato per ereditare le funzionalità di base del componente Immagine senza dover copiare e incollare. Ulteriori informazioni sulle nozioni di base di [Sling Request Processing si trova qui.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/the-basics.html?lang=it)

Il componente Poster viene riprodotto a schermo intero in modalità anteprima/produzione. In modalità di modifica, è importante eseguire il rendering del componente in modo diverso per facilitare l’authoring del canale per sequenza.

1. In **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (o IDE di scelta) sotto a `/apps/weretail-run/components/content`creare un `cq:Component` denominato `poster`.

   Aggiungi le seguenti proprietà al `poster` componente:

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

   Impostando `sling:resourceSuperType`proprietà uguale a `screens/core/components/content/image` il componente Poster eredita efficacemente tutte le funzionalità del componente Immagine . Nodi e file equivalenti trovati sotto `screens/core/components/content/image` può essere aggiunto sotto la `poster` per sovrascrivere ed estendere la funzionalità .

1. Copia il `cq:editConfig` nodo sotto `/libs/screens/core/components/content/image.`Incolla `cq:editConfig` sotto il `/apps/weretail-run/components/content/poster` componente.

   Sulla `cq:editConfig/cq:dropTargets/image/parameters` aggiorna il nodo `sling:resourceType` proprietà uguale `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   La rappresentazione XML della cq:editConfig rappresentata di seguito:

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

1. Copia di WCM Foundation `image` della finestra di dialogo `poster` componente.

   È più semplice iniziare da una finestra di dialogo esistente e quindi apportare modifiche.

   1. Copia la finestra di dialogo da: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Incolla la finestra di dialogo sottostante `/apps/weretail-run/components/content/poster`

   ![Finestra di dialogo copiata da /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   Finestra di dialogo copiata da /libs/wcm/foundation/components/image/cq:dialog a /apps/weretail-run/components/content/poster

   Schermi `image` il componente è sostituito da WCM Foundation `image` componente. Pertanto, `poster` il componente eredita funzionalità da entrambi. La finestra di dialogo per il componente poster è composta da una combinazione delle finestre di dialogo Screens e Foundation. Funzioni del **Sling Resource Merger** vengono utilizzati per nascondere i campi e le schede di dialogo non rilevanti ereditati dai componenti superati.

1. Aggiorna cq:dialog sotto `/apps/weretail-run/components/content/poster` con le seguenti modifiche rappresentate in XML:

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

   La proprietà `sling:hideChildren`= `"[linkURL,size]`&quot; viene utilizzato nella `items` per garantire che **linkURL** e **size** i campi sono nascosti dalla finestra di dialogo. La rimozione di questi nodi dalla finestra di dialogo poster non è sufficiente. La proprietà `sling:hideResource="{Boolean}true"` nella scheda accessibilità viene utilizzata per nascondere l’intera scheda .

   Nella finestra di dialogo vengono aggiunti due campi di selezione per consentire agli autori di controllare la posizione del testo e il colore del titolo e della descrizione.

   ![Poster - Struttura della finestra di dialogo finale](assets/2018-05-03_at_4_49pm.png)

   Poster - Struttura della finestra di dialogo finale

   A questo punto, un&#39;istanza del `poster` può essere aggiunto al **Canale inattivo** nel progetto di esecuzione We.Retail: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Campi della finestra di dialogo miniatura](assets/poster-dialog-full.png)

   Campi della finestra di dialogo miniatura

1. Crea un file sotto `/apps/weretail-run/components/content/poster` denominato `production.html.`

   Compila il file con le seguenti caratteristiche:

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

   Sopra è riportato il markup di produzione per il componente Poster. Ignorare lo script HTL `screens/core/components/content/image/production.html`. La `image.js` è uno script lato server che crea un oggetto immagine simile a POJO. L’oggetto Immagine può quindi essere chiamato per eseguire il rendering del `src` come immagine di sfondo in linea.

   `The h1` e i tag h2 aggiunti visualizzano Titolo e Descrizione in base alle proprietà del componente: `${properties.jcr:title}` e `${properties.jcr:description}`.

   Circondato `h1` e `h2` tags è un wrapper div con tre classi CSS con varianti di &quot; `cmp-poster__text`&quot;. Il valore per `textPosition` e `textColor` Le proprietà vengono utilizzate per modificare la classe CSS di cui è stato eseguito il rendering in base alla selezione della finestra di dialogo dell&#39;autore. Nella sezione successiva vengono scritti CSS dalle librerie client per abilitare queste modifiche nella visualizzazione.

   Nel componente è incluso anche un logo come sovrapposizione. In questo esempio, il percorso del logo We.Retail è codificato in modo rigido nel DAM. A seconda del caso d’uso, potrebbe essere più sensato creare un campo di dialogo per rendere il percorso del logo un valore popolato in modo dinamico.

   Inoltre, con il componente viene utilizzata la notazione BEM (modificatore elemento di blocco). BEM è una convenzione di codifica CSS che facilita la creazione di componenti riutilizzabili. BEM è la notazione utilizzata da [Componenti core AEM](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. Crea un file sotto `/apps/weretail-run/components/content/poster` denominato `edit.html.`

   Compila il file con le seguenti caratteristiche:

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

   Sopra è **modifica** Marcatura per il componente Poster. Ignorare lo script HTL `/libs/screens/core/components/content/image/edit.html`. Il markup è simile al `production.html` visualizza il titolo e la descrizione sopra l’immagine.

   La `aem-Screens-editWrapper`viene aggiunto in modo che nell’editor non venga eseguito il rendering del componente a schermo intero. La `data-emptytext` assicura che venga visualizzato un segnaposto quando non è stata compilata alcuna immagine o contenuto.

## Creare librerie lato client {#clientlibs}

Le librerie lato client forniscono un meccanismo per organizzare e gestire i file CSS e JavaScript necessari per un’implementazione AEM. Ulteriori informazioni sull&#39;utilizzo [Le librerie lato client si trovano qui.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

I componenti di AEM Screens vengono riprodotti in modo diverso in modalità Modifica rispetto alla modalità Anteprima/Produzione. Vengono creati due set di librerie client, uno per la modalità Modifica e uno per l’anteprima/produzione.

1. Crea una cartella per le librerie lato client per il componente Poster.

   Sotto `/apps/weretail-run/components/content/poster,`creare una cartella denominata `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. Sotto `clientlibs` creare una cartella denominata `shared` di tipo `cq:ClientLibraryFolder.`

   ![05/05/2018](assets/2018-05-03_at_1011pm.png)

1. Aggiungi le seguenti proprietà alla libreria client condivisa:

   * `allowProxy` | Booleano | `true`
   * `categories` | Stringa[] | `cq.screens.components`

   ![Proprietà per /apps/weretail-run/components/content/poster/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Proprietà per /apps/weretail-run/components/content/poster/clientlibs/shared

   La `categories` è una stringa che identifica la libreria client. La `cq.screens.components` Questa categoria viene utilizzata sia in modalità Modifica che in modalità Anteprima/Produzione. Pertanto, qualsiasi CSS/JS definito nel `shared` clientlib viene caricato in tutte le modalità.

   È consigliabile non esporre mai alcun percorso direttamente a /apps in un ambiente di produzione. La `allowProxy` assicura che la libreria client faccia riferimento a CSS e JS tramite un prefisso `/etc.clientlibs`. Ulteriori informazioni sulle [La proprietà allowProxy si trova qui.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

1. Crea file con nome `css.txt` sotto la cartella condivisa.

   Compila il file con le seguenti caratteristiche:

   ```
   #base=css
   
   styles.less
   ```

1. Crea una cartella denominata `css` sotto il `shared` cartella. Aggiungi un file denominato `style.less` sotto il `css` cartella. La struttura delle librerie client dovrebbe ora essere simile alla seguente:

   ![05/05/2018](assets/2018-05-03_at_1057pm.png)

   Invece di scrivere CSS direttamente, questa esercitazione utilizza LESS. [MENO](https://lesscss.org/) è un precompilatore CSS popolare che supporta variabili CSS, mixin e funzioni. AEM librerie client supportano in modo nativo la compilazione LESS. Sass o altri precompilatori possono essere utilizzati ma devono essere compilati al di fuori di AEM.

1. Popolare `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` con le seguenti caratteristiche:

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
   >I Web Fonts Google vengono utilizzati per le famiglie di font. I Web Fonts richiedono la connettività Internet e non tutte le implementazioni di schermi offrono una connessione affidabile. La pianificazione della modalità offline è un aspetto importante per le distribuzioni di Screens.

1. Copia il `shared` cartella della libreria client. Incollalo come elemento di pari livello e rinominalo in `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. Aggiorna `categories` proprietà della libreria client di produzione da `cq.screens.components.production.`

   La `cq.screens.components.production` Questa categoria assicura che gli stili vengano caricati solo in modalità Anteprima/Produzione.

   ![Proprietà per /apps/weretail-run/components/content/poster/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Proprietà per /apps/weretail-run/components/content/poster/clientlibs/production

1. Popolare `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` con le seguenti caratteristiche:

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

   Gli stili di cui sopra presentano il Titolo e la Descrizione in posizione assoluta sullo schermo. Il titolo viene visualizzato più grande della descrizione. La notazione BEM del componente semplifica l&#39;ambito degli stili all&#39;interno della classe cmp-poster.

Una terza categoria di clientlibrary: `cq.screens.components.edit` può essere utilizzato per aggiungere al componente Modifica solo stili specifici.

| Categoria clientlib | Utilizzo |
|---|---|
| `cq.screens.components` | Stili e script condivisi tra le modalità di modifica e di produzione |
| `cq.screens.components.edit` | Stili e script utilizzati solo in modalità di modifica |
| `cq.screens.components.production` | Stili e script utilizzati solo in modalità di produzione |

## Aggiungere un componente Poster a un canale per sequenza {#add-sequence-channel}

Il componente Poster viene utilizzato su un canale per sequenza. Il pacchetto iniziale per questa esercitazione includeva un canale inattivo. Il canale inattivo è preconfigurato per consentire i componenti del gruppo **Esecuzione We.Retail - Contenuto**. Il gruppo del componente Poster è impostato su `We.Retail Run - Content` ed è disponibile per essere aggiunto al canale.

1. Apri il Canale inattivo dal progetto We.Retail Run: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Trascina + rilascia una nuova istanza del **Miniatura** dalla barra laterale alla pagina.

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. Modifica la finestra di dialogo del componente Poster per aggiungere un’immagine, un titolo, una descrizione. Utilizza le scelte Posizione testo e Colore testo per garantire che il Titolo/Descrizione sia leggibile sull’immagine.

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. Ripeti i passaggi precedenti per aggiungere alcuni componenti Poster. Aggiungi transizioni tra i componenti.

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## Tutti gli elementi insieme {#putting-it-all-together}

Il video seguente mostra il componente finito e come può essere aggiunto a un canale Sequenza. Il canale viene quindi aggiunto a una visualizzazione Posizione e infine assegnato a un lettore Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## Codice finito {#finished-code}

Di seguito è riportato il codice finito dell&#39;esercitazione. La **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** e **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** sono i pacchetti compilati AEM. Il **SRC-screens-weretail-run-0.0.1.zip **è il codice sorgente non compilato che può essere distribuito utilizzando Maven.

[Ottieni file](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Ottieni file](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

Progetto di esecuzione We.Retail di SRC Screens finali

[Ottieni file](assets/src-screens-weretail-run-001.zip)
