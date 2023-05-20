---
title: Utilizzo di AEM Screens Player
seo-title: Working with Screens Player
description: Segui questa pagina per scoprire di più su Screens Player. Vengono inoltre illustrate l’interfaccia utente di amministrazione e il selettore di canale.
seo-description: Follow this page to learn about Screens Player. It also explains the Admin UI and the Channel Switcher.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# Utilizzo di AEM Screens Player {#working-with-aem-screens-player}

Puoi gestire il contenuto del canale e altre impostazioni in AEM Screens Player.

>[!NOTE]
>
>Premi ***Ctrl+Comando+F*** per uscire dalla modalità a schermo intero per OS X AEM Screens Player.

Dopo aver assegnato un canale a una visualizzazione, AEM Screens Player visualizza il contenuto. Puoi configurare le impostazioni per il lettore utilizzando le preferenze per l’interfaccia utente amministratore (dalla dashboard) oppure dal lettore stesso.

## Utilizzo del dashboard dei dispositivi {#using-the-device-dashboard}

Puoi configurare le preferenze per il dispositivo dalla dashboard dei dispositivi, accessibile tramite l’istanza di authoring AEM.

1. Dal progetto, accedi al dashboard dei dispositivi, ad esempio ***Progetto di prova*** —> ***Dispositivi***.

   Seleziona **Dispositivi** e **Gestione dispositivi** dalla barra delle azioni.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Fai clic sul dispositivo per aprire il dashboard del dispositivo.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Controlla la **PREFERENZE** pannello. È possibile abilitare/disabilitare **Interfaccia utente amministratore** e **Commutatore canale** per il lettore da queste due opzioni.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### Interfaccia utente amministratore {#the-admin-ui}

Abilitazione di **Interfaccia utente amministratore** dal pannello delle preferenze, consente all’utente di aprire le impostazioni di amministrazione da Screens Player. Inoltre, se disattivi questa opzione dal dashboard del dispositivo, l’utente non può aprire l’interfaccia utente di amministrazione dal lettore.

Per visualizzare l’interfaccia utente di amministrazione dal lettore Screens, premi a lungo nell’angolo in alto a sinistra per aprire il menu Amministratore, sul lettore AEM Screens touch o utilizzando un mouse. Mostra le informazioni dopo il completamento della registrazione e il caricamento dei canali.

>[!NOTE]
>
>Inoltre, puoi visualizzare il tempo di attività dell’app AEM Screens Player per verificare lo stato di integrità dell’app.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Accesso alle opzioni del menu di configurazione {#configuration-options}

Puoi aggiornare le configurazioni, se selezioni **Configurazione** dal menu laterale, come illustrato nella figura seguente:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Il menu Configurazione consente di modificare le seguenti impostazioni:

* Reimposta **Firmware**, **Preferenze**, o **In fabbrica** da questa finestra di dialogo.

* Specifica il numero massimo di file di registro da mantenere per un lettore AEM Screens in **N. max. di file di registro da mantenere**.

* Attiva o disattiva **Menu Amministrazione**, **Commutatore canale**, e **Interfaccia attività** per Screens.

   Se il **Interfaccia attività** è abilitato da **Configurazione** AEM Screens Player visualizza il menu *notifiche di attività del lettore* nell’angolo in alto a destra del lettore, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>Il **Aggiorna firmware** L’opzione funziona solo sulla cordova, ad esempio sui lettori Android.

>[!NOTE]
>
>Si consiglia di **Interfaccia utente amministratore** essere disattivato nelle distribuzioni di produzione.

#### Accesso alle opzioni del menu Content Cache {#content-cache-options}

Puoi cancellare la cache per i canali e le applicazioni dall’interfaccia utente di amministrazione nel lettore AEM Screens.

Seleziona la **Cache contenuto** dalla barra laterale per aggiornare la cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Commutatore canale {#the-channel-switcher}

Abilitazione di **Commutatore canale** dal pannello delle preferenze, consente all’utente di aprire la selezione del canale o le impostazioni da Screens Player.

Inoltre, se disattivi questa opzione dal dashboard del dispositivo, l’utente non può controllare le preferenze del canale da Screens Player.

È possibile cambiare e controllare le impostazioni per il canale dal lettore Screens.

Per visualizzare il commutatore di canale dal lettore, premere a lungo nell&#39;angolo inferiore sinistro per aprire il commutatore di canale che consente di cambiare canale e altre funzioni.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>È inoltre possibile abilitare o disabilitare il menu di amministrazione e il selettore di canale per il lettore dal lettore Screens.
>
>(vedere *Modifica preferenze da Screens Player* come indicato nella sezione seguente).

### Gestione delle preferenze da AEM Screens Player {#managing-preferences-from-the-aem-screens-player}

Puoi anche modificare le impostazioni dell’interfaccia utente di amministrazione e del selettore di canale dal lettore stesso.

Per modificare le preferenze del lettore, segui la procedura riportata di seguito:

1. Premi a lungo nell’angolo in alto a sinistra del canale inattivo per aprire il pannello di amministrazione.
1. Accedi a **Configurazione** dal menu Azioni sinistro.
1. Abilita/disabilita configurazione per **Interfaccia utente amministratore** o **Commutatore canale**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Risoluzione dei problemi di AEM Screens Player {#troubleshooting-aem-screens-player}

Puoi risolvere vari problemi associati al lettore AEM Screens (hardware e software):

| **Edizioni** | **Consigli** |
|---|---|
| Spazio di archiviazione del lettore pieno | Eliminazione dei file non necessari |
| Rete persa dal lettore | Utilizzare il cavo Cat-5/Cat-6. Per il wifi, ridurre la distanza tra il router e il dispositivo di riproduzione |
| Arresto anomalo del lettore AEM Screens | Si consiglia di disporre di un’app watchdog che garantisca l’esecuzione continua di AEM Screens Player |
| Impostazioni perse del lettore AEM Screens | Controllare la connessione al server AEM |
| AEM Screens Player non si avvia automaticamente dopo il riavvio o il riavvio del lettore | Controllare la cartella di avvio del sistema operativo o la procedura di inizializzazione |
| AEM Screens Player mostra contenuti errati/obsoleti | Verifica connessione di rete |

### Aggiornamenti per AEM Screens Player {#updates-for-aem-screens-player}

Esistono due tipi di aggiornamenti per AEM Screens Player:

| **Metodo** | **Dettagli** | **tramite remoto** | **Automatizzato** | **0 tempi di inattività** |
|---|---|---|---|---|
| Aggiornamento firmware | Applicato ai lettori installati esistenti tramite comando remoto. Dopo l’aggiornamento, il lettore viene ricaricato automaticamente con il contenuto esistente. | Sì | Personalizzati | Quasi - 1-3 secondi |
| Aggiornamenti della shell del lettore | Questo è un nuovo eseguibile da distribuire in Windows Media Player. A tal fine, è necessario copiare in remoto un nuovo file binario sul lettore, arrestare l&#39;esecuzione corrente e avviare la nuova versione. Potrebbe essere necessario ricaricare il precaricamento dei pacchetti. | Sì (tramite shell remota) | Personalizzati | No |

## Linee guida per la selezione dell&#39;hardware per il dispositivo del lettore {#hardware-selection-guidelines-for-player-device}

La sezione seguente fornisce le linee guida per la selezione dell&#39;hardware per un progetto Screens:

* Sorgente sempre ***Commerciale*** o ***Industriale*** Componenti di livello sia per il lettore PC che per il display o il proiettore.

* Interagisci sempre con i fornitori che operano nel mercato del digital signage.
* Considera sempre fattori ambientali quali la temperatura ambiente e l’umidità relativa.
* Controllare sempre i requisiti di alimentazione e il condizionamento dell&#39;alimentazione.
* Esaminare attentamente le prestazioni richieste e le porte di I/O richieste per l&#39;applicazione.

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
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI<br /> Ethernet/wireless,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Ciclo a schermo intero standard<br /> </li>
     <li>Ripartizione giornaliera</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Quad-core, processore Intel® Core i5</td>
   <td><p>8 GB di memoria</p> <p>4 MB di cache</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet/wireless,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Contenuto dinamico a sorgente singola</li>
     <li>Interattivo semplice</li>
     <li>1-3 Layout di zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzate </td>
   <td>Quad-core con hyperthreading, processore Intel® Core i7</td>
   <td><p>16 GB di memoria</p> <p>8 MB di cache</p> </td>
   <td>256 GB</td>
   <td>GPU grafica dedicata</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet/wireless,<br /> 4x USB</td>
   <td>
    <ul>
     <li>4 o più aree di contenuto, riproduzione video simultanea</li>
     <li>Interattivo a più pagine</li>
     <li>Attivatori dati multi-sorgente</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
