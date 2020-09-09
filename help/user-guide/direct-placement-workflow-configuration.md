---
title: 'Configurazione flusso di lavoro di posizionamento diretto '
seo-title: Configurazione flusso di lavoro di posizionamento diretto
description: Questa pagina evidenzia la configurazione del flusso di lavoro di posizionamento diretto.
seo-description: Questa pagina evidenzia la configurazione del flusso di lavoro di posizionamento diretto.
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Configurazione flusso di lavoro di posizionamento diretto {#direct-placement-workflow}

Seguite questa pagina per informazioni sulla configurazione di un flusso di lavoro delle risorse che consente di inserire una risorsa in un canale AEM Screens  predefinito.

Questa sezione illustra i seguenti argomenti:

* Panoramica
* Configurazione del flusso di lavoro di posizionamento diretto

## Panoramica {#overview}

La configurazione del flusso di lavoro di posizionamento diretto mappa un canale  progetto AEM Screens in una cartella specifica nelle risorse e consente di inserire qualsiasi risorsa in tale cartella. È consigliabile attivare l&#39;aggiornamento offline in blocco per completare la pubblicazione.

In alternativa, in qualità di autore del contenuto potete fare clic manualmente su **Aggiorna contenuto** offline.

>[!NOTE]
>
>Per informazioni sull&#39;utilizzo dell&#39;aggiornamento offline in blocco, consulta Aggiornamento [contenuto come servizio](/help/user-guide/content-update-as-a-service.md).

## Configurazione del flusso di lavoro di posizionamento diretto {#configuring-workflow}

>[!IMPORTANT]
>
>Prima di avviare la configurazione, è necessario installare il [Demo Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). Dopo aver installato il pacchetto, dovreste essere in grado di visualizzarlo e accedervi dall&#39;istanza AEM —> Strumenti (icona) —> **Flusso** di lavoro **—> Modelli** diworkflow.

Per configurare il flusso di lavoro per il posizionamento diretto, effettuate le seguenti operazioni:

1. Andate a  AEM Screens dall’istanza AEM e create un progetto Screens denominato **Asset Workflow**(Flusso di lavoro risorse).

1. Crea un canale denominato **Workflow-Assets** nella cartella **Channels (Canali** ).

