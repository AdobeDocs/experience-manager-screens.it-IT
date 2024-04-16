---
title: Guida di Kickstart
description: Scopri come creare un progetto demo di AEM Screens. Consente di creare un’esperienza di segnaletica digitale, a partire dall’installazione e dalla configurazione di un nuovo progetto per visualizzare i contenuti in AEM Screens player.
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1270'
ht-degree: 2%

---

# Guida di Kickstart {#kickstart-guide}

Kick-Start per AEM Screens illustra come impostare ed eseguire un progetto AEM Screens. Illustra i passaggi necessari per configurare un’esperienza di digital signage di base, aggiungere contenuti quali risorse e/o video a ciascun canale e successivamente pubblicarli su un lettore AEM Screens.

>[!NOTE]
>Prima di lavorare sui dettagli del progetto, assicurati di aver installato il Feature Pack più recente per AEM Screens. Puoi scaricare il feature pack più recente dalla sezione [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID.

## Prerequisiti {#prerequisites}

Segui i passaggi seguenti per creare un progetto di esempio per AEM Screens e pubblicare ulteriormente i contenuti su Screens player.

>[!NOTE]
>Il seguente tutorial mostra come riprodurre il contenuto del canale in Chrome OS Player.

>[!IMPORTANT]
>**Impostazioni configurazione OSGi**
>È necessario abilitare il referente vuoto per consentire al dispositivo di pubblicare dati sul server. Ad esempio, se la proprietà del referente vuoto è disabilitata, il dispositivo non può pubblicare uno screenshot. Attualmente alcune di queste funzioni sono disponibili solo se nella configurazione OSGi è abilitato Apache Sling Referrer Filter Allow Empty. È possibile che nel dashboard venga visualizzato un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzionalità.
>Per attivare la funzionalità ***Il Filtro Di Riferimento Apache Sling Consenti Vuoto***:


## Consenti richieste referrer vuote {#allow-empty-referrer-requests}

1. Accedi a **Configurazione console Web Adobe Experience Manager** tramite istanza AEM > icona a forma di martello > **Operazioni** > **Console web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Configurazione console Web Adobe Experience Manager** viene aperto. Cerca il referente sling.

   Per cercare la proprietà del referente sling, premi **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

1. Controlla la **Consenti vuoto** come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/empty-ref2.png)

1. Clic **Salva** per abilitare Apache Sling Referrer Filter Allow Empty (Consenti vuoto).

## Creazione di un&#39;esperienza di digital signage in 5 minuti {#creating-a-digital-signage-experience-in-minutes}

### Creazione di un progetto AEM Screens {#creating-project}

Il primo passaggio consiste nel creare un progetto AEM Screens.

1. Passa all’istanza di Adobe Experience Manager (AEM) e fai clic su **Schermi**. In alternativa, puoi navigare direttamente da `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Clic **Crea progetto Screens** in modo da poter creare un progetto Schermi.
1. Inserisci il titolo come **DemoScreens**, quindi fai clic su **Salva**.

   ![immagine](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Dopo aver creato il progetto, si torna alla home page del progetto AEM Screens. Ora puoi fare clic sul progetto. In un progetto, ci sono cinque cartelle diverse denominate **Applicazioni**, **Canali**, **Dispositivi**, **Posizioni**, e **Schedules**.

### Creazione di un canale {#creating-channel}

Dopo aver creato il progetto AEM Screens, crea un canale in cui gestire il contenuto.

Per creare un canale per il progetto, segui i passaggi seguenti:

1. Dopo aver creato un progetto, fai clic su **DemoScreens** e fai clic su **Canali** come illustrato nella figura seguente. Clic **+ Crea** dalla barra delle azioni.

   ![immagine](assets/kickstart/demo-2.png)

1. Scegli la **Canale sequenza** dalla procedura guidata e fai clic su **Successivo**.
   ![immagine](assets/kickstart/demo-3.png)

1. Inserisci il **Titolo** as **TestChannel** e fai clic su **Crea**.

   ![immagine](assets/kickstart/demo-4.png)

   Il **TestChannel** viene ora aggiunto alla cartella dei canali, come illustrato nella figura riportata di seguito.

   ![immagine](assets/kickstart/demo-5.png)

### Aggiunta di contenuto a un canale {#adding-content}

Una volta impostato il canale, aggiungi al canale contenuto che il lettore AEM Screens può visualizzare.

Per aggiungere contenuti al canale, segui la procedura riportata di seguito (**TestChannel**) nel progetto:

1. Accedi a **DemoProject** creato e fai clic su **TestChannel** dal **Canali** cartella.

1. Clic **Modifica** dalla barra delle azioni (vedere la figura seguente). Editor per **TestChannel** viene aperto.

   ![immagine](assets/kickstart/demo-6.png)

1. Fai clic sull’icona che attiva il pannello laterale a sinistra della barra delle azioni per aprire le risorse e i componenti.

1. Trascina i componenti da aggiungere al canale.

   ![immagine](assets/kickstart/demo-7.png)

### Creazione di una posizione {#creating-location}

Una volta impostato il canale, crea una posizione.

>[!NOTE]
>***Posizioni*** suddividere le varie esperienze di digital signage e contiene le configurazioni dei display in base alla posizione dei vari schermi.

Per creare una posizione per il progetto, segui i passaggi seguenti:

1. Accedi a **DemoProject** creato e fai clic su **Posizioni** cartella.
1. Clic **+ Crea** dalla barra delle azioni.
1. Clic **Posizione** dalla procedura guidata e fai clic su **Successivo**.
1. Inserisci il **Nome** per la tua posizione (inserisci il titolo come **TestLocation**) e fai clic su **Crea**.

Il **TestLocation** viene creato e aggiunto al tuo **Posizioni** cartella.


### Creazione di una visualizzazione per la posizione {#creating-display}

Dopo aver creato una posizione, creane una corrispondente.

>[!NOTE]
>***Visualizzazione*** rappresenta l’esperienza digitale che viene eseguita su uno o più schermi.

1. Accedi a **TestLocation** e fare clic su di esso.
1. Clic **Crea** dalla barra delle azioni.

   ![immagine](assets/kickstart/demo-disp1.png)

1. Clic **Visualizzazione** dal **Crea** e fai clic su **Successivo**.

   ![immagine](assets/kickstart/demo-disp2.png)

1. Inserisci il **Titolo** as **LobbyDisplay** e fai clic su **Crea**.

   ![immagine](assets/kickstart/demo-disp3.png)

   Una nuova visualizzazione con titolo **TestDisplay** è ora aggiunto alla tua posizione **TestLocation**, come illustrato nella figura seguente.

   ![immagine](assets/kickstart/demo-disp4.png)

### Assegnazione di un canale {#assigning-channel}

Al termine della configurazione del progetto, assegna il canale a una visualizzazione per visualizzare il contenuto.

1. Passa alla visualizzazione desiderata da **DemoScreens** > **Posizioni** > **TestLocation** > **LobbyDisplay**.

1. Clic **Assegna canale** dalla barra delle azioni.

   ![immagine](assets/kickstart/demo-assign1.png)

   Oppure

   Clic **Dashboard** dalla barra delle azioni e fai clic su **+Assegna canale** dal **CANALI E PIANIFICAZIONI ASSEGNATI** pannello.

   ![immagine](assets/kickstart/demo-assign2.png)

1. Il **Assegnazione canale** viene visualizzata.

1. Dalla sezione **Impostazioni** , scegli il canale **per percorso**  e **Eventi supportati** as **Caricamento iniziale** e **Schermata di inattività**.

   >[!NOTE]
   >
   >Il **Ruolo canale**, **Priorità**, e **Metodi di interruzione** sono tutti compilati per impostazione predefinita. Consulta [Proprietà canale](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) per ulteriori informazioni sulle proprietà di assegnazione dei canali.

   ![immagine](assets/kickstart/demo-assign3.png)

   Inoltre, puoi fare clic sul pulsante **Finestra di attivazione** e **Pianificazione ricorrenza**.

   >[!NOTE]
   >Il *Pianificazione ricorrenza* consente di impostare una pianificazione ricorrente per il canale. Puoi impostare più pianificazioni di ricorrenza per un canale.
   >Consulta [Pianificazione ricorrenza](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) per ulteriori dettagli.

1. Clic **Salva** dopo aver configurato le preferenze.

### Registrazione di un dispositivo e assegnazione del dispositivo a una visualizzazione {#registering-device}

Registra il dispositivo utilizzando il dashboard AEM.

>[!IMPORTANT]
>Chrome OS Player può essere installato come plugin del browser Chrome in modalità sviluppatore senza richiedere il dispositivo effettivo del lettore chrome. Per l&#39;installazione, procedere come segue:
>
>1. Clic [qui](https://download.macromedia.com/screens/) per scaricare il lettore Chrome più recente.
>1. Decomprimi e salva su disco.
>1. Apri il browser Chrome e fai clic su **Estensioni** dal menu o passa direttamente a ***chrome://extensions***.
>1. Accendere il **Modalità sviluppatore** dall&#39;angolo superiore destro.
>1. Clic **Carica decompresso** dall’angolo in alto a sinistra e carica Chrome Player decompresso.
>1. Verifica **AEM Screens Chrome Player** plug-in, se disponibile nell’elenco delle estensioni.
>1. Apri una nuova scheda e fai clic su **App** dall&#39;angolo in alto a sinistra, oppure passare direttamente a ***chrome://apps***.
>1. Clic **AEM Screens** Plug-in per avviare Chrome Player. Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premi **Esc** per uscire dalla modalità a tutto schermo.

Dopo che il lettore Chrome OS è acceso, segui i passaggi seguenti per registrare un dispositivo Chrome.

1. Accedi a **Dispositivi** del progetto dall’istanza AEM.

1. Fai clic su **Gestione dispositivi** dalla barra delle azioni.

   ![immagine](assets/kickstart/demo-register1.png)

1. Fai clic su **Registrazione dispositivo** in alto a destra.

1. Fai clic sul dispositivo richiesto e fai clic su **Registra dispositivo**.

   ![immagine](assets/kickstart/demo-register2.png)

1. Attendere che il dispositivo invii il suo codice di registrazione e contemporaneamente controllare **Codice di registrazione** dal dispositivo Chrome.
   ![immagine](assets/kickstart/demo-register3.png)

1. Se il **Codice di registrazione** è lo stesso in entrambi i computer, fare clic su **Convalida** nell&#39;AEM.

1. Imposta il nome desiderato come **ChromeDeviceForDemo** per il dispositivo e fare clic su **Registrati**.

   ![immagine](assets/kickstart/demo-register4.png)

1. Clic **Assegna visualizzazione** dal **Registrazione dispositivo completata** .

   ![immagine](assets/kickstart/demo-register5.png)

1. Fai clic sul percorso della visualizzazione come **DemoScreens** > **Posizioni** > **TestLocation** > **LobbyDisplay** e fai clic su **Assegna**.

   ![immagine](assets/kickstart/demo-device6.png)

1. Quando il dispositivo è stato assegnato correttamente, viene visualizzata la seguente conferma.

   ![immagine](assets/kickstart/demo-register8.png)

1. Clic **Fine** per completare il processo di registrazione. È ora possibile visualizzare il dispositivo registrato dal dashboard di visualizzazione.

   ![immagine](assets/kickstart/demo-register9.png)

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

Tutte le risorse nel canale vengono ora riprodotte sul lettore Chrome OS.

Congratulazioni per aver iniziato a riprodurre contenuti in un canale AEM Screens.

![immagine](assets/kickstart/demo-video-screens.gif)
