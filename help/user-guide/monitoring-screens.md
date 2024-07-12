---
title: Risoluzione dei problemi di Device Control Center
description: Scopri come monitorare e risolvere i problemi di prestazioni per l’attività e il dispositivo di AEM Screens Player utilizzando il dashboard Dispositivo.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 1%

---

# Risoluzione dei problemi di Device Control Center {#troubleshooting-device-control-center}

Puoi monitorare e risolvere i problemi relativi alle prestazioni per l’attività e il dispositivo di AEM Screens Player utilizzando il dashboard Dispositivo. Questa pagina fornisce informazioni su come monitorare e risolvere i problemi di prestazioni percepiti per il lettore Screens e i dispositivi assegnati.

## Monitoraggio e risoluzione dei problemi da Centro controllo dispositivi {#monitor-and-troubleshoot-from-device-control-center}

Puoi monitorare l’attività e quindi risolvere eventuali problemi del lettore AEM Screens, utilizzando il dashboard del dispositivo.

### Dashboard dispositivo {#device-dashboard}

Per accedere al dashboard dei dispositivi, segui la procedura riportata di seguito:

1. Passa al dashboard dei dispositivi dal progetto, ad esempio ***Progetto di prova*** > ***Dispositivi***.

   Fare clic su **Dispositivi** e **Gestione dispositivi** nella barra delle azioni.

   ![schermata_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. L&#39;elenco mostra i dispositivi assegnati e non assegnati, come illustrato nella figura riportata di seguito.

   ![schermata_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Fare clic sul dispositivo (**NewTestDevice**) e fare clic su **Dashboard** nella barra delle azioni.

   ![schermata_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La pagina mostra le informazioni sul dispositivo, l’attività e i dettagli del dispositivo che consentono di monitorare le attività e le funzioni del dispositivo.

   ![schermata_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorare l&#39;attività del dispositivo {#monitor-device-activity}

Il pannello **Attività** mostra l&#39;ultimo ping del lettore AEM Screens con la marca temporale. L&#39;ultimo ping corrisponde all&#39;ultimo contatto del dispositivo con il server.

![chlimage_1](assets/chlimage_1.png)

Fai clic anche su **Raccogli registri** dall&#39;angolo in alto a destra del pannello **Attività** per visualizzare i registri del lettore.

### Aggiorna dettagli dispositivo {#update-device-details}

Controlla il pannello **Dettagli dispositivo** per visualizzare l&#39;IP del dispositivo, l&#39;utilizzo dello spazio di archiviazione, la versione del firmware e il tempo di attività del lettore per il dispositivo.

![chlimage_1-1](assets/chlimage_1-1.png)

Inoltre, fare clic su **Cancella cache** e **Aggiorna** per cancellare la cache del dispositivo e aggiornare la versione [firmware](screens-glossary.md) rispettivamente da questo pannello.

Inoltre, fai clic su **...** dall&#39;angolo in alto a destra del pannello **Dettagli dispositivo** per riavviare o aggiornare lo stato del lettore.

![chlimage_1-2](assets/chlimage_1-2.png)

### Aggiorna informazioni dispositivo {#update-device-information}

Controllare il pannello **INFORMAZIONI DISPOSITIVO**. Qui puoi visualizzare l’aggiornamento della configurazione, il modello del dispositivo, il sistema operativo del dispositivo e le informazioni sulla shell.

![schermata_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Fare inoltre clic su (**...**) nell&#39;angolo superiore destro del pannello Informazioni dispositivo per visualizzare le proprietà o aggiornare il dispositivo.

![schermata_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Fare clic su **Proprietà** per visualizzare la finestra di dialogo **Proprietà dispositivo**. Puoi modificare il titolo del dispositivo o scegliere l&#39;opzione per gli aggiornamenti della configurazione come **Manuale** o **Automatico**.

>[!NOTE]
>
>Per ulteriori informazioni sugli eventi associati agli aggiornamenti automatici o manuali del dispositivo, vedere la sezione ***Aggiornamenti automatici e manuali dal dashboard del dispositivo*** in [Gestione dei canali](managing-channels.md).

![schermata_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Visualizza schermata lettore {#view-player-screenshot}

Puoi visualizzare lo screenshot del lettore dal dispositivo dal pannello **SCREENSHOT DEL LETTORE**.

Fai clic su (**...**) nell&#39;angolo in alto a destra del pannello Schermata del lettore e fai clic su **Aggiorna schermata** per visualizzare lo snapshot del lettore in esecuzione.

![schermata_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestione preferenze {#manage-preferences}

Il pannello **PREFERENCES** consente all&#39;utente di modificare le preferenze per **Interfaccia utente amministratore**, **Channel Switcher** e **Remote Debugging** per il dispositivo.

>[!NOTE]
>Per ulteriori informazioni su queste opzioni, vedere [AEM Screens Player](working-with-screens-player.md).

![schermata_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Fai clic anche su **Impostazioni** dall&#39;angolo superiore destro per aggiornare le preferenze del dispositivo. Puoi aggiornare le seguenti preferenze:

* **URL server**
* **Risoluzione**
* **Riavvia pianificazione**
* **N. max. di file di registro da mantenere**
* **Livello registro**

![schermata_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>È possibile fare clic su uno dei livelli di registro seguenti:
>* **Disattiva**
>* **Debug**
>* **Informazioni**
>* **Avviso**
>* **Errore**

![schermata_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Risoluzione dei problemi relativi alle impostazioni OSGi {#troubleshoot-osgi-settings}

Abilita il referente vuoto per consentire al dispositivo di pubblicare dati sul server. Ad esempio, se la proprietà del referente vuoto è disabilitata, il dispositivo non può pubblicare uno screenshot.

Attualmente alcune di queste funzionalità sono disponibili solo se il filtro di riferimento Sling *Apache Consenti vuoto* è abilitato nella configurazione OSGi. È possibile che nel dashboard venga visualizzato un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzionalità.

Segui i passaggi seguenti per abilitare il filtro Apache Sling Referrer Allow Empty

1. Passare a **Configurazione console Web Adobe Experience Manager**, ovvero `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Controlla l&#39;opzione **allow.empty**.
1. Fai clic su **Salva**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Consigli {#recommendations}

La sezione seguente consiglia di monitorare i collegamenti di rete, i server e i lettori per comprenderne lo stato e reagire ai problemi.

L&#39;AEM fornisce un monitoraggio integrato per:

* *Heartbeat* ogni 5 secondi per indicare che AEM Screens Player è in funzione.
* *Schermata* dal lettore che mostra ciò che viene visualizzato sul lettore.
* La versione del firmware *AEM Screens Player* è installata nel lettore.
* *Spazio di archiviazione libero* sul lettore.

Recommendations per il monitoraggio remoto con software di terze parti:

* Utilizzo della CPU nei lettori.
* Verifica se il processo di AEM Screens Player è in esecuzione.
* Riavvio/riavvio remoto del lettore.
* Notifiche in tempo reale.

Si consiglia di distribuire l&#39;hardware e il sistema operativo del lettore in modo da consentire l&#39;accesso remoto per diagnosticare i problemi e riavviare il lettore.

#### Altre risorse {#additional-resources}

Per il debug e la risoluzione dei problemi relativi alla riproduzione di video nel tuo canale, consulta [Configurazione e risoluzione dei problemi di riproduzione video](troubleshoot-videos.md).
