---
title: Riconoscimento vocale in  AEM Screens
description: La pagina descrive la funzione di riconoscimento vocale in  AEM Screens.
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---


# Riconoscimento vocale in  AEM Screens {#voice-recognition}

## Panoramica {#overview}

La funzione di riconoscimento vocale consente di modificare i contenuti in un canale  AEM Screens, basato sull&#39;interazione vocale.

Un autore del contenuto può configurare una visualizzazione in modo che sia attivata per la voce. Questo permette a tutti i giocatori registrati contro il display di capire il discorso. È necessario abilitare il riconoscimento vocale per il display e associare ogni canale a un tag univoco per attivare una transizione di canale.

>[!NOTE]
>L&#39;hardware del lettore deve supportare l&#39;ingresso vocale, ad esempio un microfono.

>[!IMPORTANT]
> La funzione di riconoscimento vocale è disponibile solo sui lettori Chrome e Electron.

## Implementazione del riconoscimento vocale {#implementing}

La sezione seguente descrive come attivare e usare la funzione di riconoscimento vocale in un progetto AEM Screens .

### Impostazione del progetto {#setting-up}

Prima di utilizzare la funzione di riconoscimento vocale, accertatevi di disporre di un progetto e di un canale con il contenuto impostato per il progetto.

1. L&#39;esempio seguente mostra un progetto demo denominato **VoiceDemo** e tre canali di sequenza **Main**, **ColdDrinks** e **HotDrinks**, come illustrato nella figura riportata di seguito.

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuti a un canale, consulta [Creazione e gestione di canali](/help/user-guide/managing-channels.md)

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, accedete a **VoiceDemo** —> **Canali** —> **Principale** e selezionate il canale. Fate clic su **Modifica** nella barra delle azioni per aprire l&#39;editor e aggiungere contenuti (immagini/video) in base alle vostre esigenze. Allo stesso modo, aggiungete contenuto sia a **ColdDrinks** che al canale **HotDrinks** .

   I canali ora contengono il contenuto seguente, come mostrato nelle figure seguenti.

   **Principale**:

   **ColdDrinks**:

   **HotDrinks**:

### Impostazione dei tag per i canali {#setting-tags}

Una volta aggiunto il contenuto ai canali, è necessario navigare fino a ciascuno dei canali e aggiungere tag appropriati per attivare il riconoscimento vocale.

Per aggiungere tag al canale, effettuate le operazioni seguenti:

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, accedete a **VoiceDemo** —> **Canali** —> **Principale** e selezionate il canale.

1. Click **Properties** from the action bar.

1. Passate alla scheda **Nozioni di base** e selezionate un tag già esistente dal campo **Tag** oppure createne uno nuovo.

1. Al termine, fate clic su **Salva e chiudi** .


### Assegnazione di un canale a uno schermo {#channel-assignment}

1. Create una visualizzazione nella cartella **Locations (Posizioni)** , come illustrato nella figura riportata di seguito.

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di schermi](/help/user-guide/managing-displays.md).

1. Assegnare i canali **Main**, **ColdDrinks** e **HotDrinks** al **LobbyDisplay**.


1. Impostate le seguenti proprietà su ciascun canale.

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di schermi](/help/user-guide/managing-displays.md).

1. Dopo aver assegnato i canali a uno schermo, andate alla **LobbyDisplay** e selezionate lo schermo. Selezionate **Proprietà** dalla barra delle azioni.

1. Passate alla scheda **Visualizza** e abilitate l&#39;opzione **Attiva** voce in **Contenuto**.

   >[!NOTE]
   >È obbligatorio attivare la funzione di riconoscimento vocale dal display.

## Visualizzazione del contenuto in Chrome Player {#viewing-content}

Una volta completati i passaggi precedenti, è possibile registrare il dispositivo chrome e visualizzare l&#39;output.

Effettua le seguenti operazioni:

1. Andate alla cartella **Devices** e fate clic su **Device Manager** dalla barra delle azioni per registrare i dispositivi.







