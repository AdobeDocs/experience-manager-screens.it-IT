---
title: Ambienti per [!UICONTROL AEM Screens]
seo-title: Environments for [!UICONTROL AEM Screens]
description: Questa pagina descrive gli ambienti per un progetto AEM Screens.
seo-description: This page highlights the environments for an AEM Screens project.
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---


# Ambienti {#environments}

Determinare in anticipo quali ambienti AEM il client dispone e si aspetta che utilizzi, sia per *sviluppo* e *distribuzione*.

>[!NOTE]
>
>Per il funzionamento dei progetti, AEM Screens richiede diversi pacchetti. Tutti gli ambienti devono eseguire la stessa versione di Adobe Experience Manager.

Segui le linee guida riportate di seguito per configurare l’ambiente per il tuo progetto AEM Screens:

1. Esegui le versioni più recenti dei seguenti pacchetti per la tua versione di Adobe Experience Manager:

   * **AEM Service Pack**
   * **Feature Pack di Screens**
   * **AEM Cumulative Fix Pack**

1. Identifica tutti i pacchetti di sviluppo (ad esempio, componenti core WCM) o i kit di strumenti di terze parti (ad esempio, SAP Hybris) necessari.

1. Installare gli stessi pacchetti software negli ambienti di sviluppo locali.

1. Istruisci il client ad adottare la stessa configurazione su tutti i server di controllo qualità, stage e produzione. Configurazioni server non corrispondenti causeranno problemi durante la distribuzione e il test.
