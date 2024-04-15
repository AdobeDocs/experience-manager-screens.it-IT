---
title: Ambienti per [!UICONTROL AEM Screens]
description: Ulteriori informazioni sugli ambienti per un progetto AEM Screens.
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Ambienti {#environments}

Determinare in anticipo quali ambienti AEM il client dispone e si aspetta che utilizzi, sia per *sviluppo* e *distribuzione*.

>[!NOTE]
>
>AEM Screens richiede diversi pacchetti per il funzionamento dei progetti. Tutti gli ambienti devono eseguire la stessa versione di Adobe Experience Manager.

Segui le linee guida riportate di seguito per configurare l’ambiente per il tuo progetto AEM Screens:

1. Esegui le versioni più recenti dei seguenti pacchetti per la tua versione di Adobe Experience Manager:

   * **Service Pack AEM**
   * **Feature Pack di Screens**
   * **AEM Cumulative Fix Pack**

1. Identifica tutti i pacchetti di sviluppo (ad esempio, componenti core WCM) o i kit di strumenti di terze parti (ad esempio, SAP Hybris) necessari.

1. Installare gli stessi pacchetti software nell&#39;ambiente di sviluppo locale.

1. Istruisci il client ad adottare la stessa configurazione su tutti i server di controllo qualità, stage e produzione. Configurazioni server non corrispondenti causano problemi durante la distribuzione e il test.
