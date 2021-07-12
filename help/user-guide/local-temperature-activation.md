---
title: Attivazione temperatura centro viaggi
seo-title: Attivazione temperatura centro viaggi
description: Il seguente caso d’uso illustra l’utilizzo dell’attivazione della temperatura locale del centro viaggi in base ai valori popolati in Google Sheets.
seo-description: Il seguente caso d’uso illustra l’utilizzo dell’attivazione della temperatura locale del centro viaggi in base ai valori popolati in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Creazione di esperienze in Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Attivazione temperatura centro viaggi {#travel-center-temperature-activation}

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della temperatura locale del centro viaggi in base ai valori popolati in Google Sheets.

## Descrizione {#description}

Per questo caso d&#39;uso, se il tuo Google Sheets ha Valore inferiore a 50, verrà visualizzata un&#39;immagine con bevande calde e se il valore è maggiore o uguale a 50, verrà visualizzata l&#39;immagine con bevande fredde. In caso di altri valori o nessun valore, il lettore visualizzerà un&#39;immagine predefinita.

## Condizioni preliminari {#preconditions}

Prima di iniziare a implementare l&#39;attivazione della temperatura locale del centro viaggi, devi imparare a configurare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per canali*** in un progetto AEM Screens.

Per informazioni dettagliate, consulta [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) .

## Flusso di base {#basic-flow}

Segui i passaggi seguenti per implementare il caso d’uso di Attivazione temperatura locale del Centro viaggi:

1. **Popolamento dei fogli di Google**

   1. Passa al foglio di Google ContextHubDemo.
   1. Aggiungi una colonna con **Intestazione1** con il valore corrispondente per la temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (fai riferimento a ***Passaggio 2: Impostazione della segmentazione del pubblico*** nella pagina **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Selezionare i **Fogli A1 1** e fare clic su **Modifica**.

   1. Seleziona la proprietà di confronto e fai clic sull’icona di configurazione per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/0** dal menu a discesa in **Nome proprietà**

   1. Seleziona **Operatore** come **maggiore o uguale a** dal menu a discesa

   1. Inserisci il **Valore** come **50**

   1. Allo stesso modo, selezionare i **Fogli A1 2** e fare clic su **Modifica**.

   1. Seleziona la **Proprietà di confronto - Valore** e fai clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/0** dal menu a discesa in **Nome proprietà**

   1. Seleziona **Operatore** come **minore di** dal menu a discesa

   1. Inserisci il **Valore** come **50**

1. Naviga e seleziona il canale () e fai clic su **Modifica** nella barra delle azioni. Nell&#39;esempio seguente, **DataDrivenWeather**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il canale deve già disporre di un&#39;immagine predefinita e i tipi di pubblico devono essere preconfigurati come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Dovresti aver impostato la scheda **ContextHub** **Configurazioni** utilizzando il canale **Proprietà** —> **Personalizzazione**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleziona **Targeting** dall’editor e seleziona **Marchio** e **Attività** dal menu a discesa, quindi fai clic su **Avvia targeting**.

   ![new_activity3](assets/new_activity3.gif)

1. **Controllo dell’anteprima**

   1. Fare clic su **Anteprima.** Inoltre, apri il tuo foglio di Google e aggiorna il suo valore.
   1. Cambia il valore a meno di 50, dovresti essere in grado di visualizzare l&#39;immagine delle bevande estive. Se il valore nel Google Sheet è 50 o superiore a dovrebbe essere in grado di visualizzare l&#39;immagine di una bevanda calda.
   ![result3](assets/result3.gif)
