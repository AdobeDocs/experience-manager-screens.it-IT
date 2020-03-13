---
title: Authoring con attivatori dati
seo-title: Authoring con attivatori dati
description: Segui questa pagina per apprendere come creare con i trigger dei dati.
translation-type: tm+mt
source-git-commit: 9490eb2aa089268884d0f39a32eb8c53de110ed7

---


# Authoring con attivatori dati {#authoring-with-data-triggers}

In questa sezione viene illustrato come abilitare il targeting nei canali.

>[!IMPORTANT]
> La versione minima che supporta le attivazioni di dati in un canale AEM Screens è AEM 6.4.3 Feature Pack 3.

## Prerequisiti {#prereqs}

Prima di seguire i passaggi indicati di seguito per abilitare il targeting nei canali, è necessario conoscere i termini [chiave in Configurazione in AEM Screens](configuring-context-hub.md) necessari per comprendere ContextHub e Targeting in AEM Screens.

>[!IMPORTANT]
> Prima di attivare il targeting in un canale AEM Screens, è consigliabile comprendere e configurare le configurazioni ContextHub.

Per ulteriori informazioni, effettuate le seguenti operazioni:

1. **[Configurazione dell&#39;archivio dati](configuring-context-hub.md)**
1. **[Impostazione della segmentazione dell&#39;audience](configuring-context-hub.md)**

Una volta completati i passaggi precedenti, potete abilitare il targeting nei vostri canali.

## Panoramica sull’authoring con attivatori dati {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Attivazione del targeting in un canale AEM Screens {#enabling-targeting}

Seguite i passaggi indicati di seguito per abilitare il targeting nei canali.

1. Passa a uno dei canali AEM Screens. I passaggi seguenti dimostrano come abilitare il targeting utilizzando **DataDrivenRetail** *(canale di sequenza)* creato in un canale AEM Screens.

1. Selezionate il canale **DataDrivenRetail** e fate clic su **Proprietà** dalla barra delle azioni.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Selezionate la scheda **Personalizzazione** per impostare le configurazioni ContextHub.

   1. Selezionate **ContextHub Path** come **libs** > **settings** > **cloud settings** > **default** **** ****>ContextHub Configurations, quindi fate clic suSelect.

   1. Selezionate Percorso **** Segmenti come **conf** > **We.Retail** > **impostazioni** > **wcm** **** ****> Segmentie fate clic su Seleziona.

   1. Fate clic su **Salva e chiudi**.
   >[!NOTE]
   >
   >Usa ContextHub e il percorso Segments, dove hai salvato inizialmente le configurazioni e i segmenti dell&#39;hub di contesto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Naviga e seleziona **DataDrivenRetail** da **DataDrivenAssets** > **Canali** , quindi fai clic su **Modifica** nella barra delle azioni.

   >[!NOTE]
   >
   >Se avete impostato tutto correttamente, l&#39;opzione **Targeting** viene visualizzata nel menu a discesa dall&#39;editor, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   >
   >Una volta configurate le configurazioni ContextHub per il canale, accertatevi di seguire i passaggi precedenti da 1 a 4, anche per gli altri tre canali di sequenza, se desiderate seguire tutti i casi di utilizzo indicati di seguito.

### Ulteriori informazioni: Esempi di utilizzo {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto AEM Screens, puoi seguire i diversi casi d’uso per comprendere in che modo le risorse attivate dai dati svolgono un ruolo fondamentale nei diversi settori:

1. **[Attivazione mirata inventario vendita al dettaglio](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro viaggio](local-temperature-activation.md)**
1. **[Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)**

