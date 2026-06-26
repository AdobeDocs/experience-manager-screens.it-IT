---
title: Authoring con Data Triggers
description: Scopri come effettuare l’authoring con i trigger di dati in un canale AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
TQID: https://experienceleague.adobe.com/Iqb4pREvZNLalXSE6sNTZPV-uwqzBJKmztLuQtWfCW0
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ff2b9b37-92e0-45fc-b853-379d44c08c89
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 421
ht-degree: 0%

---

# Authoring con Data Triggers {#authoring-with-data-triggers}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Questa sezione illustra come abilitare il targeting nei canali.

>[!IMPORTANT]
>
>La versione minima che supporta i trigger di dati in un canale AEM Screens è AEM 6.5.3 Feature Pack 3.

## Prerequisiti {#prereqs}

Prima di seguire i passaggi seguenti per abilitare il targeting nei canali, scopri i [Termini chiave nella configurazione in AEM Screens](configuring-context-hub.md) necessari per comprendere ContextHub e il targeting in AEM Screens.

>[!IMPORTANT]
>
>Prima di abilitare il targeting in un canale AEM Screens, è consigliabile comprendere e configurare le configurazioni ContextHub.

Per ulteriori informazioni, segui i collegamenti riportati di seguito:

1. **[Configurazione dell&#39;archivio dati](configuring-context-hub.md)**
1. **[Impostazione della segmentazione del pubblico](configuring-context-hub.md)**

Una volta completati i passaggi precedenti, sei pronto per abilitare il targeting nei tuoi canali.

## Panoramica sull’authoring con Data Triggers {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Abilitazione del targeting in un canale AEM Screens {#enabling-targeting}

Segui i passaggi seguenti per abilitare il targeting nei tuoi canali.

1. Passa a uno dei canali di AEM Screens. Nei passaggi seguenti viene illustrato come abilitare il targeting utilizzando **DataDrivenRetail** *(canale sequenza)* creato in un canale AEM Screens.

1. Fai clic sul canale **DataDrivenRetail** e fai clic su **Proprietà** nella barra delle azioni.

   ![schermata_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Fai clic sulla scheda **Personalization** per configurare le configurazioni ContextHub e fare clic sul percorso ContextHub e Segments.

   1. Fai clic sul percorso **ContextHub** come **libs** > **settings** > **cloudsettings** > **default** > **Configurazioni ContextHub** e fai clic su **Click**.

   1. Fai clic su **Percorso segmenti** come **conf** > **`We.Retail`** > **impostazioni** > **wcm** > **segmenti** e fai clic su **Fai clic**.

   1. Fai clic su **Salva e chiudi**.

   >[!NOTE]
   >
   >Utilizza ContextHub e il percorso Segmenti, dove hai inizialmente salvato le configurazioni e i segmenti dell’hub di contesto.

   ![schermata_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Passa a **DataDrivenRetail** da **DataDrivenAssets** > **Canali** e fai clic su **Modifica** nella barra delle azioni. Trascina e rilascia le risorse nell’editor canali.

   >[!NOTE]
   >
   >Se hai impostato tutto correttamente, puoi visualizzare l&#39;opzione **Targeting** nell&#39;elenco a discesa dall&#39;editor, come illustrato nella figura seguente.

   ![schermata_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Fare clic su **Targeting**.

1. Fai clic su **Marchio** e **Attività** dal menu a discesa, quindi fai clic su **Inizia impostazione destinazione**.

### Ulteriori informazioni: casi di utilizzo di esempio {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto AEM Screens, puoi seguire i diversi casi d’uso per comprendere in che modo le risorse attivate dai dati svolgono un ruolo fondamentale in diversi settori:

1. **[Attivazione con targeting inventario vendita al dettaglio](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro di viaggio](local-temperature-activation.md)**
1. **[Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)**

