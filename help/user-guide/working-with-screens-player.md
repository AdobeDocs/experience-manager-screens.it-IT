---
title: Utilizzo di AEM Screens Player
seo-title: Utilizzo di Screens Player
description: Segui questa pagina per informazioni su Screens Player. Viene illustrata anche Interfaccia utente amministratore e Controllo canali.
seo-description: Segui questa pagina per informazioni su Screens Player. Viene illustrata anche Interfaccia utente amministratore e Controllo canali.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: 428e1dbaa1a252d2aa9bcbb02264a0076b95291b

---


# Working with AEM Screens Player {#working-with-aem-screens-player}

Puoi gestire il contenuto del canale e altre impostazioni su AEM Screens Player.

>[!NOTE]
>
>Premi ***Ctrl+Cmd+F**per uscire dalla modalità a schermo intero per OS X di AEM Screens Player.*

Una volta assegnato un canale a una visualizzazione, AEM Screens Player mostra il contenuto. Puoi configurare le impostazioni per il lettore utilizzando le preferenze per l'interfaccia utente dell'amministratore (dal dashboard) o dal lettore stesso.

## Utilizzo del dashboard del dispositivo {#using-the-device-dashboard}

Puoi configurare le preferenze per il dispositivo dal dashboard del dispositivo, accessibile tramite l'istanza di creazione AEM.

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Fai clic sul dispositivo per aprire il dashboard del dispositivo.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Check the **PREFERENCES** panel. You can enable/disable the **Admin UI** and **Channel Switcher** for your player from these two options.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### Interfaccia utente amministratore {#the-admin-ui}

Enabling the **Admin UI** from the preferences panel allows the user to open the admin settings from the Screens Player. Inoltre, disabilitando questa opzione dal dashboard del dispositivo, l'utente non può aprire l'interfaccia utente dell'amministratore dal lettore.

Per visualizzare l'interfaccia utente dell'amministratore da Screens Player, tieni premuto nell'angolo in alto a sinistra per aprire il menu dell'amministratore, su AEM Screens Player abilitato al tocco o utilizzando il mouse. Mostra le informazioni dopo che la registrazione è stata completata e i canali sono stati caricati.

>[!NOTE]
>
>Inoltre, puoi visualizzare il tempo di attività dell'applicazione AEM Screens Player per controllare lo stato dell'applicazione.

![chlimage_1-3](assets/chlimage_1-3.gif)

Se si seleziona l'opzione **Configurazione** dal menu laterale, da questa finestra di dialogo è possibile reimpostare **firmware**, **preferenze** o **su fabbrica** .

Inoltre, potete specificare il numero massimo di file di registro da conservare per un lettore AEM Screens in Numero **massimo. dei file di registro da mantenere**. Per maggiori informazioni, consulta la schermata sottostante.

>[!NOTE]
>
>L'opzione **Aggiorna firmware** funziona solo sulla cordova, come i lettori Android.

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

>[!NOTE]
>
>Si consiglia di disabilitare l'interfaccia utente **** Amministratore nelle installazioni di produzione.

Puoi cancellare la cache per i canali e le applicazioni dall'interfaccia utente dell'amministratore in AEM Screens Player.

Seleziona la **Cache del contenuto** dalla guida laterale per aggiornare la cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Controllo canali {#the-channel-switcher}

Enabling the **Channel Switcher** from the preferences panel allows the user to open the channel selection/settings from the Screens Player.

Inoltre, disabilitando questa opzione dal dashboard del dispositivo, l'utente non può controllare le preferenze dei canali da Screens Player.

Puoi cambiare e controllare le impostazioni per il canale da Screens Player.

Per visualizzare il controllo canali dal lettore, tenere premuto a lungo nell'angolo in basso a sinistra per aprire il controllo canali che consente di passare da un canale all'altro e ad altre funzioni.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Puoi anche attivare o disattivare il menu dell'amministratore e il controllo canali per il lettore da Screens Player.
>
>(Consulta *Modifica preferenze da Screens Player* come menzionato nella sezione di seguito).

### Gestione delle preferenze da AEM Screens Player {#managing-preferences-from-the-aem-screens-player}

Puoi anche modificare le impostazioni per l'interfaccia utente dell'amministratore e il controllo canali dal lettore stesso.

Segui questi passaggi per modificare le preferenze dal lettore:

1. Tieni premuto sull'angolo in alto a sinistra del canale inattivo per aprire il pannello di amministrazione.
1. Navigate to **Configuration** from the left action menu.
1. Enable/disable configuration for **Admin UI** or **Channel Switcher**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Risoluzione problemi con AEM Screens Player {#troubleshooting-aem-screens-player}

Puoi risolvere molti problemi associati ad AEM Screens Player (hardware e software):

| **Edizioni** | **Consigli** |
|---|---|
| Archiviazione del lettore completa | Eliminare i file non necessari |
| Rete persa dal lettore | Utilizzare il cavo Cat-5/Cat-6. Per il wifi, ridurre la distanza dal router alla periferica del lettore |
| Arresto anomalo di AEM Screens Player | È consigliabile disporre di un'app di controllo che assicuri l'esecuzione costante di AEM Screens Player |
| AEM Screens Player - Impostazioni perse | Controllare la connessione al server AEM |
| AEM Screens Player non si avvia automaticamente dopo il riavvio o il riavvio del lettore | Controllare la cartella iniziale del sistema operativo o la procedura di inizializzazione |
| AEM Screens Player visualizza contenuto errato/vecchio | Verifica connessione di rete |

### Aggiornamenti per AEM Screens Player {#updates-for-aem-screens-player}

Esistono due tipi di aggiornamenti per AEM Screens Player:

| **Metodo** | **Dettagli** | **tramite telecomando** | **Automatico** | **0 Download** |
|---|---|---|---|---|
| Aggiornamento firmware | Applicato ai lettori installati esistenti tramite il comando remoto. Dopo l'aggiornamento il lettore si caricherà automaticamente con il contenuto esistente. | Sì | Personalizzata | Quasi 1-3 secondi |
| Aggiornamenti shell Player | Si tratta di un nuovo eseguibile da distribuire sul lettore. Questo tipo di operazione richiede la copia remota del nuovo binario sul lettore, l'arresto dell'esecuzione in corso e l'avvio della nuova versione. Questo potrebbe richiedere un nuovo download del precaricamento dei pacchetti. | Sì (tramite shell remota) | Personalizzata | No |

## Linee guida sulla selezione hardware per il dispositivo di riproduzione {#hardware-selection-guidelines-for-player-device}

La sezione seguente illustra le linee guida per la selezione dell'hardware per un progetto Screens:

* Produrre sempre componenti ***commerciali*** o ***industriali*** sia per il lettore PC che per il pannello di visualizzazione o per il proiettore.

* Interagisci sempre con i fornitori che operano nel mercato del digital signage.
* Considerare sempre fattori ambientali come la temperatura ambiente e l'umidità relativa.
* Controllare sempre i requisiti di alimentazione e il condizionamento.
* Esaminare attentamente le esigenze di prestazioni e le porte I/O necessarie per l'applicazione.

Nella tabella seguente sono riepilogate le configurazioni hardware con i casi di utilizzo tipici per un progetto AEM Screens:

<table>
 <tbody>
  <tr>
   <td>Configurazione del lettore</td>
   <td>Processore</td>
   <td>Memoria</td>
   <td>SSD di storage</td>
   <td>GPU</td>
   <td>Visualizzazione</td>
   <td>I/O</td>
   <td>Casi di utilizzo tipici</td>
  </tr>
  <tr>
   <td>Base</td>
   <td>Processore Intel® Atom dual-core, i3 o quad-core entry-level</td>
   <td><p>4 GB di memoria</p> <p>2 MB di cache</p> </td>
   <td><p>・ ChromeOS 32 GB</p> <p>・ Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI,<br /> Ethernet / Wireless,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Ciclo a schermo intero standard<br /> </li>
     <li>Frazionamento</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Processore quad core, Intel® Core i5</td>
   <td><p>8 GB di memoria</p> <p>4 MB di cache</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Contenuto dinamico sorgente singola</li>
     <li>Semplice interattivo</li>
     <li>1-3 Layout delle aree</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzate</td>
   <td>Quad Core con hyperthreading, processore Intel® Core i7</td>
   <td><p>16 GB di memoria</p> <p>8 MB di cache</p> </td>
   <td>256 GB</td>
   <td>GPU grafica dedicata</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 4 x USB</td>
   <td>
    <ul>
     <li>4 o più aree contenuto, riproduzione video simultanea</li>
     <li>Interattivo multipagina</li>
     <li>Attivatori di dati multi-sorgente</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
