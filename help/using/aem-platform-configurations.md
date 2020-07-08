---
title: Configurazioni della piattaforma AEM
seo-title: Configurazioni della piattaforma AEM
description: La pagina descrive le configurazioni AEM Platform
seo-description: La pagina descrive le configurazioni AEM Platform
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# Configurazioni della piattaforma AEM  {#platform-configurations}

>[!NOTE]
>
>L&#39;azionista tipico di questa attività è AEM Implementor.

Segui le sezioni seguenti per configurare le configurazioni della piattaforma AEM per iniziare a usare i AEM Screens.

## Configurazioni server {#server-configurations}

Per configurare le configurazioni del server, fare riferimento a Configurazioni [server](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Author-Publish {#author-publish}

Per impostare l’opzione di pubblicazione dell’autore, consultate [Configurazione di Author e Publish in AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Se esiste un solo autore e una sola pubblicazione, è sufficiente seguire i passaggi descritti in **Setting up Replication Agents on Author** (Impostazione degli agenti di replica sull’autore) nella pagina [Configuring Author and Publish in AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/using/author-and-publish.html) (Configurazione di Author and Publish in AEM Screens).

## Configurazioni Dispatcher {#dispatcher-configurations}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager. L’utilizzo di AEM Dispatcher consente inoltre di proteggere il server AEM da eventuali attacchi. Di conseguenza, per aumentare la sicurezza della tua istanza di AEM, puoi utilizzare Dispatcher insieme a un server web di classe Enterprise.

Fare riferimento a Configurazioni **[Dispatcher per AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)**che illustrano le linee guida per la configurazione del dispatcher per un progetto di AEM Screens.

## Installazione di rappresentazioni FFMpeg e video {#installing-ffmpeg}

Installate FFMpeg seguendo la procedura per il sistema operativo appropriato (in genere RHEL):

1. Se si esegue l’installazione abilitando EPEL e RPMFusion, è possibile installare tutti i codec gstreaming per ampliare il supporto per le conversioni FFmpeg
1. Se il codec AAC è contrassegnato come sperimentale, le conversioni ffmpeg non riusciranno. Per evitare questa situazione, aggiungete -rigorosamente -2 ai profili video (/etc/dam/video in AEM 6.3 e spostatelo in /libs/settings/dam/video in AEM 6.4)
   >[!NOTE]
   >
   > Si prega di notare che -narrow -2 deve essere gli ultimi parametri nell&#39;elenco dei parametri. Inoltre in AEM 6.4 è necessario copiare i nodi in */libs/settings/dam/video* in */conf/global/settings/dam/video* come indicato nelle rappresentazioni [video](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Verificate che si verifichino conversioni dei video e che vengano create delle rappresentazioni.

## Restrizioni per password {#password-restrictions}

Il criterio della password di AEM deve essere disabilitato nell’istanza AMS. Questa funzione può essere configurata in modo alternato nella console Web utilizzando il servizio dispositivo Screens *com.adobe.cq.screens.device.impl.DeviceService* Fare riferimento alla sezione Limitazioni **per la** password[inConfigurazione di Author e Publish in AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/using/author-and-publish.html)

## Impostazione degli ambienti {#setting-up-environments}

Installate ed eseguite le versioni più aggiornate dei pacchetti seguenti per la versione del Adobe Experience Manager  (AEM):

* AEM Service Pack
* Pacchetto di funzioni per schermi
* AEM Cumulative Fix Pack

In aggiunta a quanto sopra, identificate eventuali pacchetti di sviluppo (ad esempio, componenti WCM) o toolkit di terze parti (ad esempio, SAP Hybris) richiesti.
Installate gli stessi pacchetti software negli ambienti di sviluppo locali. Chiedete al client di adottare la stessa configurazione su tutti i server QA, Stage e Produzione. Configurazioni server non corrispondenti creeranno problemi durante l&#39;implementazione e il test.

>[!NOTE]
>
>Per installare l’ultimo Feature Pack per AEM Screens, consulta le Note sulla [versione](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Impostazione degli ACL {#setting-up-acls}

La configurazione degli ACL spiega come separare i progetti in modo che ogni singolo o team gestisca il proprio progetto.

Refer  to [Setting up ACLs](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) for more details.
