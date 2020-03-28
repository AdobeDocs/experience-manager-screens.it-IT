---
title: 'Configurazione flusso di lavoro di posizionamento diretto '
seo-title: Configurazione flusso di lavoro di posizionamento diretto
description: Questa pagina evidenzia la configurazione del flusso di lavoro di posizionamento diretto.
seo-description: Questa pagina evidenzia la configurazione del flusso di lavoro di posizionamento diretto.
translation-type: tm+mt
source-git-commit: 19baf90409eab4c72fb38e992c272338b0098d89

---


# Configurazione flusso di lavoro di posizionamento diretto {#direct-placement-workflow}

Segui questa pagina per informazioni sulla configurazione di un flusso di lavoro delle risorse per l’inserimento programmatico di una risorsa in un canale AEM Screens predefinito.

Questa sezione illustra i seguenti argomenti:

* Panoramica
* Configurazione del flusso di lavoro di posizionamento diretto

## Panoramica {#overview}

La configurazione del flusso di lavoro per il posizionamento diretto mappa un canale di progetto AEM Screens in una cartella specifica delle risorse e consente di posizionare qualsiasi risorsa in tale cartella. È consigliabile attivare l&#39;aggiornamento offline in blocco per completare la pubblicazione.

In alternativa, in qualità di autore del contenuto potete fare clic manualmente su **Aggiorna contenuto** offline.

>[!NOTE]
> Per informazioni sull&#39;utilizzo dell&#39;aggiornamento offline in blocco, consulta Aggiornamento [contenuto come servizio](/help/user-guide/content-update-as-a-service.md).

## Configurazione del flusso di lavoro di posizionamento diretto {#configuring-workflow}

>[!IMPORTANT]
> Prima di avviare la configurazione, è necessario installare il [Demo Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). Dopo aver installato il pacchetto, dovreste essere in grado di visualizzarlo e accedervi dall’istanza di AEM —> Strumenti (icona) —> **Workflow** —> **Workflow Models**.

Per configurare il flusso di lavoro per il posizionamento diretto, effettuate le seguenti operazioni:

1. Passa a AEM Screens dall’istanza di AEM e crea un progetto Screens dal titolo **Asset Workflow**(Flusso di lavoro risorse).

1. Crea un canale denominato **Workflow-Assets** nella cartella **Channels (Canali** ).

1. 
