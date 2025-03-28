---
title: Configurazione e distribuzione di AEM Screens
description: AEM Screens Player è disponibile per Android&trade;, Chrome OS, iOS e Windows. Scopri come configurare e distribuire AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 1%

---

# Configurazione e distribuzione di AEM Screens {#configuring-and-deploying-aem-screens}

Questa pagina mostra come installare e configurare i lettori Screens sui tuoi dispositivi.

## Configurazione server {#server-configuration}

>[!IMPORTANT]
>
>AEM Screens Player non utilizza il token CSRF (Cross-Site Request Forgery). Pertanto, per configurare il server AEM in modo che sia pronto all’uso per AEM Screens, ignora il filtro referente consentendo l’utilizzo di referenti vuoti.

## Framework di verifica stato {#health-check-framework}

Il framework di verifica stato consente all’utente di verificare se sono impostate due configurazioni necessarie prima di eseguire un progetto AEM Screens.

Consente all’utente di verificare i due controlli di configurazione seguenti per eseguire un progetto AEM Screens, ovvero per controllare lo stato dei due filtri seguenti:

1. **Consenti riferimento vuoto**
2. **https**

Segui i passaggi seguenti per verificare se queste due configurazioni vitali sono abilitate per AEM Screens:

1. Passare a [Verifica stato Sling Console Web Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![risorse](assets/health-check1.png)


2. Fai clic su **Esegui i controlli di integrità selezionati** per eseguire la convalida per due proprietà elencate sopra.

   Se entrambi i filtri sono abilitati, il **Servizio integrità configurazione di Screens** mostra il **Risultato** come **OK** con entrambe le configurazioni abilitate.

   ![risorse](assets/health-check2.png)

   Se uno o entrambi i filtri sono disattivati, viene visualizzato un avviso per l’utente, come illustrato nella figura riportata di seguito.

   Gli avvisi seguenti mostrano se entrambi i filtri sono disabilitati:
   ![risorse](assets/health-check3.png)

>[!NOTE]
>
>* Per abilitare il filtro **Apache Sling Referrer Filter**, vedi [Consenti richieste referrer vuote](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Per abilitare il servizio **HTTP**, vedere [Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).

### Prerequisiti {#prerequisites}

I seguenti punti chiave aiutano a configurare e a rendere il server AEM pronto all’uso per AEM Screens.

#### Consenti richieste referrer vuote {#allow-empty-referrer-requests}

1. Passa a **Configurazione console Web Adobe Experience Manager** tramite istanza AEM > icona martello > **Operazioni** > **Console Web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Configurazione console Web Adobe Experience Manager** aperta. Cerca il referente sling.

   Per eseguire ricerche nella proprietà del referente sling, premere **Comando+F** per **Mac** e **Controllo+F** per **Windows**.

1. Selezionare l&#39;opzione **Consenti vuoto**, come illustrato nella figura seguente.

   ![immagine](assets/config/empty-ref2.png)

1. Fai clic su **Salva** per abilitare il filtro di riferimento Apache Sling Consenti vuoto.


#### Servizio HTTP basato su Apache Felix Jetty {#allow-apache-felix-service}

1. Passa a **Configurazione console Web Adobe Experience Manager** tramite istanza AEM > icona martello > **Operazioni** > **Console Web**.

   ![immagine](assets/config/empty-ref1.png)

1. **Configurazione console Web Adobe Experience Manager** aperta. Cerca Apache Felix Jetty Based HTTP Service.

   Per cercare questa proprietà, premere **Comando+F** per **Mac** e **Controllo+F** per **Windows**.

1. Selezionare l&#39;opzione **ABILITA HTTP**, come illustrato nella figura seguente.

   ![immagine](assets/config/config-1.png)

1. Fai clic su **Salva** per abilitare il servizio *Http*.

#### Abilitare l’interfaccia utente touch per AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens richiede l’interfaccia utente TOUCH e non funziona con l’interfaccia classica di Adobe Experience Manager (AEM).

1. Passa a `*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*`
1. Assicurati che la **modalità predefinita dell&#39;interfaccia utente di authoring** sia impostata su **TOUCH**, come illustrato nella figura seguente

In alternativa, è possibile eseguire la stessa impostazione utilizzando gli strumenti AuthorInstance *>* (icona a forma di martello) > **Operazioni** > **Console Web** e cercare **Servizio modalità interfaccia utente di authoring WCM**.

![schermata_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Puoi sempre abilitare l’interfaccia classica per utenti specifici utilizzando le preferenze dell’utente.

#### AEM in modalità di esecuzione NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

L&#39;esecuzione di AEM in produzione utilizza la modalità di esecuzione **NOSAMPLECONTENT**. Rimuovi l&#39;intestazione *X-Frame-Options=SAMEORIGIN* (nella sezione dell&#39;intestazione di risposta aggiuntiva) da

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Questa rimozione è necessaria per consentire a AEM Screens Player di riprodurre i canali online.

#### Limitazioni password {#password-restrictions}

Con le ultime modifiche apportate a ***DeviceServiceImpl***, non è necessario rimuovere le restrizioni relative alle password.

Puoi configurare ***DeviceServiceImpl*** dal collegamento seguente per abilitare la restrizione della password durante la creazione della password per gli utenti del dispositivo di schermo:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Segui i passaggi seguenti per configurare ***DeviceServiceImpl***:

1. Passa a **Configurazione console Web Adobe Experience Manager** tramite l&#39;istanza AEM > icona martello > **Operazioni** > **Console Web**.

1. **Configurazione console Web Adobe Experience Manager** aperta. Cerca `*deviceservice*`. Per cercare la proprietà, premere **Comando+F** per macOS e **Controllo+F** per Microsoft® Windows.

![schermata_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configurazione Dispatcher {#dispatcher-configuration}

Per informazioni su come configurare Dispatcher per un progetto AEM Screens, vedere [Configurazione di Dispatcher per un progetto AEM Screens](dispatcher-configurations-aem-screens.md).

#### codifica Java™ {#java-encoding}

Impostare la codifica ***Java™*** su Unicode. `*Dfile.encoding=Cp1252*` ad esempio non funziona.

>[!NOTE]
>
>Utilizza HTTPS per il server AEM Screens nell’utilizzo in produzione.
