---
title: Attivazione temperatura centro di viaggio
seo-title: Travel Center Temperature Activation
description: Il seguente caso d’uso illustra l’utilizzo dell’attivazione della temperatura locale del centro di viaggio in base ai valori inseriti nei fogli di Google.
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Attivazione temperatura centro di viaggio {#travel-center-temperature-activation}

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della temperatura locale del centro di viaggio in base ai valori inseriti nei fogli di Google.

## Descrizione {#description}

Per questo caso d’uso, se il valore dei fogli di Google è inferiore a 50, viene visualizzata un’immagine con bevande calde e, se il valore è maggiore o uguale a 50, viene visualizzata l’immagine con bevande fredde. Se è presente un altro valore o non è presente alcun valore, verrà visualizzata un’immagine predefinita.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l’attivazione della temperatura locale del centro di viaggio, è necessario imparare a impostare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per i canali*** in un progetto AEM Screens.

Fai riferimento a [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) per informazioni dettagliate.

## Flusso di base {#basic-flow}

Per implementare il caso d’uso di attivazione della temperatura locale del Travel Center, segui i passaggi seguenti:

1. **Compilazione dei fogli di Google**

   1. Passa al foglio Google ContextHubDemo.
   1. Aggiungi una colonna con **Intestazione1** con valore corrispondente per la temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (consulta la sezione ***Passaggio 2: impostazione della segmentazione del pubblico*** in **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Seleziona la **Fogli A1 1** e fai clic su **Modifica**.

   1. Seleziona la proprietà di confronto e fai clic sull’icona di configurazione per modificarne le proprietà.
   1. Seleziona **googlesheets/value/1/0** dall’elenco a discesa in **Nome proprietà**

   1. Seleziona la **Operatore** as **maggiore di o uguale a** dal menu a discesa

   1. Inserisci il **Valore** as **50**

   1. Analogamente, selezionare **Fogli A1 2** e fai clic su **Modifica**.

   1. Seleziona la **Proprietà Comparison - Valore** e fai clic sull’icona configura per modificare le proprietà.
   1. Seleziona **googlesheets/value/1/0** dall’elenco a discesa in **Nome proprietà**

   1. Seleziona la **Operatore** as **less-than** dal menu a discesa

   1. Inserisci il **Valore** as **50**

1. Naviga e seleziona il canale () e fai clic su **Modifica** dalla barra delle azioni. Nell&#39;esempio seguente, **DataDrivenWeather**, per mostrare la funzionalità viene utilizzato un canale sequenziale.

   >[!NOTE]
   >
   >Il canale deve già avere un’immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Avresti dovuto impostare il tuo **ContextHub** **Configurazioni** utilizzo del canale **Proprietà** —> **Personalizzazione** scheda.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Seleziona **Targeting** dall’editor e seleziona **Marchio** e **Attività** dal menu a discesa e fai clic su **Inizia impostazione destinazione**.

   ![new_activity3](assets/new_activity3.gif)

1. **Controllo dell’anteprima**

   1. Clic **Anteprima.** Inoltre, aprire Google Sheet e aggiornarne il valore.
   1. Cambia il valore a meno di 50, dovresti essere in grado di visualizzare l&#39;immagine di una bevanda estiva. Se il valore nel foglio Google è 50 o maggiore di quanto dovrebbe essere in grado di visualizzare l&#39;immagine di una bevanda calda.
   ![result3](assets/result3.gif)
