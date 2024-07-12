---
title: Attivazione prenotazione ospitalità
description: Scopri come questo caso d’uso illustra l’utilizzo dell’attivazione della prenotazione dell’ospitalità in base ai valori inseriti nei fogli di Google.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Attivazione prenotazione ospitalità {#hospitality-reservation-activation}

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti nei fogli Google.

## Descrizione {#description}

Per questo caso d&#39;uso, il foglio Google viene compilato con la percentuale di prenotazioni su due ristoranti **`Restaurant1`** e **`Restaurant2`**. Viene applicata una formula basata sui valori di `Restaurant1` e `Restaurant2` e, in base alla formula, il valore 1 o 2 viene assegnato alla colonna **AdTarget**.

Se il valore di **`Restaurant1`** > **`Restaurant2`**, a **AdTarget** viene assegnato il valore **1**, altrimenti a **AdTarget** viene assegnato il valore **2**. Il valore 1 genera un&#39;opzione *Bistecca da mangiare* e il valore 2 genera una visualizzazione dell&#39;opzione *Cibo thailandese* sullo schermo.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l&#39;attivazione della prenotazione, scopri come impostare ***Archivio dati***, ***Segmentazione pubblico*** e ***Abilita targeting per canali*** in un progetto AEM Screens.

Per informazioni dettagliate, vedere [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

## Flusso di base {#basic-flow}

Segui i passaggi del caso d’uso seguenti per implementare l’attivazione della prenotazione dell’ospitalità per il tuo progetto AEM Screens:

1. **Compilazione dei fogli di Google e aggiunta della formula**.

   Applicare ad esempio la formula alla terza colonna **AdTarget**, come illustrato nella figura seguente.

   ![schermata_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (consulta ***Passaggio 2: impostazione della segmentazione del pubblico*** in **[configurazione di ContextHub nella pagina AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).
   1. Fare clic sui **fogli A1 1** e fare clic su **Modifica**.
   1. Fare clic sulla proprietà di confronto e sull&#39;icona **Configurazione**.
   1. Fare clic su **googlesheets/value/1/2** dal menu a discesa in **Nome proprietà**.
   1. Fare clic su **Operatore** come **uguale** dal menu a discesa.
   1. Immetti **Valore** come **1**.
   1. Analogamente, fare clic su **Fogli A1 2** e fare clic su **Modifica**.
   1. Fare clic sulla proprietà di confronto e sull&#39;icona **Configurazione**.
   1. Fare clic su **googlesheets/value/1/2** dal menu a discesa in **Nome proprietà**.
   1. Fare clic sull&#39;**operatore** come **2**.

1. Passa al tuo canale () e fai clic su **Modifica** nella barra delle azioni. Nell&#39;esempio seguente, **DataDrivenRestaurant**, viene utilizzato un canale sequenziale per mostrare la funzionalità.

   >[!NOTE]
   >
   >Il tuo canale deve già avere un&#39;immagine predefinita e i tipi di pubblico devono essere preconfigurati come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![schermata_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >A questo punto, le **Configurazioni** di **ContextHub** che utilizzano la scheda **Proprietà** > **Personalization** del canale dovrebbero essere già state configurate.

   ![schermata_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Fai clic su **Targeting** dall&#39;editor, quindi fai clic su **Brand** e **Activity** dal menu a discesa, quindi fai clic su **Start Targeting**.
1. **Controllo dell&#39;anteprima**

   1. Fare clic su **Anteprima.** Aprire inoltre i fogli Google e aggiornarne il valore.
   1. Aggiornare il valore in **`Restaurant1`** e **`Restaurant2`** colonne. Se **`Restaurant1`** > **`Restaurant2`,** dovresti essere in grado di visualizzare un&#39;immagine di *Bistecca* cibo altrimenti, *Thai* immagine cibo viene visualizzata sullo schermo.

   ![risultato5](assets/result5.gif)
