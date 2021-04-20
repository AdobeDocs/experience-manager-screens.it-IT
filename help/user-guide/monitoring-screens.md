---
title: Risoluzione dei problemi relativi al Centro di controllo dei dispositivi
seo-title: Monitoraggio degli schermi
description: Segui questa pagina per monitorare e risolvere i problemi relativi alle prestazioni dell’attività del lettore Screens e del dispositivo utilizzando il dashboard Dispositivo.
seo-description: Segui questa pagina per monitorare e risolvere i problemi relativi alle prestazioni dell’attività del lettore Screens e del dispositivo utilizzando il dashboard Dispositivo.
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
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Risoluzione dei problemi relativi al Centro di controllo dei dispositivi {#troubleshooting-device-control-center}

Puoi monitorare e risolvere i problemi relativi alle prestazioni dell’attività e del dispositivo di riproduzione Screens utilizzando il dashboard del dispositivo. Questa pagina fornisce informazioni su come monitorare e risolvere i problemi di prestazioni percepiti per Screens Player e i dispositivi assegnati.

## Monitoraggio e risoluzione dei problemi dal Centro controllo dispositivi {#monitor-and-troubleshoot-from-device-control-center}

Puoi monitorare l’attività e quindi risolvere i problemi del lettore Screens, utilizzando il dashboard del dispositivo.

### Dashboard del dispositivo {#device-dashboard}

Segui i passaggi seguenti per passare al dashboard del dispositivo:

1. Accedi al dashboard del dispositivo dal progetto, ad esempio ***Progetto di test*** —> ***Dispositivi***.

   Seleziona **Dispositivi** e **Gestione dispositivi** dalla barra delle azioni.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. Nell’elenco vengono visualizzati i dispositivi assegnati e non assegnati, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Seleziona il dispositivo (**NuovoTestDevice**) e fai clic su **Dashboard** dalla barra delle azioni.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La pagina mostra le informazioni sul dispositivo, l’attività e i dettagli del dispositivo che ti consentono di monitorare le attività e le funzioni del dispositivo.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorare l&#39;attività del dispositivo {#monitor-device-activity}

Il pannello **Attività** mostra l&#39;ultimo ping del lettore di schermate con il timestamp. L&#39;ultimo ping corrisponde all&#39;ultima volta che il dispositivo ha contattato il server.

![chlimage_1](assets/chlimage_1.png)

Inoltre, fai clic su **Raccogli registri** dall’angolo in alto a destra del pannello **Attività** per visualizzare i registri del lettore.

### Aggiorna i dettagli del dispositivo {#update-device-details}

Controllare il pannello **Dettagli dispositivo** per visualizzare l&#39;IP del dispositivo, l&#39;utilizzo dello storage, la versione del firmware e il tempo di funzionamento del lettore.

![chlimage_1-1](assets/chlimage_1-1.png)

Inoltre, fai clic su **Cancella cache** e **Aggiorna** per cancellare la cache del dispositivo e aggiornare la versione [firmware](screens-glossary.md) rispettivamente da questo pannello.

Inoltre, fai clic su **...** dall&#39;angolo in alto a destra del pannello **Dettagli dispositivo** per riavviare o aggiornare lo stato del lettore.

![chlimage_1-2](assets/chlimage_1-2.png)

### Aggiornare le informazioni sul dispositivo {#update-device-information}

Controlla il pannello **INFORMAZIONI DISPOSITIVO** per visualizzare l&#39;aggiornamento della configurazione, il modello di dispositivo, il sistema operativo del dispositivo e le informazioni sulla shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Inoltre, fai clic su (**...**) dall&#39;angolo in alto a destra del pannello Informazioni dispositivo per visualizzare le proprietà o aggiornare il dispositivo.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Fare clic su **Proprietà** per visualizzare la finestra di dialogo **Proprietà dispositivo**. È possibile modificare il titolo del dispositivo o scegliere l&#39;opzione per gli aggiornamenti di configurazione come **Manuale** o **Automatico**.

>[!NOTE]
>
>Per ulteriori informazioni sugli eventi associati agli aggiornamenti automatici o manuali del dispositivo, consulta la sezione ***Aggiornamenti automatici e manuali dal dashboard del dispositivo*** in [Gestione dei canali](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Visualizza schermata del lettore {#view-player-screenshot}

Puoi visualizzare la schermata del lettore dal dispositivo dal pannello **PLAYER SCREENSHOT** .

Fare clic su (**..**) nell&#39;angolo in alto a destra del pannello Screenshot del lettore e selezionare **Aggiorna schermata** per visualizzare l&#39;istantanea del lettore in esecuzione.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestisci preferenze {#manage-preferences}

Il pannello **PREFERENZE** consente all&#39;utente di modificare le preferenze per **Interfaccia utente amministratore**, **Controllo canali** e **Eseguire il debug remoto** per il dispositivo.

>[!NOTE]
>Per ulteriori informazioni su queste opzioni, consulta [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Inoltre, fai clic su **Impostazioni** nell&#39;angolo in alto a destra per aggiornare le preferenze del dispositivo. Puoi aggiornare le seguenti preferenze:

* **URL del server**
* **Risoluzione**
* **Riavvia pianificazione**
* **N. max dei file di registro da mantenere**
* **Livello registro**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Puoi selezionare uno dei seguenti livelli di log:
>* **Disattiva**
>* **Debug**
>* **Info**
>* **Avvertenza**
>* **Errore**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Risolvere i problemi relativi alle impostazioni OSGi {#troubleshoot-osgi-settings}

È necessario abilitare il referente vuoto per consentire al dispositivo di inviare dati al server. Ad esempio, se la proprietà referrer vuota è disabilitata, il dispositivo non può inviare nuovamente una schermata.

Attualmente alcune di queste funzioni sono disponibili solo se il *filtro di riferimento Apache Sling Allow Empty* è abilitato nella configurazione OSGi. È possibile che nel dashboard venga visualizzato un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzioni.

Segui i passaggi riportati di seguito per abilitare il filtro di riferimento Apache Sling Consenti vuoto

1. Passa a **Configurazione console Web Adobe Experience Manager**, ovvero `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Seleziona l&#39;opzione **allow.empty** .
1. Fai clic su **Salva**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Consigli {#recommendations}

La sezione seguente consiglia di monitorare i collegamenti di rete, il server e i lettori per comprendere lo stato di salute e reagire ai problemi.

AEM fornisce un monitoraggio integrato per:

* ** Heartbeat ogni 5 secondi per indicare che AEM Screens Player è in funzione.
* ** Screenshot dal lettore che mostra ciò che è attualmente visualizzato sul lettore.
* La versione *Firmware di AEM Screens Player* installata sul lettore.
* *Spazio di archiviazione gratuito* sul lettore.

Recommendations per il monitoraggio remoto con software di terze parti:

* Utilizzo della CPU sui lettori.
* Controlla se il processo di AEM Screens Player è in esecuzione.
* Riavvio/riavvio remoto del lettore.
* Notifiche in tempo reale.

Si consiglia di implementare l&#39;hardware e il sistema operativo di Windows Media Player in modo da consentire l&#39;accesso remoto per diagnosticare i problemi e riavviare il lettore.

#### Risorse aggiuntive {#additional-resources}

Per eseguire il debug e risolvere eventuali problemi relativi alla riproduzione di video nel canale, consulta [Configurazione e risoluzione dei problemi di riproduzione video](troubleshoot-videos.md) .
