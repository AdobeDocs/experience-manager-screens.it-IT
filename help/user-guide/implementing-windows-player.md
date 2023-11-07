---
title: Implementazione di Windows 10 Player
seo-title: Implementing Windows 10 Player
description: Segui questa pagina per scoprire come configurare il lettore AEM Screens Windows 10.
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 970762bb08f19ab07917dd5a21f67a007ec1143f
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 1%

---

# Implementazione di Windows 10 Player {#implementing-windows-player}

In questa sezione viene descritta la configurazione di AEM Screens Windows 10 Player. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili, nonché consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

## Installazione di Windows Player {#installing-windows-player}

Per implementare Windows Player per AEM Screens, installare Windows Player per AEM Screens.

Visita il [**Download del lettore AEM 6.5**](https://download.macromedia.com/screens/) pagina.

>[!NOTE]
>Nessuna modalità finestra in Windows Player. È sempre in modalità a schermo intero.

### Configurazione dell’ambiente per AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Se utilizzi AEM Screens 6.5.5 Service Pack, devi configurare un ambiente per Windows Player.

Imposta il **Attributo SameSite per i cookie del token di accesso** da **Lax** a **Nessuno** da **Configurazione console Web Adobe Experience Manager** su tutte le istanze di authoring e pubblicazione AEM.

Effettua le seguenti operazioni:

1. Accedi a **Configurazione console Web Adobe Experience Manager** utilizzo `http://localhost:4502/system/console/configMgr`.

1. Cerca *Adobe Gestore autenticazione token Granite*.

1. Imposta il **Attributo SameSite per i cookie del token di accesso** da **Lax** a **Nessuno**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.

### Metodo ad hoc {#ad-hoc-method}

Il metodo Ad Hoc consente di installare la versione più recente di Windows Player (*.exe*). Visita [**Download del lettore AEM 6.5**](https://download.macromedia.com/screens/) pagina.

Dopo aver scaricato l’applicazione, segui i passaggi sul lettore per completare l’installazione ad hoc:

1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Accedi a **Configurazione** dal menu Azioni sinistro, inserisci la posizione (indirizzo) dell’istanza AEM a cui desideri connetterti e fai clic su **Salva**.
1. Accedi a **Dispositivo** **Registrazione** dal menu Azioni sinistro per controllare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se il **Stato** è **REGISTRATO**, noterai la **ID dispositivo** verrà compilato.
>
>Se il **Stato** è **NON REGISTRATO**, è possibile utilizzare **Token** per registrare il dispositivo.

## Denominazione di Windows Player {#name-windows}

È possibile assegnare un nome di dispositivo descrittivo al lettore di Windows, inviando in tal modo il nome di dispositivo assegnato a Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Windows, ma anche di assegnare facilmente il contenuto appropriato.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Una volta registrato, il nome del lettore non può più essere modificato.

Segui i passaggi seguenti per configurare il nome in Windows Player:

1. Fai clic su **inizio** —> **eseguire**
1. Inserisci `system.cpl`
1. Utilizzare la scheda Nome computer per impostare il nome host del computer

## Modifica delle opzioni predefinite in Windows Installer {#changing-default-options}

Seguire questa sezione per scoprire come modificare le opzioni predefinite di Windows Installer e l&#39;elenco delle personalizzazioni disponibili.

## Installazione tramite CLI (PowerShell) {#install-powershell}

1. Creare una posizione personalizzata **dedicato** per Screens Player, ad esempio:
   `C:\Users\User\screens-player`)
1. Installa
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

Quando si implementa Windows Player, non è necessario configurare manualmente ogni singolo lettore. Al contrario, puoi aggiornare il file JSON di configurazione dopo averlo testato ed essere pronto per la distribuzione.

La configurazione assicurerà che tutti i lettori eseguano il ping dello stesso server fornito nel file di configurazione. È comunque necessario registrare manualmente ogni lettore.

Per configurare Windows 10 Player, attenersi alla procedura descritta di seguito.

1. Installare Windows Player.
1. Trova il file di configurazione in ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Aggiorna il JSON di configurazione utilizzando le informazioni riportate di seguito, quindi copia la stessa cartella in tutti i sistemi in cui risiede il lettore.

### Attributi dei criteri {#policy-attributes}

La tabella seguente riepiloga gli attributi dei criteri con un esempio di JSON per i criteri a scopo di riferimento:


| **Nome criterio** | **Scopo** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| registrationKey | Utilizzato per la registrazione in blocco di dispositivi utilizzando una chiave già condivisa. |
| risoluzione | Risoluzione del dispositivo. |
| rebootSchedule | Pianificazione per il riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente di amministrazione per configurare il dispositivo sul sito. Impostato su false una volta che è completamente configurato e in produzione. |
| enableOSD | Abilita l’interfaccia utente per cambiare canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false, una volta che è completamente configurato e in produzione. |
| enableActivityUI | Abilita questa opzione per mostrare l’avanzamento di attività come download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| cloudMode | Imposta su true se desideri che il lettore Tizen si connetta a Screens as a Cloud Service. Impostare su false per connettersi a AMS o a un AEM locale. |
| cloudToken | Token di registrazione da registrare su Screens as a Cloud Service. |

#### Esempio di file JSON del criterio {#example-policy-json-file}

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

## Abilitazione della modalità Kiosk (chiosco) {#enabling-kiosk-mode}

Quando si distribuisce il lettore Windows, è importante attivare la modalità Chiosco in modo che sul desktop di Windows non vengano visualizzate altre applicazioni o la barra delle applicazioni.

>[!CAUTION]
>
>L&#39;Adobe consiglia una soluzione di gestione dei dispositivi per abilitare Kiosk per Windows. Se non disponi di una soluzione di gestione dispositivi per attivare la modalità Kiosk, segui la procedura riportata di seguito. Questo metodo utilizza la funzionalità di avvio della shell disponibile in Windows 10 enterprise ed Edu. Qualsiasi altro mezzo consigliato da Microsoft per le app non UWP può essere applicato per abilitare Kiosk specialmente su altre edizioni di Windows.

Per attivare la modalità Kiosk (chiosco), procedere come segue:

>[!NOTE]
>
>Prima di seguire la procedura riportata di seguito, assicurarsi di utilizzare Windows 10 Enterprise o Education.

1. Attiva modulo di avvio shell.

   Consulta la sezione ***Configura modulo di avvio shell*** in **[Modulo di avvio shell](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** pagina del supporto di Microsoft per ulteriori informazioni.

1. Crea un utente non amministrativo (se non ne hai già uno) da utilizzare per il chiosco. Può essere un utente locale o di dominio.
1. Installare il lettore Windows per l&#39;utente Kiosk da [Download di AEM Screens Player](https://download.macromedia.com/screens/) pagina.
1. Fai riferimento a [Utilizza Shell Launcher per creare un chiosco Windows 10](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) per modificare lo script di PowerShell per ulteriori informazioni.

   Modificare lo script di PowerShell in modo da sostituire il nome utente con quello creato. Verificare che il percorso dell&#39;eseguibile dell&#39;applicazione sia corretto. La shell personalizzata verrà impostata come applicazione Windows Player per l&#39;utente del chiosco e quella predefinita come explorer.exe per gli altri utenti.

1. Eseguire lo script di PowerShell come amministratore.
1. Riavvia e accedi come l’utente Kiosk e l’applicazione del lettore devono avviarsi subito.

### Risoluzione dei problemi {#troubleshooting}

Se quando accedi come utente Kiosk viene visualizzata una schermata nera, significa che potresti aver specificato in modo errato il percorso dell’eseguibile di Windows Player. Accedi nuovamente come amministratore, quindi verifica ed esegui nuovamente lo script.

Il percorso di installazione predefinito per Windows Player è:

***C:\Users\&amp;lt;utente>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

Lo script di esempio nei collegamenti attiverà e disabiliterà la shell personalizzata. Di conseguenza, potrebbe essere necessario suddividere lo script in due e abilitare/disabilitare le righe applicabili seguenti:

>[!NOTE]
>
>In alcuni ambienti Windows gli script di PowerShell possono essere limitati da criteri (in particolare gli script non firmati). Per eseguire lo script potrebbe essere necessario disattivare temporaneamente e riattivare questa restrizione per eseguire lo script. Aprire una finestra di PowerShell e utilizzare questi comandi.
>
>*set-execution policy senza restrizioni* - per rimuovere temporaneamente le restrizioni
>
>*set-execution policy limitato* - per riattivare la restrizione dopo l&#39;esecuzione dello script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Utilizzo del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzione qui: [Controllo remoto Schermi](implementing-remote-control.md)