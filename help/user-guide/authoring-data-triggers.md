---
title: Authoring con Data Triggers
seo-title: Authoring con Data Triggers
description: Segui questa pagina per scoprire come creare con i trigger di dati.
feature: Creazione di esperienze in Screens
role: Amministratore, sviluppatore
level: Intermedio
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---


# Authoring con Data Triggers {#authoring-with-data-triggers}

Questa sezione illustra come abilitare il targeting nei canali.

>[!IMPORTANT]
>
>La versione minima che supporta gli attivatori di dati in un canale AEM Screens è AEM 6.5.3 Feature Pack 3.

## Prerequisiti {#prereqs}

Prima di seguire i passaggi seguenti per abilitare il targeting nei canali, è necessario conoscere i [Termini chiave nella configurazione in AEM Screens](configuring-context-hub.md) necessari per comprendere ContextHub e il targeting in AEM Screens.

>[!IMPORTANT]
>
>Prima di abilitare il targeting in un canale AEM Screens, è consigliabile comprendere e configurare le configurazioni ContextHub.

Segui i link qui sotto per ulteriori informazioni:

1. **[Configurazione dell’archivio dati](configuring-context-hub.md)**
1. **[Impostazione della segmentazione del pubblico](configuring-context-hub.md)**

Una volta completati i passaggi precedenti, puoi abilitare il targeting nei tuoi canali.

## Panoramica sull’authoring con i trigger di dati {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Abilitazione del targeting in un canale AEM Screens {#enabling-targeting}

Segui i passaggi seguenti per abilitare il targeting nei tuoi canali.

1. Passa a uno dei canali AEM Screens. I passaggi seguenti mostrano come abilitare il targeting utilizzando **DataDrivenRetail** *(canale di sequenza)* creato in un canale AEM Screens.

1. Seleziona il canale **DataDrivenRetail** e fai clic su **Proprietà** dalla barra delle azioni.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Seleziona la scheda **Personalizzazione** per impostare le configurazioni di ContextHub e seleziona il percorso ContextHub e Segments.

   1. Seleziona il **Percorso ContextHub** come **libs** > **impostazioni** > **impostazioni cloud** > **predefinito** > **Configurazioni ContextHub** e fai clic su **Predefinito Seleziona**.

   1. Seleziona il **Percorso segmenti** come **conf** > **We.Retail** > **impostazioni** > **wcm** > **segmenti** e fai clic su **Seleziona&lt;a1 3/>.**

   1. Fai clic su **Salva e chiudi**.
   >[!NOTE]
   >
   >Utilizza ContextHub e il percorso Segmenti, in cui hai inizialmente salvato le configurazioni e i segmenti dell&#39;hub di contesto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Naviga e seleziona **DataDrivenRetail** da **DataDrivenAssets** > **Canali** e fai clic su **Modifica** dalla barra delle azioni. Trascina e rilascia le risorse nell’editor canali.

   >[!NOTE]
   >
   >Se hai configurato tutto correttamente, vedrai l&#39;opzione **Targeting** nel menu a discesa dall&#39;editor, come mostrato nella figura seguente.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Fai clic su **Targeting**.

1. Seleziona **Marchio** e **Attività** dal menu a discesa, quindi fai clic su **Avvia targeting**.

### Ulteriori informazioni: Esempi di casi d&#39;uso {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto AEM Screens, puoi seguire i diversi casi d’uso per comprendere in che modo i dati che hanno attivato le risorse svolgono un ruolo fondamentale in settori diversi:

1. **[Attivazione mirata inventario retail](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro viaggi](local-temperature-activation.md)**
1. **[Attivazione prenotazione alberghiera](hospitality-reservation-activation.md)**
