---
title: Configurazione e distribuzione di AEM Screens
seo-title: Configuring and Deploying Screens
description: Il lettore AEM Screens è disponibile per Android, Chrome OS, iOS e Windows. Questa pagina descrive la configurazione e la distribuzione di AEM Screens e riepiloga le linee guida per la selezione di hardware per il dispositivo di riproduzione.
seo-description: The AEM Screens player is available for Android, Chrome OS, iOS, and Windows. This page describes the configuration and deployment of AEM Screens and also summarizes the h/w selection guidelines for player device.
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
source-wordcount: '714'
ht-degree: 0%

---

# Configurazione e distribuzione di AEM Screens {#configuring-and-deploying-aem-screens}

Questa pagina mostra come installare e configurare i lettori Screens sui tuoi dispositivi.

## Configurazione server {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>Il lettore AEM Screens non utilizza il token CSRF (Cross-Site Request Forgery). Pertanto, per configurare e rendere il server AEM pronto all’uso per AEM Screens, ignora il filtro referente consentendo l’utilizzo di referenti vuoti.

## Framework di verifica stato {#health-check-framework}

Il framework di Verifica stato consente all’utente di verificare se sono impostate due configurazioni necessarie prima di eseguire un progetto AEM Screens.

Consente all’utente di verificare i due controlli di configurazione seguenti per eseguire un progetto AEM Screens, ovvero per controllare lo stato dei due filtri seguenti:

1. **Consenti referrer vuoto**
2. **https**

Segui i passaggi seguenti per verificare se queste due configurazioni vitali sono abilitate per AEM Screens:

1. Accedi a [Verifica stato Sling della console web di Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![risorse](assets/health-check1.png)


2. Fai clic su **Esegui i controlli di integrità selezionati** per eseguire la convalida per due proprietà elencate sopra.

   Se entrambi i filtri sono abilitati, il **Servizio integrità configurazione Screens** mostra la **Risultato** as **OK** con entrambe le configurazioni abilitate.

   ![risorse](assets/health-check2.png)

   Se uno o entrambi i filtri sono disattivati, viene visualizzato un avviso per l’utente, come illustrato nella figura riportata di seguito.

   Gli avvisi seguenti mostrano se entrambi i filtri sono disabilitati:
   ![risorse](assets/health-check3.png)

>[!NOTE]
>
>* Per attivare **Filtro referrer Apache Sling**, fare riferimento a [Consenti richieste referrer vuote](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Per attivare **HTTP** servizio, fare riferimento a [Servizio HTTP basato su Apache Felix Jetty](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Prerequisiti {#prerequisites}

I seguenti punti chiave aiutano a configurare e a rendere il server AEM pronto all’uso per AEM Screens.

#### Consenti richieste referrer vuote {#allow-empty-referrer-requests}

1. Accedi a **Configurazione della console web Adobe Experience Manager** tramite istanza AEM —> icona martello —> **Operazioni** —> **Console web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Configurazione della console web Adobe Experience Manager** viene aperto. Cerca il referente sling.

   Per cercare la proprietà del referente sling, premi **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

1. Controlla la **Consenti vuoto** come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/empty-ref2.png)

1. Clic **Salva** per abilitare Apache Sling Referrer Filter Allow Empty (Consenti vuoto).


#### Servizio HTTP basato su Apache Felix Jetty {#allow-apache-felix-service}

1. Accedi a **Configurazione della console web Adobe Experience Manager** tramite istanza AEM —> icona martello —> **Operazioni** —> **Console web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Configurazione della console web Adobe Experience Manager** viene aperto. Cerca Apache Felix Jetty Based HTTP Service.

   Per cercare questa proprietà, premere **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

1. Controlla la **ABILITA HTTP** come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/config-1.png)

1. Clic **Salva** per attivare *http* servizio.

#### Abilitare l’interfaccia utente touch per AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens richiede l’interfaccia touch e non funzionerà con l’interfaccia classica di Adobe Experience Manager (AEM).

1. Accedi a *&lt;yourauthorinstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Assicurati che **Modalità interfaccia utente di authoring predefinita** è impostato su **TOUCH**, come illustrato nella figura seguente

In alternativa, è possibile eseguire la stessa impostazione utilizzando l’istanza Author *->* strumenti (icona martello) -> **Operazioni** -> **Console web** e cerca **Servizio modalità interfaccia utente di authoring WCM**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Puoi sempre abilitare l’interfaccia classica per utenti specifici utilizzando le preferenze dell’utente.

#### AEM in modalità di esecuzione NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

L’esecuzione dell’AEM in produzione utilizza **NOSAMPLECONTENT** runmode. Rimuovi il *X-Frame-Options=SAMEORIGIN* (nella sezione dell’intestazione di risposta aggiuntiva) da

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Questa opzione è necessaria per consentire a AEM Screens Player di riprodurre i canali online.

#### Limitazioni password {#password-restrictions}

Con le ultime modifiche apportate a ***DeviceServiceImpl***, non è necessario rimuovere le restrizioni relative alla password.

Puoi configurare ***DeviceServiceImpl*** dal collegamento seguente per abilitare la restrizione della password durante la creazione della password per gli utenti del dispositivo Screens:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Segui i passaggi seguenti per configurare ***DeviceServiceImpl***:

1. Accedi a **Configurazione della console web Adobe Experience Manager** tramite istanza AEM —> icona martello —> **Operazioni** —> **Console web**.

1. **Configurazione della console web Adobe Experience Manager** viene aperto. Cerca *deviceservice*. Per cercare la proprietà, premi **Comando+F** per macOS e **Ctrl+F** per Microsoft Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configurazione del Dispatcher {#dispatcher-configuration}

Per informazioni su come configurare Dispatcher per un progetto AEM Screens, consulta [Configurazione di Dispatcher per un progetto AEM Screens](dispatcher-configurations-aem-screens.md).

#### Codifica Java {#java-encoding}

Imposta il ***Codifica Java*** a Unicode. Ad esempio: *Dfile.encoding=Cp1252* non funzionerà.

>[!NOTE]
>**Consiglio:**
>Si consiglia di utilizzare HTTPS per AEM Screens Server nell’utilizzo in produzione.
