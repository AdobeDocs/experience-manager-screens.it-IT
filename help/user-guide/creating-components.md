---
title: Creare componenti
description: Scopri come i componenti AEM vengono utilizzati per contenere, formattare ed eseguire il rendering dei contenuti resi disponibili sulle pagine web.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 1%

---

# Creare componenti {#creating-components}

I componenti AEM vengono utilizzati per contenere, formattare ed eseguire il rendering del contenuto reso disponibile sulle pagine web.

>[!NOTE]
>
>Per informazioni dettagliate sulla creazione di componenti AEM, consulta Sviluppo di componenti AEM.

## Canali autore {#authoring-channels}

Il canale è l&#39;oggetto principale dei contenuti inviati a un insieme di display. Pertanto, un autore di contenuti in genere apre un canale nell’editor per aggiungere o modificare contenuti. Poiché il canale è un ***`cq:Page`***, segue lo stesso pattern UX tradizionale per aggiungere e modificare componenti sul canale.

Tuttavia, poiché in genere i componenti di un canale vengono riprodotti a schermo intero, l’esperienza di authoring ne risente quando si tenta di modificare singoli componenti o di comporre nuovi ordini. Pertanto, il canale si basa sui selettori per eseguire il rendering di diverse viste dei componenti. L&#39;ambiente di authoring utilizza il selettore `edit` per attivare il rendering del canale personalizzato.

Ad esempio `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

L’utente non deve preoccuparsi di aggiungere il selettore all’URL durante la modifica. Una logica lato client sta ascoltando l&#39;evento di switch di livello e aggiunge il selettore se il canale ha il tipo di risorsa dedicato *screens/core/components/channel*.

## Rendering dei componenti {#rendering-components}

Per abilitare l’authoring corretto, i componenti devono fornire i due rendering seguenti:

| **Component** | **Rappresentazioni** |
|---|---|
| *my-component/my-component.html* | rendering di produzione |
| *my-component/edit.html* | modifica del rendering in una vista più piccola |

I componenti incorporati utilizzano le seguenti categorie di librerie client:

| **Component** | **Libreria client** |
|---|---|
| *cq.screens.components.edit* | CSS e JS che devono essere caricati durante l’authoring |
| *cq.screens.components.production* | CSS e JS da caricare quando il canale è in esecuzione |
| *cq.screens.components* | CSS e JS condivisi |

>[!NOTE]
>
>Per sviluppare componenti personalizzati, utilizzare il modello di componente di esempio ***[AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
