---
title: Sviluppo di un componente personalizzato per AEM Screens
description: Scopri come creare un componente personalizzato per AEM Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: d14f8c55-dc09-4ac9-8d75-bafffa82ccc0
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 1%

---

# Sviluppo di un componente personalizzato per AEM Screens {#developing-a-custom-component-for-aem-screens}

Il seguente tutorial illustra i passaggi necessari per creare un componente personalizzato per AEM Screens. AEM Screens riutilizza molti modelli di progettazione e tecnologie esistenti di altri prodotti AEM. Il tutorial evidenzia differenze e considerazioni speciali durante lo sviluppo per AEM Screens.

## Panoramica {#overview}

Questo tutorial è destinato agli sviluppatori che hanno poca esperienza con AEM Screens. In questo tutorial, viene creato un semplice componente &quot;Hello World&quot; per un canale Sequence in AEM Screens. Una finestra di dialogo consente agli autori di aggiornare il testo visualizzato.

![overviewhellow](assets/overviewhellow.png)

## Prerequisiti {#prerequisites}

Per completare questa esercitazione, è necessario quanto segue:

1. [AEM 6.5](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/release-notes/release-notes) e il pacchetto con le funzioni più recenti di Screens.

1. [Lettore AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction)
1. Ambiente di sviluppo locale

I passaggi del tutorial e le schermate vengono eseguiti utilizzando **CRXDE-Lite**. È inoltre possibile utilizzare gli IDE per completare l&#39;esercitazione. Ulteriori informazioni sull&#39;utilizzo di un IDE per sviluppare [con AEM si trova qui.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)


## Configurazione del progetto {#project-setup}

Il codice sorgente di un progetto Screens viene in genere gestito come progetto Maven con più moduli. Per accelerare l’esercitazione, un progetto è stato pregenerato utilizzando [Archetipo progetto AEM 13](https://github.com/adobe/aem-project-archetype). Ulteriori dettagli su [creazione di un progetto con Archetipo progetto AEM Maven disponibile qui](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup).

1. Scarica e installa i seguenti pacchetti utilizzando [Gestione pacchetti CRX](http://localhost:4502/crx/packmgr/index.jsp):

[Ottieni file](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [Ottieni file](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **Facoltativamente** se lavori con Eclipse o un altro IDE, scarica il pacchetto sorgente seguente. Distribuisci il progetto in un’istanza AEM locale utilizzando il comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Avvia HelloWorld SRC Screens `We.Retail` Esegui progetto.

[Ottieni file](assets/src-screens-weretail-run.zip)

1. In entrata [Gestione pacchetti CRX](http://localhost:4502/crx/packmgr/index.jsp), verifica che siano installati i seguenti due pacchetti:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens Esecuzione di pacchetti Ui.Apps e Ui.Content tramite CRX Package Manager](assets/crx-packages.png)

   Schermi `We.Retail` Esegui `Ui.Apps` e `Ui.Content` pacchetti installati tramite Gestione pacchetti CRX.

1. Il **screens-weretail-run.ui.apps** il pacchetto installa il codice sotto a `/apps/weretail-run`.

   Questo pacchetto contiene il codice responsabile del rendering dei componenti personalizzati per il progetto. Questo pacchetto include il codice del componente ed eventuali codici JavaScript o CSS necessari. Questo pacchetto incorpora anche **screens-weretail-run.core-0.0.1-SNAPSHOT.jar** che contiene il codice Java™ necessario per il progetto.

   >[!NOTE]
   >
   >In questa esercitazione non viene scritto alcun codice Java™. Se è necessaria una logica di business più complessa, è possibile creare e distribuire Java™ di back-end utilizzando il bundle Java™ di base.

   ![Rappresentazione del codice ui.apps in CRXDE Liti](assets/uipps-contents.png)

   Rappresentazione del codice ui.apps in CRXDE Liti

   Il **Hello World** il componente è solo un segnaposto. Nel corso dell’esercitazione, viene aggiunta una funzionalità che consente all’autore di aggiornare il messaggio visualizzato dal componente.

1. Il **screens-weretail-run.ui.content** il pacchetto installa il codice sotto:

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   Questo pacchetto contiene il contenuto iniziale e la struttura di configurazione necessaria per il progetto. **`/conf/we-retail-run`** contiene tutte le configurazioni per `We.Retail` Esegui il progetto. **`/content/dam/we-retail-run`** include l’avvio delle risorse digitali per il progetto. **`/content/screens/we-retail-run`** contiene la struttura del contenuto Screens. Il contenuto sotto tutti questi percorsi viene aggiornato principalmente in AEM. Per promuovere la coerenza tra gli ambienti (locale, di sviluppo, di staging, di produzione) spesso nel controllo del codice sorgente viene salvata una struttura di contenuto di base.

1. **Passa a AEM Screens > `We.Retail` Esegui progetto:**

   Dal menu Start dell’AEM, fai clic sull’icona Schermi. Verificare la `We.Retail` Viene visualizzato Esegui progetto.

   ![we-retaiul-run-starter](assets/we-retaiul-run-starter.png)

## Creare il componente Hello World {#hello-world-cmp}

Il componente Hello World è un componente semplice che consente a un utente di inserire un messaggio da visualizzare sullo schermo. Il componente è basato su [Modello del componente AEM Screens: https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

AEM Screens presenta alcuni vincoli interessanti che non sono necessariamente validi per i componenti WCM Sites tradizionali.

* La maggior parte dei componenti Screens deve essere eseguita a schermo intero sui dispositivi di digital signage di destinazione
* La maggior parte dei componenti Schermi deve essere incorporabile nei canali di sequenza per generare presentazioni
* L’authoring deve consentire la modifica di singoli componenti in un canale di sequenza, pertanto non è necessario eseguirne il rendering a schermo intero

1. In entrata **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (o IDE scelto) Accedi a `/apps/weretail-run/components/content/helloworld.`

   Aggiungi le seguenti proprietà alla `helloworld` componente:

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![Proprietà per /apps/weretail-run/components/content/helloworld](assets/2018-04-28_at_4_23pm.png)

   Proprietà per /apps/weretail-run/components/content/helloworld

   Il **Hello World** il componente estende **foundation/components/parbase** in modo che possa essere utilizzato correttamente all&#39;interno di un canale di sequenza.

1. Crea un file sotto `/apps/weretail-run/components/content/helloworld` denominato `helloworld.html.`

   Compila il file con quanto segue:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   I componenti Screens richiedono due rendering diversi a seconda di quale [modalità di authoring](https://experienceleague.adobe.com/en/docs/experience-manager-64/authoring/authoring/author-environment-tools) è in uso:

   1. **Produzione**: modalità Anteprima o Pubblicazione (wcmmode=disabled)
   1. **Modifica**: utilizzato per tutte le altre modalità di authoring, ad esempio modifica, progettazione, scaffolding, sviluppatore...

   `helloworld.html`funge da switch, controllando quale modalità di authoring è attiva e reindirizzando a un altro script HTL. Una convenzione comune utilizzata dai componenti Screens consiste nell’avere `edit.html` script per la modalità di modifica e un `production.html` script per la modalità di produzione.

1. Crea un file sotto `/apps/weretail-run/components/content/helloworld` denominato `production.html.`

   Compila il file con quanto segue:

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   Di seguito è riportato il markup di produzione per il componente Hello World. A `data-duration` Questo attributo è incluso poiché il componente viene utilizzato su un canale Sequenza. Il `data-duration` L&#39;attributo viene utilizzato dal canale della sequenza per sapere per quanto tempo deve essere visualizzato un elemento della sequenza.

   Il componente genera un `div` e un `h1` con testo. `${properties.message}` è una parte dello script HTL che restituisce il contenuto di una proprietà JCR denominata `message`. In seguito viene creata una finestra di dialogo che consente all&#39;utente di immettere un valore per `message` testo della proprietà.

   Si noti inoltre che con il componente viene utilizzata la notazione BEM (Block Element Modifier). BEM è una convenzione di codifica CSS che semplifica la creazione di componenti riutilizzabili. BEM è la notazione utilizzata da [Componenti core AEM](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. Crea un file sotto `/apps/weretail-run/components/content/helloworld` denominato `edit.html.`

   Compila il file con quanto segue:

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

   Il markup modificato per il componente Hello World è il seguente: Se il messaggio della finestra di dialogo è stato compilato, nel primo blocco viene visualizzata una versione modificata del componente.

   Se non è stato immesso alcun messaggio di dialogo, viene eseguito il rendering del secondo blocco. Il `cq-placeholder` e `data-emptytext` eseguire il rendering dell’etichetta ***Hello World*** come detentore del luogo in tale caso. La stringa per l’etichetta può essere internazionalizzata utilizzando i18n per supportare l’authoring in più lingue.

1. **Finestra di dialogo Copia immagine di Screens da utilizzare per il componente Hello World.**

   È più semplice iniziare da una finestra di dialogo esistente e quindi apportare modifiche.

   1. Copia la finestra di dialogo da: `/libs/screens/core/components/content/image/cq:dialog`
   1. Incolla la finestra di dialogo sotto `/apps/weretail-run/components/content/helloworld`

   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **Aggiorna la finestra di dialogo Hello World per includere una scheda per il messaggio.**

   Aggiorna la finestra di dialogo in modo che corrisponda a quanto segue. La struttura dei nodi JCR della finestra di dialogo finale è presentata di seguito in XML:

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
                                   fieldDescription="Amount of time the image is shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (milliseconds)"
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

   Il campo di testo per il messaggio viene salvato in una proprietà denominata `message` e che il campo numerico della Durata venga salvato in una proprietà denominata `duration`. Entrambe queste proprietà sono indicate in `/apps/weretail-run/components/content/helloworld/production.html` da HTL come `${properties.message}` e `${properties.duration}`.

   ![Hello World - finestra di dialogo completata](assets/2018-04-29_at_5_21pm.png)

   Hello World - finestra di dialogo completata

## Creare librerie lato client {#clientlibs}

Le librerie lato client forniscono un meccanismo per organizzare e gestire i file CSS e JavaScript necessari per un’implementazione AEM.

Il rendering dei componenti di AEM Screens varia in modalità Modifica rispetto alla modalità Anteprima/Produzione. Vengono create due librerie client: una per la modalità di modifica e la seconda per l’anteprima/produzione.

1. Crea una cartella per le librerie lato client per il componente Hello World.

   Sotto `/apps/weretail-run/components/content/helloworld`, crea una cartella denominata `clientlibs`.

   ![04/04/2018_at_1046](assets/2018-04-30_at_1046am.png)

1. Sotto `clientlibs` cartella, crea un nodo denominato `shared` di tipo `cq:ClientLibraryFolder`.

   ![04/04/2018_at_1115](assets/2018-04-30_at_1115am.png)

1. Aggiungi le seguenti proprietà alla libreria client condivisa:

   * `allowProxy` | Booleano | `true`

   * `categories`| Stringa[] | `cq.screens.components`

   ![Proprietà per /apps/weretail-run/components/content/helloworld/clientlibs/shared](assets/2018-05-03_at_1026pm.png)

   Proprietà per /apps/weretail-run/components/content/helloworld/clientlibs/shared

   La proprietà Categories è una stringa che identifica la libreria client. La categoria cq.screens.component viene utilizzata sia in modalità Modifica che Anteprima/Produzione. Di conseguenza, qualsiasi CSS/JS definito nella libreria client condivisa viene caricato in tutte le modalità.

   È consigliabile non esporre mai percorsi direttamente a /apps in un ambiente di produzione. La proprietà allowProxy garantisce che venga fatto riferimento alle librerie client CSS e JS tramite un prefisso of/etc.clientlibs.

1. Crea file denominato `css.txt` sotto la cartella condivisa.

   Compila il file con quanto segue:

   ```
   #base=css
   
   styles.less
   ```

1. Crea una cartella denominata `css` sotto `shared` cartella. Aggiungi un file denominato `style.less` sotto `css` cartella. La struttura delle librerie client ora dovrebbe essere simile alla seguente:

   ![2018-04-30_at_3_11 pm](assets/2018-04-30_at_3_11pm.png)

   Invece di scrivere direttamente CSS, questa esercitazione utilizza MENO. [MENO](https://lesscss.org/) è un popolare precompilatore CSS che supporta variabili, mixin e funzioni CSS. Le librerie client AEM supportano in modo nativo la compilazione LESS. È possibile utilizzare gli Sass o altri precompilatori, ma questi devono essere compilati al di fuori dell’AEM.

1. Popolare `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` con le seguenti caratteristiche:

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

1. Copiare e incollare `shared` cartella della libreria client per creare una libreria client denominata `production`.

   ![Copiare la libreria client condivisa per creare una nuova libreria client di produzione](assets/copy-clientlib.gif)

   Copia la libreria client condivisa per creare una libreria client di produzione.

1. Aggiornare il `categories` proprietà della libreria client di produzione da impostare `cq.screens.components.production.`

   In questo modo gli stili vengono caricati solo in modalità Anteprima/Produzione.

   ![Proprietà per /apps/weretail-run/components/content/helloworld/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Proprietà per `/apps/weretail-run/components/content/helloworld/clientlibs/production`.

1. Popolare `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` con le seguenti caratteristiche:

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

   Gli stili di cui sopra visualizzano il messaggio centrato al centro dello schermo, ma solo in modalità Produzione.

Una terza categoria di librerie client: `cq.screens.components.edit` può essere utilizzato per aggiungere al componente stili specifici per la sola modifica.

| Categoria Clientlib | Utilizzo |
|---|---|
| `cq.screens.components` | Stili e script condivisi tra le modalità di modifica e di produzione |
| `cq.screens.components.edit` | Stili e script utilizzati solo in modalità di modifica |
| `cq.screens.components.production` | Stili e script utilizzati solo in modalità di produzione |

## Creare una pagina di progettazione {#design-page}

AEM Screens utilizza [Modelli di pagina statici](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-static) e [Configurazioni di progettazione](https://experienceleague.adobe.com/en/docs/experience-manager-64/authoring/siteandpage/default-components-designmode) per le modifiche globali. Le configurazioni di progettazione vengono spesso utilizzate per configurare i componenti consentiti per Parsys su un canale. Una best practice consiste nell’archiviare queste configurazioni in un modo specifico per l’app.

Sotto a `We.Retail` Viene creata la pagina Esegui progettazione in cui sono memorizzate tutte le configurazioni specifiche di `We.Retail` Esegui il progetto.

1. In entrata **CRXDE Liti** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs`, passa a `/apps/settings/wcm/designs`.
1. Crea un nodo sotto la cartella delle progettazioni, denominato `we-retail-run` con un tipo di `cq:Page`.
1. Sotto `we-retail-run` , aggiungere un altro nodo denominato `jcr:content` di tipo `nt:unstructured`. Aggiungi le seguenti proprietà alla `jcr:content` nodo:

   | Nome | Tipo | Valore |
   |---|---|---|
   | `jcr:title` | Stringa | `We.Retail` Esegui |
   | `sling:resourceType` | Stringa | wcm/core/components/designer |
   | `cq:doctype` | Stringa | html_5 |

   ![Pagina di progettazione in /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   Pagina di progettazione in `/apps/settings/wcm/designs/we-retail-run`.

## Creare un canale sequenza {#create-sequence-channel}

Il componente Hello World deve essere utilizzato su un canale di sequenza. Per testare il componente, viene creato un nuovo canale di sequenza.

1. Dal menu Start dell’AEM, vai a **Schermi** > **`We.Retail`Esegui** > e fai clic su **Canali**.

1. Fai clic su **Crea** pulsante

   1. Scegli **Crea entità**

   ![2018-04-30_at_5_18 pm](assets/2018-04-30_at_5_18pm.png)

1. Nella procedura guidata Crea:

1. Passaggio modello - scegli **Canale sequenza**

   1. Passaggio proprietà

   * Scheda Base > Titolo = **Canale inattivo**
   * Scheda Canale > spunta **Rendi il canale online**

   ![inattivo-canale](assets/idle-channel.gif)

1. Apri le proprietà della pagina per il canale inattivo.
1. Aggiornare il campo Struttura in modo che punti a `/apps/settings/wcm/designs/we-retail-run`, la pagina di progettazione creata nella sezione precedente.

   ![Configurazione progettazione /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   Configurazione di progettazione che punta a /apps/settings/wcm/designs/we-retail-run

1. Modifica il canale inattivo appena creato in modo da poterlo aprire.

1. Passa alla modalità pagina **Progettazione** Modalità.

   1. Fai clic su **chiave inglese** Icona in Parsys per configurare i componenti consentiti.

   1. Fai clic su **Schermi** gruppo e **`We.Retail`Esegui - Contenuto** gruppo.

   ![2018-04-30_at_5_43 pm](assets/2018-04-30_at_5_43pm.png)

1. Passa alla modalità pagina **Modifica**. Il componente Hello World può ora essere aggiunto alla pagina e combinato con altri componenti del canale di sequenza.

   ![2018-04-30_at_5_53 pm](assets/2018-04-30_at_5_53pm.png)

1. In entrata **CRXDE Liti** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par`, passa a `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`. Osserva `components` La proprietà ora include `group:Screens`, `group:We.Retail Run - Content`.

   ![Configurazione del progetto in /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1_14pm.png)

   Configurazione del progetto in /apps/settings/wcm/designs/we-retail-run

## Modello per gestori personalizzati {#custom-handlers}

Se il componente personalizzato utilizza risorse esterne come risorse (immagini, video, font e icone), rappresentazioni di risorse specifiche o librerie lato client (css e js), queste non vengono aggiunte automaticamente alla configurazione offline. Il motivo è che per impostazione predefinita è incluso solo il markup HTML.

Per personalizzare e ottimizzare le risorse esatte scaricate sul lettore, Adobe offre un meccanismo di estensione per i componenti personalizzati, in modo da esporre le loro dipendenze alla logica di caching offline in AEM Screens.

La sezione seguente presenta il modello per i gestori di risorse offline personalizzati e i requisiti minimi in `pom.xml` per quel progetto specifico.

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

Il codice che segue riporta i requisiti minimi di `pom.xml` per quel progetto specifico:

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

## Tutti gli elementi insieme {#putting-it-all-together}

Il video seguente mostra il componente finito e come può essere aggiunto a un canale Sequenza. Il canale viene quindi aggiunto a una visualizzazione Posizione e infine assegnato a un lettore Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## Altre considerazioni sui componenti personalizzati che incorporano altre pagine o frammenti {#additional-considerations}

Se il componente personalizzato deve includere altre pagine o frammenti di esperienza e desideri che le modifiche nel contenuto incorporato vengano automaticamente selezionate dal lettore, senza ripubblicare il canale, considera questi due vincoli:

1. Invece di estendere direttamente `foundation/components/parbase`, dovrai estendere entrambi `screens/core/components/content/page` o `screens/core/components/content/experiencefragment`
2. Il nome della proprietà utilizzata per fare riferimento al contenuto incorporato deve essere `pagePath`.

L’utilizzo di questi due componenti core Schermi offre anche il vantaggio aggiuntivo di poter gestire il raggruppamento di alcune delle dipendenze necessarie (librerie lato client, font e così via). Questo avviene tramite le opzioni di configurazione offline nella finestra di dialogo del componente, che quindi riduce la responsabilità di qualsiasi gestore offline personalizzato che dovresti utilizzare per questo. A volte può anche rimuovere completamente la necessità di utilizzarne uno in primo luogo.

## Codice finito {#finished-code}

Di seguito è riportato il codice finito dell&#39;esercitazione. Il **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** e **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** sono i pacchetti AEM compilati. **SRC-screens-weretail-run-0.0.1.zip **è il codice sorgente non compilato che può essere distribuito utilizzando Maven.

[Ottieni file](assets/screens-weretail-runuiapps-001-snapshot.zip)

[Ottieni file](assets/screens-weretail-runuicontent-001-snapshot.zip)

[Ottieni file](assets/screens-weretail-run.zip)
