---
title: Creazione e gestione dei canali
description: Scopri come creare e gestire i canali. Spiega anche la dashboard del canale e la modifica del contenuto per un canale.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 7bbd211a-f54f-42b9-a1b3-516efe6fb579
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 3%

---

# Creazione e gestione dei canali {#creating-and-managing-channels}

Un canale visualizza una sequenza di contenuti (immagini e video) e mostra anche un sito web o un’applicazione a pagina singola.

Questa pagina mostra come creare e gestire i canali per AEM Screens.

**Prerequisiti**:

* [Configurazione e distribuzione di Screens](configuring-screens-introduction.md)
* [Creazione e gestione di un progetto Screens](creating-a-screens-project.md)

## Creazione di un nuovo canale {#creating-a-new-channel}

Dopo aver creato il progetto per AEM Screens, segui i passaggi riportati di seguito per creare un canale per il progetto:

1. Fai clic sul collegamento Adobe Experience Manager (in alto a sinistra) e quindi su Screens. In alternativa, è possibile passare direttamente a `https://localhost:4502/screens.html/content/screens`.

1. Passa al progetto Screens e fai clic sulla cartella **Canali**.

1. Fai clic su **Crea** nella barra delle azioni.

   ![demochannel](assets/create-channel1.png)

1. Fai clic sul modello **Canale sequenza** dalla procedura guidata **Crea** e fai clic su **Avanti**.

   ![demochannel](assets/create-channel2.png)

1. Immetti il titolo come **ScreensChannel** e fai clic su **Crea**.

   ![demochannel](assets/create-project4.png)

1. Alla cartella **Channels** è stato aggiunto un canale di sequenza.

### Tipi di canale {#channel-types}

Durante l’utilizzo della procedura guidata sono disponibili le seguenti opzioni di modello, ad esempio:

| **Opzione modello** | **Descrizione** |
|---|---|
| Cartella canali | Crea una cartella in cui archiviare un insieme di canali. |
| Canale per sequenza | Create un canale che riproduca i componenti in sequenza (uno per uno in una presentazione). |
| Canale di applicazione | Mostra l’applicazione web personalizzata nel lettore Screens. |
| Canale schermo diviso 1x1 | Visualizzare un componente in una singola zona. |
| Canale schermo diviso 1x2 | Visualizza le risorse in due aree (suddivise orizzontalmente). |
| Canale schermo diviso 2X1 | Visualizza le risorse in due aree (divise verticalmente). |
| Canale schermo diviso 2x2 | Visualizza le risorse in quattro aree (suddivise orizzontalmente e verticalmente in una matrice). |
| Canale schermo diviso da 2 a 3 | Visualizza le risorse in due zone (divise orizzontalmente) in cui una è più grande dell’altra. |
| Canale schermo diviso barra a L sinistra o destra | Gli autori dei contenuti possono visualizzare diversi tipi di risorse nelle aree di dimensioni appropriate. |

>[!NOTE]
>
>I canali Schermo diviso dividono la visualizzazione in più aree in modo da poter riprodurre più esperienze contemporaneamente, una accanto all’altra. Le esperienze possono essere risorse/testo statico o sequenze incorporate.

>[!IMPORTANT]
>
>Dopo aver creato e aggiunto il contenuto al canale, il passaggio successivo consiste nel creare una posizione seguita dalla creazione di una visualizzazione. Inoltre, assegna il canale a una visualizzazione. Consulta le risorse sottostanti alla fine della sezione.

## Utilizzo dei canali {#working-with-channels}

Puoi modificare, visualizzare proprietà e dashboard, copiare, visualizzare in anteprima ed eliminare un canale.


![schermata_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### Aggiunta/modifica di contenuti a un canale {#adding-editing-content-to-a-channel}

Per aggiungere o modificare il contenuto di un canale, effettua le seguenti operazioni:

1. Fate clic sul canale da modificare (come illustrato nella figura precedente).
1. Fai clic su **Modifica** dall&#39;angolo superiore sinistro della barra delle azioni per modificare le proprietà del canale. Viene aperto l’editor che consente di aggiungere risorse/componenti al canale da pubblicare.

>[!NOTE]
>Puoi aggiungere componenti al tuo canale. Per ulteriori dettagli, vedere **[Aggiunta di componenti a un canale](adding-components-to-a-channel.md)**.

![demochannel1](assets/demochannel1.gif)

**Caricamento video nel canale**

Per caricare i video sul tuo canale, segui la procedura riportata di seguito:

1. Fai clic sul canale in cui desideri caricare il video.
1. Fai clic su **Modifica** nella barra delle azioni.
1. Nell&#39;editor, fai clic su **Video** in Assets e trascina i video richiesti.

>[!NOTE]
>Se riscontri problemi durante il caricamento di video nel tuo canale, consulta [Risoluzione dei problemi relativi ai video](troubleshoot-videos.md).

### Visualizzazione o modifica delle proprietà di un canale {#viewing-properties}

1. Fai clic sul canale da modificare.
1. Fai clic su **Proprietà** nella barra delle azioni per visualizzare/modificare le proprietà del canale. La scheda seguente consente di modificare le opzioni.

![proprietà](assets/properties.gif)

### Visualizzazione del dashboard {#viewing-dashboard}

1. Fai clic sul canale da modificare.
1. Fai clic su **Dashboard** nella barra delle azioni.

![dashboard](assets/dashboard.gif)

### Informazioni canale {#channel-information}

Il pannello Informazioni canale descrive le proprietà del canale, insieme all’anteprima sul canale. Inoltre, fornisce informazioni sul fatto che il canale sia offline o online.

Fare clic su (**...**) nella barra delle azioni **INFORMAZIONI CANALE** per visualizzare le proprietà, modificare il contenuto o aggiornare la cache (contenuto non in linea) per il canale.

![schermata_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### Visualizzazione del manifesto {#view-manifest}

Puoi visualizzare il manifesto dal dashboard del canale.

>[!IMPORTANT]
>Questa opzione è disponibile solo con il Feature Pack 8 di AEM 6.4 o il Feature Pack 4 di AEM 6.5.

Segui questi passaggi per abilitare questa opzione dal dashboard dei canali:

1. **Impostare il canale su Non in linea**
   1. Fai clic sul canale e fai clic su **Proprietà** nella barra delle azioni
   1. Passa alla scheda **Canale** e accertati di deselezionare l&#39;opzione **Modalità sviluppatore (forza canale online)**
   1. Fai clic su **Salva e chiudi**
1. **Aggiorna contenuto offline**
   1. Fai clic sul canale e fai clic su **Dashboard** nella barra delle azioni
   1. Passa al pannello **INFORMAZIONI CANALE** e fai clic su *...*
   1. Fai clic su **Aggiorna contenuto offline**

Dovresti visualizzare l&#39;opzione **Visualizza manifesto** dal pannello **INFORMAZIONI SUL CANALE** nel dashboard Canale.

![immagine1](assets/channel-one.png)


### Canali online e offline {#online-and-offline-channels}

>[!NOTE]
>Per impostazione predefinita, quando si crea un canale, questo è offline.

Quando crei un canale, questo può essere definito come canale online o offline.

Un ***canale online*** mostra il contenuto aggiornato nell&#39;ambiente in tempo reale, mentre un ***canale offline*** mostra il contenuto nella cache.

Segui i passaggi seguenti per rendere il canale online:

1. Passa al canale come **ProgettoTest** > **Canali** > **CanaleTest**.

   Fai clic sul canale.

   ![schermata_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Fai clic su **Dashboard** nella barra delle azioni per visualizzare lo stato del lettore. Il pannello **INFORMAZIONI CANALE** fornisce informazioni sul fatto che il canale sia online o offline.

   ![schermata_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. Fai clic su **Proprietà** nella barra delle azioni e passa alla scheda **Canale** come illustrato di seguito:

   ![schermata_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. Controlla la modalità **Sviluppatore** **(imposta la modalità online del canale)** per rendere il canale online.

   Fai clic su **Salva e chiudi** per salvare l&#39;opzione.

   ![schermata_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Torna alla dashboard dei canali e ora il pannello **INFORMAZIONI SUL CANALE** mostra lo stato in linea del lettore.

   ![schermata_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>Per configurare nuovamente il canale in modalità non in linea, deselezionare l&#39;opzione Modalità sviluppatore nella scheda **Proprietà** (come illustrato nel passaggio 3). Quindi, dal pannello **INFORMAZIONI CANALE**, fai clic su **Aggiorna contenuto offline**, come illustrato nella figura seguente.

![dashboard2](assets/dashboard2.gif)

#### Aggiornamenti automatici e manuali dal dashboard dei dispositivi {#automatic-versus-manual-updates-from-the-device-dashboard}

Nella tabella seguente sono riepilogati gli eventi associati agli aggiornamenti automatici e manuali dal dashboard del dispositivo.

<table>
 <tbody>
  <tr>
   <td><strong>Evento</strong></td>
   <td><strong>Aggiornamento automatico del dispositivo</strong></td>
   <td><strong>Aggiornamento manuale del dispositivo</strong></td>
  </tr>
  <tr>
   <td>Modifica nel canale online</td>
   <td>Il contenuto viene aggiornato automaticamente</td>
   <td><p>Contenuto aggiornato in "Device: Push Config"</p> <p>Oppure</p> <p>Contenuto aggiornato nel <strong><i>Dispositivo: riavvio</i></strong></p> </td>
  </tr>
  <tr>
   <td>Modifica nel canale offline ma IL CANALE "Contenuto push" NON viene attivato (non verrà ricreato alcun pacchetto offline)</td>
   <td>Nessun aggiornamento del contenuto</td>
   <td>Nessun aggiornamento del contenuto</td>
  </tr>
  <tr>
   <td>Modifica in "Contenuto push" per canale e canale offline attivata (nuovo pacchetto offline)</td>
   <td>Il contenuto viene aggiornato automaticamente</td>
   <td><p>Contenuto aggiornato sul <strong><i>dispositivo: configurazione push</i></strong></p> <p>Oppure</p> <p>Contenuto aggiornato nel <strong><i>Dispositivo: riavvio</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>Modifica nella configurazione</p>
    <ul>
     <li>Visualizzazione (canale forzato)</li>
     <li>Dispositivo</li>
     <li>Assegnazioni canale (nuovo canale, canale rimosso)</li>
     <li>Assegnazione canale (ruolo, evento, pianificazione)</li>
    </ul> </td>
   <td>La configurazione viene aggiornata automaticamente</td>
   <td><p>Configurazione aggiornata su <strong><i>Dispositivo: configurazione push</i></strong></p> <p>Oppure</p> <p>Configurazione aggiornata sul <strong><i>dispositivo: riavvio</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### Visualizzazioni assegnate {#assigned-displays}

Il pannello **Visualizzazioni assegnate** mostra la visualizzazione associata al canale. Fornisce un&#39;istantanea della visualizzazione assegnata insieme alla risoluzione.

Le visualizzazioni associate sono elencate nel pannello **Visualizzazioni assegnate**, come illustrato di seguito:

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>Per informazioni sulla creazione di una visualizzazione in una posizione, consulta:
>
>* [Crea e gestisci posizioni](managing-locations.md)
>* [Crea e gestisci visualizzazioni](managing-displays.md)
>

Fare inoltre clic sulla visualizzazione nel pannello **VISUALIZZAZIONI ASSEGNATE** per visualizzare le informazioni di visualizzazione, come illustrato di seguito:

![chlimage_1-28](assets/chlimage_1-28.png)

### Passaggi successivi {#the-next-steps}

Il passaggio successivo dopo aver creato un canale e aver aggiunto/modificato contenuti nel canale consiste nell’apprendere come creare una posizione e una visualizzazione. Inoltre, assegna un canale a tale visualizzazione.

Consulta le risorse seguenti per i passaggi successivi:

* [Creare e gestire i canali](managing-channels.md)
* [Creare e gestire le posizioni](managing-locations.md)
* [Creare e gestire le visualizzazioni](managing-displays.md)
