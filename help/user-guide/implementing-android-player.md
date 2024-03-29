---
title: Implementazione di Android Player
seo-title: Implementation of Android Player
description: Segui questa pagina per scoprire l’implementazione di Android Watchdog, una soluzione per recuperare il lettore dagli arresti anomali.
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# Implementazione di Android Player {#implementing-android-player}

Questa sezione descrive come configurare il lettore Android. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili, nonché consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

Inoltre, **Watchdog** è una soluzione per recuperare il lettore dagli arresti anomali. Un’applicazione deve registrarsi presso il servizio di watchdog e quindi inviare periodicamente messaggi al servizio per informarlo che è attiva. Nel caso in cui il servizio watchdog non riceva un messaggio keep-alive entro il tempo stabilito, il servizio tenta di riavviare il dispositivo per un ripristino pulito (se dispone dei privilegi sufficienti) o riavviare l&#39;applicazione.

## Installazione di Android Player {#installing-android-player}

Per implementare Android Player per AEM Screens, installa Android Player per AEM Screens.

Visita il [**Download del lettore AEM 6.5**](https://download.macromedia.com/screens/) pagina.

### Configurazione dell’ambiente per AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Devi impostare un ambiente per il lettore Android se utilizzi AEM Screens 6.5.5 Service Pack.

Imposta il **Attributo SameSite per i cookie del token di accesso** da **Lax** a **Nessuno** da **Configurazione della console web Adobe Experience Manager** su tutte le istanze di authoring e pubblicazione AEM.

Effettua le seguenti operazioni:

1. Accedi a **Configurazione della console web Adobe Experience Manager** utilizzo `http://localhost:4502/system/console/configMgr`.

1. Cerca *Adobe Gestore autenticazione token Granite*.

1. Imposta il **Attributo SameSite per i cookie del token di accesso** da **Lax** a **Nessuno**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.


### Metodo Ad Hoc {#ad-hoc-method}

Il metodo Ad Hoc consente di installare il lettore Android più recente (*.exe*). Visita [**Download del lettore AEM 6.5**](https://download.macromedia.com/screens/) pagina.

Dopo aver scaricato l’applicazione, segui i passaggi sul lettore per completare l’installazione ad hoc:

1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Accedi a **Configurazione** dal menu Azioni sinistro, inserisci la posizione (indirizzo) dell’istanza AEM a cui desideri connetterti e fai clic su **Salva**.

1. Accedi a **Dispositivo** **Registrazione** dal menu Azioni sinistro per controllare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se il **Stato** è **REGISTRATO**, noterai la **ID dispositivo** verrà compilato.
>
>Se il **Stato** è **NON REGISTRATO**, è possibile utilizzare **Token** per registrare il dispositivo.

## Implementazione di Android Watchdog {#implementing-android-watchdog}

A causa dell&#39;architettura di Android, il riavvio del dispositivo richiede che l&#39;applicazione disponga di privilegi di sistema. A questo scopo, devi firmare l’app utilizzando i tasti di firma del produttore, altrimenti watchdog riavvia l’applicazione del lettore e non il dispositivo.

### Segnaletica di app Android tramite chiavi del produttore {#signage-of-android-apks-using-manufacturer-keys}

Per accedere ad alcune delle API privilegiate di Android, ad esempio *PowerManager* o *HDMIControlServices*, è necessario firmare l&#39;apk android utilizzando i tasti del produttore.

>[!CAUTION]
>
>Prerequisiti:
>
>Dovresti aver installato l’SDK per Android prima di eseguire i seguenti passaggi.

Segui i passaggi seguenti per firmare l&#39;apk android utilizzando i tasti del produttore:

1. Scarica l’app da Google Play o da [Download di AEM Screens Player](https://download.macromedia.com/screens/) pagina
1. Ottenere le chiavi della piattaforma dal produttore per ottenere un *pk8* e un *pem* file

1. Individua lo strumento apksigner nell’sdk Android utilizzando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —chiave platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Trovare il percorso dello strumento di allineamento zip nell&#39;SDK di Android
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Installa ***aemscreensaligned.apk*** utilizzo dell&#39;installazione adb sul dispositivo

## Informazioni sui servizi di watchdog per Android {#android-watchdog-services}

Il servizio watchdog cross-Android è implementato come plug-in cordova utilizzando *Gestione allarmi*.

Il diagramma seguente mostra l’implementazione del servizio watchdog:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inizializzazione** Al momento dell&#39;inizializzazione del plug-in cordova, le autorizzazioni vengono controllate per verificare se disponiamo dei privilegi di sistema e quindi dell&#39;autorizzazione di riavvio. Se questi due criteri sono soddisfatti, viene creato un Intento in sospeso per il riavvio, altrimenti viene creato un Intento in sospeso per il riavvio dell&#39;applicazione (in base alla relativa attività di avvio).

**2. Timer Keep Alive** Viene utilizzato un timer keep alive per attivare un evento ogni 15 secondi. In questo caso, è necessario annullare l&#39;intento in sospeso esistente (per riavviare o riavviare l&#39;app) e registrare un nuovo intento in sospeso per gli stessi 60 secondi in futuro (essenzialmente posticipando il riavvio).

>[!NOTE]
>
>In Android, il *Gestione allarmi* viene utilizzato per registrare *pendingIntents* che può essere eseguito anche se l’app si è bloccata e la sua trasmissione dell’allarme non è esatta dall’API 19 (Kitkat). Mantieni una certa spaziatura tra l&#39;intervallo del timer e il *di AlarmManager* *pendingIntent* allarme.

**3. Arresto anomalo dell’applicazione** In caso di arresto anomalo, pendingIntent per il riavvio registrato con AlarmManager non viene più reimpostato ed esegue quindi un riavvio o un riavvio dell&#39;app (a seconda delle autorizzazioni disponibili al momento dell&#39;inizializzazione del plug-in cordova).

## Provisioning in blocco di Android Player {#bulk-provision-android-player}

Quando si esegue il rollout in blocco del lettore Android, è necessario eseguire il provisioning del lettore per puntare a un’istanza AEM e configurare altre proprietà senza immetterle manualmente nell’interfaccia utente di amministrazione.

>[!NOTE]
>Questa funzione è disponibile dal lettore Android 42.0.372.

Segui i passaggi seguenti per consentire il provisioning in blocco nel lettore Android:

1. Crea un file JSON di configurazione con il nome `player-config.default.json`.
Fai riferimento a un [Esempio di criterio JSON](#example-json) nonché una tabella che descrive l&#39;utilizzo dei vari [Attributi dei criteri](#policy-attributes).

1. Utilizza uno strumento di esplorazione dei file MDM, ADB o Android Studio per rilasciare questo file JSON per i criteri in *sdcard* sul dispositivo Android.

1. Una volta distribuito il file, usa MDM per installare l’applicazione del lettore.

1. All’avvio dell’applicazione del lettore, questo file di configurazione viene letto e fa riferimento al server AEM applicabile in cui può essere registrato e successivamente controllato.

   >[!NOTE]
   >Questo file è *sola lettura* la prima volta che l’applicazione viene avviata e non può essere utilizzata per le configurazioni successive. Se il lettore viene avviato prima dell&#39;eliminazione del file di configurazione, è sufficiente disinstallare e reinstallare l&#39;applicazione sul dispositivo.

### Attributi dei criteri {#policy-attributes}

La tabella seguente riepiloga gli attributi dei criteri con un esempio di JSON per i criteri a scopo di riferimento:

| **Nome criterio** | **Scopo** |
|---|---|
| *server* | L’URL del server Adobe Experience Manager. |
| *risoluzione* | Risoluzione del dispositivo. |
| *rebootSchedule* | La pianificazione per il riavvio si applica a tutte le piattaforme. |
| *enableAdminUI* | Abilita l’interfaccia utente di amministrazione per configurare il dispositivo sul sito. Imposta su *false* una volta che è completamente configurato e in produzione. |
| *enableOSD* | Abilita l’interfaccia utente per cambiare canale affinché gli utenti possano cambiare canale sul dispositivo. Considerare l&#39;impostazione su *false* una volta che è completamente configurato e in produzione. |
| *enableActivityUI* | Abilita questa opzione per mostrare l’avanzamento di attività come download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| *enableNativeVideo* | Abilita per utilizzare l’accelerazione hardware nativa per la riproduzione video (solo Android). |

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
>Tutti i dispositivi Android hanno un *sdcard* cartella se un valore effettivo *sdcard* è inserito o meno. Quando viene distribuito, questo file si trova allo stesso livello della cartella Download. Alcuni MDM come Samsung Knox possono fare riferimento a questo *sdcard* percorso cartella come *Memoria interna*.

## Provisioning in blocco di Android Player tramite Enterprise Mobility Management {#bulk-provisioning}

Quando si distribuisce il lettore Android in massa, diventa noioso registrare manualmente ogni singolo lettore con AEM. Si consiglia vivamente di utilizzare una soluzione EMM (Enterprise Mobility Management) come VMWare Airwatch, MobileIron o Samsung Knox per effettuare il provisioning e gestire l&#39;installazione in remoto. AEM Screens Android Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.

## Denominazione del lettore Android {#name-android}

Puoi assegnare un nome descrittivo del dispositivo al lettore Android, inviando in tal modo il nome del dispositivo assegnato ad Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Android, ma anche di assegnare facilmente i contenuti appropriati.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Una volta registrato, il nome del lettore non può più essere modificato.

Per configurare il nome in Android Player, segui i passaggi seguenti:

1. Accedi a **impostazioni** —> **Informazioni sul dispositivo**
1. Modifica e imposta il nome del dispositivo per denominare il lettore Android

### Implementazione del provisioning in blocco di Android Player tramite Enterprise Mobility Management {#implementation}

Segui i passaggi seguenti per consentire il provisioning in blocco in Android Player:

1. Assicurati che il tuo dispositivo Android supporti i servizi Google Play.
1. Iscrivi i dispositivi di riproduzione Android con la tua soluzione EMM preferita che supporta AppConfig.
1. Accedi alla console EMM e richiama l’applicazione AEM Screens Player da Google Play.
1. Seleziona la configurazione gestita o l’opzione correlata.
1. A questo punto dovrebbe essere visualizzato un elenco di opzioni del lettore che possono essere configurate, ad esempio il codice di registrazione del server e in blocco.
1. Configura questi parametri, salva e distribuisci il criterio nei dispositivi.

   >[!NOTE]
   >I dispositivi devono ricevere l&#39;applicazione insieme alla configurazione e puntare al server AEM corretto con la configurazione selezionata. Se hai scelto di configurare il codice di registrazione in blocco e lo hai mantenuto come configurato in AEM, il lettore deve essere in grado di registrarsi automaticamente. Se hai configurato una visualizzazione predefinita, questa può anche scaricare e mostrare alcuni contenuti predefiniti (che possono essere successivamente modificati per comodità).

Inoltre, è necessario verificare con il fornitore EMM il supporto di AppConfig. Quelli più popolari come [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Ferro da stiro](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) e [Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) tra gli altri, supporta questo standard di settore.

### Utilizzo del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzione qui: [Controllo remoto Schermi](implementing-remote-control.md)
