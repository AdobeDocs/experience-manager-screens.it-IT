---
title: Attivazione temperatura centro viaggio
seo-title: Attivazione temperatura centro viaggio
description: Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della temperatura locale del centro viaggi in base ai valori popolati in Google Sheets.
seo-description: Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della temperatura locale del centro viaggi in base ai valori popolati in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# Attivazione temperatura centro viaggio {#travel-center-temperature-activation}

Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della temperatura locale del centro viaggi in base ai valori popolati in Google Sheets.

## Descrizione {#description}

Per questo caso d&#39;uso, se il tuo Google Sheets ha un Valore inferiore a 50, verrà visualizzata un&#39;immagine con bevande calde e se il valore è maggiore o uguale a 50, verrà visualizzata l&#39;immagine con bevande fredde. In caso di un altro valore o nessun valore, il lettore visualizzerà un&#39;immagine predefinita.

## Precondizioni {#preconditions}

Prima di iniziare ad implementare l&#39;attivazione della temperatura locale del centro viaggi, è necessario apprendere come impostare ***Data Store***, ***Segmentation del pubblico*** e ***Enable Targeting for Channels*** in un progetto AEM Screens .

Per informazioni dettagliate, fare riferimento a [Configurazione di ContextHub in  AEM Screens](configuring-context-hub.md).

## Flusso di base {#basic-flow}

Seguire i passaggi indicati di seguito per implementare il caso d’uso di attivazione della temperatura locale del centro viaggi:

1. **Compilazione dei fogli di Google**

   1. Passare al foglio di Google ContextHubDemo.
   1. Aggiungere una colonna con **Intestazione1** con il valore corrispondente per la temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Andate ai segmenti del pubblico (fate riferimento a ***Passaggio 2: Impostazione della segmentazione dell&#39;audience*** in **[Configurazione di ContextHub  pagina AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Selezionare il **Fogli A1 1** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/0** dall&#39;elenco a discesa in **Nome proprietà**

   1. Selezionare **Operatore** come **maggiore di o uguale** dal menu a discesa

   1. Immettere il **Valore** come **50**

   1. Analogamente, selezionare le **Fogli A1 2** e fare clic su **Modifica**.

   1. Selezionare la **proprietà di confronto - Valore** e fare clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/0** dall&#39;elenco a discesa in **Nome proprietà**

   1. Selezionare **Operatore** come **minore di** dal menu a discesa

   1. Immettere il **Valore** come **50**

1. Navigare e selezionare il canale () e fare clic su **Modifica** dalla barra delle azioni. Nell&#39;esempio seguente, **DataDrivenWeather**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il canale deve già avere un&#39;immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configuring ContextHub in  AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >È necessario impostare la scheda **ContextHub** **Configurations** utilizzando il canale **Properties** —> **Personalization**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selezionare **Targeting** dall&#39;editor e selezionare **Brand** e **Activity** dal menu a discesa, quindi fare clic su **Avvia targeting**.

   ![new_activity3](assets/new_activity3.gif)

1. **Verifica dell’anteprima**

   1. Fare clic su **Anteprima.** Inoltre, aprite il foglio di Google e aggiornate il relativo valore.
   1. Modificate il valore impostando un valore inferiore a 50, dovreste essere in grado di visualizzare l&#39;immagine delle bevande estive. Se il valore in Google Sheet è 50 o maggiore di quanto dovrebbe essere in grado di visualizzare l&#39;immagine di una bevanda calda.

   ![result3](assets/result3.gif)

