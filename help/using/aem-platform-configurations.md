---
title: Configurazioni della piattaforma AEM
description: La pagina descrive le configurazioni della piattaforma AEM
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 3%

---

# Configurazioni della piattaforma AEM {#platform-configurations}

>[!NOTE]
>
>Un soggetto interessato tipico per questa attività è un implementatore AEM.

Inizia a usare AEM Screens seguendo le sezioni seguenti per configurare le configurazioni della piattaforma AEM

## Configurazioni server {#server-configurations}

Per configurare le configurazioni del server, vedere [Configurazioni del server](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Author-Publish {#author-publish}

Vedi [Configurazione di Author e Publish in AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>Se esiste un solo Autore e un solo Publish, è possibile seguire solo i passaggi descritti in **Impostazione degli agenti di replica sull&#39;Autore** nella pagina [Configurazione di Author e Publish in AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

## Configurazioni di Dispatcher {#dispatcher-configurations}

Dispatcher è lo strumento di caching e bilanciamento del carico di Adobe Experience Manager. L’utilizzo di AEM Dispatcher consente inoltre di proteggere il server AEM da eventuali attacchi. Pertanto, puoi aumentare la sicurezza dell’istanza AEM utilizzando Dispatcher con un server web di classe enterprise.

Consulta **[Configurazioni Dispatcher per AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** che evidenzia le linee guida per la configurazione di Dispatcher per un progetto AEM Screens.

## Installazione di rappresentazioni FFMpeg e video {#installing-ffmpeg}

Installare FFMpeg seguendo la procedura per il sistema operativo appropriato (in genere RHEL):

1. Se si installa attivando EPEL e RPMFusion, è possibile installare tutti i codec gstreamer per ampliare il supporto per le conversioni FFmpeg
1. Se il codec AAC è contrassegnato come sperimentale, le conversioni ffmpeg non riescono. Per evitare questo, aggiungi `-strict -2` ai profili video (/etc/dam/video in AEM 6.3 e spostati in /libs/settings/dam/video in AEM 6.4)

   >[!NOTE]
   >
   >`-strict -2` deve essere l&#39;ultimo parametro nell&#39;elenco dei parametri. Inoltre, in AEM 6.4, copiare i nodi in */libs/settings/dam/video* in */conf/global/settings/dam/video* come indicato in [Rappresentazioni video](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Verifica che le conversioni video siano in corso e che vengano create le rappresentazioni.

## Limitazioni password {#password-restrictions}

I criteri password dell&#39;AEM devono essere disabilitati nell&#39;istanza AMS. Può anche essere configurato in alternativa nella console Web utilizzando il servizio dispositivo di Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulta la sezione **Password Restrictions** in[Configuring Author and Publish in AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Configurazione degli ambienti {#setting-up-environments}

Installa ed esegui le versioni più recenti dei seguenti pacchetti per la tua versione di Adobe Experience Manager (AEM):

* Service Pack AEM
* Feature Pack di Screens
* AEM Cumulative Fix Pack

Oltre a quanto sopra, identifica eventuali pacchetti di sviluppo (ad esempio, WCM Core
componenti) o toolkit di terze parti (ad esempio SAP Hybris) necessari.
Installare gli stessi pacchetti software nell&#39;ambiente di sviluppo locale. Istruisci il client ad adottare la stessa configurazione su tutti i server di controllo qualità, stage e produzione. Configurazioni server non corrispondenti causano problemi durante la distribuzione e il test.

>[!NOTE]
>
>Per installare il Feature Pack più recente per AEM Screens, consulta [Note sulla versione](https://experienceleague.adobe.com/it/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Impostazione di ACL {#setting-up-acls}

La sezione Configurazione di ACL spiega come separare i progetti in modo che ogni singolo utente o team gestisca il proprio progetto.

Per ulteriori dettagli, vedere [Configurazione di ACL](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls).
