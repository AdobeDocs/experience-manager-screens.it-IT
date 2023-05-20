---
title: Attivazione prenotazione ospitalità
seo-title: Hospitality Reservation Activation
description: Il seguente caso d’uso illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti nei fogli Google.
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Attivazione prenotazione ospitalità {#hospitality-reservation-activation}

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della prenotazione ospedaliera in base ai valori inseriti nei fogli Google.

## Descrizione {#description}

Per questo caso d’uso, il foglio di Google viene compilato con la percentuale di prenotazione su due ristoranti **Ristorante1** e **Ristorante2**. Viene applicata una formula basata sui valori di Restaurant1 e Restaurant2 e sulla formula viene assegnato il valore 1 o 2 alla **AdTarget** Colonna.

Se il valore di **Ristorante1** > **Ristorante2**, quindi **AdTarget** è un valore assegnato **1** altrimenti **AdTarget** è un valore assegnato **2**. Il valore 1 genera *Bistecca* opzione e Valore 2 determina la visualizzazione di *Cibo thailandese* sullo schermo.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l’attivazione della prenotazione, devi imparare a impostare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per i canali*** in un progetto AEM Screens.

Fai riferimento a [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) per informazioni dettagliate.

## Flusso di base {#basic-flow}

Segui i passaggi seguenti per implementare il caso di utilizzo dell’attivazione della prenotazione dell’ospitalità per il tuo progetto AEM Screens:

1. **Compilazione dei fogli di Google e aggiunta della formula.**

   Applicare ad esempio la formula alla terza colonna **AdTarget**, come illustrato nella figura seguente.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (consulta la sezione ***Passaggio 2: impostazione della segmentazione del pubblico*** in **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Seleziona la **Fogli A1 1** e fai clic su **Modifica**.

   1. Seleziona la proprietà di confronto e fai clic sull’icona di configurazione per modificarne le proprietà.
   1. Seleziona **googlesheets/value/1/2** dall’elenco a discesa in **Nome proprietà**

   1. Seleziona la **Operatore** as **uguale** dal menu a discesa

   1. Inserisci il **Valore** as **1**

   1. Analogamente, selezionare **Fogli A1 2** e fai clic su **Modifica**.

   1. Seleziona la proprietà di confronto e fai clic sull’icona di configurazione per modificarne le proprietà.
   1. Seleziona **googlesheets/value/1/2** dall’elenco a discesa in **Nome proprietà**

   1. Seleziona la **Operatore** as **2**

1. Naviga e seleziona il canale () e fai clic su **Modifica** dalla barra delle azioni. Nell&#39;esempio seguente, **DataDrivenRestaurant**, per mostrare la funzionalità viene utilizzato un canale sequenziale.

   >[!NOTE]
   >
   >Il canale deve già avere un’immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Avresti dovuto impostare il tuo **ContextHub** **Configurazioni** utilizzo del canale **Proprietà** —> **Personalizzazione** scheda.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleziona **Targeting** dall’editor e seleziona **Marchio** e **Attività** dal menu a discesa e fai clic su **Inizia impostazione destinazione**.
1. **Controllo dell’anteprima**

   1. Clic **Anteprima.** Inoltre, apri i fogli Google e aggiornane il valore.
   1. Aggiornare il valore in **Ristorante1** e **Ristorante2** colonne. Se **Ristorante1** > **Ristorante2,** dovrebbe essere possibile visualizzare un&#39;immagine di *Bistecca* altri prodotti alimentari, *Thailandese* l’immagine del cibo viene visualizzata sullo schermo.
   ![result5](assets/result5.gif)
