---
title: Utilizzo di  AEM Screens Player
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
source-git-commit: 5aea3e032cc5279de7f3abab679825aa2794a89e
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 43%

---


# Utilizzo di  AEM Screens Player {#working-with-aem-screens-player}

È possibile gestire il contenuto del canale e altre impostazioni sul  AEM Screens Player.

>[!NOTE]
>
>Premi ***Ctrl+Cmd+F*** per uscire dalla modalità a schermo intero per OS X di AEM Screens Player.

Una volta assegnato un canale a una visualizzazione, AEM Screens Player mostra il contenuto. Puoi configurare le impostazioni per il lettore utilizzando le preferenze per l&#39;interfaccia utente dell&#39;amministratore (dal dashboard) o dal lettore stesso.

## Utilizzo del dashboard del dispositivo {#using-the-device-dashboard}

Puoi configurare le preferenze per il dispositivo dal dashboard del dispositivo, accessibile tramite l&#39;istanza di creazione AEM.

1. Andate al dashboard del dispositivo dal progetto, ad esempio ***Test Project*** —> ***Devices***.

   Selezionare **Devices** e **Device Manager** dalla barra delle azioni.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Fai clic sul dispositivo per aprire il dashboard del dispositivo.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Controllare il pannello **PREFERENZE**. È possibile abilitare o disabilitare l&#39; **interfaccia utente amministratore** e **Switcher canale** per il lettore da queste due opzioni.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### Interfaccia utente amministratore {#the-admin-ui}

L&#39;attivazione dell&#39; **interfaccia utente amministratore** dal pannello delle preferenze consente all&#39;utente di aprire le impostazioni dell&#39;amministratore da Screens Player. Inoltre, disabilitando questa opzione dal dashboard del dispositivo, l&#39;utente non può aprire l&#39;interfaccia utente dell&#39;amministratore dal lettore.

Per visualizzare l&#39;interfaccia utente dell&#39;amministratore da Screens Player, tieni premuto nell&#39;angolo in alto a sinistra per aprire il menu dell&#39;amministratore, su AEM Screens Player abilitato al tocco o utilizzando il mouse. Mostra le informazioni dopo che la registrazione è stata completata e i canali sono stati caricati.

>[!NOTE]
>
>Inoltre, puoi visualizzare il tempo di attività dell&#39;applicazione AEM Screens Player per controllare lo stato dell&#39;applicazione.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Accesso alle opzioni del menu di configurazione {#configuration-options}

Se selezionate l&#39;opzione **Configurazione** dal menu laterale, potete aggiornare le configurazioni, come illustrato nella figura seguente:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Il menu Configurazione consente di modificare le seguenti impostazioni:

* Reimpostare **Firmware**, **Preferences** o **To Factory** da questa finestra di dialogo.

* Specificate il numero massimo di file di registro da mantenere per un lettore AEM Screens  in **N. max. dei file di registro da mantenere**.

* Abilitare o disabilitare **Menu Amministratore**, **Switcher canale** e **Interfaccia utente attività** per il lettore Screens.

   Se l&#39; **Interfaccia utente dell&#39;attività** è abilitata dal menu **Configurazione**, il lettore AEM Screens  visualizza le *notifiche dell&#39;attività del lettore* nell&#39;angolo superiore destro del lettore, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>L&#39;opzione **Aggiorna firmware** funziona solo sulla cordova, come i lettori Android.

>[!NOTE]
>
>Si consiglia di disabilitare l&#39; **interfaccia utente amministratore** nelle installazioni di produzione.

#### Accesso alle opzioni del menu Cache contenuto {#content-cache-options}

Puoi cancellare la cache per i canali e le applicazioni dall&#39;interfaccia utente dell&#39;amministratore in AEM Screens Player.

Seleziona la **Cache del contenuto** dalla guida laterale per aggiornare la cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Controllo canali {#the-channel-switcher}

Attivando il **Channel Switcher** dal pannello delle preferenze, l&#39;utente può aprire la selezione dei canali o le impostazioni dal lettore Screens.

Inoltre, disabilitando questa opzione dal dashboard del dispositivo, l&#39;utente non può controllare le preferenze dei canali da Screens Player.

Puoi cambiare e controllare le impostazioni per il canale da Screens Player.

Per visualizzare il controllo canali dal lettore, tenere premuto a lungo nell&#39;angolo in basso a sinistra per aprire il controllo canali che consente di passare da un canale all&#39;altro e ad altre funzioni.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Puoi anche attivare o disattivare il menu dell&#39;amministratore e il controllo canali per il lettore da Screens Player.
>
>(Consulta *Modifica preferenze da Screens Player* come menzionato nella sezione di seguito).

### Gestione delle preferenze da AEM Screens Player  {#managing-preferences-from-the-aem-screens-player}

Puoi anche modificare le impostazioni per l&#39;interfaccia utente dell&#39;amministratore e il controllo canali dal lettore stesso.

Segui questi passaggi per modificare le preferenze dal lettore:

1. Tieni premuto sull&#39;angolo in alto a sinistra del canale inattivo per aprire il pannello di amministrazione.
1. Andate a **Configuration** dal menu delle azioni a sinistra.
1. Attiva/disattiva la configurazione per **Interfaccia utente amministratore** o **Switcher canale**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Risoluzione problemi con AEM Screens Player {#troubleshooting-aem-screens-player}

Puoi risolvere molti problemi associati ad AEM Screens Player (hardware e software):

| **Edizioni** | **Consigli** |
|---|---|
| Archiviazione del lettore completa | Eliminare i file non necessari |
| Rete persa dal lettore | Utilizzare il cavo Cat-5/Cat-6. Per il wifi, ridurre la distanza dal router alla periferica del lettore |
|  AEM Screens Player arrestato | Si consiglia di avere un&#39;app di controllo che assicuri che  AEM Screens Player venga sempre eseguito |
|  AEM Screens Player ha perso le impostazioni | Controllare la connessione al server AEM |
|  AEM Screens Player non si avvia automaticamente dopo il riavvio o il riavvio del lettore | Controllare la cartella iniziale del sistema operativo o la procedura di inizializzazione |
|  AEM Screens Player mostra il contenuto errato | Verifica connessione di rete |

### Aggiornamenti per AEM Screens Player {#updates-for-aem-screens-player}

Esistono due tipi di aggiornamenti per AEM Screens Player:

| **Metodo** | **Dettagli** | **tramite telecomando** | **Automatico** | **0 Download** |
|---|---|---|---|---|
| Aggiornamento firmware | Applicato ai lettori installati esistenti tramite il comando remoto. Dopo l&#39;aggiornamento il lettore si caricherà automaticamente con il contenuto esistente. | Sì | Personalizzata | Quasi 1-3 secondi |
| Aggiornamenti shell Player | Si tratta di un nuovo eseguibile da distribuire sul lettore. Questo tipo di operazione richiede la copia remota del nuovo binario sul lettore, l&#39;arresto dell&#39;esecuzione in corso e l&#39;avvio della nuova versione. Questo potrebbe richiedere un nuovo download del precaricamento dei pacchetti. | Sì (tramite shell remota) | Personalizzata | No |

## Linee guida sulla selezione hardware per il dispositivo lettore {#hardware-selection-guidelines-for-player-device}

La sezione seguente illustra le linee guida per la selezione dell&#39;hardware per un progetto Screens:

* Produrre sempre i componenti ***Commercial*** o ***Industrial*** Grade sia per il lettore PC che per il pannello di visualizzazione o il proiettore.

* Interagisci sempre con i fornitori che operano nel mercato del digital signage.
* Considerare sempre fattori ambientali come la temperatura ambiente e l&#39;umidità relativa.
* Controllare sempre i requisiti di alimentazione e il condizionamento.
* Esaminare attentamente le esigenze di prestazioni e le porte I/O necessarie per l&#39;applicazione.

Nella tabella seguente sono riepilogate le configurazioni hardware con casi di utilizzo tipici per un progetto AEM Screens :

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
   <td>DVI,<br /> Ethernet / Wireless,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Ciclo a schermo intero standard<br /> </li>
     <li>Frazionamento del giorno</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Processore quad core, Intel® Core i5</td>
   <td><p>8 GB di memoria</p> <p>4 MB di cache</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Contenuto dinamico sorgente singola</li>
     <li>Semplice interattivo</li>
     <li>1-3 Layout delle aree</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzate </td>
   <td>Quad Core con hyperthreading, processore Intel® Core i7</td>
   <td><p>16 GB di memoria</p> <p>8 MB di cache</p> </td>
   <td>256 GB</td>
   <td>GPU grafica dedicata</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 4x USB</td>
   <td>
    <ul>
     <li>4 o più aree contenuto, riproduzione video simultanea</li>
     <li>Interattivo multipagina</li>
     <li>Attivatori di dati multi-sorgente</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
