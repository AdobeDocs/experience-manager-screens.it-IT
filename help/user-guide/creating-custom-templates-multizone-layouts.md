---
title: Creazione di modelli personalizzati in layout MultiZone
seo-title: Creazione di modelli personalizzati in layout MultiZone
description: Seguite questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
seo-description: Seguite questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6a0967580d06e749db878d74aad2ffb1fec82f43

---


# Creazione di modelli personalizzati in layout MultiZone {#creating-custom-templates-multizone}

In questa pagina viene illustrato come creare un modello personalizzato in un layout con più aree.

## Convenzione di denominazione {#name-terms}

Prima di comprendere come creare modelli personalizzati per più aree da utilizzare in un progetto AEM Screens, è consigliabile conoscere la versione dei modelli da creare.

| **Nome layout** | **Descrizione** |
|---|---|
| Left20-LandscapeHD3Zone | Si riferisce a un layout orizzontale a 3 zone che consente di creare 3 zone con la zona 1 come 20% dello schermo orizzontale e verticale da sinistra, la zona 2 come 80% dello schermo orizzontale e il 20% dello schermo verticale giustificato, la zona 3 come 100% dello schermo orizzontale e l&#39;80% dello schermo verticale con proporzioni pari a 16:9 |
| Upper20-PortraitHD2Zone | Si riferisce a un modello verticale a 2 zone che copre il 20% dello schermo dalla parte superiore, con proporzioni pari a 16:9 |
| Right20-LandscapeSD3Zone | Si riferisce a un modello a 3 zone che copre il 20% dello schermo da destra, con proporzioni pari a 4:3 |

##  Esempi di utilizzo {#example-use-cases}

## Layout Left20-LandscapeHD3Zone {#custom-template-one}

Seguite la sezione seguente per creare un modello personalizzato *Left20-LandscapeHD3Zone* con la seguente configurazione:

* **Left20** fa riferimento alla zona superiore sinistra che copre il 20% delle dimensioni orizzontali e verticali dello schermo.
* **Orizzontale** si riferisce all&#39;orientamento dello schermo
* **HD** indica le proporzioni 16:9
* **3Zone** si riferisce a tre zone del display

## Rappresentazione visiva del layout MultiZone {#multi-layout-visual-one}

Il layout Left20-LandscapeHD3Zone consente di creare nel progetto il seguente layout a più zone:

![image](/help/user-guide/assets/custom-multizone/custom-multizone1.png)

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

1. Rinominare la **barra a sinistra** copiata (`/apps/customtemplate/template`) in **layout** personalizzato.

1. Andate a `/apps/customtemplate/template/my-custom-layout` e aggiornate le proprietà **jcr:description** in *Template for Left20-LandscapeHD3Zone* and **jcr:title** to *Left20-LandscapeHD3Zone*(Modello per Left20-Landscape).

1. Andate al nodo **offline-config** da `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` e aggiornate **jcr:title** a *Left20-LandscapeHD3Zone*.

1. Andate alla proprietà *jcr:content* di **my-custom-template** da `/apps/customtemplate/template/my-custom-layout/jcr:content` e aggiornate la proprietà **cq:cssClass** su **aem-Layout my-custom-layout**.

1. Facendo riferimento al passaggio (4), in cui avete copiato il modello a sinistra, potrete visualizzare 3 griglie reattive sotto `my-custom-layout/jcr:content`. Aggiungi classe css personalizzata a ciascuna griglia reattiva nella proprietà *cq:cssClass* , ad esempio, *my-custom-layout—top-left*, *my-custom-layout—top-right*, *my-custom-layout—bottom*.

   >[!NOTE]
   >Queste classi personalizzate verranno utilizzate nel css per impostare larghezza/altezza per queste griglie reattive.

   >[!NOTE]
   > Potete aggiungere o rimuovere le griglie reattive in base al numero totale di griglie desiderato. In questo esempio, vengono mostrate 2 griglie nella prima riga e 1 griglia nella seconda riga, quindi ci sono un totale di 3 griglie reattive (r1c1, r1c2, r2c1).

1. Copiare `/libs/settings/wcm/designs/screens` in `/apps/settings/wcm/designs/` e rinominare come modelli **personalizzati**

1. Andate a `/apps/settings/wcm/designs/custom-template-designs` e aggiornate la proprietà *jcr:title* della struttura **custom-template-designs** alla progettazione **di modelli** personalizzati.

1. aggiornate il `/apps/settings/wcm/designs/<project>-designs/static.css` contenuto in modo che corrisponda alle seguenti

## Creazione di un modello personalizzato con una configurazione specifica {#basic-flow-setting}

![image](assets/custom-template1.png)

Per creare un modello personalizzato, effettuate le operazioni seguenti.

1. Crea il modello in `/apps/<project>/templates/my-custom-layout`

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. Creare una struttura di pagina in `/apps/settings/wcm/designs/<project>`.

   >[!NOTE]
   >
   >Verificate che il percorso `cq:designPath` sopra corrisponda al percorso.

1. Aggiornare il nodo **offline-config** affinché la progettazione punti anche al nuovo percorso

1. Aggiungete un file **static.css** nella `/apps/settings/wcm/designs/<project>` cartella e impostatene il contenuto su

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

## Inserimento di un’immagine come livello di sfondo {#inserting-image}

Potete inserire nel layout un’immagine come livello di sfondo:

Potete regolare la regola CSS in modo da usare l&#39;elemento denominato &quot;data-uri&quot; e allineare direttamente l&#39;immagine (con codifica Base64) nel file CSS.

Tale operazione è effettuata come segue:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

In alternativa, puoi seguire i passaggi seguenti:

1. Accertatevi che l&#39;immagine sia in qualche modo inclusa nella configurazione offline per il canale
1. Utilizzate un collegamento diretto all&#39;immagine nel CSS precedente, invece della variante &quot;data-uri&quot;


## Aggiornamento colore di sfondo {#updating-color}

Per modificare il colore di sfondo, aggiungete il seguente codice al file xml:

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



