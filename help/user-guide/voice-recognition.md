---
title: Riconoscimento vocale in  AEM Screens
description: La pagina descrive la funzione di riconoscimento vocale in  AEM Screens.
translation-type: tm+mt
source-git-commit: eb85269cfeccd837fdf1f752618013fefeddbfd7
workflow-type: tm+mt
source-wordcount: '1554'
ht-degree: 3%

---


# Riconoscimento vocale in  AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informazioni importanti sulla privacy**
>
>Quando si utilizza la funzione di riconoscimento vocale, seguire tutte le linee guida legali ed etiche applicabili alla propria area geografica (incluso, tra l&#39;altro, l&#39;invio di un avviso visibile agli utenti finali che il lettore utilizza il riconoscimento vocale).  Adobe Inc., non riceve, archivia o elabora le informazioni relative alla voce. I lettori AEM Screens  utilizzano l&#39;API vocale Web standard integrata nel motore di navigazione. Dietro le quinte, una forma d&#39;onda del vostro discorso viene inviata ai server di Google per la conversione da discorso a testo e questo testo viene associato dal lettore rispetto alle parole chiave configurate.
>
>Per ulteriori informazioni, consultate [il white paper sulla privacy di Google sull&#39;API](https://www.google.com/chrome/privacy/whitepaper.html#speech) vocale Web.



La funzione di riconoscimento vocale consente di modificare i contenuti in un canale  AEM Screens, basato sull&#39;interazione vocale.

Un autore del contenuto può configurare una visualizzazione in modo che sia attivata per la voce. Lo scopo di questa funzione è consentire ai clienti di utilizzare il linguaggio vocale come metodo per interagire con i loro schermi. Alcuni casi di utilizzo simili includono la ricerca di raccomandazioni sui prodotti nei negozi, l&#39;ordinazione di voci di menu presso ristoranti e ristoranti. Questa funzione aumenta l&#39;accessibilità per gli utenti e può migliorare notevolmente l&#39;esperienza dei clienti.

>[!NOTE]
>L&#39;hardware del lettore deve supportare l&#39;ingresso vocale, ad esempio un microfono.

## Implementazione del riconoscimento vocale {#implementing}

>[!IMPORTANT]
> La funzione di riconoscimento vocale è disponibile solo sui lettori Chrome e Electron.

Per implementare il riconoscimento vocale nel progetto AEM Screens , è necessario abilitare il riconoscimento vocale per il display e associare ogni canale a un tag univoco per attivare una transizione di canale.

La sezione seguente descrive come attivare e usare la funzione di riconoscimento vocale in un progetto AEM Screens .

Potete impostare il progetto utilizzando i due modelli seguenti:

* [Canale per sequenza](#sequence-channel)
* [Canale a schermo diviso](#split-channel)

## Utilizzo del canale della sequenza come modello {#sequence-channel}

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

   Potete creare un nuovo tag digitando un nuovo nome per assegnare un tag e un `return` tasto di scelta rapida, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-6.png)

   Oppure,

   Potete creare tag dall’istanza AEM prima per il progetto e selezionarli. Dopo aver seguito i passaggi descritti in [Creazione di tag](#creating-tags), potete selezionare il tag dalla posizione e aggiungerlo al canale, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-tag1.png)

1. Allo stesso modo, aggiungete il tag **hot** al canale **HotDrinks** .

1. Al termine, fate clic su **Salva e chiudi** .


### Creazione di tag {#creating-tags}

Per creare i tag, effettuate le seguenti operazioni:

1. Passate all&#39;istanza AEM.
1. Fate clic sugli strumenti > **Assegnazione tag**.
   ![immagine](assets/voice-recognition/vr-7.png)
1. Fare clic su **Crea** —> **Crea spazio nomi**.
   ![immagine](assets/voice-recognition/vr-tag3.png)
1. Inserite il nome del progetto, ad esempio: **VoiceDemo** e fate clic su **Crea**.
   ![immagine](assets/voice-recognition/vr-tag2.png)
1. Selezionate il progetto **VoiceDemo** e fate clic su **Crea tag** nella barra delle azioni.
   ![immagine](assets/voice-recognition/vr-tag4.png)
1. Immettete il nome del tag e fate clic su **Invia**.
   ![immagine](assets/voice-recognition/vr-tag5.png)

Ora potete usare questi tag nel progetto AEM Screens .

### Assegnazione del canale a uno schermo e abilitazione del riconoscimento vocale {#channel-assignment}

1. Create una visualizzazione nella cartella **Locations (Posizioni)** , come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di schermi](/help/user-guide/managing-displays.md).

1. Assegnare i canali **Main**, **ColdDrinks** e **HotDrinks** al **LobbyDisplay**.

1. Impostate le seguenti proprietà su ciascun canale, mentre assegnate il canale.

   | **Nome canale** | **Priorità** | **Eventi supportati** |
   |---|---|---|
   | Principale | 2 | Carico iniziale, Schermo inattivo, Timer |
   | HotDrinks | 1 | Interazione utente |
   | ColdDrinks | 1 | Interazione utente |

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di schermi](/help/user-guide/managing-displays.md).

1. Dopo aver assegnato i canali a uno schermo, andate alla **LobbyDisplay** e selezionate lo schermo. Selezionate **Proprietà** dalla barra delle azioni.

1. Passate alla scheda **Visualizza** e abilitate l&#39;opzione **Attiva** voce in **Contenuto**.

   ![immagine](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >È obbligatorio attivare la funzione di riconoscimento vocale dal display.

### Visualizzazione del contenuto in Chrome Player {#viewing-content}

Una volta completati i passaggi precedenti, è possibile registrare il dispositivo chrome per visualizzare l&#39;output.

>[!NOTE]
>Per informazioni su come registrare un dispositivo su un lettore AEM Screens , fare riferimento a Registrazione [](device-registration.md) dispositivo.

Questo esempio mostra l&#39;output su un lettore Chrome.

Il canale **Principale** sta riproducendo il contenuto, ma quando si utilizzano parole con parole chiave **calde** come *vorrei avere una bevanda* calda, il canale inizia a riprodurre il contenuto del canale **HotDrinks** .

Allo stesso modo, se si utilizza la parola con una parola chiave **fredda** come *vorrei avere qualcosa di freddo*, il canale inizia a riprodurre il contenuto del canale **ColdDrinks** .

![newimage](assets/voice-recognition/voice-video.gif)


## Utilizzo del canale per schermi divisi come modello {#split-channel}

Prima di utilizzare la funzione di riconoscimento vocale, accertatevi di disporre di un progetto e di un canale con il contenuto impostato per il progetto.

1. L&#39;esempio seguente mostra un progetto dimostrativo denominato **VoiceDemo** e tre canali di sequenza **Main**, **ColdDrinks**, **HotDrinks** e uno schermo diviso canale di 1x2 **SplitScreen** come mostrato nella figura seguente.

   ![immagine](assets/voice-recognition/vr-emb-1.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuti a un canale, consulta [Creazione e gestione di canali](/help/user-guide/managing-channels.md)

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, accedete a **VoiceDemo** —> **Canali** —> **Principale** e selezionate il canale. Fate clic su **Modifica** nella barra delle azioni per aprire l&#39;editor e aggiungere contenuti (immagini/video) in base alle vostre esigenze. Allo stesso modo, aggiungete contenuto sia a **ColdDrinks** che al canale **HotDrinks** .

   I canali ora contengono risorse (immagini), come mostrato nelle figure seguenti.

   **Principale**:

   ![immagine](assets/voice-recognition/vr-emb-3.png)


   **ColdDrinks**:
   ![immagine](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![immagine](assets/voice-recognition/vr-2.png)

1. Passate a **SplitScreen** e trascinate e rilasciate due sequenze incorporate e aggiungete i percorsi ai canali **ColdDrinks** e **HotDrinks** come illustrato nella figura riportata di seguito.
   ![immagine](assets/voice-recognition/vr-emb-6.png)


### Impostazione dei tag per i canali {#setting-tags-split}

Una volta aggiunto il contenuto ai canali, è necessario navigare fino a ciascuno dei canali e aggiungere tag appropriati per attivare il riconoscimento vocale.

Per aggiungere tag al canale, effettuate le operazioni seguenti:

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, accedete a **VoiceDemo** —> **Canali** —> **Principale** e selezionate il canale.

1. Click **Properties** from the action bar.

   ![immagine](assets/voice-recognition/vr-5.png)

1. Passate alla scheda **Nozioni di base** e selezionate un tag già esistente dal campo **Tag** oppure createne uno nuovo.

   Potete creare un nuovo tag digitando un nuovo nome per assegnare un tag e un `return` tasto di scelta rapida, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-6.png)

   Oppure,

   Potete creare tag dall’istanza AEM prima per il progetto e selezionarli. Dopo aver seguito i passaggi descritti in [Creazione di tag](#creating-tags), potete selezionare il tag dalla posizione e aggiungerlo al canale, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-tag1.png)

1. Allo stesso modo, aggiungete il tag **hot** al canale **HotDrinks** .

1. Aggiungete entrambi i tag (**caldo** e **freddo**) alle proprietà del canale **SplitScreen** .

   ![immagine](assets/voice-recognition/vr-emb-7.png)


1. Al termine, fate clic su **Salva e chiudi** .

### Assegnazione del canale a uno schermo e abilitazione del riconoscimento vocale {#channel-assignment-split}

1. Create una visualizzazione nella cartella **Locations (Posizioni)** , come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di schermi](/help/user-guide/managing-displays.md).

1. Assegnate i canali **Main**, **ColdDrinks**, **HotDrinks** e **SplitScreen** al display **Lobby** .

1. Impostate le seguenti proprietà su ciascun canale, mentre assegnate il canale.

   | **Nome canale** | **Priorità** | **Eventi supportati** |
   |---|---|---|
   | Principale | 2 | Carico iniziale, Schermo inattivo, Timer |
   | HotDrinks | 1 | Interazione utente |
   | ColdDrinks | 1 | Interazione utente |
   | SplitScreen | 1 | Interazione utente |

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di schermi](/help/user-guide/managing-displays.md).

1. Dopo aver assegnato i canali a uno schermo, andate alla visualizzazione **Sala d&#39;attesa** e selezionate lo schermo. Selezionate **Proprietà** dalla barra delle azioni.

1. Passate alla scheda **Visualizza** e abilitate l&#39;opzione **Attiva** voce in **Contenuto**.

   ![immagine](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >È obbligatorio attivare la funzione di riconoscimento vocale dal display.


### Visualizzazione del contenuto in Chrome Player {#viewing-content-split}

Una volta completati i passaggi precedenti, è possibile registrare il dispositivo chrome per visualizzare l&#39;output.

>[!NOTE]
>Per informazioni su come registrare un dispositivo su un lettore AEM Screens , fare riferimento a Registrazione [](device-registration.md) dispositivo.

Questo esempio mostra l&#39;output su un lettore Chrome.

Il canale **Principale** sta riproducendo il suo contenuto, ma quando si utilizzano parole con parole chiave **calde** e **fredde** insieme, come *vorrei vedere il menu per bevande* calde e fredde, il canale inizia a riprodurre il contenuto del canale **SplitScreen** .








