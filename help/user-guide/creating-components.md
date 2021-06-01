---
title: Creazione di componenti
seo-title: Creazione di componenti
description: I componenti AEM vengono utilizzati per conservare, formattare ed eseguire il rendering del contenuto reso disponibile sulle pagine web. Segui questa pagina per informazioni sull’authoring dei canali e sul rendering dei componenti.
seo-description: I componenti AEM vengono utilizzati per conservare, formattare ed eseguire il rendering del contenuto reso disponibile sulle pagine web. Segui questa pagina per informazioni sull’authoring dei canali e sul rendering dei componenti.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Sviluppo di schermi
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 2%

---


# Creazione di componenti {#creating-components}

I componenti AEM vengono utilizzati per conservare, formattare ed eseguire il rendering del contenuto reso disponibile sulle pagine web.

>[!NOTE]
>
>Per informazioni dettagliate sulla creazione di componenti AEM, consulta Sviluppo di componenti AEM.

## Canali di authoring {#authoring-channels}

Il canale è l&#39;oggetto centrale del contenuto distribuito a un set di display. Pertanto, un autore di contenuti solitamente apre un canale nell’editor per aggiungere o modificare contenuti. Poiché il Canale è un ***cq:Page***, seguirà lo stesso pattern UX tradizionale per aggiungere e modificare i componenti sul canale.

Tuttavia, poiché in genere i componenti all’interno di un canale vengono sottoposti a rendering a schermo intero, l’esperienza di authoring subirà delle conseguenze quando si tenta di modificare singoli componenti o comporre nuovi ordini. Pertanto, il canale si affiderà ai selettori per eseguire il rendering di diverse viste dei componenti. L’ambiente di authoring sfrutta il selettore di modifica per attivare il rendering del canale personalizzato.

Esempio, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

L’utente non deve occuparsi di aggiungere il selettore all’URL durante la modifica. Una logica lato client sta ascoltando l&#39;evento dell&#39;interruttore di livello e aggiunge il selettore se un canale ha il tipo di risorsa dedicato *screens/core/components/channel.*

## Componenti di rendering {#rendering-components}

Per abilitare l’authoring corretto, i componenti devono fornire i due rendering seguenti:

| **Componente** | **Rappresentazioni** |
|---|---|
| *my-component/my-component.html* | rendering della produzione |
| *my-component/edit.html* | modifica del rendering in una visualizzazione più piccola |

I componenti incorporati sfruttano le seguenti categorie di librerie client:

| **Componente** | **Libreria client** |
|---|---|
| *cq.screens.components.edit* | CSS e JS da caricare durante l’authoring |
| *cq.screens.components.production* | CSS e JS da caricare quando il canale è in esecuzione |
| *cq.screens.components* | CSS e JS condivisi |

>[!NOTE]
>
>Per sviluppare componenti personalizzati, utilizza il modello di componente di esempio ***[AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

