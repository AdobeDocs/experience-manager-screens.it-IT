---
title: Riconoscimento vocale in  AEM Screens
description: La pagina descrive la funzione di riconoscimento vocale in  AEM Screens.
translation-type: tm+mt
source-git-commit: e355d648846034c4762ef8fdcb3e218d868044b6
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 3%

---


# Riconoscimento vocale in  AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informazioni importanti sulla privacy**
>
>Quando si utilizza la funzione di riconoscimento vocale, seguire tutte le linee guida legali ed etiche applicabili alla propria regione (incluso, tra l&#39;altro, l&#39;invio di un avviso visibile agli utenti finali che il lettore utilizza il riconoscimento vocale).  Adobe Inc., non riceve, archivia o elabora le informazioni relative alla voce. I lettori AEM Screens  utilizzano l&#39;API vocale Web standard integrata nel motore di navigazione. Dietro le quinte questa API invia una forma d&#39;onda del discorso ai server Google per la conversione da discorso a testo e questo testo viene associato dal lettore alle parole chiave configurate.
>
>Per ulteriori informazioni, fare riferimento al [white paper sulla privacy di Google sull&#39;API vocale Web](https://www.google.com/chrome/privacy/whitepaper.html#speech).


La funzione di riconoscimento vocale consente la modifica del contenuto in un canale  AEM Screens guidato dall&#39;interazione vocale.

Un autore del contenuto può configurare una visualizzazione in modo che sia attivata per la voce. Lo scopo di questa funzione è consentire ai clienti di utilizzare la voce come metodo per interagire con i loro schermi. Alcuni casi di utilizzo simili includono la ricerca di raccomandazioni sui prodotti nei negozi, l&#39;ordinazione di voci di menu presso ristoranti e ristoranti. Questa funzione aumenta l&#39;accessibilità per gli utenti e può migliorare notevolmente l&#39;esperienza dei clienti.

>[!NOTE]
>L&#39;hardware del lettore deve supportare l&#39;ingresso vocale, ad esempio un microfono.

## Implementazione del riconoscimento vocale {#implementing}

>[!IMPORTANT]
> La funzione di riconoscimento vocale è disponibile solo sui lettori Chrome OS e Windows.

Per implementare il riconoscimento vocale nel progetto AEM Screens , è necessario abilitare il riconoscimento vocale per il display e associare ogni canale a un tag univoco per attivare una transizione di canale.

La sezione seguente descrive come attivare e usare la funzione di riconoscimento vocale in un progetto AEM Screens .

## Visualizzazione del contenuto a schermo intero o dello switch canale diviso {#sequence-channel}

Prima di utilizzare la funzione di riconoscimento vocale, accertatevi di disporre di un progetto e di un canale con il contenuto impostato per il progetto.

1. L&#39;esempio seguente mostra un progetto dimostrativo denominato **VoiceDemo** e tre canali di sequenza **Main**, **ColdDrinks** e **HotDrinks**, come illustrato nella figura seguente.

   ![immagine](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuti a un canale, fare riferimento a [Creazione e gestione di canali](/help/user-guide/managing-channels.md)

   Oppure,

   È possibile creare tre canali di sequenza **Main**, **ColdDrinks**, **HotDrinks** e un canale di 1x2 Split Screens aggiuntivo **SplitScreen** come illustrato nella figura seguente.

   ![immagine](assets/voice-recognition/vr-emb-1.png)

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, andate a **VoiceDemo** —> **Channels** —> **Main** e selezionate il canale. Fate clic su **Modifica** nella barra delle azioni per aprire l&#39;editor e aggiungere contenuti (immagini/video) in base alle vostre esigenze. Allo stesso modo, aggiungete contenuto sia al canale **ColdDrinks** che al canale **HotDrinks**.

   I canali ora contengono risorse (immagini), come mostrato nelle figure seguenti.

   **Principale**:

   ![immagine](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![immagine](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![immagine](assets/voice-recognition/vr-2.png)

   Se hai aggiunto il canale Dividi schermate al progetto, vai al canale **DividiSchermo** e trascina e rilascia due sequenze incorporate e aggiungi i percorsi al canale **ColdDrinks** e **HotDrinks** come mostrato nella figura seguente.
   ![immagine](assets/voice-recognition/vr-emb-6.png)


### Impostazione dei tag per i canali {#setting-tags}

Una volta aggiunto il contenuto ai canali, è necessario navigare fino a ciascuno dei canali e aggiungere tag appropriati per attivare il riconoscimento vocale.

Per aggiungere tag al canale, effettuate le operazioni seguenti:

1. Andate a ciascun canale e aggiungete contenuto. Ad esempio, andate a **VoiceDemo** —> **Channels** —> **Main** e selezionate il canale.

1. Fare clic su **Proprietà** dalla barra delle azioni.

   ![immagine](assets/voice-recognition/vr-5.png)

1. Passare alla scheda **Nozioni di base** e selezionare un tag già esistente dal campo **Tag** oppure crearne uno nuovo.

   Potete creare un nuovo tag digitando un nuovo nome per il tag e premendo il tasto `return`, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-6.png)

   Oppure,

   Potete anche creare tag dall’istanza AEM prima per il progetto e selezionarli. Dopo aver seguito i passaggi descritti in [Creazione di tag](#creating-tags), è possibile selezionare il tag dalla posizione e aggiungerlo al canale, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-tag1.png)

1. Allo stesso modo, aggiungere il tag denominato **hot** al canale **HotDrinks**.

1. Se si utilizza un canale di schermate divise, aggiungere sia i tag (**hot** che **cold**) alle proprietà del canale **SplitScreen**, come illustrato nella figura seguente.

   ![immagine](assets/voice-recognition/vr-emb-7.png)

1. Fare clic su **Salva e chiudi** al termine.


### Creazione di tag {#creating-tags}

Per creare i tag, effettuate le seguenti operazioni:

1. Passate all&#39;istanza AEM.

1. Fare clic sull&#39;icona degli strumenti —> **Assegnazione tag**.
   ![immagine](assets/voice-recognition/vr-7.png)

1. Fare clic su **Crea** —> **Crea spazio nomi**.
   ![immagine](assets/voice-recognition/vr-tag3.png)

1. Inserite il nome del progetto, ad esempio **VoiceDemo** e fate clic su **Crea**.

1. Selezionare il progetto **VoiceDemo** e fare clic su **Crea tag** dalla barra delle azioni.
   ![immagine](assets/voice-recognition/vr-tag4.png)

1. Immettete il nome del tag e fate clic su **Invia**.
   ![immagine](assets/voice-recognition/vr-tag5.png)

Ora potete usare questi tag nel progetto AEM Screens .

### Assegnazione del canale a un display e abilitazione del riconoscimento vocale {#channel-assignment}

1. Create una visualizzazione nella cartella **Locations**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di display](/help/user-guide/managing-displays.md).

1. Assegnare i canali **Main**, **ColdDrinks** e **HotDrinks** al **LobbyDisplay**. Inoltre, se utilizzate il canale **SplitScreen** per il progetto, accertatevi di assegnarlo anche allo schermo.

   >[!NOTE]
   >Se avete creato un canale di schermo diviso, assegnate il canale **SplitScreen** al vostro display.

1. Impostate le seguenti proprietà su ciascun canale, mentre assegnate il canale.

   | **Nome canale** | **Priorità** | **Eventi supportati** |
   |---|---|---|
   | Principale | 2 | Carico iniziale, Schermo inattivo, Timer |
   | HotDrinks | 1 | Interazione utente |
   | ColdDrinks | 1 | Interazione utente |
   | SplitScreen | 3 | Interazione utente |

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a uno schermo, fare riferimento a [Creazione e gestione di display](/help/user-guide/managing-displays.md).

1. Dopo aver assegnato i canali a uno schermo, andate alla **LobbyDisplay** e selezionate lo schermo. Selezionare **Properties** dalla barra delle azioni.

1. Passare alla scheda **Display** e attivare l&#39;opzione **Voice enabled** in **Content**.

   ![immagine](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >È obbligatorio attivare la funzione di riconoscimento vocale dal display.

### Visualizzazione del contenuto in Chrome Player {#viewing-content}

Una volta completati i passaggi precedenti, è possibile registrare il dispositivo chrome per visualizzare l&#39;output.

>[!NOTE]
>Per informazioni su come registrare un dispositivo su un lettore AEM Screens , fare riferimento a [Registrazione dispositivo](device-registration.md).

**Output desiderato per il canale della sequenza**

Il canale **Main** sta riproducendo il contenuto, ma quando si utilizzano parole con la parola chiave **hot** come *vorrei avere una bevanda calda*, il canale inizia a riprodurre il contenuto del canale **HotDrinks**.

Allo stesso modo, se si utilizza la parola con la parola chiave **cold** come *Vorrei avere qualcosa di freddo*, il canale inizia a riprodurre il contenuto del canale **ColdDrinks**.

**Output desiderato per il canale di schermi divisi**

Il canale **Principale** sta riproducendo il contenuto, ma quando si utilizzano parole con parole chiave **hot** e **cold** insieme come *vorrei vedere il menu per bevande calde e fredde*, il canale inizia a riprodurre il contenuto del canale **SplitScreen**. Se si dice *di nuovo al menu principale*, torna al canale principale.





