---
title: Configurazione e risoluzione dei problemi della riproduzione video
seo-title: Risoluzione dei problemi relativi ai video
description: null
seo-description: Segui questa pagina per scoprire come risolvere i problemi dei video. Quando carichi un video in DAM e lo aggiungi al tuo canale, potrebbero verificarsi problemi che potrebbero impedire la riproduzione del video nel lettore Screens e in questa sezione viene descritto come eseguire il debug e risolvere i problemi della riproduzione video nel tuo canale.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: 6abe309a8beb264f1505b6f39d786acc035bad05

---


# Configurazione e risoluzione dei problemi della riproduzione video {#video-playback-configuration-and-troubleshooting}

Quando carichi un video in DAM e lo aggiungi al tuo canale, potrebbero verificarsi problemi che potrebbero non essere riprodotti nel lettore Screens.

Le sezioni seguenti descrivono come eseguire il debug e risolvere i problemi relativi alla riproduzione video nel canale.

## Rappresentazioni DAM {#dam-renditions}

Una volta caricato il video sul canale, AEM dovrebbe iniziare a creare alcune rappresentazioni per esso. Puoi visualizzare i video sotto Risorse.

Per visualizzare il video:

1. Andate al video, ad esempio `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Fate clic sul video, espandete il menu in alto a sinistra e fate clic su **Rappresentazioni**.

Devono essere presenti diverse rappresentazioni (MP4 o M4V).

Se non è presente una rappresentazione, accertatevi che nel sistema operativo in cui è in esecuzione AEM sia installato ffmpeg.

>[!CAUTION]
>
>Se non è presente una rappresentazione, accertatevi che nel sistema operativo in cui è in esecuzione AEM sia installato ffmpeg.
>
>Fate clic [qui](https://www.ffmpeg.org/download.html) per installare ffmpeg.

## Risorse video {#video-assets}

Se in video non viene visualizzato un attributo sorgente, il video potrebbe non essere stato transcodificato. Se il video è transcodificato correttamente, verrà visualizzato nel dashboard, come illustrato nella figura riportata di seguito.

Controllare che ffmpeg sia installato e che i profili video siano impostati.

![chlimage_1-2](assets/chlimage_1-2.png)

### Verifica del profilo video {#checking-video-profile}

1. Individuate il profilo **** video `http://localhost:4502/etc/dam/video.html` e fate clic su **Carica video** di prova.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Caricate un video di prova e fate clic su **OK** per iniziare la transcodifica.

   Se la transcodifica non riesce, espandete l&#39;output ffmpeg per comprendere eventuali errori nell&#39;output della console di ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Inoltre, se la transcodifica video ha esito positivo, è possibile scaricare il file transcodificato.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Assicuratevi di disporre del tempo sufficiente per la transcodifica del video (il video deve mostrare il tag nuovo invece dell’elaborazione) prima di aggiungerlo a qualsiasi canale.

### Controllo del profilo con un componente video {#checking-profile-with-a-video-component}

Se il componente video non è configurato correttamente, controllate l’elenco dei profili dalla progettazione della pagina.

1. Passate al canale e selezionate la modalità **Progettazione** .

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Selezionate il video e aprite la finestra di dialogo **Modifica** . Open the **Profiles** tab.

   Selezionare profili diversi (dovrebbe essere presente almeno il profilo &quot;H.264 di alta qualità&quot;).

   ![chlimage_1-7](assets/chlimage_1-7.png)

### Controllo del video nel lettore Web {#checking-the-video-in-the-web-player}

Utilizzate **Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` per convalidare la riproduzione nei browser (Chrome e Safari). Chrome è utilizzato sui dispositivi Android mentre Safari è il browser OSX e iOS.

Se il video non viene eseguito su Safari, non verrà eseguito nei lettori OSX e iOS. Si tratta probabilmente di un problema di codifica e il video deve essere nuovamente codificato.

Per utilizzare un flusso di lavoro DAM per creare rappresentazioni Full HD, effettuate le seguenti operazioni:

1. Andate all&#39;amministratore *del modello di* workflow, ovvero `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Selezionate il modello **Schermate Aggiorna risorsa** .
1. fate clic su **Avvia flusso di lavoro** nella barra delle azioni per aprire la finestra di dialogo **Esegui flusso di lavoro** .

1. Selezionate la risorsa video nel **payload**.
1. Fate clic su **Esegui**.

>[!NOTE]
>
>Consentite un po&#39; di tempo per creare le rappresentazioni, ma dopo alcuni secondi/minuti (a seconda della dimensione del video), ricaricate il lettore Web su Safari.

#### Risoluzione dei problemi relativi al contrassegno dei criteri di riproduzione automatica {#troubleshooting-autoplay-policy-flag}

Se il lettore AEM Screens rileva il video ma non lo visualizza, è necessario risolvere il problema del flag Autoplay Policy.

Seguite i passaggi indicati di seguito per risolvere il problema relativo al flag di analisi automatica di Google:

1. Andate a ***chrome://flags/#autoplay-policy ***
1. Cambia il criterio **di** esecuzione automatica da **Predefinito** a **nessun gesto dell&#39;utente**

1. Riavviate il browser Web e aggiornate il lettore

>[!NOTE]
>
>Per ulteriori informazioni sulle procedure ottimali per le esperienze utente ottimali con i nuovi criteri di riproduzione automatica in Chrome, consultare la documentazione per le modifiche *ai criteri di* esecuzione automatica, vale a dire, `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Sincronizzazione dei video tra più lettori {#syncing-video-across-multiple-players}

Per riprodurre i video in modo sincrono su più dispositivi, occorre utilizzare la strategia assoluta per la sequenza di cui fa parte il video.

#### Requisiti {#requirements}

* giocatori identici 2+
* hardware idealmente simile
* topologia di rete identica (i lettori sono collegati a un server NTP che allinea i loro orologi di sistema interni)

#### Impostazione della strategia assoluta {#setting-up-the-absolute-strategy}

La strategia assoluta:

* calcola un orario di ancoraggio (mezzanotte del giorno corrente)
* calcola la durata della sequenza (somma della durata di tutto l’elemento)
* in qualsiasi momento, calcola quale elemento deve essere attualmente riprodotto e l&#39;elemento successivo risolvendo la sequenza _residue_time = (current_time - anchor_time) % sequence_durata.

Per impostare una strategia assoluta, effettuate le seguenti operazioni:

1. Passate all’autore del canale e selezionate il componente della sequenza come illustrato nella figura riportata di seguito.
1. Aprite la relativa finestra di dialogo di configurazione.
1. Modificate la **strategia** e aggiungete valori assoluti.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Il sistema operativo dei giocatori deve avere lo stesso orologio.

**Allineamento degli orologi su OS X** Seguire i passaggi seguenti per allineare gli orologi su OSX:

1. Aprire le preferenze **Data e ora** in ciascuna casella OSX
1. Controlla automaticamente data e ora **impostata**
1. Incolla il valore 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com nel menu a discesa o esegui semplicemente *sudo ntpdate -u -v 0.pool.ntp.org*
1. Avvio dei 2+ giocatori

Potrebbe essere necessario un po&#39; di tempo prima che i giocatori inizino una nuova sequenza allineata.

