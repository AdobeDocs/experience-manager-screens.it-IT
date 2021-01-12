---
title: Implementazione di Android Player
seo-title: Implementazione di Android Player
description: Segui questa pagina per imparare l'implementazione di Android Watchdog, una soluzione per recuperare il lettore da arresti anomali.
seo-description: Segui questa pagina per imparare l'implementazione di Android Watchdog, una soluzione per recuperare il lettore da arresti anomali.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
translation-type: tm+mt
source-git-commit: e2096260d06cc2db17d690ecbc39e8dc4f1b5aa7
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---


# Implementazione di Android Player {#implementing-android-player}

Questa sezione descrive la configurazione del lettore Android. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili e consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

Inoltre, **Watchdog** è una soluzione per recuperare il lettore da arresti anomali. Un&#39;applicazione deve registrarsi presso il servizio di controllo e inviare periodicamente messaggi al servizio che è attivo. Nel caso in cui il servizio di controllo non riceva un messaggio keep-alive entro un tempo stabilito, il servizio tenta di riavviare il dispositivo per un ripristino pulito (se dispone dei privilegi sufficienti) o di riavviare l&#39;applicazione.

## Installazione di Android Player {#installing-android-player}

Per implementare Android Player per  AEM Screens, installate Android Player per  AEM Screens.

Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

### Impostazione dell&#39;ambiente per  AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>È necessario configurare un ambiente per il lettore Android se si utilizza  AEM Screens 6.5.5 Service Pack.

Impostate l&#39;attributo **SameSite per i cookie di token di login** da **Lax** a **None** da **Configurazione della console Web di Adobe Experience Manager** su tutte AEM istanze di creazione e pubblicazione.

Effettua le seguenti operazioni:

1. Passa a **Configurazione console Web Adobe Experience Manager** utilizzando `http://localhost:4502/system/console/configMgr`.

1. Cercare *gestore autenticazione token granito Adobe*.

1. Impostate l&#39;attributo **SameSite per i cookie del token di login** da **Lax** a **None**.
   ![immagine](/help/user-guide/assets/granite-updates.png)

1. Fai clic su **Salva**.


### Metodo ad hoc {#ad-hoc-method}

Il metodo Ad-Hoc consente di installare la versione più recente di Android Player (*.exe*). Visita la pagina [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

Una volta scaricata l’applicazione, seguite i passaggi del lettore per completare l’installazione ad hoc:

1. Tenete premuto sull’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Andate a **Configuration** dal menu delle azioni a sinistra e immettete la posizione (indirizzo) dell&#39;istanza AEM a cui desiderate connettervi e fate clic su **Save**.

1. Andate al collegamento **Dispositivo** **Registrazione** dal menu delle azioni a sinistra per verificare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se **State** è **REGISTERED**, il campo **Device id** verrà popolato.
>
>Se **State** è **UNREGISTERED**, è possibile utilizzare il **Token** per registrare il dispositivo.

## Implementazione di Android Watchdog {#implementing-android-watchdog}

A causa dell&#39;architettura di Android, il riavvio del dispositivo richiede che l&#39;applicazione disponga dei privilegi di sistema. A tal fine, è necessario firmare l&#39;apk utilizzando i tasti di firma del produttore. In caso contrario, watchdog riavvierà l&#39;applicazione del lettore e non riavvierà il dispositivo.

### Segnalazione di apposite app Android utilizzando le chiavi produttore {#signage-of-android-apks-using-manufacturer-keys}

Per accedere ad alcune delle API privilegiate di Android, come *PowerManager* o *HDMIControlServices*, è necessario firmare l&#39;app Android utilizzando le chiavi del produttore.

>[!CAUTION]
>
>Prerequisiti:
>
>Prima di eseguire i seguenti passaggi, devi installare l’SDK Android.

Seguite i passaggi indicati di seguito per firmare il disco Android utilizzando i tasti del produttore:

1. Scarica l&#39;app da Google Play o dalla pagina [ Download di AEM Screens Player](https://download.macromedia.com/screens/)
1. Ottenete i tasti della piattaforma dal produttore per ottenere un file *pk8* e un file *pem*

1. Individuate lo strumento apksigner in android sdk utilizzando trova ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Trovare il percorso dello strumento di allineamento zip in android sdk
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Installare ***aemscreensalign.apk*** utilizzando l&#39;installazione adb nel dispositivo

## Implementazione Android Watchdog {#android-watchdog-implementation}

Il servizio di controllo Android è implementato come plug-in cordova utilizzando *AlarmManager*.

Il diagramma seguente mostra l’implementazione del servizio di controllo:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inizializzazione** Al momento dell&#39;inizializzazione del plug-in cordova, le autorizzazioni vengono verificate per verificare se disponiamo dei privilegi di sistema e quindi dell&#39;autorizzazione Riavvia. Se questi due criteri vengono soddisfatti, viene creato un Intento in sospeso per il riavvio. In caso contrario viene creato un Intento in sospeso per riavviare l&#39;applicazione (in base all&#39;attività di avvio).

**2. Tenere il timer attivo** Per attivare un evento ogni 15 secondi viene utilizzato un timer di conservazione in vita. In questo caso, è necessario annullare l&#39;intento in sospeso esistente (per riavviare o riavviare l&#39;app) e registrare un nuovo intento in sospeso per gli stessi 60 secondi in futuro (in sostanza, posticipare il riavvio).

>[!NOTE]
>
>In Android, l&#39; *AlarmManager* viene utilizzato per registrare gli *pendingIntents* che possono essere eseguiti anche se l&#39;app si è bloccata e la relativa consegna dell&#39;allarme non è esatta dall&#39;API 19 (Kitkat). Mantenere una certa spaziatura tra l&#39;intervallo del timer e l&#39;allarme *AlarmManager* *pendingIntent*.

**3. Arresto anomalo dell&#39;applicazione** In caso di arresto anomalo, l&#39;intento in sospeso per il riavvio registrato con AlarmManager non viene più reimpostato ed esegue quindi un riavvio o riavvio dell&#39;app (a seconda delle autorizzazioni disponibili al momento dell&#39;inizializzazione del plug-in cordova).

## Provisioning di massa di Android Player {#bulk-provision-android-player}

Quando si distribuisce il lettore Android in massa, è necessario fornire al lettore un&#39;istanza AEM e configurare altre proprietà senza immettere manualmente quelle nell&#39;interfaccia utente di amministrazione.

>[!NOTE]
>Questa funzione è disponibile dal lettore Android 42.0.372.

Seguite i passaggi indicati di seguito per consentire il provisioning in blocco nel lettore Android:

1. Create un file JSON di configurazione con il nome `player-config.default.json`.
Fare riferimento a un [esempio di criteri JSON](#example-json) e a una tabella che descrive l&#39;uso dei vari [attributi del criterio](#policy-attributes).

1. Utilizzate un file Explorer MDM, ADB o Android Studio per rilasciare il file JSON del criterio nella cartella *sdcard* sul dispositivo Android.

1. Una volta distribuito il file, utilizzate il MDM per installare l&#39;applicazione del lettore.

1. Quando l&#39;applicazione del lettore viene avviata, leggerà questo file di configurazione e indicherà il server AEM applicabile, dove può essere registrato e successivamente controllato.

   >[!NOTE]
   >Questo file è di *sola lettura* la prima volta che l&#39;applicazione viene avviata e non può essere utilizzato per le configurazioni successive. Se il lettore viene avviato prima che il file di configurazione venga eliminato, disinstallate e reinstallate l&#39;applicazione sul dispositivo.

### Attributi del criterio {#policy-attributes}

La tabella seguente riassume gli attributi del criterio con un JSON di esempio per riferimento:

| **Nome criterio** | **Scopo** |
|---|---|
| *server* | URL del server Adobe Experience Manager. |
| *risoluzione* | La risoluzione del dispositivo. |
| *RestartSchedule* | La pianificazione del riavvio si applica a tutte le piattaforme. |
| *enableAdminUI* | Abilita l’interfaccia utente amministratore per configurare il dispositivo sul sito. Impostare su *false* una volta che è completamente configurato e in produzione. |
| *enableOSD* | Abilitare l&#39;interfaccia utente dello switcher di canale per consentire agli utenti di cambiare canale sul dispositivo. Considerare l&#39;impostazione su *false* una volta che è completamente configurato e in produzione. |
| *enableActivityUI* | Consente di visualizzare l&#39;avanzamento delle attività quali il download e la sincronizzazione. Abilitate per la risoluzione dei problemi e disattivate una volta configurato completamente e in produzione. |
| *enableNativeVideo* | Abilitate l’utilizzo dell’accelerazione hardware nativa per la riproduzione video (solo Android). |

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
>Tutti i dispositivi Android dispongono di una cartella *sdcard* indipendentemente dal fatto che sia inserita o meno una *sdcard* effettiva. Il file distribuito deve trovarsi allo stesso livello della cartella Download. Alcuni MDM, come Samsung Knox, possono fare riferimento a questa cartella *sdcard* come *Archiviazione interna*.