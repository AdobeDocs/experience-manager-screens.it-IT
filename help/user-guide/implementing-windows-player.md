---
title: Implementazione di Windows 10 Player
seo-title: Implementazione di Windows 10 Player
description: Seguite questa pagina per informazioni sulla configurazione  lettore AEM Screens Windows 10.
seo-description: Seguite questa pagina per informazioni sulla configurazione  lettore AEM Screens Windows 10.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: 529bcaf7ded850b8f7fec95d2f85e84c5d79a66a
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 1%

---


# Implementazione di Windows 10 Player {#implementing-windows-player}

Questa sezione descrive la configurazione  lettore AEM Screens Windows 10. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili e consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

## Installazione di Windows Player {#installing-windows-player}

Per implementare Windows Player per  AEM Screens, installare Windows Player per  AEM Screens.

Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

>[!NOTE]
>Nessuna modalità finestra nel lettore Windows. È sempre la modalità a schermo intero.

### Impostazione dell&#39;ambiente per  AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>È necessario configurare un ambiente per Windows Player se si utilizza  AEM Screens 6.5.5 Service Pack.

Impostare l&#39;attributo **SameSite per i cookie di token di login** da **Lax** a **None** dalla **console Web di Adobe Experience Manager
Configurazione** su tutte AEM istanze di creazione e pubblicazione.

Effettua le seguenti operazioni:

1. Passa a **Adobe Experience Manager Web Console
Configurazione** utilizzando `http://localhost:4502/system/console/configMgr`.

1. Cercare *gestore autenticazione token granito Adobe*.

1. Impostate l&#39;attributo **SameSite per i cookie del token di login** da **Lax** a **None**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.

### Metodo ad hoc {#ad-hoc-method}

Il metodo Ad-Hoc consente di installare la versione più recente di Windows Player (*.exe*). Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

Una volta scaricata l’applicazione, seguite i passaggi del lettore per completare l’installazione ad hoc:

1. Tenete premuto sull’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Andate a **Configuration** dal menu delle azioni a sinistra e immettete la posizione (indirizzo) dell&#39;istanza AEM a cui desiderate connettervi e fate clic su **Save**.
1. Andate al collegamento **Dispositivo** **Registrazione** dal menu delle azioni a sinistra per verificare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se **State** è **REGISTERED**, il campo **Device id** verrà popolato.
>
>Se **State** è **UNREGISTERED**, è possibile utilizzare il **Token** per registrare il dispositivo.

## Modifica delle opzioni predefinite in Windows Installer {#changing-default-options}

Seguite questa sezione per apprendere come modificare le opzioni predefinite di Windows Installer e l&#39;elenco delle personalizzazioni disponibili.

## Installazione tramite CLI (PowerShell) {#install-powershell}

1. Create una posizione personalizzata **dedicata** per Screens Player, ad esempio:
   `C:\Users\User\screens-player`)
1. Installare la versione
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. Apri
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**Esempio**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

>[!NOTE]
>
>**Registrazione di massa di Windows Player**
>
>Quando si implementa Windows Player non è necessario configurare manualmente ogni singolo lettore. Al contrario, potete aggiornare il file JSON di configurazione dopo che è stato testato ed è pronto per la distribuzione.
>
>La configurazione assicurerà che tutti i lettori eseguano il ping dello stesso server fornito nel file di configurazione. È comunque necessario registrare manualmente ogni lettore.

Per configurare Windows 10 Player, effettuate le seguenti operazioni:

1. Installare Windows Player.
1. Individuate il file di configurazione in ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Aggiornate il JSON di configurazione utilizzando le informazioni riportate di seguito, quindi copiate la stessa cartella in tutti i sistemi in cui risiede il lettore.

### Attributi del criterio {#policy-attributes}

La tabella seguente riassume gli attributi del criterio con un JSON di esempio per riferimento:

| **Nome criterio** | **Scopo** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| risoluzione | La risoluzione del dispositivo. |
| RestartSchedule | Pianificazione del riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente amministratore per configurare il dispositivo sul sito. Impostato su false una volta configurato completamente e in produzione. |
| enableOSD | Abilitare l&#39;interfaccia utente dello switcher di canale per consentire agli utenti di cambiare canale sul dispositivo. Considerate l&#39;impostazione su false una volta che è completamente configurato e in produzione. |
| enableActivityUI | Consente di visualizzare l&#39;avanzamento delle attività quali il download e la sincronizzazione. Abilitate per la risoluzione dei problemi e disattivate una volta configurato completamente e in produzione. |

#### Esempio di file JSON dei criteri {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## Abilitazione della modalità Kiosk {#enabling-kiosk-mode}

Quando si distribuisce il lettore Windows, è importante abilitare una modalità Kiosk in modo che altre applicazioni o la barra delle applicazioni non vengano visualizzate sul desktop di Windows.

>[!CAUTION]
>
> Adobe consiglia una soluzione di gestione dispositivi per abilitare Kiosk per Windows. Se non disponete di una soluzione di gestione dispositivo per abilitare la modalità Kiosk, eseguite i passaggi indicati di seguito. Questo metodo utilizza la funzionalità Shell Launcher disponibile in Windows 10 Enterprise ed Edu. Qualsiasi altro metodo consigliato da Microsoft per le app non UWP può essere applicato anche per abilitare il chiosco, specialmente su altre edizioni di Windows.

Per attivare la modalità Kiosk, effettuate le seguenti operazioni:

>[!NOTE]
>
>Prima di procedere come segue, assicurarsi di utilizzare Windows 10 Enterprise o Education.

1. Abilita il lancio della shell.

   Fare riferimento alla sezione ***Configura il lanciatore shell*** in **[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** della pagina del supporto di Microsoft Windows per ulteriori informazioni.

1. Create un utente non amministrativo (se non ne avete già uno) da utilizzare per il chiosco. Può essere un utente locale o di dominio.
1. Installare il lettore Windows per l&#39;utente Kiosk dalla pagina [ Download di AEM Screens Player](https://download.macromedia.com/screens/).
1. Fare riferimento a [Utilizzare Shell Launcher per creare un chiosco Windows 10](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) per modificare lo script PowerShell per ulteriori informazioni.

   Modificare lo script PowerShell per sostituire il nome utente con quello creato. Verificare che il percorso dell&#39;applicazione eseguibile sia corretto. Questo imposterà la shell personalizzata come applicazione Windows Player per l&#39;utente kiosk e imposta il valore predefinito come explorer.exe per gli altri utenti.

1. Eseguire lo script PowerShell come amministratore.
1. Riavviate e accedete come l&#39;utente Kiosk e l&#39;applicazione del lettore dovrebbero iniziare immediatamente.

### Risoluzione dei problemi {#troubleshooting}

Se si ottiene una schermata nera quando si accede come utente Kiosk, significa che si potrebbe aver specificato erroneamente il percorso del lettore Windows eseguibile. Accedete nuovamente come amministratore e verificate ed eseguite nuovamente lo script.

Il percorso di installazione predefinito per Windows Player è:

***C:\Users\&amp;lt;your user>\AppData\Local\Programs\@aem-screensscreens-player-Electron\ AEM Screens Player.exe***

Lo script di esempio nei collegamenti attiverà e disattiverà la shell personalizzata. Potrebbe quindi essere necessario dividere lo script in due e attivare/disattivare le righe applicabili seguenti:

>[!NOTE]
>
>In alcuni ambienti di Windows, gli script PowerShell possono essere limitati dai criteri (in particolare dagli script non firmati). Per eseguire lo script potrebbe essere necessario disattivare temporaneamente e riabilitare questa limitazione per eseguire lo script. Aprire una finestra di PowerShell e utilizzare questi comandi.
>
>*set-execute policy illimitato*  - per rimuovere temporaneamente le restrizioni
>
>*set-execute policy limitato* : per riabilitare la restrizione dopo l&#39;esecuzione dello script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

