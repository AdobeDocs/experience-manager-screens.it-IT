---
title: Risoluzione dei problemi di Device Control Center
seo-title: Monitoring Screens
description: Segui questa pagina per monitorare e risolvere i problemi di prestazioni per l’attività del lettore Screens e il dispositivo utilizzando il dashboard Dispositivo.
seo-description: Follow this page to monitor and troubleshoot performance for your Screens player activity and device usingtheDevice dashboard.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 2%

---

# Risoluzione dei problemi di Device Control Center {#troubleshooting-device-control-center}

Puoi monitorare e risolvere i problemi di prestazioni per l’attività e il dispositivo del lettore Screens utilizzando il dashboard Dispositivo. Questa pagina fornisce informazioni su come monitorare e risolvere i problemi di prestazioni percepiti per Screens player e i dispositivi assegnati.

## Monitoraggio e risoluzione dei problemi da Centro controllo dispositivi {#monitor-and-troubleshoot-from-device-control-center}

Puoi monitorare l’attività e quindi risolvere eventuali problemi del lettore Screens, utilizzando il dashboard del dispositivo.

### Dashboard dispositivo {#device-dashboard}

Per accedere al dashboard dei dispositivi, segui la procedura riportata di seguito:

1. Dal progetto, accedi al dashboard dei dispositivi, ad esempio ***Progetto di prova*** —> ***Dispositivi***.

   Seleziona **Dispositivi** e **Gestione dispositivi** dalla barra delle azioni.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. L&#39;elenco mostra i dispositivi assegnati e non assegnati, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Seleziona il dispositivo (**NewTestDevice**) e fai clic su **Dashboard** dalla barra delle azioni.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La pagina mostra le informazioni sul dispositivo, l’attività e i dettagli del dispositivo che consentono di monitorare le attività e le funzioni del dispositivo.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorare l&#39;attività del dispositivo {#monitor-device-activity}

Il **Attività** Il pannello mostra l’ultimo ping del lettore Screens con la marca temporale. L&#39;ultimo ping corrisponde all&#39;ultimo contatto del dispositivo con il server.

![chlimage_1](assets/chlimage_1.png)

Inoltre, fai clic **Raccogli registri** dall&#39;angolo in alto a destra del **Attività** per visualizzare i registri del lettore.

### Aggiorna dettagli dispositivo {#update-device-details}

Controlla la **Dettagli dispositivo** per visualizzare l&#39;IP del dispositivo, l&#39;utilizzo dello storage, la versione del firmware e il tempo di attività del lettore per il dispositivo.

![chlimage_1-1](assets/chlimage_1-1.png)

Inoltre, fai clic **Cancella cache** e **Aggiorna** per cancellare la cache del dispositivo e aggiornare [firmware](screens-glossary.md) versione rispettivamente da questo pannello.

Inoltre, fai clic su **...** dall&#39;angolo in alto a destra del **Dettagli dispositivo** per riavviare o aggiornare lo stato del lettore.

![chlimage_1-2](assets/chlimage_1-2.png)

### Aggiorna informazioni dispositivo {#update-device-information}

Controlla la **INFORMAZIONI DISPOSITIVO** per visualizzare l&#39;aggiornamento della configurazione, il modello del dispositivo, il sistema operativo del dispositivo e le informazioni sulla shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Inoltre, fai clic su (**...**) dall&#39;angolo superiore destro del pannello Informazioni dispositivo per visualizzare le proprietà o aggiornare il dispositivo.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Clic **Proprietà** per visualizzare **Proprietà dispositivo** . Puoi modificare il titolo del dispositivo o scegliere l’opzione per gli aggiornamenti della configurazione come **Manuale** o **Automatico**.

>[!NOTE]
>
>Per ulteriori informazioni sugli eventi associati agli aggiornamenti automatici o manuali del dispositivo, consulta la sezione ***Aggiornamenti automatici e manuali dal dashboard dei dispositivi*** in [Gestione dei canali](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Visualizza schermata lettore {#view-player-screenshot}

Puoi visualizzare lo screenshot del lettore dal dispositivo dalla sezione **SCHERMATA DEL LETTORE** pannello.

Fai clic su (**...**) nell&#39;angolo in alto a destra del pannello Schermata del lettore e selezionare **Aggiorna schermata** per visualizzare l&#39;istantanea del lettore in esecuzione.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestione preferenze {#manage-preferences}

Il **PREFERENZE** consente all&#39;utente di modificare le preferenze per **Interfaccia utente amministratore**, **Commutatore canale**, e **Debug remoto** per il dispositivo.

>[!NOTE]
>Per ulteriori informazioni su queste opzioni, vedi [Lettore AEM Screens](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Inoltre, fai clic **Impostazioni** dall’angolo in alto a destra per aggiornare le preferenze del dispositivo. Puoi aggiornare le seguenti preferenze:

* **URL del server**
* **Risoluzione**
* **Riavvia pianificazione**
* **N. max. di file di registro da mantenere**
* **Livello registro**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>È possibile selezionare uno dei seguenti livelli di registro:
>* **Disattiva**
>* **Debug**
>* **Info**
>* **Avvertenza**
>* **Errore**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Risoluzione dei problemi relativi alle impostazioni OSGi {#troubleshoot-osgi-settings}

È necessario abilitare il referente vuoto per consentire al dispositivo di pubblicare dati sul server. Ad esempio, se la proprietà del referente vuoto è disabilitata, il dispositivo non può pubblicare uno screenshot.

Attualmente alcune di queste funzioni sono disponibili solo se *Il Filtro Di Riferimento Apache Sling Consenti Vuoto* è abilitato nella configurazione OSGi. È possibile che nel dashboard venga visualizzato un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzionalità.

Segui i passaggi seguenti per abilitare il filtro Apache Sling Referrer Allow Empty

1. Accedi a **Configurazione della console web Adobe Experience Manager**, ovvero `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Controlla la **allow.empty** opzione.
1. Fai clic su **Salva**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Consigli {#recommendations}

La sezione seguente consiglia di monitorare i collegamenti di rete, il server e i lettori per comprenderne lo stato e reagire ai problemi.

L&#39;AEM fornisce un monitoraggio integrato per:

* *Heartbeat* ogni 5 secondi per indicare che AEM Screens Player è in funzione.
* *Schermata* dal lettore che mostra ciò che è attualmente visualizzato sul lettore.
* Il *Firmware del lettore AEM Screens* versione installata nel lettore.
* *Spazio di archiviazione libero* sul lettore.

Recommendations per il monitoraggio remoto con software di terze parti:

* Utilizzo della CPU sui lettori.
* Controlla se il processo di AEM Screens Player è in esecuzione.
* Riavvio/riavvio remoto del lettore.
* Notifiche in tempo reale.

Si consiglia di distribuire l&#39;hardware e il sistema operativo del lettore in modo da consentire l&#39;accesso remoto per diagnosticare i problemi e riavviare il lettore.

#### Risorse aggiuntive {#additional-resources}

Consulta [Configurazione della riproduzione video e risoluzione dei problemi](troubleshoot-videos.md) per eseguire il debug e risolvere i problemi relativi alla riproduzione di video nel canale.
