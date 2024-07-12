---
title: Configurazione del flusso di lavoro di posizionamento diretto
description: Questa pagina evidenzia la configurazione del flusso di lavoro di posizionamento diretto.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 1%

---


# Configurazione del flusso di lavoro di posizionamento diretto {#direct-placement-workflow}

Segui questa pagina per scoprire come configurare un flusso di lavoro per le risorse che consente di inserire in modo programmatico una risorsa in un canale AEM Screens predefinito.

Questa sezione tratta i seguenti argomenti:

* Panoramica
* Configurazione del flusso di lavoro di posizionamento diretto

## Panoramica {#overview}

La configurazione del flusso di lavoro di posizionamento diretto mappa un canale di progetto AEM Screens in una cartella specifica delle risorse e consente di posizionare qualsiasi risorsa in tale cartella. L’Adobe consiglia di attivare un aggiornamento offline in blocco per completare la pubblicazione.

In alternativa, come autore di contenuti è possibile fare clic manualmente su **Aggiorna contenuto offline**.

>[!NOTE]
>
>Per informazioni su come utilizzare l&#39;aggiornamento offline in blocco, vedere [Aggiornamento contenuto come servizio](/help/user-guide/content-update-as-a-service.md).

## Configurazione del flusso di lavoro di posizionamento diretto {#configuring-workflow}

>[!IMPORTANT]
>
>Prima di avviare la configurazione, installare `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. Dopo aver installato il pacchetto, dovresti essere in grado di visualizzarlo e accedervi dall&#39;istanza AEM > Strumenti (icona) > **Flusso di lavoro** > **Modelli di flusso di lavoro**.

Segui i passaggi seguenti per configurare il flusso di lavoro di posizionamento diretto:

1. Passa ad AEM Screens dalla tua istanza AEM e crea un progetto Screens denominato **Flusso di lavoro risorse**.

1. Crea un canale con titolo **Workflow-Assets** nella cartella **Channels**.

