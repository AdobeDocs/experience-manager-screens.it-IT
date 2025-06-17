---
title: Utilizzo di AEM Screens Player
description: Scopri come utilizzare AEM Screens Player, l’interfaccia utente di amministrazione e il selettore di canale.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 1%

---

# Utilizzo di AEM Screens Player

Puoi gestire il contenuto del canale e altre impostazioni in AEM Screens Player.

>[!NOTE]
>
>Premere ***Ctrl+Cmd+F*** per uscire dalla modalità a schermo intero per OS X AEM Screens Player.

Dopo aver assegnato un canale a una visualizzazione, AEM Screens Player visualizza il contenuto. Puoi configurare le impostazioni per il lettore utilizzando le preferenze per l’interfaccia utente amministratore (dalla dashboard) oppure dal lettore stesso.

## Utilizzo del dashboard dei dispositivi {#using-the-device-dashboard}

Puoi configurare le preferenze per il dispositivo dal dashboard Dispositivo, accessibile tramite l’istanza di authoring di AEM.

1. Passa al dashboard dei dispositivi dal progetto, ad esempio ***Progetto di prova*** > ***Dispositivi***.

   Fare clic su **Dispositivi** e **Gestione dispositivi** nella barra delle azioni.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Fare clic sul dispositivo per aprirne il dashboard.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Controlla il pannello **PREFERENCES**. Puoi abilitare o disabilitare **l&#39;interfaccia utente amministratore** e **il cambio canale** per il lettore da queste due opzioni.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### Interfaccia utente amministratore {#the-admin-ui}

L&#39;attivazione della **interfaccia utente amministratore** dal pannello delle preferenze consente all&#39;utente di aprire le impostazioni di amministrazione da Screens Player. Inoltre, se disattivi questa opzione dal dashboard del dispositivo, l’utente non può aprire l’interfaccia utente di amministrazione dal lettore.

Per visualizzare l’interfaccia utente di amministrazione da Screens Player, premi a lungo l’angolo in alto a sinistra per aprire il menu Amministratore, sul lettore AEM Screens touch o utilizzando un mouse. Le informazioni vengono visualizzate al termine della registrazione e dopo il caricamento dei canali.

>[!NOTE]
>
>Inoltre, puoi visualizzare il tempo di attività dell’app AEM Screens Player per verificare lo stato di integrità dell’app.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Accesso alle opzioni del menu di configurazione {#configuration-options}

Puoi aggiornare le configurazioni facendo clic sull&#39;opzione **Configurazione** nel menu laterale, come illustrato nella figura seguente:

![schermata_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Il menu Configurazione consente di modificare le seguenti impostazioni:

* Reimpostare **Firmware**, **Preferenze** o **Alla factory** da questa finestra di dialogo.

* Specificare il numero massimo di file di registro che si desidera mantenere per un lettore AEM Screens in **Numero massimo. di file di registro da mantenere**.

* Attiva o disattiva **Menu amministratore**, **Cambia canale** e **Interfaccia attività** per Screens Player.

  Se l&#39;**interfaccia utente attività** è abilitata dal menu **Configurazione**, AEM Screens Player visualizza le *notifiche attività lettore* nell&#39;angolo superiore destro del lettore, come illustrato nella figura seguente.

  ![immagine](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>L&#39;opzione **Aggiorna firmware** funziona solo su Cordova, ad esempio i lettori Android™.

>[!NOTE]
>
>Si consiglia di disabilitare l&#39;**interfaccia utente amministratore** nelle distribuzioni di produzione.

#### Accesso alle opzioni del menu Content Cache {#content-cache-options}

Puoi cancellare la cache per i canali e le applicazioni dall’interfaccia utente di amministrazione in AEM Screens Player.

Fai clic su **Cache contenuto** dalla barra laterale per aggiornare la cache.

![schermata_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Commutatore canale {#the-channel-switcher}

L&#39;attivazione di **Channel Switcher** dal pannello delle preferenze consente all&#39;utente di aprire le impostazioni di selezione del canale da Screens Player.

Inoltre, se disattivi questa opzione dal dashboard del dispositivo, l’utente non può controllare le preferenze del canale da Screens Player.

È possibile cambiare e controllare le impostazioni per il canale dal lettore Screens.

Per visualizzare il commutatore di canale dal lettore, premere a lungo l&#39;angolo inferiore sinistro per aprire il commutatore di canale che consente di cambiare canale e altre funzioni.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>È inoltre possibile attivare o disattivare il menu di amministrazione e il selettore di canale per il lettore dal lettore Screens.
>
>(Vedi *Modifica preferenze da Screens Player* come indicato nella sezione seguente).

### Gestione delle preferenze da AEM Screens Player

Puoi anche modificare le impostazioni per l’interfaccia utente di amministrazione e il selettore di canale dal lettore stesso.

Per modificare le preferenze dal lettore:

1. Premi a lungo sull’angolo in alto a sinistra del canale inattivo per aprire il pannello di amministrazione.
1. Passa a **Configurazione** dal menu Azioni a sinistra.
1. Abilita o disabilita la configurazione per **Interfaccia utente amministratore** o **Cambio canale**.

![schermata_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Risoluzione dei problemi di AEM Screens Player

Puoi risolvere vari problemi associati al lettore AEM Screens (hardware e software):

| **Problemi** | **Consigli** |
|---|---|
| Spazio di archiviazione del lettore pieno | Eliminazione dei file non necessari |
| Rete persa dal lettore | Utilizzare il cavo CAT-5 o CAT-6. Per il wifi, ridurre la distanza tra il router e il dispositivo di riproduzione |
| Arresto anomalo del lettore AEM Screens | Si consiglia di disporre di un’app watchdog che garantisca l’esecuzione continua di AEM Screens Player |
| Impostazioni perse del lettore AEM Screens | Verifica la connessione al server AEM |
| AEM Screens Player non si avvia automaticamente dopo il riavvio o il riavvio del lettore | Controllare la cartella di avvio del sistema operativo o la procedura di inizializzazione |
| AEM Screens Player mostra contenuti errati o obsoleti | Verifica connessione di rete |

### Aggiornamenti per AEM Screens Player

Esistono due tipi di aggiornamenti per AEM Screens Player:

| **Metodo** | **Dettagli** | **tramite telecomando** | **Automatizzato** | **0 downtime** |
|---|---|---|---|---|
| Aggiornamento firmware | Applicato ai lettori installati esistenti tramite comando remoto. Dopo l&#39;aggiornamento, il lettore viene ricaricato automaticamente con il contenuto esistente. | Sì | Personalizzato | Quasi - 1-3 secondi |
| Aggiornamenti della shell del lettore | Un nuovo eseguibile distribuito sul lettore. Questa funzionalità richiede di copiare in remoto il nuovo binario sul lettore, arrestare l’esecuzione corrente e avviare la nuova versione. Potrebbe essere necessario scaricare nuovamente il precaricamento dei pacchetti. | Sì (tramite shell remota) | Personalizzato | No |

## Linee guida per la selezione dell&#39;hardware per il dispositivo del lettore {#hardware-selection-guidelines-for-player-device}

Nella sezione seguente vengono fornite le linee guida per la selezione dell&#39;hardware per un progetto Screens:

* Crea sempre l&#39;origine dei componenti di livello ***Commercial*** o ***Industrial*** sia per il lettore PC che per il pannello o il proiettore.

* Interagisci sempre con i fornitori che operano nel mercato del digital signage.
* Considera sempre i fattori ambientali, come la temperatura ambiente e l’umidità relativa.
* Controllare sempre i requisiti di alimentazione e il condizionamento dell&#39;alimentazione.
* Esaminare attentamente le prestazioni richieste e le porte di I/O necessarie per l&#39;applicazione.

La tabella seguente riepiloga le configurazioni hardware con casi d’uso tipici per un progetto AEM Screens:

<table>
 <tbody>
  <tr>
   <td>Configurazione lettore</td>
   <td>Processore</td>
   <td>Memoria</td>
   <td>SSD di storage</td>
   <td>GPU</td>
   <td>Visualizzazione</td>
   <td>I/O</td>
   <td>Casi d’uso tipici</td>
  </tr>
  <tr>
   <td>Base</td>
   <td>Processore Intel® Atom dual-core, i3 o quad-core entry-level</td>
   <td><p>4 GB di memoria</p> <p>2 MB di cache</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> Ethernet / Wireless<br /> 2x USB</td>
   <td>
    <ul>
     <li>Ciclo a schermo intero standard<br /> </li>
     <li>Ripartizione giornaliera</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Quad-core, processore Intel® Core™ i5</td>
   <td><p>8 GB di memoria</p> <p>4 MB di cache</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Contenuto dinamico Source singolo</li>
     <li>Interattivo semplice</li>
     <li>1-3 Layout di zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzato</td>
   <td>Quad-core con hyperthreading, processore Intel® Core™ i7</td>
   <td><p>16 GB di memoria</p> <p>8 MB di cache</p> </td>
   <td>256 GB</td>
   <td>GPU grafica dedicata</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 o più aree di contenuto, riproduzione video simultanea</li>
     <li>Interattivo a più pagine</li>
     <li>Attivatori di dati Source multipli</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
