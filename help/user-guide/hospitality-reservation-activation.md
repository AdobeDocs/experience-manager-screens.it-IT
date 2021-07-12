---
title: Attivazione prenotazione alberghiera
seo-title: Attivazione prenotazione alberghiera
description: Il seguente caso d’uso illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori popolati in Google Sheets.
seo-description: Il seguente caso d’uso illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori popolati in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Creazione di esperienze in Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# Attivazione prenotazione alberghiera {#hospitality-reservation-activation}

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori popolati in Google Sheets.

## Descrizione {#description}

Per questo caso d&#39;uso, Google Sheet è popolato con percentuale di prenotazione su due ristoranti **Ristorante1** e **Ristorante2**. Una formula viene applicata in base ai valori di Ristorante1 e Ristorante2 e in base alla formula, il valore 1 o 2 viene assegnato alla colonna **AdTarget**.

Se il valore di **Ristorante1** > **Ristorante2**, a **AdTarget** viene assegnato il valore **1** altrimenti **AdTarget** viene assegnato il valore **2**. Il valore 1 genera l&#39;opzione *Bistecca food* e il valore 2 visualizza l&#39;opzione *Thai food* sullo schermo del display.

## Condizioni preliminari {#preconditions}

Prima di iniziare a implementare l&#39;attivazione della prenotazione, devi imparare a configurare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per canali*** in un progetto AEM Screens.

Per informazioni dettagliate, consulta [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) .

## Flusso di base {#basic-flow}

Per implementare il caso d’uso per l’attivazione della prenotazione di un’ospitalità per il progetto AEM Screens, effettua le seguenti operazioni:

1. **Popolare i fogli di Google e aggiungere la formula.**

   Ad esempio, applica la formula alla terza colonna **AdTarget**, come illustrato nella figura seguente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (fai riferimento a ***Passaggio 2: Impostazione della segmentazione del pubblico*** nella pagina **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Selezionare i **Fogli A1 1** e fare clic su **Modifica**.

   1. Seleziona la proprietà di confronto e fai clic sull’icona di configurazione per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/2** dal menu a discesa in **Nome proprietà**

   1. Seleziona **Operatore** come **uguale** dal menu a discesa

   1. Inserisci **Valore** come **1**

   1. Allo stesso modo, selezionare i **Fogli A1 2** e fare clic su **Modifica**.

   1. Seleziona la proprietà di confronto e fai clic sull’icona di configurazione per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/2** dal menu a discesa in **Nome proprietà**

   1. Seleziona **Operatore** come **2**

1. Naviga e seleziona il canale () e fai clic su **Modifica** nella barra delle azioni. Nell&#39;esempio seguente, **DataDrivenRestaurant**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il canale deve già disporre di un&#39;immagine predefinita e i tipi di pubblico devono essere preconfigurati come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Dovresti aver impostato la scheda **ContextHub** **Configurazioni** utilizzando il canale **Proprietà** —> **Personalizzazione**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleziona **Targeting** dall’editor e seleziona **Marchio** e **Attività** dal menu a discesa, quindi fai clic su **Avvia targeting**.
1. **Controllo dell’anteprima**

   1. Fare clic su **Anteprima.** Inoltre, apri i tuoi Google Sheets e ne aggiorna il valore.
   1. Aggiorna il valore nelle colonne **Ristorante1** e **Ristorante2** . Se **Ristorante1** > **Ristorante2,** si deve essere in grado di visualizzare un&#39;immagine di *Bistecca* cibo altrimenti, sullo schermo viene visualizzata l&#39;immagine del cibo *Thai*.
   ![risultato5](assets/result5.gif)
