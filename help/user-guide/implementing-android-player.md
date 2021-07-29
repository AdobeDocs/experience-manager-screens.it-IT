---
title: Implementazione di Android Player
seo-title: Implementazione di Android Player
description: Segui questa pagina per imparare l'implementazione di Android Watchdog, una soluzione per recuperare il giocatore da arresti anomali.
seo-description: Segui questa pagina per imparare l'implementazione di Android Watchdog, una soluzione per recuperare il giocatore da arresti anomali.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Amministrazione di schermi, lettore Android
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 3bda698ca44f58c177f8e87a5c50b789966909de
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 0%

---

# Implementazione di Android Player {#implementing-android-player}

Questa sezione descrive la configurazione di Android Player. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili e fornisce raccomandazioni sulle impostazioni da utilizzare per lo sviluppo e il test.

Inoltre, **Watchdog** è una soluzione per recuperare il lettore da arresti anomali. Un&#39;applicazione deve registrarsi con il servizio watchdog e quindi inviare periodicamente messaggi al servizio che è attivo. Nel caso in cui il servizio watchdog non riceva un messaggio keep-alive entro un tempo stabilito, il servizio tenta di riavviare il dispositivo per un ripristino pulito (se dispone dei privilegi sufficienti) o di riavviare l&#39;applicazione.

## Installazione di Android Player {#installing-android-player}

Per implementare Android Player per AEM Screens, installa Android Player per AEM Screens.

Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

### Configurazione dell’ambiente per AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Se utilizzi AEM Screens 6.5.5 Service Pack, devi configurare un ambiente per Android Player.

Imposta l&#39;attributo **SameSite per i cookie login-token** da **Lax** a **None** da **Configurazione della console Web Adobe Experience Manager** su tutte le istanze di authoring e pubblicazione AEM.

Effettua le seguenti operazioni:

1. Passa a **Configurazione della console Web Adobe Experience Manager** utilizzando `http://localhost:4502/system/console/configMgr`.

1. Cerca *Adobe gestore autenticazione token di Granite*.

1. Imposta l&#39;attributo **SameSite per i cookie login-token** da **Lax** a **None**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.


### Metodo Ad Hoc {#ad-hoc-method}

Il metodo Ad-Hoc consente di installare l&#39;ultimo lettore Android (*.exe*). Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

Una volta scaricata l&#39;applicazione, segui i passaggi sul lettore per completare l&#39;installazione ad-hoc:

1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Passa a **Configurazione** dal menu di azione a sinistra e immetti la posizione (indirizzo) dell&#39;istanza AEM a cui desideri connetterti e fai clic su **Salva**.

1. Passa al collegamento **Dispositivo** **Registrazione** dal menu di azione a sinistra per controllare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se il campo **Stato** è **REGISTRATO**, noterai che il campo **ID dispositivo** sarà popolato.
>
>Se il **Stato** è **NON REGISTRATO**, puoi utilizzare il **Token** per registrare il dispositivo.

## Implementazione Android Watchdog {#implementing-android-watchdog}

A causa dell&#39;architettura di Android, il riavvio del dispositivo richiede che l&#39;applicazione abbia i privilegi di sistema. A questo scopo, è necessario firmare l&#39;apk utilizzando le chiavi di firma del produttore, altrimenti watchdog riavvierà l&#39;applicazione del lettore e non riavvierà il dispositivo.

### Segnalazione di apk Android utilizzando chiavi del produttore {#signage-of-android-apks-using-manufacturer-keys}

Per accedere ad alcune delle API privilegiate di Android come *PowerManager* o *HDMIControlServices*, devi firmare l&#39;apk android utilizzando le chiavi del produttore.

>[!CAUTION]
>
>Prerequisiti:
>
>Prima di eseguire i seguenti passaggi, è necessario installare l’SDK per Android.

Segui i passaggi seguenti per firmare l&#39;apk android utilizzando le chiavi del produttore:

1. Scarica l&#39;app da Google Play o dalla pagina [Download di AEM Screens Player](https://download.macromedia.com/screens/)
1. Per ottenere un file *pk8* e un file *pem*, ottieni i tasti della piattaforma dal produttore

1. Individua lo strumento apksigner nell’sdk per android utilizzando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Trova il percorso dello strumento di allineamento zip nell&#39;sdk android
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Installa ***aemscreensalign.apk*** utilizzando l’installazione adb nel dispositivo

## Informazioni sui servizi Android Watchdog {#android-watchdog-services}

Il servizio di watchdog cross-Android è implementato come plug-in cordova utilizzando *AlarmManager*.

Il diagramma seguente illustra l’implementazione del servizio watchdog:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inizializzazione** Al momento dell&#39;inizializzazione del plug-in cordova, le autorizzazioni vengono controllate per vedere se disponiamo dei privilegi di sistema e quindi dell&#39;autorizzazione Riavvio. Se questi due criteri vengono soddisfatti, viene creato un Intent for Reboot in sospeso, altrimenti viene creato un Intent in sospeso per riavviare l&#39;applicazione (in base alla sua attività Launch).

**2. Mantieni timer attivo** Per attivare un evento ogni 15 secondi viene utilizzato un timer di conservazione in vita. In questo caso, devi annullare l’intento in sospeso esistente (per riavviare o riavviare l’app) e registrare un nuovo intento in sospeso per gli stessi 60 secondi in futuro (in sostanza, per posticipare il riavvio).

>[!NOTE]
>
>In Android, il *AlarmManager* viene utilizzato per registrare gli *pendingIntents* che possono essere eseguiti anche se l&#39;app si è bloccata e la relativa consegna dell&#39;allarme non è esatta dall&#39;API 19 (Kitkat). Mantenere una certa spaziatura tra l&#39;intervallo del timer e l&#39;allarme *AlarmManager* *pendingIntent&#39;s*.

**3. Arresto anomalo dell&#39;applicazione** In caso di arresto anomalo, l&#39;intento in sospeso per il riavvio registrato con AlarmManager non viene più reimpostato e quindi esegue un riavvio o un riavvio dell&#39;app (a seconda delle autorizzazioni disponibili al momento dell&#39;inizializzazione del plug-in cordova).

## Provisioning in blocco di Android Player {#bulk-provision-android-player}

Quando si esegue il rollout in massa del lettore Android, è necessario eseguire il provisioning del lettore per puntare a un&#39;istanza AEM e configurare altre proprietà senza immettere manualmente quelle nell&#39;interfaccia utente amministratore.

>[!NOTE]
>Questa funzione è disponibile da Android Player 42.0.372.

Segui i passaggi seguenti per consentire il provisioning in massa nel lettore Android:

1. Crea un file JSON di configurazione con il nome `player-config.default.json`.
Fai riferimento a un [Esempio di criteri JSON](#example-json) e a una tabella che descrive l&#39;uso dei vari [attributi dei criteri](#policy-attributes).

1. Utilizza un file explorer MDM o ADB o Android Studio per rilasciare questo file JSON di criteri nella cartella *sdcard* sul dispositivo Android.

1. Una volta distribuito il file, utilizza MDM per installare l’applicazione del lettore.

1. Quando l&#39;applicazione player viene avviata, leggerà questo file di configurazione e punterà al server AEM applicabile dove può essere registrato e successivamente controllato.

   >[!NOTE]
   >Questo file è *di sola lettura* la prima volta che l&#39;applicazione viene avviata e non può essere utilizzato per le configurazioni successive. Se il lettore viene avviato prima dell&#39;eliminazione del file di configurazione, è sufficiente disinstallare e reinstallare l&#39;applicazione sul dispositivo.

### Attributi dei criteri {#policy-attributes}

La tabella seguente riepiloga gli attributi del criterio con un esempio di codice JSON per riferimento:

| **Nome criterio** | **Scopo** |
|---|---|
| *server* | URL del server Adobe Experience Manager. |
| *risoluzione* | La risoluzione del dispositivo. |
| *RestartSchedule* | La pianificazione da riavviare si applica a tutte le piattaforme. |
| *enableAdminUI* | Abilita l’interfaccia utente amministratore per configurare il dispositivo sul sito. Imposta su *false* una volta configurato completamente e in produzione. |
| *enableOSD* | Abilita l’interfaccia utente del commutatore del canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l&#39;impostazione su *false* una volta configurato completamente e in produzione. |
| *enableActivityUI* | Attiva per mostrare l&#39;avanzamento delle attività come il download e la sincronizzazione. Attiva per la risoluzione dei problemi e disattiva una volta configurato completamente e in produzione. |
| *enableNativeVideo* | Abilitare l&#39;uso dell&#39;accelerazione hardware nativa per la riproduzione video (solo Android). |

### Criteri JSON di esempio {#example-json}

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
>Tutti i dispositivi Android hanno una cartella *sdcard* indipendentemente dal fatto che sia stato inserito o meno un *sdcard* effettivo. Questo file, se distribuito, si trova allo stesso livello della cartella Download. Alcuni MDM, come Samsung Knox, possono fare riferimento a questa posizione della cartella *sdcard* come *Archiviazione interna*.

## Provisioning in blocco di Android Player tramite Enterprise Mobility Management {#bulk-provisioning}

Quando si distribuisce il lettore Android in serie, diventa noioso registrare manualmente ogni singolo lettore con AEM. Si consiglia vivamente di utilizzare una soluzione EMM (Enterprise Mobility Management) come VMWare Airwatch, MobileIron o Samsung Knox per il provisioning e la gestione remota dell&#39;implementazione. AEM Screens Android Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.

## Denominazione di Android Player {#name-android}

È possibile assegnare un nome di dispositivo facile da usare al lettore Android, inviando in tal modo il nome assegnato ad Adobe Experience Manager (AEM). Questa funzionalità consente non solo di assegnare un nome al lettore Android, ma anche di assegnare facilmente il contenuto appropriato.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Una volta registrato il lettore, il nome del lettore non può più essere cambiato.

Per configurare il nome in Android Player, effettua le seguenti operazioni:

1. Passa a **impostazioni** —> **Informazioni su dispositivo**
1. Modifica e imposta il nome del dispositivo per denominare il lettore Android

### Implementazione del provisioning in blocco di Android Player utilizzando Enterprise Mobility Management {#implementation}

Segui i passaggi seguenti per consentire il provisioning in massa in Android Player:

1. Assicurati che il tuo dispositivo Android supporti i servizi Google Play.
1. Registrati i tuoi dispositivi Android Player con la tua soluzione EMM preferita che supporta AppConfig.
1. Accedi alla tua console EMM e estrae l&#39;applicazione AEM Screens Player da Google Play.
1. Seleziona la configurazione gestita o l&#39;opzione correlata.
1. Ora dovresti visualizzare un elenco delle opzioni del lettore che possono essere configurate, ad esempio il codice di registrazione di massa e il server.
1. Configura questi parametri, salva e distribuisci il criterio sui dispositivi.

   >[!NOTE]
   >I dispositivi devono ricevere l&#39;applicazione insieme alla configurazione e puntare al server AEM corretto con la configurazione selezionata. Se hai scelto di configurare il codice di registrazione in serie e lo hai mantenuto come configurato in AEM, il lettore dovrebbe essere in grado di registrarsi automaticamente. Se hai configurato una visualizzazione predefinita, può anche scaricare e mostrare alcuni contenuti predefiniti (che possono essere successivamente modificati secondo le tue esigenze).

Inoltre, è necessario verificare con il fornitore EMM il supporto AppConfig. I più popolari come [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Ferro mobile](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) e [Samsung Knox&lt;a8 11/> tra gli altri supportano questo standard di settore.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)
