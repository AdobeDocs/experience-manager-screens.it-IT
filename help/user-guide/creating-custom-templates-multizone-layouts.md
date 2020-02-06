---
title: Creazione di modelli personalizzati in layout MultiZone
seo-title: Creazione di modelli personalizzati in layout MultiZone
description: Seguite questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
seo-description: Seguite questa pagina per informazioni sulla creazione di modelli personalizzati nei layout MultiZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: a4d48ba04bb8ab863f4f07b932892676b70e1e23

---


# Creazione di modelli personalizzati in layout MultiZone {#creating-custom-templates-multizone}

L&#39;esempio seguente mostra come creare un modello personalizzato in un layout multiZone.

Ad esempio, la sezione seguente illustra la creazione di un modello personalizzato in un layout a più livelli con le seguenti configurazioni:

![image](assets/custom-template1.png)


## Creazione di un modello personalizzato con una configurazione specifica {#basic-flow-setting}

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



