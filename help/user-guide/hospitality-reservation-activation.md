---
title: Attivazione prenotazione ospitalità
seo-title: Attivazione prenotazione ospitalità
description: Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti in Google Sheets.
seo-description: Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# Attivazione prenotazione ospitalità {#hospitality-reservation-activation}

Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti in Google Sheets.

## Descrizione {#description}

Per questo caso d&#39;uso, Google Sheet è popolato con percentuale di prenotazione su due ristoranti **Ristorante1** e **Ristorante2**. Una formula viene applicata in base ai valori di Ristorante1 e Ristorante2 e in base alla formula, il valore 1 o 2 è assegnato alla colonna **AdTarget**.

Se il valore di **Ristorante1** > **Ristorante2**, **AdTaget** viene assegnato il valore **1** altrimenti **AdTarget** viene assegnato il valore **2**. Il valore 1 genera l&#39;opzione *Bistecca food* e il valore 2 visualizza l&#39;opzione *Thai food* sullo schermo del display.

## Precondizioni {#preconditions}

Prima di iniziare ad implementare l&#39;attivazione della prenotazione, è necessario apprendere come impostare ***Data Store***, ***Audience Segmentation*** e ***Enable Targeting for Channels*** in un progetto AEM Screens .

Per informazioni dettagliate, fare riferimento a [Configurazione di ContextHub in  AEM Screens](configuring-context-hub.md).

## Flusso di base {#basic-flow}

Segui i passaggi indicati di seguito per implementare il caso di attivazione della prenotazione di ospitalità per il tuo progetto AEM Screens :

1. **Compilazione dei fogli di Google e aggiunta della formula.**

   Ad esempio, applicare la formula alla terza colonna **AdTarget**, come illustrato nella figura seguente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Andate ai segmenti del pubblico (fate riferimento a ***Passaggio 2: Impostazione della segmentazione dell&#39;audience*** in **[Configurazione di ContextHub  pagina AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Selezionare il **Fogli A1 1** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/2** dall&#39;elenco a discesa in **Nome proprietà**

   1. Selezionare **Operatore** come **uguale** dal menu a discesa

   1. Immettere **Value** come **1**

   1. Analogamente, selezionare le **Fogli A1 2** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull&#39;icona di configurazione per modificare le proprietà.
   1. Selezionare **googlesheets/value/1/2** dall&#39;elenco a discesa in **Nome proprietà**

   1. Selezionare **Operatore** come **2**

1. Navigare e selezionare il canale () e fare clic su **Modifica** dalla barra delle azioni. Nell&#39;esempio seguente, **DataDrivenRestaurant**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il canale deve già avere un&#39;immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configuring ContextHub in  AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >È necessario impostare la scheda **ContextHub** **Configurations** utilizzando il canale **Properties** —> **Personalization**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selezionare **Targeting** dall&#39;editor e selezionare **Brand** e **Activity** dal menu a discesa, quindi fare clic su **Avvia targeting**.
1. **Verifica dell’anteprima**

   1. Fare clic su **Anteprima.** Inoltre, aprite i vostri Google Sheets e aggiornate il relativo valore.
   1. Aggiornare il valore nelle colonne **Ristorante1** e **Ristorante2**. Se **Ristorante1** > **Ristorante2,** è necessario essere in grado di visualizzare un&#39;immagine di *Bistecca* cibo, altrimenti sullo schermo viene visualizzata l&#39;immagine relativa al cibo *Thai*.

   ![result5](assets/result5.gif)

