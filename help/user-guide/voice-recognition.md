---
title: Riconoscimento vocale in  AEM Screens
description: La pagina descrive la funzione di riconoscimento vocale in  AEM Screens.
translation-type: tm+mt
source-git-commit: 0300af2ef44756dddbb27f3da15c52bc877b93ea
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 2%

---


# Riconoscimento vocale in  AEM Screens {#voice-recognition}

## Panoramica {#overview}

La funzione di riconoscimento vocale consente di modificare i contenuti in un canale  AEM Screens, basato sull&#39;interazione vocale.

Un autore del contenuto può configurare una visualizzazione in modo che sia attivata per la voce. Lo scopo di questa funzione è consentire ai clienti di utilizzare il linguaggio vocale come metodo per interagire con i loro schermi. Alcuni casi di utilizzo simili includono la ricerca di raccomandazioni sui prodotti nei negozi, l&#39;ordinazione di voci di menu presso ristoranti e ristoranti. Questa funzione aumenta l&#39;accessibilità per gli utenti e può migliorare notevolmente l&#39;esperienza dei clienti.


>[!NOTE]
>L&#39;hardware del lettore deve supportare l&#39;ingresso vocale, ad esempio un microfono.

>[!IMPORTANT]
> La funzione di riconoscimento vocale è disponibile solo sui lettori Chrome e Electron.

## Implementazione del riconoscimento vocale {#implementing}


Per implementare il riconoscimento vocale nel progetto AEM Screens , è necessario abilitare il riconoscimento vocale per il display e associare ogni canale a un tag univoco per attivare una transizione di canale.

La sezione seguente descrive come attivare e usare la funzione di riconoscimento vocale in un progetto AEM Screens .

### Impostazione del progetto {#setting-up}

Prima di utilizzare la funzione di riconoscimento vocale, accertatevi di disporre di un progetto e di un canale con il contenuto impostato per il progetto.

1. L&#39;esempio seguente mostra un progetto demo denominato **VoiceDemo** e tre canali di sequenza **Main**, **ColdDrinks** e **HotDrinks**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuti a un canale, consulta [Creazione e gestione di canali](/help/user-guide/managing-channels.md)

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, accedete a **VoiceDemo** —> **Canali** —> **Principale** e selezionate il canale. Fate clic su **Modifica** nella barra delle azioni per aprire l&#39;editor e aggiungere contenuti (immagini/video) in base alle vostre esigenze. Allo stesso modo, aggiungete contenuto sia a **ColdDrinks** che al canale **HotDrinks** .

   I canali ora contengono risorse (immagini), come mostrato nelle figure seguenti.

   **Principale**:

   ![immagine](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![immagine](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![immagine](assets/voice-recognition/vr-2.png)

### Impostazione dei tag per i canali {#setting-tags}

Una volta aggiunto il contenuto ai canali, è necessario navigare fino a ciascuno dei canali e aggiungere tag appropriati per attivare il riconoscimento vocale.

Per aggiungere tag al canale, effettuate le operazioni seguenti:

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, accedete a **VoiceDemo** —> **Canali** —> **Principale** e selezionate il canale.

1. Click **Properties** from the action bar.

   ![immagine](assets/voice-recognition/vr-5.png)

1. Passate alla scheda **Nozioni di base** e selezionate un tag già esistente dal campo **Tag** oppure createne uno nuovo.

   Potete creare un nuovo tag digitando un nuovo nome per il tag , come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-6.png)

   Oppure,

   Potete creare tag dall’istanza AEM prima per il progetto e selezionarli.

   Per creare i tag, effettuate le seguenti operazioni:

   1. Passate all&#39;istanza AEM.
   1. Fate clic sugli strumenti > **Assegnazione tag**.
      ![immagine](assets/voice-recognition/vr-7.png)

1. Al termine, fate clic su **Salva e chiudi** .

Allo stesso modo, aggiungere tag **hot** al canale **HotDrinks** e **Cold** al canale **ColdDrinks** .

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







