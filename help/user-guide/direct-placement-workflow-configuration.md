---
title: Configurazione del flusso di lavoro di posizionamento diretto
seo-title: Direct Placement Workflow Configuration
description: Questa pagina evidenzia la configurazione del flusso di lavoro di posizionamento diretto.
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Configurazione del flusso di lavoro di posizionamento diretto {#direct-placement-workflow}

Segui questa pagina per scoprire come configurare un flusso di lavoro per le risorse che consente di inserire in modo programmatico una risorsa in un canale AEM Screens predefinito.

Questa sezione tratta i seguenti argomenti:

* Panoramica
* Configurazione del flusso di lavoro di posizionamento diretto

## Panoramica {#overview}

La configurazione del flusso di lavoro di posizionamento diretto mappa un canale di progetto AEM Screens in una cartella specifica delle risorse e consente di posizionare qualsiasi risorsa in tale cartella. Si consiglia di attivare l’aggiornamento offline in blocco per completare la pubblicazione.

In alternativa, come autore di contenuti puoi fare clic manualmente su **Aggiorna contenuto offline**.

>[!NOTE]
>
>Per informazioni su come utilizzare l’aggiornamento offline in blocco, consulta [Aggiornamento contenuti come servizio](/help/user-guide/content-update-as-a-service.md).

## Configurazione del flusso di lavoro di posizionamento diretto {#configuring-workflow}

>[!IMPORTANT]
>
>Prima di avviare la configurazione, è necessario installare [Pacchetto dimostrativo](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). Dopo aver installato il pacchetto, dovresti essere in grado di visualizzarlo e accedervi dall’istanza AEM —> Strumenti (icona) —> **Flusso di lavoro** —> **Modelli flusso di lavoro**.

Segui i passaggi seguenti per configurare il flusso di lavoro di posizionamento diretto:

1. Passa ad AEM Screens dalla tua istanza AEM e crea un progetto Screens con il nome di **Flusso di lavoro risorse**.

1. Crea un canale con titolo **Workflow-Assets** in **Canali** cartella.

