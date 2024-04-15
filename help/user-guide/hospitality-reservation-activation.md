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
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Attivazione prenotazione ospitalità {#hospitality-reservation-activation}

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti nei fogli Google.

## Descrizione {#description}

Per questo caso d’uso, il foglio Google viene compilato con la percentuale di prenotazioni su due ristoranti **`Restaurant1`** e **`Restaurant2`**. Viene applicata una formula in base ai valori di `Restaurant1` e `Restaurant2` e in base alla formula, il valore 1 o 2 è assegnato al **AdTarget** Colonna.

Se il valore di **`Restaurant1`** > **`Restaurant2`**, quindi **AdTarget** è un valore assegnato **1** altrimenti **AdTarget** è un valore assegnato **2**. Il valore 1 genera *Bistecca* opzione e Valore due determina la visualizzazione di *Cibo thailandese* sullo schermo.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l’attivazione della prenotazione, scopri come impostare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per i canali*** in un progetto AEM Screens.

Consulta [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) per informazioni dettagliate.

## Flusso di base {#basic-flow}

Segui i passaggi del caso d’uso seguenti per implementare l’attivazione della prenotazione dell’ospitalità per il tuo progetto AEM Screens:

1. **Compilazione dei fogli di Google e aggiunta della formula**.

   Applicare ad esempio la formula alla terza colonna **AdTarget**, come illustrato nella figura seguente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (consulta ***Passaggio 2: impostazione della segmentazione del pubblico*** in **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).
   1. Seleziona la **Fogli A1 1** e fai clic su **Modifica**.
   1. Seleziona la proprietà di confronto e fai clic su **Configurazione** icona.
   1. Seleziona **googlesheets/value/1/2** dall’elenco a discesa in **Nome proprietà**.
   1. Seleziona la **Operatore** as **uguale** dal menu a discesa.
   1. Inserisci il **Valore** as **1**.
   1. Analogamente, selezionare **Fogli A1 2** e fai clic su **Modifica**.
   1. Seleziona la proprietà di confronto e fai clic su **Configurazione** icona.
   1. Seleziona **googlesheets/value/1/2** dall’elenco a discesa in **Nome proprietà**.
   1. Seleziona la **Operatore** as **2**.

1. Naviga e seleziona il canale () e fai clic su **Modifica** dalla barra delle azioni. Nell&#39;esempio seguente, **DataDrivenRestaurant**, per mostrare la funzionalità viene utilizzato un canale sequenziale.

   >[!NOTE]
   >
   >Il canale deve già avere un’immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Avresti dovuto impostare il tuo **ContextHub** **Configurazioni** utilizzo del canale **Proprietà** > **Personalizzazione** scheda.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleziona **Targeting** dall’editor e seleziona **Marchio** e **Attività** dal menu a discesa e fai clic su **Inizia impostazione destinazione**.
1. **Controllo dell’anteprima**

   1. Clic **Anteprima.** Inoltre, apri i fogli Google e aggiornane il valore.
   1. Aggiornare il valore in **`Restaurant1`** e **`Restaurant2`** colonne. Se **`Restaurant1`** > **`Restaurant2`,** dovrebbe essere possibile visualizzare un&#39;immagine di *Bistecca* altri prodotti alimentari, *Thailandese* l’immagine del cibo viene visualizzata sullo schermo.

   ![risultato5](assets/result5.gif)
