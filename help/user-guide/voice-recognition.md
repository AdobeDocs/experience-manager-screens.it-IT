---
title: Riconoscimento vocale in AEM Screens
description: La pagina descrive la funzione di riconoscimento vocale di AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 3%

---

# Riconoscimento vocale in AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informazioni importanti sulla privacy**
>
>Quando utilizzi la funzione di riconoscimento vocale, segui tutte le linee guida legali ed etiche applicabili per la tua area geografica (inclusa, a titolo esemplificativo e non esaustivo, la notifica visibile agli utenti finali che il lettore utilizza il riconoscimento vocale). Adobe Inc. non riceve, archivia o elabora le informazioni relative alla voce. I lettori AEM Screens utilizzano l’API di riconoscimento vocale web standard incorporata nel motore di navigazione. Dietro le quinte questa API invia una forma ondulata del discorso ai server di Google per la conversione da discorso a testo e questo testo viene confrontato dal lettore con parole chiave configurate.
>
>Fai riferimento a [White paper sulla privacy di Google sull&#39;API di riconoscimento vocale Web](https://www.google.com/chrome/privacy/whitepaper.html#speech) per ulteriori dettagli.


La funzione di riconoscimento vocale consente la modifica del contenuto in un canale AEM Screens guidata dall’interazione vocale.

Un autore di contenuti può configurare una visualizzazione in modo che sia abilitata per la voce. Lo scopo di questa funzione è quello di consentire ai clienti di utilizzare la sintesi vocale come metodo di interazione con i loro display. Alcuni casi d’uso simili includono la ricerca di prodotti consigliati nei negozi, l’ordine di voci di menu in ristoranti e ristoranti. Questa funzione aumenta l’accessibilità per gli utenti e può migliorare notevolmente l’esperienza del cliente.

>[!NOTE]
>L&#39;hardware del lettore deve supportare l&#39;input vocale, ad esempio un microfono.

## Implementazione del riconoscimento vocale {#implementing}

>[!IMPORTANT]
> La funzione di riconoscimento vocale è disponibile solo sui lettori Chrome OS e Windows.

Per implementare il riconoscimento vocale nel progetto AEM Screens, devi abilitare il riconoscimento vocale per Display e associare ciascun canale a un tag univoco per attivare una transizione di canale.

Nella sezione seguente viene descritto come abilitare e utilizzare la funzione di riconoscimento vocale in un progetto AEM Screens.

## Visualizzazione del contenuto nel passaggio di canale Schermo intero o Schermo diviso {#sequence-channel}

Prima di utilizzare la funzione di riconoscimento vocale, accertarsi di disporre di un progetto e di un canale con il contenuto impostato per il progetto.

1. L’esempio seguente mostra un progetto demo denominato **Demo vocale** e tre canali di sequenza **Principale**, **ColdDrinks**, e **HotDrinks**, come illustrato nella figura seguente.

   ![immagine](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuto a un canale, consulta [Creazione e gestione dei canali](/help/user-guide/managing-channels.md)

   Oppure,

   Puoi creare tre canali di sequenza **Principale**, **ColdDrinks**, e **HotDrinks** e un canale aggiuntivo Screens diviso 1x2 **SplitScreen** come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-emb-1.png)

1. Passa a ciascun canale e aggiungi il contenuto. Ad esempio, passa a **Demo vocale** —> **Canali** —> **Principale** e selezionare il canale. Clic **Modifica** dalla barra delle azioni per aprire l’editor e aggiungere contenuto (immagini/video) in base alle tue esigenze. Allo stesso modo, aggiungi contenuto a entrambi **ColdDrinks** e **HotDrinks** canale.

   I canali ora contengono risorse (immagini), come illustrato nelle figure riportate di seguito.

   **Principale**:

   ![immagine](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![immagine](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![immagine](assets/voice-recognition/vr-2.png)

   Se hai aggiunto al progetto il canale Schermi suddivisi, passa a **SplitScreen** e trascina e rilascia due sequenze incorporate e aggiungi percorsi a entrambi **ColdDrinks** e **HotDrinks** come illustrato nella figura riportata di seguito.
   ![immagine](assets/voice-recognition/vr-emb-6.png)


### Impostazione dei tag per i canali {#setting-tags}

Dopo aver aggiunto il contenuto ai canali, è necessario passare a ciascuno di essi e aggiungere i tag appropriati che attiverebbero il riconoscimento vocale.

Per aggiungere tag al canale, segui la procedura riportata di seguito:

1. Passa a ciascun canale e aggiungi il contenuto. Ad esempio, passa a **Demo vocale** —> **Canali** —> **Principale** e selezionare il canale.

1. Clic **Proprietà** dalla barra delle azioni.

   ![immagine](assets/voice-recognition/vr-5.png)

1. Accedi a **Nozioni di base** e seleziona un tag già esistente dalla scheda **Tag** o crearne uno nuovo.

   Per creare un nuovo tag, digita un nuovo nome per il tag e premi `return` come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-6.png)

   Oppure,

   Puoi anche creare tag dall’istanza AEM in anticipo per il progetto e selezionarli. Dopo aver seguito i passaggi descritti in [Creazione di tag](#creating-tags), è possibile selezionare il tag dalla posizione e aggiungerlo al canale, come illustrato nella figura seguente:

   ![immagine](assets/voice-recognition/vr-tag1.png)

1. Allo stesso modo, aggiungi il tag con titolo **caldo** al **HotDrinks** canale.

1. Se utilizzi un canale Schermi divisi, aggiungi entrambi i tag (**caldo** e **freddo**) al **SplitScreen** proprietà di canale, come illustrato nella figura riportata di seguito.

   ![immagine](assets/voice-recognition/vr-emb-7.png)

1. Clic **Salva e chiudi** quando hai finito.


### Creazione di tag {#creating-tags}

Per creare i tag, segui i passaggi seguenti:

1. Passa all’istanza AEM.

1. Fai clic sull&#39;icona degli strumenti —> **Assegnazione tag**.
   ![immagine](assets/voice-recognition/vr-7.png)

1. Clic **Crea** —> **Crea spazio dei nomi**.
   ![immagine](assets/voice-recognition/vr-tag3.png)

1. Inserisci il nome del progetto, ad esempio: **Demo vocale** e fai clic su **Crea**.

1. Seleziona la **Demo vocale** progetto e fai clic su **Crea tag** dalla barra delle azioni.
   ![immagine](assets/voice-recognition/vr-tag4.png)

1. Inserisci il nome del tag e fai clic su **Invia**.
   ![immagine](assets/voice-recognition/vr-tag5.png)

Ora puoi utilizzare questi tag nel tuo progetto AEM Screens.

### Assegnazione di un canale a un display e attivazione del riconoscimento vocale {#channel-assignment}

1. Creare una visualizzazione in **Posizioni** come illustrato nella figura seguente.

   ![immagine](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta [Creazione e gestione delle visualizzazioni](/help/user-guide/managing-displays.md).

1. Assegna i canali **Principale**, **ColdDrinks**, e **HotDrinks** al tuo **LobbyDisplay**. Inoltre, se utilizzi il **SplitScreen** canale per il progetto, assicurati di assegnarlo anche alla visualizzazione.

   >[!NOTE]
   >Se hai creato un canale schermo diviso, assegna il **SplitScreen** canale per il display.

1. Durante l&#39;assegnazione del canale, impostate le seguenti proprietà su ciascun canale.

   | **Nome canale** | **Priorità** | **Eventi supportati** |
   |---|---|---|
   | Principale | 2 | Caricamento iniziale, schermata di inattività, timer |
   | HotDrinks | 1 | Interazione utente |
   | ColdDrinks | 1 | Interazione utente |
   | SplitScreen | 1 | Interazione utente |

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta [Creazione e gestione delle visualizzazioni](/help/user-guide/managing-displays.md).

1. Dopo aver assegnato i canali a una visualizzazione, passa alla **LobbyDisplay** e selezionare la visualizzazione. Seleziona **Proprietà** dalla barra delle azioni.

1. Accedi a **Visualizzazione** e abilita **Voce abilitata** opzione in **Contenuto**.

   ![immagine](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >È obbligatorio attivare la funzione di riconoscimento vocale dal display.

### Visualizzazione del contenuto nel lettore Chrome {#viewing-content}

Una volta completati i passaggi precedenti, puoi registrare il dispositivo Chrome per visualizzare l’output.

>[!NOTE]
>Fai riferimento a [Registrazione dispositivo](device-registration.md) per scoprire come registrare un dispositivo su un lettore AEM Screens.

**Output desiderato per il canale sequenza**

Il **Principale** canale ne sta riproducendo il contenuto, ma quando utilizzi parole con parola chiave **caldo** come *Vorrei avere una bevanda calda*, il canale avvia la riproduzione del contenuto del **HotDrinks** canale.

Analogamente, se si utilizza una parola con una parola chiave **freddo** come *Vorrei avere qualcosa di freddo*, il canale avvia la riproduzione del contenuto del **ColdDrinks** canale.

**Uscita desiderata per canale schermo diviso**

Il **Principale** canale ne sta riproducendo il contenuto, ma quando utilizzi parole con parola chiave **caldo** e **freddo** insieme come *Vorrei vedere il menù per le bevande calde e fredde*, il canale avvia la riproduzione del contenuto del **SplitScreen** canale. Se dite *torna al menu principale*, torna al canale principale.
