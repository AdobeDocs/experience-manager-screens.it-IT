---
title: Configurazione del flusso di lavoro di posizionamento diretto
description: Questa pagina evidenzia la configurazione del flusso di lavoro di posizionamento diretto.
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---


# Configurazione del flusso di lavoro di posizionamento diretto {#direct-placement-workflow}

Segui questa pagina per scoprire come configurare un flusso di lavoro per le risorse che consente di inserire in modo programmatico una risorsa in un canale AEM Screens predefinito.

Questa sezione tratta i seguenti argomenti:

* Panoramica
* Configurazione del flusso di lavoro di posizionamento diretto

## Panoramica {#overview}

La configurazione del flusso di lavoro di posizionamento diretto mappa un canale di progetto AEM Screens in una cartella specifica delle risorse e consente di posizionare qualsiasi risorsa in tale cartella. L’Adobe consiglia di attivare un aggiornamento offline in blocco per completare la pubblicazione.

In alternativa, come autore di contenuti puoi fare clic manualmente su **Aggiorna contenuto offline**.

>[!NOTE]
>
>Per informazioni su come utilizzare l’aggiornamento offline in blocco, consulta [Aggiornamento contenuti come servizio](/help/user-guide/content-update-as-a-service.md).

## Configurazione del flusso di lavoro di posizionamento diretto {#configuring-workflow}

>[!IMPORTANT]
>
>Prima di avviare la configurazione, installa `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. Dopo aver installato il pacchetto, dovresti essere in grado di visualizzarlo e accedervi dall’istanza AEM > Strumenti (icona) > **Flusso di lavoro** > **Modelli flusso di lavoro**.

Segui i passaggi seguenti per configurare il flusso di lavoro di posizionamento diretto:

1. Dalla tua istanza AEM, accedi ad AEM Screens e crea un progetto Screens denominato **Flusso di lavoro risorse**.

1. Crea un canale con titolo **Workflow-Assets** in **Canali** cartella.

