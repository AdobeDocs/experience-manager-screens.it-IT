---
title: Implementazione di Windows Player
description: Informazioni sulla configurazione di Windows Player in AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 1%

---

# Implementazione di Windows Player {#implementing-windows-player}

Questa sezione descrive la configurazione di Windows Player in AEM Screens. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili, nonché consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

## Installazione di Windows Player {#installing-windows-player}

Per implementare Windows Player per AEM Screens, installare Windows Player per AEM Screens.

Visita la pagina [**Download di AEM 6.5 Player**](https://download.macromedia.com/screens/).

>[!NOTE]
>In Windows Player non è disponibile alcuna modalità finestra. È sempre in modalità a schermo intero.

### Configurazione dell’ambiente per AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Configurare un ambiente per Windows Player se si utilizza AEM Screens 6.5.5 Service Pack.

Imposta l&#39;attributo **SameSite per i cookie token di accesso** da **Lax** a **None** da **Console Web Adobe Experience Manager
Configurazione** su tutte le istanze di authoring e pubblicazione di AEM.

Effettua le seguenti operazioni:

1. Passa a **Console Web Adobe Experience Manager
Configurazione** tramite `http://localhost:4502/system/console/configMgr`.

1. Cerca *Gestore autenticazione token Adobe Granite*.

1. Imposta l&#39;attributo **SameSite per i cookie token di accesso** da **Lax** a **None**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.

### Metodo ad hoc {#ad-hoc-method}

Il metodo Ad Hoc consente di installare il Windows Player più recente (*.exe*). Visita la pagina [**Download di AEM 6.5 Player**](https://download.macromedia.com/screens/).

Dopo aver scaricato l’applicazione, segui i passaggi sul lettore per completare l’installazione ad hoc:

1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Passa a **Configurazione** dal menu Azioni a sinistra, immetti il percorso (indirizzo) dell&#39;istanza di AEM a cui desideri connetterti e fai clic su **Salva**.
1. Passa al collegamento **Dispositivo** **Registrazione** dal menu Azioni sinistro per controllare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se lo **Stato** è **REGISTRATO**, il campo **ID dispositivo** è popolato.
>
>Se lo stato **State** è **UNREGISTERED**, è possibile utilizzare il token **Token** per registrare il dispositivo.

## Denominazione di Windows Player {#name-windows}

È possibile assegnare un nome di dispositivo descrittivo a Windows Player, inviando in tal modo il nome di dispositivo assegnato a Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Windows, ma anche di assegnare facilmente il contenuto appropriato.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Dopo la registrazione del lettore, il nome del lettore non può più essere modificato.

Per configurare il nome in Windows Player, eseguire la procedura seguente:

1. Fai clic su **start** > **run**.
1. Immettere `system.cpl`.
1. Utilizzare la scheda Nome computer per impostare il nome host del computer.

## Modifica delle opzioni predefinite in Windows Installer {#changing-default-options}

Seguire questa sezione per apprendere come modificare le opzioni predefinite di Windows Installer e l&#39;elenco delle personalizzazioni disponibili.

## Installazione tramite CLI (PowerShell) {#install-powershell}

1. Crea un percorso personalizzato **dedicato** per Screens Player, ad esempio:
   `C:\Users\User\screens-player`
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

Quando si implementa Windows Player, non è necessario configurare manualmente ogni lettore. Al contrario, puoi aggiornare il file JSON di configurazione dopo averlo testato ed essere pronto per la distribuzione.

La configurazione assicura che tutti i lettori eseguano il ping dello stesso server fornito nel file di configurazione. Registra manualmente ogni lettore.

Per configurare Windows 10 Player, attenersi alla procedura descritta di seguito.

1. Installare Windows Player.
1. Trovare il file di configurazione in ***%appdata%\com.adobe.aem.screens.player\config.json***.
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
| enableOSD | Abilita l’interfaccia utente per cambiare canale affinché gli utenti possano cambiare canale sul dispositivo. Considera di impostarlo su false una volta che è completamente configurato e in produzione. |
| enableActivityUI | Abilita questa opzione affinché tu possa visualizzare l’avanzamento di attività quali download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| cloudMode | Impostare su true se si desidera che Windows Player si connetta a Screens as a Cloud Service. Imposta su false per collegarti ad AMS o ad AEM on-premise. |
| cloudToken | Token di registrazione per la registrazione a Screens as a Cloud Service. |

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

Durante la distribuzione di Windows Player, è importante attivare la modalità Chiosco in modo che sul desktop di Windows non vengano visualizzate altre applicazioni o la barra delle applicazioni.

>[!CAUTION]
>
>Adobe consiglia una soluzione di gestione dei dispositivi per abilitare il chiosco per Windows. Se non disponi di una soluzione di gestione dispositivi per attivare la modalità Kiosk, segui la procedura riportata di seguito. Questo metodo utilizza la funzionalità di avvio della shell disponibile in Windows 10 Enterprise ed Edu. Per attivare il chiosco può essere utilizzato anche qualsiasi altro strumento consigliato da Microsoft per le app non UWP, in particolare per altre edizioni di Windows.

Per attivare la modalità Kiosk (chiosco), procedere come segue:

>[!NOTE]
>
>Prima di seguire la procedura riportata di seguito, assicurarsi di utilizzare Windows 10 Enterprise o Education.

1. Attiva modulo di avvio shell.

   Per ulteriori informazioni, vedere ***Configurare l&#39;utilità di avvio della shell*** nella pagina **[Utilità di avvio della shell](https://learn.microsoft.com/en-us/windows/configuration/shell-launcher/)** del supporto di Microsoft® Windows.

1. Crea un utente non amministrativo (se non ne hai già uno) da utilizzare per il chiosco. Può essere un utente locale o di dominio.
1. Installa Windows Player per l&#39;utente Kiosk dalla pagina [Download del lettore AEM Screens](https://download.macromedia.com/screens/).
1. Consulta [Utilizzare Shell Launcher per creare un chiosco di Windows 10](https://learn.microsoft.com/en-us/windows/configuration/shell-launcher/?tabs=intune) per modificare lo script di PowerShell per ulteriori informazioni.

   Modificare lo script di PowerShell in modo da poter sostituire il nome utente con quello creato. Verificare che il percorso dell&#39;eseguibile dell&#39;applicazione sia corretto. In questo modo la shell personalizzata verrà impostata come applicazione Windows Player per l&#39;utente del chiosco e il file predefinito verrà impostato come explorer.exe per gli altri utenti.

1. Eseguire lo script di PowerShell come amministratore.
1. Riavvia e accedi come l’utente Kiosk e l’applicazione del lettore devono avviarsi subito.

### Risoluzione dei problemi {#troubleshooting}

Se dopo aver effettuato l&#39;accesso come utente Kiosk viene visualizzata una schermata nera, è possibile che il percorso dell&#39;eseguibile di Windows Player non sia stato specificato correttamente. Accedi nuovamente come amministratore, quindi verifica ed esegui nuovamente lo script.

Il percorso di installazione predefinito per Windows Player è:

***C:\Users\&lt;utente>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

Lo script di esempio nei collegamenti abilita e disabilita la shell personalizzata. Pertanto, divide lo script in due e abilita/disabilita le righe applicabili seguenti:

>[!NOTE]
>
>Alcuni ambienti Windows limitano gli script di PowerShell in base ai criteri, in particolare se gli script non sono firmati. Per eseguire lo script, disattivare temporaneamente e riattivare questa restrizione per eseguire lo script. Aprire una finestra di PowerShell e utilizzare questi comandi.
>
>*`set-executionpolicy unrestricted`* - per rimuovere temporaneamente le restrizioni.
>
>*`set-executionpolicy restricted`* - per riattivare la restrizione dopo l&#39;esecuzione dello script.

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Uso del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzionalità: [Controllo remoto Screens](implementing-remote-control.md)