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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Attivazione temperatura centro viaggio {#travel-center-temperature-activation}

Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della temperatura locale del centro viaggi in base ai valori popolati in Google Sheets.

## Descrizione {#description}

Per questo caso d'uso, se il tuo Google Sheets ha un Valore inferiore a 50, verrà visualizzata un'immagine con bevande calde e se il valore è maggiore o uguale a 50, verrà visualizzata l'immagine con bevande fredde. In caso di un altro valore o nessun valore, il lettore visualizzerà un'immagine predefinita.

## Premesse {#preconditions}

Prima di iniziare a implementare l’attivazione della temperatura locale del centro viaggi, devi imparare a configurare ***Archivio*** dati, Segmentazione ****** pubblico e ***Attiva targeting per canali*** in un progetto AEM Screens.

Per informazioni dettagliate, consultate [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) .

## Flusso di base {#basic-flow}

Seguire i passaggi indicati di seguito per implementare il caso d’uso di attivazione della temperatura locale del centro viaggi:

1. **Compilazione dei fogli di Google**

   1. Passare al foglio di Google ContextHubDemo.
   1. Aggiungete una colonna con **Titolo1** con il valore corrispondente per la temperatura.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Andate ai segmenti del pubblico (fate riferimento al ***Passaggio 2: Impostazione della segmentazione*** dell'audience nella pagina **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Selezionare i **fogli A1 1** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/0** dall'elenco a discesa in Nome **proprietà**

   1. Selezionare l' **operatore** come **maggiore o uguale a **dal menu a discesa

   1. Immettere il **valore** come **50**

   1. Analogamente, selezionare i Fogli** A1 2 **e fare clic su **Modifica**.

   1. Selezionate la proprietà **Confronto - Valore** e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/0** dall'elenco a discesa in Nome **proprietà**

   1. Selezionare l' **operatore** come **less-than **dal menu a discesa

   1. Immettere il **valore** come **50**

1. Spostatevi e selezionate il canale (), quindi fate clic su **Modifica** nella barra delle azioni. Nell'esempio seguente, **DataDrivenWeather**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il canale deve già avere un'immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Avreste dovuto configurare le vostre **configurazioniContextHub** **configurando** il canale **Proprietà** —&gt; scheda **Personalizzazione** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selezionate **Targeting** dall'editor, selezionate **Marchio** e **Attività** dal menu a discesa, quindi fate clic su **Avvia targeting**.

   ![new_activity3](assets/new_activity3.gif)

1. **Verifica dell’anteprima**

   1. Fate clic su **Anteprima.** Inoltre, aprite il foglio di Google e aggiornate il relativo valore.
   1. Modificate il valore impostando un valore inferiore a 50, dovreste essere in grado di visualizzare l'immagine delle bevande estive. Se il valore in Google Sheet è 50 o maggiore di quanto dovrebbe essere in grado di visualizzare l'immagine di una bevanda calda.
   ![result3](assets/result3.gif)

