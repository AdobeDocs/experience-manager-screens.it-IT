---
title: Configurazione e risoluzione dei problemi della riproduzione video
seo-title: Video sulla risoluzione dei problemi
description: Segui questa pagina per scoprire come eseguire il debug e risolvere i problemi relativi alla riproduzione video nel tuo canale.
seo-description: Segui questa pagina per scoprire come risolvere i problemi dei video. Quando carichi un video nel DAM e lo aggiungi al tuo canale, potresti riscontrare problemi che il video potrebbe non essere riprodotto in Screens Player e questa sezione descrive come eseguire il debug e risolvere i problemi relativi alla riproduzione video nel tuo canale.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: Canali, interattivi
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---


# Configurazione e risoluzione dei problemi di riproduzione video {#video-playback-configuration-and-troubleshooting}

Quando carichi un video nel DAM e lo aggiungi al tuo canale, potresti riscontrare problemi che il video potrebbe non essere riprodotto in Screens Player.

Le sezioni seguenti descrivono come eseguire il debug e risolvere i problemi relativi alla riproduzione video nel canale.

## Rendering DAM {#dam-renditions}

Una volta caricato il video sul canale, AEM iniziare a creare alcune rappresentazioni per esso. Puoi visualizzare i video in Risorse.

Per visualizzare il video:

1. Passa al video, ad esempio `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Fai clic sul video ed espandi il menu in alto a sinistra e fai clic su **Rendering**.

Devono essere disponibili rappresentazioni diverse (MP4 o M4V).

Se non è presente alcun rendering, assicurati di aver installato ffmpeg sul sistema operativo in cui è in esecuzione AEM.

>[!CAUTION]
>
>Se non è presente alcun rendering, assicurati di aver installato ffmpeg sul sistema operativo in cui è in esecuzione AEM.
>
>Fai clic [qui](https://www.ffmpeg.org/download.html) per installare ffmpeg.

## Risorse video {#video-assets}

Se non vedi un attributo sorgente sotto il video, potrebbe essere che il video non è stato transcodificato. Se il video viene codificato correttamente, verrà visualizzato nel dashboard, come illustrato nella figura riportata di seguito.

Controlla che ffmpeg sia installato e che i profili video siano installati.

![chlimage_1-2](assets/chlimage_1-2.png)

### Controllo del profilo video {#checking-video-profile}

1. Passa al **Profilo video**, ovvero `http://localhost:4502/etc/dam/video.html` e fai clic su **Carica video di prova**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Carica un video di test e fai clic su **Ok** per iniziare la transcodifica.

   Se la transcodifica non riesce, espandi l’output ffmpeg per comprendere eventuali errori nell’output della console di ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Inoltre, se la transcodifica video è riuscita, è possibile scaricare il file transcodificato.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Assicurati di dare tempo sufficiente alla transcodifica del video (dovrebbe mostrare il tag nuovo invece dell’elaborazione) prima di aggiungerlo a qualsiasi canale.

### Controllo del profilo con un componente video {#checking-profile-with-a-video-component}

Se il componente video non è configurato correttamente, controlla l’elenco dei profili dalla progettazione della pagina.

1. Passa al canale e seleziona la modalità **Progettazione** .

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Seleziona il video e apri la finestra di dialogo **Modifica** . Apri la scheda **Profili** .

   >[!NOTE]
   >Selezionare profili diversi (dovrebbe essere presente almeno il profilo &quot;H.264&quot; di alta qualità).

### Controllo del video nel lettore Web {#checking-the-video-in-the-web-player}

Utilizza il **Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` per convalidare la riproduzione nei browser (Chrome e Safari). Chrome viene utilizzato sui dispositivi Android mentre Safari è il browser OSX e iOS.

Se il video non viene eseguito su Safari, non verrà eseguito nei lettori OSX e iOS. Si tratta probabilmente di un problema di codifica e il video deve essere codificato nuovamente.

Segui questi passaggi per utilizzare un flusso di lavoro DAM per creare rappresentazioni FullHD:

1. Passa all&#39; *amministratore del modello di flusso di lavoro*, ovvero `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Seleziona il modello **Risorsa di aggiornamento Screens** .
1. fai clic su **Avvia flusso di lavoro** nella barra delle azioni per aprire la finestra di dialogo **Esegui flusso di lavoro**.

1. Seleziona la risorsa video nel **Payload**.
1. Fare clic su **Esegui**.

>[!NOTE]
>
>Consenti un po&#39; di tempo per creare le rappresentazioni, ma dopo alcuni secondi/minuti (a seconda delle dimensioni del video), ricarica il lettore web su Safari.

#### Flag dei criteri di riproduzione automatica {#troubleshooting-autoplay-policy-flag}

Nel caso in cui AEM Screens Player raccolga il video ma non lo visualizzi, è necessario risolvere i problemi relativi al flag Autoplay Policy.

Segui i passaggi riportati di seguito per risolvere il problema del flag di policy di riproduzione automatica di google:

1. Passa a ***chrome://flags/#autoplay-policy***
1. Cambia **Autoplay policy** da **Default** a **non è richiesto alcun gesto dell&#39;utente**

1. Riavvia il browser Web e aggiorna il lettore

>[!NOTE]
>
>Per ulteriori informazioni sulle best practice per esperienze utente ottimali con i nuovi criteri di riproduzione automatica in Chrome, consulta la documentazione relativa alle *modifiche ai criteri di riproduzione automatica*, ovvero `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Sincronizzazione video tra più lettori {#syncing-video-across-multiple-players}

Per riprodurre video in modo sincrono su più dispositivi, è necessario utilizzare la strategia assoluta per la sequenza di cui il video fa parte.

#### Requisiti {#requirements}

* giocatori uguali 2+
* hardware ideale
* topologia di rete identica (i lettori sono collegati a un server NTP che allinea i loro orologi di sistema interni)

#### Impostazione della strategia assoluta {#setting-up-the-absolute-strategy}

La strategia assoluta:

* calcola un orario di ancoraggio (mezzanotte del giorno corrente)
* calcola la durata della sequenza (somma della durata di tutti gli elementi)
* in qualsiasi momento, calcola quale elemento deve essere attualmente riprodotto e l&#39;elemento successivo risolvendo la sequenza _rest_time = (current_time - anchor_time) % sequence_duration.

Segui i passaggi seguenti per impostare una strategia assoluta:

1. Passa all’autore del canale e seleziona il componente per sequenza come mostrato nella figura seguente.
1. Apri la relativa finestra di dialogo di configurazione.
1. Modifica la **Strategia** e aggiungi assoluto.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >Il sistema operativo dei giocatori deve avere lo stesso orologio.

**Allineamento degli orologi sul sistema operativo** Seguire i passaggi seguenti per allineare gli orologi su OSX:

1. Apri le preferenze **Data e ora** su ogni casella OSX
1. Controlla **Imposta automaticamente data e ora**
1. Incolla il valore 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com nel menu a discesa o esegui semplicemente *sudo ntpdate -u -v 0.pool.ntp.org*
1. Avvia i 2+ giocatori

Potrebbe essere necessario un po&#39; di tempo prima che i giocatori inizino una nuova sequenza allineata.

