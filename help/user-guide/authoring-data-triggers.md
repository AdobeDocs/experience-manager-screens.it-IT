---
title: Authoring con attivatori dati
seo-title: Authoring con attivatori dati
description: Segui questa pagina per apprendere come creare con i trigger dei dati.
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---


# Authoring con attivatori di dati {#authoring-with-data-triggers}

In questa sezione viene illustrato come abilitare il targeting nei canali.

>[!IMPORTANT]
>
>La versione minima che supporta le attivazioni di dati in un canale AEM Screens  è AEM 6.5.3 Feature Pack 3.

## Prerequisiti {#prereqs}

Prima di seguire i passaggi indicati di seguito per abilitare il targeting nei canali, è necessario conoscere i [Termini chiave in Configurazione in  AEM Screens](configuring-context-hub.md) richiesti per comprendere ContextHub e Targeting in  AEM Screens.

>[!IMPORTANT]
>
>È consigliabile comprendere e configurare le configurazioni ContextHub prima di abilitare il targeting in un canale AEM Screens .

Per ulteriori informazioni, effettuate le seguenti operazioni:

1. **[Configurazione dell&#39;archivio dati](configuring-context-hub.md)**
1. **[Impostazione della segmentazione dell&#39;audience](configuring-context-hub.md)**

Una volta completati i passaggi precedenti, potete abilitare il targeting nei vostri canali.

## Panoramica sull&#39;authoring con attivatori dati {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Abilitazione del targeting in un canale AEM Screens  {#enabling-targeting}

Seguite i passaggi indicati di seguito per abilitare il targeting nei canali.

1. Andate a uno dei canali AEM Screens . I passaggi seguenti dimostrano come abilitare il targeting utilizzando **DataDrivenRetail** *(canale di sequenza)* creato in un canale AEM Screens .

1. Selezionare il canale **DataDrivenRetail** e fare clic su **Properties** dalla barra delle azioni.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Selezionate la scheda **Personalizzazione** per impostare le configurazioni ContextHub e selezionate il percorso ContextHub e Segments.

   1. Selezionare il percorso **ContextHub** come **libs** > **settings** > **cloud settings** > **default** > **ContextHub Configurations** e fare clic su **Selezionate**.

   1. Selezionare il percorso **Segments Path** come **conf** > **We.Retail** > **settings** > **wcm** > **Segmenti** e fare clic su **Select&lt;a 3/>.**

   1. Fai clic su **Salva e chiudi**.
   >[!NOTE]
   >
   >Usa ContextHub e il percorso Segments, dove hai salvato inizialmente le configurazioni e i segmenti dell&#39;hub di contesto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Selezionare **DataDrivenRetail** da **DataDrivenAssets** > **Channels** e fare clic su **Edit** dalla barra delle azioni. Trascina e rilascia le risorse nell’editor canale.

   >[!NOTE]
   >
   >Se avete impostato tutto correttamente, nel menu a discesa dell&#39;editor verrà visualizzata l&#39;opzione **Targeting**, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Fare clic su **Targeting**.

1. Selezionare **Marchio** e **Attività** dal menu a discesa, quindi fare clic su **Avvia targeting**.

### Ulteriori informazioni: Esempi di utilizzo {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto  AEM Screens, potete seguire i diversi casi d’uso per comprendere in che modo le risorse attivate dai dati svolgono un ruolo fondamentale nei diversi settori:

1. **[Attivazione mirata inventario vendita al dettaglio](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro viaggio](local-temperature-activation.md)**
1. **[Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)**
