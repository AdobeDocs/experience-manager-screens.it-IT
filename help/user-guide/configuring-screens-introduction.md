---
title: Configurazione e distribuzione di AEM Screens
seo-title: Configurazione e distribuzione di Screens
description: Il lettore AEM Screens è disponibile per Android, Chrome OS, iOS e Windows. Questa pagina descrive la configurazione e l’implementazione di AEM Screens e riepiloga le linee guida per la selezione h/w del dispositivo di riproduzione.
seo-description: Il lettore AEM Screens è disponibile per Android, Chrome OS, iOS e Windows. Questa pagina descrive la configurazione e l’implementazione di AEM Screens e riepiloga le linee guida per la selezione h/w del dispositivo di riproduzione.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# Configurazione e distribuzione di AEM Screens {#configuring-and-deploying-aem-screens}

Questa pagina mostra come installare e configurare i lettori Screens sui dispositivi.

## Configurazione server {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>AEM Screens Player non utilizza il token CSRF (Cross-Site Request Forgery). Pertanto, per configurare e AEM server in modo che sia pronto per l’uso per AEM Screens, salta il filtro di riferimento consentendo i referenti vuoti.

## Framework di controllo dello stato {#health-check-framework}

Il framework di verifica dello stato consente all’utente di verificare se sono configurate due configurazioni necessarie prima di eseguire un progetto AEM Screens.

Consente all’utente di verificare i due seguenti controlli di configurazione per eseguire un progetto AEM Screens, ovvero per controllare lo stato dei due filtri seguenti:

1. **Consenti referente vuoto**
2. **https**

Segui i passaggi seguenti per verificare se queste due configurazioni vitali sono abilitate per AEM Screens:

1. Passa a [Verifica dello stato dello sling della console Web Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![assets](assets/health-check1.png)


2. Fare clic su **Esegui controlli di integrità selezionati** per eseguire la convalida per due proprietà elencate sopra.

   Se entrambi i filtri sono attivati, il **Servizio integrità configurazione Screens** mostra il **Risultato** come **OK** con entrambe le configurazioni come abilitate.

   ![assets](assets/health-check2.png)

   Se uno o entrambi i filtri sono disabilitati, viene visualizzato un avviso per l’utente, come illustrato nella figura riportata di seguito.

   Il seguente avviso mostra se i due filtri sono disabilitati:
   ![assets](assets/health-check3.png)

>[!NOTE]
>
>* Per abilitare il **Filtro referente Apache Sling**, fai riferimento a [Consenti richieste referente vuote](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Per abilitare il servizio **HTTP**, consulta [Servizio HTTP basato su Jetty Apache Felix](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Prerequisiti {#prerequisites}

I seguenti punti chiave aiutano a configurare e AEM server per renderlo pronto all’uso per AEM Screens.

#### Consenti richieste referente vuote {#allow-empty-referrer-requests}

1. Passa a **Configurazione della console Web Adobe Experience Manager** tramite AEM istanza —> icona a forma di martello —> **Operazioni** —> **Console web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Viene visualizzata la** configurazione della console Web Adobe Experience Manager. Cerca il referrer sling.

   Per cercare la proprietà del referente sling, premere **Comando+F** per **Mac** e **Control+F** per **Windows**.

1. Selezionare l&#39;opzione **Consenti valori vuoti**, come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/empty-ref2.png)

1. Fai clic su **Salva** per abilitare il filtro di riferimento Apache Sling Allow Empty.


#### Servizio HTTP basato su Apache Felix Jetty {#allow-apache-felix-service}

1. Passa a **Configurazione della console Web Adobe Experience Manager** tramite AEM istanza —> icona a forma di martello —> **Operazioni** —> **Console web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Viene** aperta la configurazione della console Web Adobe Experience Manager. Cerca Apache Felix Jetty Based HTTP Service.

   Per cercare questa proprietà, premere **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

1. Seleziona l’opzione **ENABLE HTTP** , come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/config-1.png)

1. Fai clic su **Salva** per abilitare il servizio *http*.

#### Abilitare l’interfaccia utente touch per AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens richiede l’interfaccia utente TOUCH e non funziona con l’interfaccia classica di Adobe Experience Manager (AEM).

1. Passa a *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Assicurati che la **modalità predefinita dell&#39;interfaccia utente di authoring** sia impostata su **TOUCH**, come illustrato nella figura seguente

In alternativa, puoi anche eseguire la stessa impostazione utilizzando gli strumenti *->* (icona a forma di martello) -> **Operazioni** -> **Console web** e cercare **Servizio modalità interfaccia utente di authoring WCM**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Puoi sempre abilitare l’interfaccia classica per utenti specifici utilizzando le preferenze utente.

#### AEM in modalità runmode NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

L&#39;esecuzione AEM in produzione utilizza la modalità runmode **NOSAMPLECONTENT**. Rimuovi l&#39;intestazione *X-Frame-Options=SAMEORIGIN* (nella sezione di intestazione di risposta aggiuntiva) da

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Questo è necessario affinché AEM Screens Player possa riprodurre i canali online.

#### Restrizioni per le password {#password-restrictions}

Con le ultime modifiche apportate a ***DeviceServiceImpl***, non è necessario rimuovere le restrizioni relative alle password.

Puoi configurare ***DeviceServiceImpl*** dal collegamento seguente per abilitare la restrizione della password durante la creazione della password per gli utenti del dispositivo screens:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Segui i passaggi seguenti per configurare ***DeviceServiceImpl***:

1. Passa a **Configurazione della console Web Adobe Experience Manager** tramite AEM istanza —> icona a forma di martello —> **Operazioni** —> **Console web**.

1. **Viene visualizzata la** configurazione della console Web Adobe Experience Manager. Cerca *deviceservice*. Per cercare la proprietà, premere **Comando+F** per macOS e **Ctrl+F** per Microsoft Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configurazione del Dispatcher {#dispatcher-configuration}

Per informazioni su come configurare il dispatcher per un progetto AEM Screens, consulta [Configurazione del dispatcher per un progetto AEM Screens](dispatcher-configurations-aem-screens.md).

#### Codifica Java {#java-encoding}

Imposta la ***codifica Java*** su Unicode. Ad esempio, *Dfile.encoding=Cp1252* non funzionerà.

>[!NOTE]
>**Consiglio:**
>Si consiglia di utilizzare HTTPS per AEM Screens Server in uso di produzione.
