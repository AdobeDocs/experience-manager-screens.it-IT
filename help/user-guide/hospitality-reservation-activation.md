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

---


# Attivazione prenotazione ospitalità {#hospitality-reservation-activation}

Il seguente caso di utilizzo illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti in Google Sheets.

## Descrizione {#description}

Per questo caso d'uso, Google Sheet è popolato con percentuale di prenotazione su due ristoranti **Ristorante1** e **Ristorante2**. Una formula viene applicata in base ai valori di Restaurant1 e Restaurant2 e in base alla formula, il valore 1 o 2 viene assegnato alla colonna **AdTarget** .

Se il valore di **Restaurant1** &gt; **Restaurant2**, **AdTaget** viene assegnato al valore **1** , altrimenti **AdTarget** viene assegnato il valore seguente: **** AdTarget2. Il valore 1 genera l'opzione *Bistecca food* e il valore 2 mostra l'opzione *Thai food* sullo schermo.

## Premesse {#preconditions}

Prima di iniziare ad implementare l'attivazione della prenotazione, devi imparare a configurare ***Archivio*** dati, Segmentazione ****** pubblico e ***Abilitare il targeting per canali*** in un progetto AEM Screens.

Per informazioni dettagliate, consultate [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) .

## Flusso di base {#basic-flow}

Segui i passaggi indicati di seguito per implementare il caso d’uso per l’attivazione della prenotazione di ospitalità per il progetto AEM Screens:

1. **Compilazione dei fogli di Google e aggiunta della formula.**

   Ad esempio, applicare la formula alla terza colonna **AdTarget**, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Andate ai segmenti del pubblico (fate riferimento al ***Passaggio 2: Impostazione della segmentazione*** dell'audience nella pagina **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Selezionare i **fogli A1 1** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionate **googlesheets/value/1/2** dall’elenco a discesa in Nome **proprietà**

   1. Selezionate **Operatore** come **uguale** dal menu a discesa

   1. Immettere il **valore** come **1**

   1. Analogamente, selezionare i **fogli A1 2** e fare clic su **Modifica**.

   1. Selezionate la proprietà di confronto e fate clic sull'icona di configurazione per modificare le proprietà.
   1. Selezionate **googlesheets/value/1/2** dall’elenco a discesa in Nome **proprietà**

   1. Selezionare l' **operatore** come **2**

1. Spostatevi e selezionate il canale (), quindi fate clic su **Modifica** nella barra delle azioni. Nell'esempio seguente, **DataDrivenRestaurant**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il canale deve già avere un'immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Avreste dovuto configurare le vostre **configurazioniContextHub** **configurando** il canale **Proprietà** —&gt; scheda **Personalizzazione** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selezionate **Targeting** dall'editor, selezionate **Marchio** e **Attività** dal menu a discesa, quindi fate clic su **Avvia targeting**.
1. **Verifica dell’anteprima**

   1. Fate clic su **Anteprima.** Inoltre, aprite i vostri Google Sheets e aggiornate il relativo valore.
   1. Aggiornare il valore nelle colonne **Ristorante1** e **Ristorante2** . Se **Ristorante1** &gt; **Ristorante2,** dovreste essere in grado di visualizzare un'immagine di *Bistecca* cibo altrimenti, *Thai* food immagine viene visualizzata sul vostro schermo.
   ![result5](assets/result5.gif)

