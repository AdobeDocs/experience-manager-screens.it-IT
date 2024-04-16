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
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Attivazione temperatura centro di viaggio {#travel-center-temperature-activation}

Il seguente caso d’uso illustra l’utilizzo dell’attivazione della temperatura locale del centro di viaggio in base ai valori inseriti nei fogli di Google.

## Descrizione {#description}

Per questo caso d’uso, se il valore in Google Sheets è inferiore a 50, viene visualizzata un’immagine con bevande calde. Se il valore è maggiore o uguale a 50, viene visualizzata un’immagine con bevande fredde. Se è presente un altro valore o non è presente alcun valore, il lettore visualizza un’immagine predefinita.

## Precondizioni {#preconditions}

Prima di iniziare a implementare l’attivazione della temperatura locale del centro di viaggio, scopri come impostare ***Archivio dati***, ***Segmentazione del pubblico*** e ***Abilita targeting per i canali*** in un progetto AEM Screens.

Consulta [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md) per informazioni dettagliate.

## Flusso di base {#basic-flow}

Per implementare il caso d’uso di attivazione della temperatura locale del Travel Center, segui i passaggi seguenti:

1. **Compilazione dei fogli di Google**

   1. Passa al foglio Google ContextHubDemo.
   1. Aggiungi una colonna con **`Heading1`** con valore corrispondente per la temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurazione dei segmenti in Audiences in base ai requisiti**

   1. Passa ai segmenti del pubblico (consulta ***Passaggio 2: impostazione della segmentazione del pubblico*** in **[Configurazione di ContextHub in AEM Screens](configuring-context-hub.md)** per ulteriori dettagli).

   1. Fai clic su **Fogli A1 1** e fai clic su **Modifica**.

   1. Fai clic sulla proprietà di confronto e fai clic sull&#39;icona di configurazione.
   1. Clic **googlesheets/value/1/0** dall’elenco a discesa in **Nome proprietà**

   1. Fai clic su **Operatore** as **maggiore di o uguale a** dal menu a discesa

   1. Inserisci il **Valore** as **50**

   1. Allo stesso modo, seleziona la **Fogli A1 2** e fai clic su **Modifica**.

   1. Fai clic su **Proprietà Comparison - Valore** e seleziona l’icona di configurazione.
   1. Clic **googlesheets/value/1/0** dall’elenco a discesa in **Nome proprietà**

   1. Fai clic su **Operatore** as **less-than** dal menu a discesa

   1. Inserisci il **Valore** as **50**

1. Naviga e seleziona il canale () e fai clic su **Modifica** dalla barra delle azioni. Nell&#39;esempio seguente, **DataDrivenWeather**, per mostrare la funzionalità viene utilizzato un canale sequenziale.

   >[!NOTE]
   >
   >Il canale deve già avere un’immagine predefinita e il pubblico deve essere preconfigurato come descritto in [Configurazione di ContextHub in AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Avresti dovuto impostare il tuo **ContextHub** **Configurazioni** utilizzo del canale **Proprietà** > **Personalizzazione** scheda.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Clic **Targeting** dall’editor e fai clic su **Marchio** e **Attività** dal menu a discesa e fai clic su **Inizia impostazione destinazione**.

   ![new_activity3](assets/new_activity3.gif)

1. **Controllo dell’anteprima**

   1. Clic **Anteprima.** Inoltre, aprire Google Sheet e aggiornarne il valore.
   1. Modifica il valore in meno di 50. Dovreste essere in grado di vedere l&#39;immagine di una bevanda fredda. Se il valore in Google Sheets è uguale o superiore a 50, dovrebbe essere visualizzata l&#39;immagine di una bevanda calda.

   ![risultato3](assets/result3.gif)
