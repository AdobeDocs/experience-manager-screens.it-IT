---
title: Implementazione di Windows 10 Player
seo-title: Implementazione di Windows 10 Player
description: Segui questa pagina per informazioni sulla configurazione di AEM Screens Windows 10 Player.
seo-description: Segui questa pagina per informazioni sulla configurazione di AEM Screens Windows 10 Player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 1%

---


# Implementazione di Windows 10 Player {#implementing-windows-player}

Questa sezione descrive la configurazione di AEM Screens Windows 10 Player. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili e fornisce raccomandazioni sulle impostazioni da utilizzare per lo sviluppo e il test.

## Installazione di Windows Player {#installing-windows-player}

Per implementare Windows Player per AEM Screens, installare Windows Player per AEM Screens.

Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

>[!NOTE]
>Non è disponibile una modalità finestra in Windows Player. È sempre in modalità a schermo intero.

### Configurazione dell&#39;ambiente per AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Se si utilizza AEM Screens 6.5.5 Service Pack, è necessario configurare un ambiente per Windows Player.

Imposta l&#39;attributo **SameSite per i cookie login-token** da **Lax** a **None** dalla **Console Web Adobe Experience Manager
Configurazione** su tutte le istanze di authoring e pubblicazione AEM.

Effettua le seguenti operazioni:

1. Passa a **Console web Adobe Experience Manager
Configurazione** utilizzando `http://localhost:4502/system/console/configMgr`.

1. Cerca *Adobe gestore autenticazione token di Granite*.

1. Imposta l&#39;attributo **SameSite per i cookie login-token** da **Lax** a **None**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.

### Metodo ad hoc {#ad-hoc-method}

Il metodo Ad-Hoc consente di installare l&#39;ultimo Windows Player (*.exe*). Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

Una volta scaricata l&#39;applicazione, segui i passaggi sul lettore per completare l&#39;installazione ad-hoc:

1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Passa a **Configurazione** dal menu di azione a sinistra e immetti la posizione (indirizzo) dell&#39;istanza AEM a cui desideri connetterti e fai clic su **Salva**.
1. Passa al collegamento **Dispositivo** **Registrazione** dal menu di azione a sinistra per controllare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se il campo **Stato** è **REGISTRATO**, noterai che il campo **ID dispositivo** sarà popolato.
>
>Se il **Stato** è **NON REGISTRATO**, puoi utilizzare il **Token** per registrare il dispositivo.

## Modifica delle opzioni predefinite in Windows Installer {#changing-default-options}

Seguire questa sezione per scoprire come modificare le opzioni predefinite in Windows Installer e l&#39;elenco delle personalizzazioni disponibili.

## Installazione tramite CLI (PowerShell) {#install-powershell}

1. Crea una posizione personalizzata **dedicata** per Screens Player, ad esempio:
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

## Registrazione in blocco di Windows Player {#bulk-registration}

Quando si implementa Windows Player, non è necessario configurare manualmente ogni singolo lettore. Al contrario, puoi aggiornare il file JSON di configurazione dopo che è stato testato ed è pronto per la distribuzione.

La configurazione assicurerà che tutti i lettori eseguano il ping dello stesso server fornito nel file di configurazione. È comunque necessario registrare manualmente ogni lettore.

Segui i passaggi seguenti per configurare Windows 10 Player:

1. Installare Windows Player.
1. Trova il file di configurazione in ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Aggiorna la configurazione JSON utilizzando le informazioni riportate di seguito, quindi copia la stessa cartella in tutti i sistemi in cui risiede il lettore.

### Attributi dei criteri {#policy-attributes}

La tabella seguente riepiloga gli attributi del criterio con un esempio di codice JSON per riferimento:

| **Nome criterio** | **Scopo** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| risoluzione | La risoluzione del dispositivo. |
| RestartSchedule | Pianificazione del riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente amministratore per configurare il dispositivo sul sito. Imposta su false una volta configurato completamente e in produzione. |
| enableOSD | Abilita l’interfaccia utente del commutatore del canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false una volta configurata completamente e in produzione. |
| enableActivityUI | Attiva per mostrare l&#39;avanzamento delle attività come il download e la sincronizzazione. Attiva per la risoluzione dei problemi e disattiva una volta configurato completamente e in produzione. |

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

Quando si distribuisce Windows Player, è importante attivare la modalità Kiosk in modo che altre applicazioni o la barra delle applicazioni non vengano visualizzate sul desktop Windows.

>[!CAUTION]
>
>Adobe consiglia una soluzione di gestione dispositivi per abilitare Kiosk per Windows. Segui i passaggi seguenti, se non disponi di una soluzione di gestione dispositivi per abilitare la modalità Kiosk. Questo metodo utilizza la funzione di avvio della shell disponibile in Windows 10 Enterprise ed Edu. Qualsiasi altro mezzo Microsoft consigliato per applicazioni non UWP può anche essere applicato per abilitare Kiosk, specialmente su altre edizioni di Windows.

Per attivare la modalità Kiosk, effettua le seguenti operazioni:

>[!NOTE]
>
>Prima di seguire i passaggi seguenti, assicurarsi di utilizzare Windows 10 Enterprise o Education.

1. Abilita Shell Launcher.

   Per ulteriori informazioni, consulta la sezione ***Configurare Shell Launcher*** nella pagina **[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** del supporto di Microsoft Windows.

1. Crea un utente non amministrativo (se non ne hai già uno) da utilizzare per il chiosco. Può essere un utente locale o di dominio.
1. Installa il lettore Windows per l&#39;utente Kiosk dalla pagina [Download di AEM Screens Player](https://download.macromedia.com/screens/) .
1. Fare riferimento a [Utilizzare Shell Launcher per creare un chiosco Windows 10](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) per modificare lo script PowerShell per ulteriori informazioni.

   Modificare lo script PowerShell per sostituire il nome utente con quello creato. Verificare che il percorso dell&#39;eseguibile dell&#39;applicazione sia corretto. Questo imposterà la shell personalizzata come applicazione windows player per l&#39;utente chiosco e imposta il valore predefinito come explorer.exe per altri utenti.

1. Eseguire lo script PowerShell come amministratore.
1. Riavvia e accedi come l&#39;utente Kiosk e l&#39;applicazione del lettore dovrebbero essere avviati subito.

### Risoluzione dei problemi {#troubleshooting}

Se ottieni una schermata nera quando accedi come utente Kiosk, significa che potresti aver specificato il percorso del eseguibile di windows player in modo errato. Accedi nuovamente come amministratore e verifica ed esegui nuovamente lo script.

Il percorso di installazione predefinito per Windows Player è:

***C:\Users\&amp;lt;your user>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

Lo script di esempio nei collegamenti attiverà e disattiverà la shell personalizzata. Quindi potrebbe essere necessario dividere lo script in due e abilitare/disabilitare le righe applicabili seguenti:

>[!NOTE]
>
>In alcuni ambienti Windows gli script PowerShell possono essere limitati da criteri (in particolare da script non firmati). Per eseguire lo script potrebbe essere necessario disattivare temporaneamente e riattivare questa restrizione per eseguire lo script. Aprire una finestra di PowerShell e utilizzare questi comandi.
>
>*set-execute policy illimitato*  - per rimuovere temporaneamente le restrizioni
>
>*set-execute policy limitato*  - per riabilitare la restrizione dopo l&#39;esecuzione dello script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

