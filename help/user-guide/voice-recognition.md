---
title: Riconoscimento vocale in AEM Screens
description: La pagina descrive la funzione di riconoscimento vocale in AEM Screens.
feature: Creazione di esperienze in Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 3%

---

# Riconoscimento vocale in AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informazioni importanti sulla privacy**
>
>Quando si utilizza la funzione di riconoscimento vocale, seguire tutte le linee guida legali ed etiche applicabili nella propria area geografica (compresi, tra l&#39;altro, l&#39;invio di un avviso visibile agli utenti finali che il lettore sta utilizzando il riconoscimento vocale). Adobe Inc. non riceve, archivia o elabora alcuna delle informazioni relative alla voce. I lettori AEM Screens utilizzano l’API vocale web standard integrata nel motore di navigazione. Dietro le quinte questa API invia una forma d&#39;onda del tuo discorso ai server di Google per la conversione da discorso a testo e questo testo viene abbinato dal lettore alle parole chiave configurate.
>
>Per ulteriori informazioni, consulta il [white paper sulla privacy di Google sull&#39;API di linguaggio web](https://www.google.com/chrome/privacy/whitepaper.html#speech) .


La funzione di riconoscimento vocale consente il cambiamento dei contenuti in un canale AEM Screens guidato dall&#39;interazione vocale.

Un autore di contenuti può configurare una visualizzazione per l’attivazione vocale. Lo scopo di questa funzione è quello di consentire ai clienti di utilizzare il linguaggio come metodo per interagire con i loro schermi. Alcuni casi d’uso simili includono la ricerca di consigli sui prodotti nei negozi, l’ordinazione di voci di menu in ristoranti e ristoranti. Questa funzione aumenta l’accessibilità per gli utenti e può migliorare notevolmente l’esperienza del cliente.

>[!NOTE]
>L&#39;hardware del lettore deve supportare l&#39;ingresso vocale, ad esempio un microfono.

## Implementazione del riconoscimento vocale {#implementing}

>[!IMPORTANT]
> La funzione di riconoscimento vocale è disponibile solo sui lettori Chrome OS e Windows.

Per implementare il riconoscimento vocale nel progetto AEM Screens, è necessario abilitare il riconoscimento vocale per la visualizzazione e associare ogni canale a un tag univoco per attivare una transizione di canale.

La sezione seguente descrive come abilitare e utilizzare la funzione di riconoscimento vocale in un progetto AEM Screens.

## Visualizzazione del contenuto a schermo intero o dello switch di canale a schermo diviso {#sequence-channel}

Prima di utilizzare la funzione di riconoscimento vocale, assicurati di disporre di un progetto e di un canale con contenuto configurato per il progetto.

1. Nell&#39;esempio seguente viene illustrato un progetto demo denominato **VoiceDemo** e tre canali di sequenza **Principale**, **ColdDrinks** e **HotDrinks**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuti a un canale, consulta [Creazione e gestione di canali](/help/user-guide/managing-channels.md)

   Oppure,

   È possibile creare tre canali di sequenza **Principale**, **ColdDrinks** e **HotDrinks** e un canale di schermo diviso 1x2 aggiuntivo **SplitScreen** come mostrato nella figura seguente.

   ![immagine](assets/voice-recognition/vr-emb-1.png)

1. Passa a ciascun canale e aggiungi contenuto. Ad esempio, accedi a **VoiceDemo** —> **Canali** —> **Principale** e seleziona il canale. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor e aggiungere contenuto (immagini/video) in base alle tue esigenze. Allo stesso modo, aggiungi contenuto sia al canale **ColdDrinks** che al canale **HotDrinks**.

   I canali ora contengono risorse (immagini), come mostrato nelle figure seguenti.

   **Principale**:

   ![immagine](assets/voice-recognition/vr-4.png)

   **Bevande** fredde:

   ![immagine](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![immagine](assets/voice-recognition/vr-2.png)

   Se hai aggiunto il canale Split Screens al progetto, passa al canale **SplitScreen** e trascina e rilascia due sequenze incorporate e aggiungi percorsi sia al canale **ColdDrinks** che al canale **HotDrinks** come mostrato nella figura seguente.
   ![immagine](assets/voice-recognition/vr-emb-6.png)


### Impostazione dei tag per i canali {#setting-tags}

Una volta aggiunto il contenuto ai canali, devi accedere a ciascuno dei canali e aggiungere tag appropriati per attivare il riconoscimento vocale.

Per aggiungere tag al canale, effettua le seguenti operazioni:

1. Passa a ciascun canale e aggiungi contenuto. Ad esempio, accedi a **VoiceDemo** —> **Canali** —> **Principale** e seleziona il canale.

1. Fai clic su **Proprietà** nella barra delle azioni.

   ![immagine](assets/voice-recognition/vr-5.png)

1. Passa alla scheda **Nozioni di base** e seleziona un tag già esistente dal campo **Tag** oppure creane uno nuovo.

   Puoi creare un nuovo tag digitando un nuovo nome per il tag e premendo il tasto `return` , come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-6.png)

   Oppure,

   Puoi anche creare tag dall’istanza AEM in precedenza per il progetto e selezionarli. Dopo aver seguito i passaggi descritti in [Creazione di tag](#creating-tags), puoi selezionare il tag dalla posizione e aggiungerlo al canale, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-tag1.png)

1. Allo stesso modo, aggiungi il tag **hot** al canale **HotDrinks**.

1. Se utilizzi un canale Screens divisi, aggiungi entrambi i tag (**hot** e **cold**) alle proprietà del canale **SplitScreen**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-emb-7.png)

1. Al termine, fai clic su **Salva e chiudi**.


### Creazione di tag {#creating-tags}

Per creare i tag, effettua le seguenti operazioni:

1. Passa all’istanza AEM.

1. Fai clic sull’icona degli strumenti —> **Assegnazione tag**.
   ![immagine](assets/voice-recognition/vr-7.png)

1. Fai clic su **Crea** —> **Crea spazio dei nomi**.
   ![immagine](assets/voice-recognition/vr-tag3.png)

1. Inserisci il nome del progetto, ad esempio **VoiceDemo** e fai clic su **Crea**.

1. Seleziona il progetto **VoiceDemo** e fai clic su **Crea tag** nella barra delle azioni.
   ![immagine](assets/voice-recognition/vr-tag4.png)

1. Immetti il nome del tag e fai clic su **Invia**.
   ![immagine](assets/voice-recognition/vr-tag5.png)

Ora puoi utilizzare questi tag nel tuo progetto AEM Screens.

### Assegnazione del canale a una visualizzazione e abilitazione del riconoscimento vocale {#channel-assignment}

1. Crea una visualizzazione nella cartella **Posizioni**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta [Creazione e gestione di visualizzazioni](/help/user-guide/managing-displays.md).

1. Assegna i canali **Main**, **ColdDrinks** e **HotDrinks** al tuo **LobbyDisplay**. Inoltre, se utilizzi il canale **SplitScreen** per il progetto, assicurati di assegnarlo alla visualizzazione.

   >[!NOTE]
   >Se hai creato un canale a schermo diviso, assegna il canale **SplitScreen** al tuo display.

1. Imposta le seguenti proprietà su ciascun canale, durante l&#39;assegnazione del canale.

   | **Nome canale** | **Priorità** | **Eventi supportati** |
   |---|---|---|
   | Principale | 2 | Caricamento iniziale, Schermo inattivo, Timer |
   | HotDrinks | 1 | Interazione utente |
   | Bevande fredde | 1 | Interazione utente |
   | Schermo diviso | 1 | Interazione utente |

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta [Creazione e gestione di visualizzazioni](/help/user-guide/managing-displays.md).

1. Dopo aver assegnato i canali a un display, passa a **LobbyDisplay** e seleziona il display. Seleziona **Proprietà** dalla barra delle azioni.

1. Passa alla scheda **Visualizzazione** e abilita l&#39;opzione **Voce abilitata** in **Contenuto**.

   ![immagine](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >È obbligatorio attivare la funzione di riconoscimento vocale dal display.

### Visualizzazione del contenuto in Chrome Player {#viewing-content}

Una volta completati i passaggi precedenti, puoi registrare il dispositivo chrome per visualizzare l’output.

>[!NOTE]
>Per informazioni su come registrare un dispositivo su un lettore AEM Screens, consulta [Registrazione dispositivo](device-registration.md) .

**Uscita desiderata per il canale della sequenza**

Il canale **Principale** sta riproducendo il suo contenuto, ma quando utilizzi parole con parola chiave **hot** come *Vorrei avere una bevanda calda*, il canale inizia a riprodurre il contenuto del canale **HotDrinks**.

Allo stesso modo, se utilizzi una parola chiave **cold** come *Vorrei avere qualcosa di freddo*, il canale inizia a riprodurre il contenuto del canale **ColdDrinks**.

**Output desiderato per il canale schermo diviso**

Il canale **Principale** sta riproducendo il suo contenuto, ma quando si utilizzano parole con parole chiave **hot** e **cold** insieme come *Vorrei vedere il menu per bevande calde e fredde*, il canale inizia a riprodurre il contenuto del canale **SplitScreen**. Se dici *di nuovo al menu principale*, torna al canale principale.
