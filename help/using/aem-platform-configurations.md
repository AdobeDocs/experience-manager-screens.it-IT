---
title: Configurazioni della piattaforma AEM
seo-title: Configurazioni della piattaforma AEM
description: La pagina descrive AEM configurazioni della piattaforma
seo-description: La pagina descrive AEM configurazioni della piattaforma
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# Configurazioni della piattaforma AEM  {#platform-configurations}

>[!NOTE]
>
>Le parti interessate tipiche di questa attività sono un AEM Implementatore.

Per iniziare a utilizzare AEM Screens, segui le sezioni seguenti per configurare AEM configurazioni di piattaforma .

## Configurazioni server {#server-configurations}

Per configurare le configurazioni del server, fare riferimento a [Configurazioni server](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Author-Publish {#author-publish}

Per configurare author-publish, consulta [Configurazione di Author e Publish in AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Se esiste un solo autore e una sola pubblicazione, è sufficiente seguire i passaggi descritti in **Setting up Replication Agents on Author** (Impostazione degli agenti di replica sull’autore) nella pagina [Configuring Author and Publish in AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html) (Configurazione di Author and Publish in AEM Screens).

## Configurazioni del dispatcher {#dispatcher-configurations}

Dispatcher è lo strumento di caching e/o bilanciamento del carico di Adobe Experience Manager. L’utilizzo di AEM Dispatcher consente inoltre di proteggere il server AEM da eventuali attacchi. Di conseguenza, per aumentare la sicurezza della tua istanza di AEM, puoi utilizzare Dispatcher insieme a un server web di classe Enterprise.

Fai riferimento a **[Configurazioni del dispatcher per AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** che evidenzia le linee guida per la configurazione del dispatcher per un progetto AEM Screens.

## Installazione di rappresentazioni FFMpeg e video {#installing-ffmpeg}

Installa FFMpeg seguendo i passaggi per il sistema operativo appropriato (solitamente RHEL):

1. Se si installa abilitando EPEL e RPMFusion, è possibile installare tutti i codec per ampliare il supporto per le conversioni FFmpeg
1. Se il codec AAC viene contrassegnato come sperimentale, le conversioni ffmpeg non avranno esito positivo. Per evitare questo aggiungere -rigorosamente -2 ai profili video (/etc/dam/video in AEM 6.3 e spostato in /libs/settings/dam/video in AEM 6.4)
   >[!NOTE]
   >
   > Tieni presente che -stricto -2 deve essere l’ultimo parametro nell’elenco dei parametri. Inoltre, nella AEM 6.4 è necessario copiare i nodi sotto */libs/settings/dam/video* in */conf/global/settings/dam/video* come indicato in [Rendering video](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Verifica che siano in corso conversioni video e che vengano create rappresentazioni.

## Restrizioni per le password {#password-restrictions}

Il criterio della password di AEM deve essere disabilitato nell’istanza AMS. Può essere configurato alternativamente nella console Web utilizzando il servizio dispositivo Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulta la sezione **Limitazioni password** in[Configurazione di authoring e pubblicazione in AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## Impostazione degli ambienti {#setting-up-environments}

Installa ed esegui le versioni più recenti dei seguenti pacchetti per la tua versione di Adobe Experience Manager (AEM):

* AEM Service Pack
* Feature Pack di Screens
* AEM Cumulative Fix Pack

Oltre a quanto sopra, identifica eventuali pacchetti di sviluppo (ad esempio, WCM Core)
componenti) o toolkit di terze parti (ad esempio, SAP Hybris) necessari.
Installa gli stessi pacchetti software negli ambienti di sviluppo locali. Chiedi al tuo client di adottare la stessa configurazione su tutti i loro server di controllo qualità, stage e produzione. Configurazioni server non corrispondenti causeranno problemi durante la distribuzione e il test.

>[!NOTE]
>
>Per installare l&#39;ultimo Feature Pack per AEM Screens, consulta [Note sulla versione](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Impostazione delle ACL {#setting-up-acls}

L&#39;impostazione delle ACL spiega come separare i progetti in modo che ogni singolo utente o team gestisca il proprio progetto.

Per ulteriori informazioni, consulta [Impostazione delle ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) .
