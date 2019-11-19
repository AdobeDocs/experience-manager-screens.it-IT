---
title: Creazione di componenti
seo-title: Creazione di componenti
description: I componenti AEM sono utilizzati per conservare, formattare ed eseguire il rendering del contenuto reso disponibile sulle pagine Web. Seguite questa pagina per informazioni sull’authoring di canali e componenti di rendering.
seo-description: I componenti AEM sono utilizzati per conservare, formattare ed eseguire il rendering del contenuto reso disponibile sulle pagine Web. Seguite questa pagina per informazioni sull’authoring di canali e componenti di rendering.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Creazione di componenti {#creating-components}

I componenti AEM sono utilizzati per conservare, formattare ed eseguire il rendering del contenuto reso disponibile sulle pagine Web.

>[!NOTE]
>
>Per informazioni dettagliate sulla creazione di componenti AEM, consultate Sviluppo di componenti AEM.

## Creazione di canali {#authoring-channels}

Il canale è l'oggetto centrale del contenuto distribuito a una serie di schermi. Di conseguenza, un autore di contenuti apriva solitamente un canale nell’editor per aggiungere o modificare contenuti. Poiché il canale è un ***cq:Page*** , seguirà lo stesso pattern UX tradizionale per aggiungere e modificare componenti sul canale.

Tuttavia, poiché all’interno di un canale viene generalmente eseguito il rendering a schermo intero dei componenti, l’esperienza di authoring risulterà compromessa quando si tenta di modificare singoli componenti o comporre nuovi ordini. Pertanto, il canale si basa sui selettori per rappresentare diverse viste dei componenti. L’ambiente di authoring sfrutta il selettore di modifica per attivare il rendering del canale personalizzato.

Esempio, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

Durante la modifica, l’utente non deve occuparsi di aggiungere il selettore all’URL. Una logica lato client è l'ascolto dell'evento switch del livello e aggiunge il selettore se un canale ha il tipo di risorsa dedicato *schermi/core/components/channel.*

## Componenti di rendering {#rendering-components}

Per abilitare la creazione corretta, i componenti devono fornire i due rendering seguenti:

| **Componente** | **Rappresentazioni** |
|---|---|
| *my-component/my-component.html* | rendering produzione |
| *my-component/edit.html* | modifica del rendering in una visualizzazione più piccola |

I componenti incorporati sfruttano le seguenti categorie di librerie client:

| **Componente** | **Libreria client** |
|---|---|
| *cq.screens.components.edit* | CSS e JS da caricare durante l'authoring |
| *cq.screens.components.production* | CSS e JS da caricare quando il canale è in esecuzione |
| *cq.screens.components* | CSS e JS condivisi |

>[!NOTE]
>
>Per sviluppare componenti personalizzati, utilizzate il modello [di componente di esempio ***](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)AEM Screens**.

