---
title: Risoluzione dei problemi del Centro di controllo del dispositivo
seo-title: Monitoraggio degli schermi
description: Segui questa pagina per monitorare e risolvere i problemi di prestazioni per l'attività del lettore e il dispositivo Screens utilizzando il dashboard del dispositivo.
seo-description: Segui questa pagina per monitorare e risolvere i problemi di prestazioni per l'attività del lettore e il dispositivo Screens utilizzando il dashboard del dispositivo.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Risoluzione dei problemi del Centro di controllo del dispositivo {#troubleshooting-device-control-center}

Puoi monitorare e risolvere i problemi di prestazioni per l'attività del lettore e il dispositivo Screens utilizzando il dashboard del dispositivo. Questa pagina fornisce informazioni su come monitorare e risolvere eventuali problemi di prestazioni per il lettore Screens e i dispositivi assegnati.

## Monitoraggio e risoluzione dei problemi da Device Control Center {#monitor-and-troubleshoot-from-device-control-center}

È possibile monitorare l'attività e quindi risolvere i problemi del lettore Screens, utilizzando Device Dashboard.

### Pannello dispositivo {#device-dashboard}

Seguite i passaggi riportati di seguito per passare al dashboard del dispositivo:

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. Nell'elenco vengono visualizzati i dispositivi assegnati e non assegnati, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Selezionate il dispositivo (**NewTestDevice**) e fate clic su **Dashboard** dalla barra delle azioni.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La pagina mostra le informazioni sul dispositivo, l'attività e i dettagli del dispositivo che consentono di monitorare le attività e le funzioni del dispositivo.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorare l'attività del dispositivo {#monitor-device-activity}

Il pannello **Attività** mostra l'ultimo ping del lettore di schermate con la marca temporale. L'ultimo ping corrisponde all'ultima volta che il dispositivo ha contattato il server.

![chlimage_1](assets/chlimage_1.png)

Inoltre, fate clic su **Raccogli registri** nell’angolo in alto a destra del pannello **Attività** per visualizzare i registri del lettore.

### Aggiorna dettagli dispositivo {#update-device-details}

Controllare il pannello Dettagli **** dispositivo per visualizzare l'IP del dispositivo, l'utilizzo dello storage, la versione del firmware e il tempo di attività del lettore per il dispositivo.

![chlimage_1-1](assets/chlimage_1-1.png)

Inoltre, fare clic su **Cancella cache** e **Aggiorna** per cancellare la cache del dispositivo e aggiornare la versione [firmware](screens-glossary.md) rispettivamente da questo pannello.

**Inoltre, fate clic sul**.. dall'angolo superiore destro del pannello Dettagli **** dispositivo per riavviare o aggiornare lo stato del lettore.

![chlimage_1-2](assets/chlimage_1-2.png)

### Aggiorna informazioni dispositivo {#update-device-information}

Controllate il pannello **INFORMAZIONI** DISPOSITIVO per visualizzare l'aggiornamento della configurazione, il modello di dispositivo, il sistema operativo del dispositivo e le informazioni sulla shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Inoltre, fai clic su (**...**) nell'angolo superiore destro del pannello Informazioni dispositivo per visualizzare le proprietà o aggiornare il dispositivo.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Fare clic su **Proprietà** per visualizzare la finestra di dialogo Proprietà **** dispositivo. Potete modificare il titolo del dispositivo o scegliere l'opzione per gli aggiornamenti di configurazione come **Manuale** o **Automatico**.

>[!NOTE]
>
>Per ulteriori informazioni sugli eventi associati agli aggiornamenti automatici o manuali del dispositivo, consulta la sezione Aggiornamenti ***automatici e manuali dal Pannello*** di controllo del dispositivo in [Gestione dei canali](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Visualizza schermata del lettore {#view-player-screenshot}

È possibile visualizzare la schermata del lettore dal dispositivo dal pannello **PLAYER SCREENSHOT **.

Fare clic (**...**) nell'angolo superiore destro del pannello Screenshot del lettore e selezionare **Refresh Screenshot **per visualizzare l'istantanea del lettore in esecuzione.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestisci preferenze {#manage-preferences}

Il pannello **PREFERENZE** consente all'utente di modificare le preferenze per l'interfaccia utente **** Amministratore, **Channel Switcher** e **Remote Debugging** del dispositivo.

>[!NOTE]
>
>Per ulteriori informazioni su questa opzione, consulta Lettore [](working-with-screens-player.md)AEM Screens.

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Inoltre, fai clic su **Impostazioni** nell'angolo in alto a destra per aggiornare le preferenze del dispositivo. Potete aggiornare le seguenti preferenze:

* **URL server**
* **Risoluzione**
* **Riavvia pianificazione**
* **N. max dei file di registro da mantenere**
* **Livello registro**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>
>È possibile selezionare uno dei seguenti livelli di registro:
>
>* **Disattiva**
>* **Debug**
>* **Info**
>* **Avvertenza**
>* **Errore**
>



![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Risoluzione dei problemi relativi alle impostazioni OSGI {#troubleshoot-osgi-settings}

È necessario abilitare il referente vuoto per consentire al dispositivo di inviare dati al server. Ad esempio, se la proprietà del referente vuoto è disabilitata, il dispositivo non può inviare una schermata indietro.

Attualmente alcune di queste funzioni sono disponibili solo se il filtro *Apache Sling Referrer Consenti valori nulli* è abilitato nel configurazione OSGI. Il dashboard potrebbe visualizzare un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzioni.

Seguite i passaggi riportati di seguito per attivare il filtro Apache Sling Referrer Consenti vuoto

1. Passa alla configurazione **della console Web di** Adobe Experience Manager, ovvero `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Selezionare l'opzione **allow.empty **.
1. Fai clic su **Salva**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Consigli {#recommendations}

La sezione seguente raccomanda di monitorare i collegamenti di rete, il server e i lettori per comprendere lo stato e reagire ai problemi.

AEM fornisce il monitoraggio integrato per:

* *Heartbeat* ogni 5 secondi per indicare che AEM Screens Player è in funzione.
* *Screenshot* del lettore che mostra il contenuto visualizzato sul lettore.
* Versione firmware del lettore *AEM Screens* installata nel lettore.
* *Spazio* di archiviazione gratuito sul lettore.

Raccomandazioni per il monitoraggio remoto con software di terze parti:

* Utilizzo della CPU sui lettori.
* Verifica se è in esecuzione il processo AEM Screens Player.
* Riavvio/riavvio remoto del lettore.
* Notifiche in tempo reale.

Si consiglia di implementare l'hardware e il sistema operativo Player in modo da consentire il login remoto per diagnosticare i problemi e riavviare il lettore.

#### Additional Resources {#additional-resources}

Consultate Configurazione della riproduzione [video e Risoluzione](troubleshoot-videos.md) dei problemi per eseguire il debug e risolvere i problemi relativi alla riproduzione di video nel canale.
