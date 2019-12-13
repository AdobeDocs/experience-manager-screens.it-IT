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
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Implementazione di Android Player {#implementing-android-player}

Questa sezione descrive la configurazione del lettore Android. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili e consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

Inoltre, **Watchdog** è una soluzione per recuperare il lettore da arresti anomali. Un'applicazione deve registrarsi presso il servizio di controllo e inviare periodicamente messaggi al servizio che è attivo. Nel caso in cui il servizio di controllo non riceva un messaggio keep-alive entro un tempo stabilito, il servizio tenta di riavviare il dispositivo per un ripristino pulito (se dispone dei privilegi sufficienti) o di riavviare l'applicazione.

## Installazione di Android Player {#installing-android-player}

Per implementare Android Player per AEM Screens, installate Android Player per AEM Screens.

Visita la pagina dei download [**di**](https://download.macromedia.com/screens/) AEM 6.4 Player.

### Metodo Ad Hoc {#ad-hoc-method}

Il metodo Ad-Hoc consente di installare la versione più recente di Android Player (*.exe*). Visita la pagina dei download [**di**](https://download.macromedia.com/screens/) AEM 6.4 Player.

Una volta scaricata l’applicazione, seguite i passaggi del lettore per completare l’installazione ad hoc:

1. Tenete premuto sull’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Andate a **Configurazione** dal menu delle azioni a sinistra e immettete il percorso (indirizzo) dell’istanza AEM a cui desiderate connettervi e fate clic su **Salva**.

1. Andate al collegamento **Device** **Registration** (Registrazione dispositivo) dal menu delle azioni a sinistra per verificare lo stato del processo di registrazione del dispositivo.

>[!NOTE]
>
>Se lo **stato** è **REGISTRATO**, il campo ID **** dispositivo verrà popolato.
>
>Se lo **stato** è **NON REGISTRATO**, potete utilizzare il **token** per registrare il dispositivo.

## Implementazione di Android Watchdog {#implementing-android-watchdog}

A causa dell'architettura di Android, il riavvio del dispositivo richiede che l'applicazione disponga dei privilegi di sistema. A tal fine, è necessario firmare l'apk utilizzando i tasti di firma del produttore. In caso contrario, watchdog riavvierà l'applicazione del lettore e non riavvierà il dispositivo.

### Segnalazione di apk Android con produttore chiavi {#signage-of-android-apks-using-manufacturer-keys}

Per accedere ad alcune delle API privilegiate di Android, come *PowerManager* o *HDMIControlServices*, è necessario firmare l'app Android utilizzando le chiavi del produttore.

>[!CAUTION]
>
>Prerequisiti:
>
>Prima di eseguire i seguenti passaggi, devi installare l’SDK Android.

Seguite i passaggi indicati di seguito per firmare il disco Android utilizzando i tasti del produttore:

1. Scaricate l'app da Google Play o dalla pagina dei download [](https://download.macromedia.com/screens/) di AEM Screens Player
1. Ottenete le chiavi della piattaforma dal produttore per ottenere un *pk8* e un file *pem*

1. Individuate lo strumento apksigner in android sdk utilizzando trova ~/Library/Android/sdk/build-tools -name "apksigner"
1. &lt;percorso&gt; /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Trovare il percorso dello strumento di allineamento zip in android sdk
1. &lt;percorso&gt; /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Installare ***aemscreensalign.apk*** utilizzando l'installazione adb nel dispositivo

## Implementazione Android Watchdog {#android-watchdog-implementation}

Il servizio di controllo Android è implementato come plug-in cordova utilizzando *AlarmManager*.

Il diagramma seguente mostra l’implementazione del servizio di controllo:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inizializzazione** Al momento dell'inizializzazione del plug-in cordova, le autorizzazioni vengono verificate per verificare se disponiamo dei privilegi di sistema e quindi dell'autorizzazione Riavvia. Se questi due criteri vengono soddisfatti, viene creato un Intento in sospeso per il riavvio, altrimenti viene creato un Intento in sospeso per riavviare l'applicazione (in base all'attività di avvio).

**2. Mantieni timer** attivo Un timer per mantenere in vita viene utilizzato per attivare un evento ogni 15 secondi. In questo caso, è necessario annullare l'intento in sospeso esistente (per riavviare o riavviare l'app) e registrare un nuovo intento in sospeso per gli stessi 60 secondi in futuro (in sostanza, posticipare il riavvio).

>[!NOTE]
>
>In Android, *AlarmManager* viene utilizzato per registrare gli *pendingIntents* che possono essere eseguiti anche se l'app si è bloccata e la relativa consegna dell'allarme non è esatta dall'API 19 (Kitkat). Mantenere una certa distanza tra l'intervallo del timer e l'allarme di *AlarmManager* *pendingIntent* .

**3. Arresto anomalo** dell'applicazione In caso di arresto anomalo, l'intento in sospeso per il riavvio registrato con AlarmManager non viene più reimpostato ed esegue quindi un riavvio o un riavvio dell'app (a seconda delle autorizzazioni disponibili al momento dell'inizializzazione del plug-in cordova).
