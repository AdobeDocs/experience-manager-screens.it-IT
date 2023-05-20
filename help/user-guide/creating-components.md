---
title: Creazione di componenti
seo-title: Creating Components
description: I componenti AEM vengono utilizzati per memorizzare, formattare ed eseguire il rendering dei contenuti resi disponibili sulle pagine web. Segui questa pagina per scoprire come creare canali e componenti di rendering.
seo-description: AEM components are used to hold, format, and render the content made available on your webpages. Follow this page to learn about authoring channels and rendering components.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 3%

---

# Creazione di componenti {#creating-components}

I componenti AEM vengono utilizzati per memorizzare, formattare ed eseguire il rendering dei contenuti resi disponibili sulle pagine web.

>[!NOTE]
>
>Per informazioni dettagliate sulla creazione di componenti AEM, consulta Sviluppo di componenti AEM.

## Authoring dei canali {#authoring-channels}

Il canale è l&#39;oggetto principale dei contenuti inviati a un insieme di display. Pertanto, un autore di contenuti in genere apre un canale nell’editor per aggiungere o modificare contenuti. Poiché il canale è un ***cq:Page*** seguirà lo stesso pattern UX tradizionale per aggiungere e modificare componenti sul canale.

Tuttavia, poiché i componenti di un canale vengono in genere visualizzati a schermo intero, l’esperienza di authoring ne risentirà quando si tenta di modificare singoli componenti o di comporre nuovi ordini. Pertanto, il canale si basa sui selettori per eseguire il rendering di diverse viste dei componenti. L’ambiente di authoring sfrutta il selettore di modifica per attivare il rendering del canale personalizzato.

Ad esempio `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

L’utente non deve preoccuparsi di aggiungere il selettore all’URL durante la modifica. Una logica lato client è in ascolto dell’evento di switch di livello e aggiunge il selettore se un canale ha il tipo di risorsa dedicato *screens/core/components/channel.*

## Rendering dei componenti {#rendering-components}

Per abilitare l’authoring corretto, i componenti devono fornire i due rendering seguenti:

| **Component** | **Rappresentazioni** |
|---|---|
| *my-component/my-component.html* | rendering di produzione |
| *my-component/edit.html* | modifica del rendering in una vista più piccola |

I componenti incorporati sfruttano le seguenti categorie di librerie client:

| **Component** | **Libreria client** |
|---|---|
| *cq.screens.components.edit* | CSS e JS che devono essere caricati durante la creazione |
| *cq.screens.components.production* | CSS e JS che devono essere caricati quando il canale è in esecuzione |
| *cq.screens.components* | CSS e JS condivisi |

>[!NOTE]
>
>Per sviluppare componenti personalizzati, utilizza la ***[Modello di componente di esempio AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
