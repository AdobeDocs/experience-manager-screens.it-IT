---
title: Implementazione di Android&trade; Player
description: Scopri l’implementazione di Android&trade; Watchdog, una soluzione che consente di recuperare Android&trade; player dagli arresti anomali.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 45b9fce303989e2c090775131dd6188053053fc8
workflow-type: tm+mt
source-wordcount: '1497'
ht-degree: 0%

---

# Implementazione di Android™ Player {#implementing-android-player}

>[!CAUTION]
>Adobe consiglia di eseguire l’aggiornamento alla versione più recente di Adobe Experience Manager 6.5 (AEM 6.5). Puoi ottenere le informazioni sulla versione più recente da [qui](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/release-notes/release-notes).

Questa sezione descrive come configurare il lettore Android™. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili, nonché consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

Inoltre, **Watchdog** è una soluzione per recuperare il lettore dagli arresti anomali. Un&#39;applicazione deve registrarsi presso il servizio di watchdog e quindi inviare periodicamente messaggi al servizio per informarlo che è attiva. Nel caso in cui il servizio watchdog non riceva un messaggio keep-alive entro il tempo stabilito, il servizio tenta di riavviare il dispositivo. Questa operazione viene eseguita per un ripristino pulito (se dispone dei privilegi sufficienti) o per riavviare l&#39;applicazione.

## Installazione di Android™ Player {#installing-android-player}

Per implementare Android™ Player for AEM Screens, installa Android™ Player for AEM Screens.

Visita la pagina [**Download di AEM 6.5 Player**](https://download.macromedia.com/screens/).

### Configurazione dell’ambiente per AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Se utilizzi AndroidAEM Screens ™ 6.5.5 Service Pack, imposta un ambiente per il lettore.

Imposta l&#39;attributo **SameSite per i cookie token di accesso** da **Lax** a **None** da **Configurazione console Web Adobe Experience Manager** in tutte le istanze di authoring e pubblicazione di AEM.

Effettua le seguenti operazioni:

1. Passare a **Configurazione console Web Adobe Experience Manager** utilizzando `http://localhost:4502/system/console/configMgr`.

1. Cerca *Gestore autenticazione token Adobe Granite*.

1. Imposta l&#39;attributo **SameSite per i cookie token di accesso** da **Lax** a **None**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.


### Metodo Ad Hoc {#ad-hoc-method}

Il metodo Ad Hoc consente di installare il lettore Android™ più recente (*.exe*). Visita la pagina [**Download di AEM 6.5 Player**](https://download.macromedia.com/screens/).

Dopo aver scaricato l’applicazione, segui i passaggi sul lettore per completare l’installazione ad hoc:

1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Passa a **Configurazione** dal menu Azioni a sinistra, immetti il percorso (indirizzo) dell&#39;istanza di AEM a cui desideri connetterti e fai clic su **Salva**.

1. Passa al collegamento **Dispositivo** **Registrazione** dal menu Azioni sinistro per controllare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se lo **Stato** è **REGISTRATO**, il campo **ID dispositivo** è popolato.
>
>Se lo stato **State** è **UNREGISTERED**, è possibile utilizzare il token **Token** per registrare il dispositivo.

## Implementazione di Android™ Watchdog {#implementing-android-watchdog}

A causa dell&#39;architettura di Android™, il riavvio del dispositivo richiede che l&#39;applicazione disponga dei privilegi di sistema. Firma l’apk utilizzando i tasti di firma del produttore, altrimenti il watchdog può riavviare l’applicazione del lettore e non il dispositivo.

### Segnaletica di Android™ `apks` tramite chiavi del produttore {#signage-of-android-apks-using-manufacturer-keys}

Per accedere ad alcune delle API con privilegi di Android™, ad esempio *PowerManager* o *HDMIControlServices*, firmare Android™ `apk` utilizzando le chiavi del produttore.

>[!CAUTION]
>
>Prerequisiti:
>
>Prima di eseguire la procedura seguente, è necessario aver installato Android™ SDK.

Segui i passaggi seguenti per firmare il pacchetto Android™ utilizzando i tasti del produttore:

1. Scarica l&#39;apk da Google Play o dalla pagina [Download del lettore AEM Screens](https://download.macromedia.com/screens/)
1. Ottieni le chiavi della piattaforma dal produttore in modo da ottenere un file *pk8* e un file *pem*

1. Individuare lo strumento `apksigner` in Android™ SDK utilizzando Trova `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Trova il percorso dello strumento allineamento zip in Android™ SDK
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. Installa ***aemscreensaligned.apk*** tramite l&#39;installazione adb nel dispositivo

## Informazioni su Android™ Watchdog Services {#android-watchdog-services}

Il servizio watchdog cross-Android™ è implementato come plug-in Cordova utilizzando *AlarmManager*.

Il diagramma seguente mostra l’implementazione del servizio watchdog:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inizializzazione** - Al momento dell&#39;inizializzazione del plug-in Cordova, le autorizzazioni vengono verificate per verificare se si dispone dei privilegi di sistema e quindi dell&#39;autorizzazione di riavvio. Se questi due criteri sono soddisfatti, viene creato un Intento in sospeso per il riavvio, altrimenti viene creato un Intento in sospeso per il riavvio dell&#39;applicazione (in base alla relativa attività di avvio).

**2. Keep Alive Timer** - Viene utilizzato un timer keep alive per attivare un evento ogni 15 secondi. In questo caso, annulla l’intento in sospeso esistente (per riavviare o riavviare l’app) e registra un nuovo intento in sospeso per gli stessi 60 secondi in futuro (essenzialmente posticipando il riavvio).

>[!NOTE]
>
>In Android™, *AlarmManager* viene utilizzato per registrare *pendingIntents* che può essere eseguito anche se l&#39;app si è arrestata in modo anomalo e la consegna dell&#39;allarme non è esatta dall&#39;API 19 (Kitkat). Mantieni una spaziatura tra l&#39;intervallo del timer e l&#39;avviso *di* *pendingIntent di* AlarmManager.

**3. Arresto anomalo dell&#39;applicazione** - Se si verifica un arresto anomalo, l&#39;oggetto pendingIntent per il riavvio registrato con AlarmManager non viene più reimpostato. Esegue quindi il riavvio o il riavvio dell&#39;app (a seconda delle autorizzazioni disponibili al momento dell&#39;inizializzazione del plug-in Cordova).

## Provisioning in blocco di Android™ Player {#bulk-provision-android-player}

Quando si esegue il rollout in massa del lettore Android™, è necessario eseguire il provisioning del lettore in modo che punti a un’istanza di AEM e configurare altre proprietà senza immetterle manualmente nell’interfaccia utente di amministrazione.

>[!NOTE]
>Questa funzione è disponibile dal lettore Android™ 42.0.372.

Segui i passaggi seguenti per consentire il provisioning in blocco nel lettore Android™:

1. Creare un file JSON di configurazione denominato `player-config.default.json`.
Vedere un [Esempio di criteri JSON](#example-json) e una tabella che descrive l&#39;utilizzo dei vari [attributi dei criteri](#policy-attributes).

1. Utilizza uno strumento di esplorazione file MDM, ADB o Android™ Studio per rilasciare questo file JSON per i criteri nella cartella *sdcard* sul dispositivo Android™.

1. Quando il file viene distribuito, utilizzare MDM per installare l&#39;applicazione del lettore.

1. All’avvio dell’applicazione del lettore, questo file di configurazione viene letto e punta al server AEM applicabile in cui viene registrato e quindi controllato.

   >[!NOTE]
   >Il file è *di sola lettura* al primo avvio dell&#39;applicazione e non può essere utilizzato per le configurazioni successive. Se il lettore viene avviato prima dell&#39;eliminazione del file di configurazione, è sufficiente disinstallare e reinstallare l&#39;applicazione sul dispositivo.

### Attributi dei criteri {#policy-attributes}

La tabella seguente riepiloga gli attributi dei criteri con un esempio di JSON per i criteri a scopo di riferimento:

| **Nome criterio** | **Scopo** |
|---|---|
| *server* | URL del server Adobe Experience Manager. |
| *risoluzione* | Risoluzione del dispositivo. |
| *riavviaPianificazione* | La pianificazione per il riavvio si applica a tutte le piattaforme. |
| *enableAdminUI* | Abilita l’interfaccia utente di amministrazione per configurare il dispositivo sul sito. Imposta su *false* una volta che è completamente configurato e in produzione. |
| *enableOSD* | Abilita l’interfaccia utente per cambiare canale affinché gli utenti possano cambiare canale sul dispositivo. Considera di impostarlo su *false* dopo che è stato completamente configurato e in produzione. |
| *enableActivityUI* | Abilita questa opzione se desideri visualizzare l’avanzamento di attività quali download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| *enableNativeVideo* | Attiva se desideri utilizzare l’accelerazione hardware nativa per la riproduzione video (solo Android™). |

### Esempio di criterio JSON {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>Tutti i dispositivi Android™ hanno una cartella `*sdcard*`, sia che sia stato inserito o meno un `*sdcard*` effettivo. Quando viene distribuito, questo file si trova allo stesso livello della cartella Download. Alcuni MDM, come Samsung Knox, potrebbero visualizzare la cartella *sdcard* come *memoria interna*.

## Provisioning in blocco di Android™ Player tramite Enterprise Mobility Management {#bulk-provisioning}

Quando si distribuisce in massa il lettore Android™, diventa noioso registrare ogni lettore manualmente con AEM. Utilizzare una soluzione EMM (Enterprise Mobility Management) come [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), MobileIron o Samsung Knox per eseguire il provisioning e gestire l&#39;installazione in remoto. AEM Screens Android™ Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.

## Denominazione di Android™ Player {#name-android}

Puoi assegnare un nome descrittivo del dispositivo al lettore Android™, inviando in tal modo il nome assegnato ad AEM (Adobe Experience Manager). Questa funzionalità consente non solo di denominare il lettore Android™, ma anche di assegnare facilmente il contenuto appropriato.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Dopo la registrazione del lettore, il nome del lettore non può più essere modificato.

Segui i passaggi seguenti per configurare il nome nel lettore Android™:

1. Passa a **impostazioni** > **Informazioni sul dispositivo**
1. Modifica e imposta il nome del dispositivo per denominare il lettore Android™

### Implementazione del provisioning in blocco di Android™ Player tramite Enterprise Mobility Management {#implementation}

Segui i passaggi seguenti per consentire il provisioning in blocco in Android™ Player:

1. Assicurati che il tuo dispositivo Android™ supporti i servizi Google Play.
1. Iscrivi i dispositivi di riproduzione Android™ con la tua soluzione EMM preferita che supporta AppConfig.
1. Accedi alla console EMM e richiama l’applicazione AEM Screens Player da Google Play.
1. Fai clic sulla configurazione gestita o sull’opzione correlata.
1. A questo punto dovrebbe essere visualizzato un elenco di opzioni del lettore che possono essere configurate, ad esempio il codice di registrazione del server e in blocco.
1. Configura questi parametri, salva e distribuisci il criterio nei dispositivi.

   >[!NOTE]
   >I dispositivi devono ricevere l&#39;applicazione insieme alla configurazione. Deve puntare al server AEM corretto con la configurazione selezionata. Se hai scelto di configurare il codice di registrazione in blocco mantenendolo invariato rispetto a quello configurato in AEM, il lettore dovrebbe essere in grado di registrarsi automaticamente. Se hai configurato una visualizzazione predefinita, questa può anche scaricare e mostrare alcuni contenuti predefiniti (che possono essere successivamente modificati per comodità).

Inoltre, devi verificare con il fornitore EMM il supporto di AppConfig. I più popolari tra cui [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) e [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) supportano questo standard di settore.

### Uso del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzionalità: [Controllo remoto Screens](implementing-remote-control.md)
