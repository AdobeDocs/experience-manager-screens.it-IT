---
title: Configurazioni della piattaforma AEM
seo-title: Configurazioni della piattaforma AEM
description: La pagina descrive le configurazioni della piattaforma AEM
seo-description: La pagina descrive le configurazioni della piattaforma AEM
translation-type: tm+mt
source-git-commit: 5c83a2b59769dfd3736a830f7d7d3cc35137c182

---

# Configurazioni della piattaforma AEM {#platform-configurations}

>[!NOTE]
>
>L'azionista tipico di questa attività è AEM Implementor.

Segui le sezioni seguenti per configurare le configurazioni della piattaforma AEM per iniziare a utilizzare AEM Screens.

## Configurazioni server {#server-configurations}

Per configurare le configurazioni del server, fare riferimento a Configurazioni [server](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Author-Publish {#author-publish}

Per configurare la pubblicazione per l’authoring, consultate [Configurazione di Author e Publish in AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
> Se esiste un solo autore e una sola pubblicazione, è sufficiente seguire i passaggi descritti in **Impostazione degli agenti di replica sull’autore** nella pagina [Configurazione di Author and Publish in AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html) .

## Configurazioni del dispatcher {#dispatcher-configurations}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager. L’utilizzo di AEM Dispatcher consente inoltre di proteggere il server AEM da eventuali attacchi. Di conseguenza, per aumentare la sicurezza della tua istanza di AEM, puoi utilizzare Dispatcher insieme a un server web di classe Enterprise.

Fate riferimento a Configurazioni **[del dispatcher per AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** che illustra le linee guida per la configurazione del dispatcher per un progetto AEM Screens.

## Installazione di rappresentazioni FFMpeg e video {#installing-ffmpeg}

Installate FFMpeg seguendo la procedura per il sistema operativo appropriato (in genere RHEL):

1. Se si esegue l’installazione abilitando EPEL e RPMFusion, è possibile installare tutti i codec gstreaming per ampliare il supporto per le conversioni FFmpeg
1. Se il codec AAC è contrassegnato come sperimentale, le conversioni ffmpeg non riusciranno. Per evitare questa situazione, aggiungete -rigorosamente -2 ai profili video (/etc/dam/video in AEM 6.3 e spostatelo in /libs/settings/dam/video in AEM 6.4)
   >[!NOTE]
   >
   > Si prega di notare che -narrow -2 deve essere gli ultimi parametri nell'elenco dei parametri. Inoltre in AEM 6.4 è necessario copiare i nodi in */libs/settings/dam/video* in */conf/global/settings/dam/video* come indicato nelle rappresentazioni [video](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Verificate che si verifichino conversioni video e che vengano create delle rappresentazioni.

## Restrizioni per password {#password-restrictions}

Il criterio della password di AEM deve essere disabilitato nell’istanza AMS. Questa funzione può essere configurata in modo alternativo nella console Web utilizzando il servizio dispositivo Screens *com.adobe.cq.screens.device.impl.DeviceService* Fare riferimento alla sezione Limitazioni **per la** password[inConfigurazione di Author e Publish in AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## Impostazione degli ambienti {#setting-up-environments}

Installate ed eseguite le versioni più aggiornate dei pacchetti seguenti per la versione di Adobe Experience Manager (AEM):

* AEM Service Pack
* Feature Pack per schermi
* AEM Cumulative Fix Pack

In aggiunta a quanto sopra, identificate eventuali pacchetti di sviluppo (ad esempio, componenti WCM) o toolkit di terze parti (ad esempio, SAP Hybris) richiesti.
Installate gli stessi pacchetti software negli ambienti di sviluppo locali. Chiedete al client di adottare la stessa configurazione su tutti i server di controllo qualità, fase e produzione. Configurazioni server non corrispondenti creeranno problemi durante l'implementazione e il test.

>[!NOTE]
> Per installare l’ultimo Feature Pack per AEM Screens, consulta le [Note](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)sulla versione.

## Impostazione degli ACL {#setting-up-acls}

La configurazione degli ACL spiega come separare i progetti in modo che ogni singolo o team gestisca il proprio progetto.

Per ulteriori informazioni, vedere [Impostazione degli ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) .
