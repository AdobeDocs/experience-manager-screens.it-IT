---
title: Attivazione temperatura centro di viaggio
description: Utilizzando AEM Screens, scopri come questo caso d’uso dimostra l’utilizzo dell’attivazione della temperatura locale del centro di viaggio in base ai valori inseriti nei fogli Google.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
TQID: https://experienceleague.adobe.com/C8FAKzAKUjdochkR96MShKiu2Ig-g-9BDnoX09g4xnM
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
source-wordcount: 500
ht-degree: 0%

---

# Attivazione temperatura centro di viaggio {#travel-center-temperature-activation}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della temperatura locale del centro di viaggio in base ai valori inseriti nei fogli di Google.

## Descrizione {#description}

Per questo caso d’uso, se il valore in Google Sheets è inferiore a 50, viene visualizzata un’immagine con bevande calde. Se il valore è maggiore o uguale a 50, viene visualizzata un’immagine con bevande fredde. Se è presente un altro valore o non è presente alcun valore, il lettore visualizza un’immagine predefinita.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l&#39;attivazione della temperatura locale del centro viaggi, scopri come impostare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per canali*** in un progetto AEM Screens.

Per informazioni dettagliate, vedere [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

## Flusso di base {#basic-flow}

Per implementare il caso d’uso di attivazione della temperatura locale del Travel Center, segui i passaggi seguenti:

1. **Compilazione dei fogli di Google**

   1. Passa al foglio Google ContextHubDemo.
   1. Aggiungi una colonna con **`Heading1`** con il valore di temperatura corrispondente.

   ![schermata_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (consulta ***Passaggio 2: impostazione della segmentazione del pubblico*** in **[configurazione di ContextHub nella pagina AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Fare clic sui **fogli A1 1** e fare clic su **Modifica**.

   1. Fai clic sulla proprietà di confronto e fai clic sull&#39;icona di configurazione.
   1. Fai clic su **googlesheets/value/1/0** dal menu a discesa in **Nome proprietà**

   1. Fai clic su **Operatore** come **maggiore o uguale** dal menu a discesa

   1. Immetti **Valore** come **50**

   1. Analogamente, selezionare i **fogli A1 2** e fare clic su **Modifica**.

   1. Fare clic su **Proprietà confronto - Valore** e selezionare l&#39;icona di configurazione.
   1. Fai clic su **googlesheets/value/1/0** dal menu a discesa in **Nome proprietà**

   1. Fai clic su **Operatore** come **minore di** dal menu a discesa

   1. Immetti **Valore** come **50**

1. Naviga e seleziona il tuo canale () e fai clic su **Modifica** nella barra delle azioni. Nell&#39;esempio seguente, **DataDrivenWeather**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il tuo canale deve già avere un&#39;immagine predefinita e i tipi di pubblico devono essere preconfigurati come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![schermata_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >**ContextHub** **Configurazioni** tramite la scheda **Proprietà** > **Personalization** del canale devono essere già configurate.

   ![schermata_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Fai clic su **Targeting** dall&#39;editor, quindi fai clic su **Brand** e **Activity** dal menu a discesa, quindi fai clic su **Start Targeting**.

   ![nuova_attività3](assets/new_activity3.gif)

1. **Controllo dell&#39;anteprima**

   1. Fare clic su **Anteprima.** Inoltre, aprire Google Sheet e aggiornarne il valore.
   1. Modifica il valore in meno di 50. Si può vedere l&#39;immagine di una bevanda fredda. Se il valore in Google Sheets è uguale o superiore a 50, dovrebbe essere visualizzata l&#39;immagine di una bevanda calda.

   ![risultato3](assets/result3.gif)

