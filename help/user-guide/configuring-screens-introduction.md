---
title: Configurazione e distribuzione  AEM Screens
seo-title: Configurazione e distribuzione di Screens
description: Il lettore AEM Screens  è disponibile per Android, Chrome OS, iOS e Windows. Questa pagina descrive la configurazione e l'implementazione di  AEM Screens e riassume le linee guida per la selezione di h/w per il dispositivo del lettore.
seo-description: Il lettore AEM Screens  è disponibile per Android, Chrome OS, iOS e Windows. Questa pagina descrive la configurazione e l'implementazione di  AEM Screens e riassume le linee guida per la selezione di h/w per il dispositivo del lettore.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: acc0278631a4be2c90de7cc43d3b40a358ffa93e
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 1%

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

Questa pagina mostra come installare e configurare i lettori Screens sui dispositivi.

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
> lettore AEM Screens non utilizza il token CSRF (Cross-Site Request Forgery). Pertanto, per configurare e AEM server da utilizzare per  AEM Screens, ignorate il filtro di riferimento consentendo riferimenti vuoti.

## Quadro di controllo dello stato {#health-check-framework}

Il framework Health Check consente all&#39;utente di verificare se sono state configurate due configurazioni necessarie prima di eseguire un progetto AEM Screens .

Consente all&#39;utente di verificare i due seguenti controlli di configurazione per eseguire un progetto AEM Screens , vale a dire per verificare lo stato dei due filtri seguenti:

1. **Consenti referente vuoto**
2. **https**

Per verificare se queste due configurazioni vitali sono abilitate per  AEM Screens, effettuate le seguenti operazioni:

1. Passa a Controllo [stato sling console Web](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)Adobe Experience Manager.

   ![assets](assets/health-check1.png)


2. Fare clic su **Esegui controlli** di integrità selezionati per eseguire la convalida per due proprietà elencate sopra.

   Se entrambi i filtri sono attivati, il servizio **integrità configurazione** Screens mostra il **risultato** come **OK** con entrambe le configurazioni abilitate.

   ![assets](assets/health-check2.png)

   Se uno o entrambi i filtri sono disattivati, viene visualizzato un avviso per l&#39;utente, come illustrato nella figura riportata di seguito.

   Il seguente avviso mostra se entrambi i filtri sono disattivati:
   ![assets](assets/health-check3.png)

>[!NOTE]
>
>* Per abilitare il filtro **di riferimento** Apache Sling, fare riferimento a [Consenti richieste](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)di referente vuote.
>* Per abilitare il servizio **HTTP** , fare riferimento al servizio [HTTP](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)Apache Felix Jetty.


### Prerequisiti {#prerequisites}

I seguenti punti chiave aiutano a configurare e AEM server per essere pronto per  AEM Screens.

#### Consenti richieste referente vuote {#allow-empty-referrer-requests}

1. Passa a Configurazione **console Web** Adobe Experience Manager tramite AEM&#39;istanza —> icona a forma di martello —> **Operazioni** —> Console **** Web.

   ![immagine](assets/config/empty-ref1.png)

1. **Viene visualizzata la configurazione** della console Web di Adobe Experience Manager. Cerca referrer di fionda.

   Per cercare la proprietà sling referrer, premere **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

1. Selezionare l&#39;opzione **Consenti valori nulli** , come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/empty-ref2.png)

1. Fate clic su **Salva** per attivare l&#39;opzione Consenti valori nulli per il filtro Apache Sling Referrer.


#### Servizio HTTP Apache Felix Jetty {#allow-apache-felix-service}

1. Passa a Configurazione **console Web** Adobe Experience Manager tramite AEM&#39;istanza —> icona a forma di martello —> **Operazioni** —> Console **** Web.

   ![immagine](assets/config/empty-ref1.png)

1. **Viene visualizzata la configurazione** della console Web di Adobe Experience Manager. Cercate il servizio HTTP Apache Felix Jetty.

   Per effettuare una ricerca in questa proprietà, premere **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

1. Selezionate l’opzione **ABILITA HTTP** , come illustrato nella figura riportata di seguito.

   ![immagine](assets/config/config-1.png)

1. Fate clic su **Salva** per abilitare il servizio *http* .

#### Abilita interfaccia utente touch per  AEM Screens {#enable-touch-ui-for-aem-screens}

 AEM Screens richiede l’interfaccia utente TOUCH e non funziona con l’interfaccia classica di Adobe Experience Manager (AEM).

1. Passa a *&lt;istanzaAutore>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Verificate che la modalità **interfaccia utente di authoring** predefinita sia impostata su **TOUCH**, come illustrato nella figura seguente

In alternativa, potete eseguire la stessa impostazione anche utilizzando *&lt;yourAuthorInstance>*->*strumenti (icona a forma di martello)* -> **Operazioni** -> Console **** Web e cercare il servizio **** WCM per la modalità dell’interfaccia utente di authoring.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Potete sempre attivare l’interfaccia classica per utenti specifici utilizzando le preferenze utente.

#### AEM in modalità di esecuzione NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

L&#39;esecuzione AEM in produzione utilizza la modalità di esecuzione **NOSAMPLECONTENT** . *Rimuovete l’intestazione X-Frame-Options=SAMEORIGIN* (nella sezione dell’intestazione della risposta aggiuntiva)

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Questo è necessario per  AEM Screens Player per riprodurre i canali online.

#### Restrizioni per la password {#password-restrictions}

Con le ultime modifiche apportate a ***DeviceServiceImpl***, non è necessario rimuovere le restrizioni relative alla password.

Puoi configurare ***DeviceServiceImpl*** dal collegamento seguente per abilitare la limitazione della password durante la creazione della password per gli utenti del dispositivo dello schermo:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Segui i passaggi indicati di seguito per configurare ***DeviceServiceImpl***:

1. Passa a Configurazione **console Web** Adobe Experience Manager tramite AEM&#39;istanza —> icona a forma di martello —> **Operazioni** —> Console **** Web.

1. **Viene aperta la configurazione della console Web di Adobe Experience Manager **6. Cercare il servizio di assistenza. Per effettuare una ricerca nella proprietà, premere **Comando+F** per **Mac** e **Ctrl+F** per **Windows**.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

Per informazioni su come configurare il dispatcher per un progetto AEM Screens , vedere [Configurazione del dispatcher per un progetto](dispatcher-configurations-aem-screens.md)AEM Screens .

#### Codifica Java {#java-encoding}

Impostare la codifica ****** Java su Unicode. Ad esempio, *Dfile.encoding=Cp1252* non funzionerà.

>[!NOTE]
>
>**Consiglio:**
>
>Si consiglia di utilizzare HTTPS per  AEM Screens Server in uso di produzione.








