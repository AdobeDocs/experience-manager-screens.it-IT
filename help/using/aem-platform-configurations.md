---
title: Configurazioni della piattaforma AEM
seo-title: AEM Platform Configurations
description: La pagina descrive le configurazioni della piattaforma AEM
seo-description: The page describes AEM Platform Configurations
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 21%

---

# Configurazioni della piattaforma AEM  {#platform-configurations}

>[!NOTE]
>
>Questa attività è in genere gestita da un implementatore AEM.

Segui le sezioni seguenti per configurare le configurazioni della piattaforma AEM per iniziare a utilizzare AEM Screens.

## Configurazioni server {#server-configurations}

Per configurare le configurazioni del server, fare riferimento a [Configurazioni server](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Author-Publish {#author-publish}

Per impostare l’authoring-pubblicazione, consulta [Configurazione di Author e Publish in AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Se esiste un solo autore e una sola pubblicazione, è sufficiente seguire i passaggi descritti in **Setting up Replication Agents on Author** (Impostazione degli agenti di replica sull’autore) nella pagina [Configuring Author and Publish in AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/using/author-and-publish.html) (Configurazione di Author and Publish in AEM Screens).

## Configurazioni di Dispatcher {#dispatcher-configurations}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager. L’utilizzo di AEM Dispatcher consente inoltre di proteggere il server AEM da eventuali attacchi. Di conseguenza, per aumentare la sicurezza della tua istanza di AEM, puoi utilizzare Dispatcher insieme a un server web di classe Enterprise.

Fai riferimento a **[Configurazioni del Dispatcher per AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** vengono evidenziate le linee guida per la configurazione di dispatcher per un progetto AEM Screens.

## Installazione di rappresentazioni FFMpeg e video {#installing-ffmpeg}

Installare FFMpeg seguendo la procedura per il sistema operativo appropriato (in genere RHEL):

1. Se si installa attivando EPEL e RPMFusion, è possibile installare tutti i codec gstreamer per ampliare il supporto per le conversioni FFmpeg
1. Se il codec AAC è contrassegnato come sperimentale, le conversioni ffmpeg avranno esito negativo. Per evitare questo, aggiungi -strict -2 ai profili video (/etc/dam/video in AEM 6.3 e spostati in /libs/settings/dam/video in AEM 6.4)
   >[!NOTE]
   >
   > Tieni presente che -strict -2 deve essere gli ultimi parametri nell’elenco dei parametri. Inoltre, in AEM 6.4 è necessario copiare i nodi in */libs/settings/dam/video* a */conf/global/settings/dam/video* come indicato in [Rappresentazioni video](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Verifica che le conversioni video siano in corso e che vengano create le rappresentazioni.

## Limitazioni password {#password-restrictions}

È necessario disabilitare i criteri password dell&#39;AEM nell&#39;istanza AMS. Questa può essere configurata alternativamente nella console web utilizzando il servizio per dispositivi Screens *com.adobe.cq.screens.device.impl.DeviceService*
Fai riferimento a **Limitazioni password** sezione in[Configurazione di Author e Publish in AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/using/author-and-publish.html)

## Configurazione degli ambienti {#setting-up-environments}

Installa ed esegui le versioni più recenti dei seguenti pacchetti per la tua versione di Adobe Experience Manager (AEM):

* AEM Service Pack
* Feature Pack di Screens
* AEM Cumulative Fix Pack

Oltre a quanto sopra, identifica tutti i pacchetti di sviluppo (ad esempio, componenti core WCM) o i toolkit di terze parti (ad esempio, SAP Hybris) necessari.
Installare gli stessi pacchetti software negli ambienti di sviluppo locali. Istruisci il client ad adottare la stessa configurazione su tutti i server di controllo qualità, stage e produzione. Configurazioni server non corrispondenti causeranno problemi durante la distribuzione e il test.

>[!NOTE]
>
>Per installare il Feature Pack più recente per AEM Screens, fare riferimento a [Note sulla versione](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Impostazione di ACL {#setting-up-acls}

La sezione Configurazione di ACL spiega come separare i progetti in modo che ogni singolo utente o team gestisca il proprio progetto.

Fai riferimento a [Impostazione di ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) per ulteriori dettagli.
