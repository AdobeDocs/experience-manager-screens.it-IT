---
title: Rappresentazioni video
seo-title: Rappresentazioni video
description: Segui questa pagina per scoprire ulteriori informazioni sulla generazione di rappresentazioni in Full HD per i tuoi progetti Screens.
seo-description: Segui questa pagina per scoprire ulteriori informazioni sulla generazione di rappresentazioni in Full HD per i tuoi progetti Screens.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 64%

---


# Rappresentazioni video {#video-renditions}

Puoi generare elementi video in Full HD manuali e automatici. La sezione seguente descrive il flusso di lavoro che consente di aggiungere elementi video alle tue risorse.

## Generazione automatica di rappresentazioni in Full HD  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Nel caso in cui i rendering video di AEM Screens non vengano riprodotti in modo ottimale sul tuo dispositivo, contatta il fornitore dell&#39;hardware per avere le specifiche del video. Questo ti consentirà di ottenere le migliori prestazioni sul dispositivo, e creare il tuo profilo video personalizzato in cui immettere i parametri che consentano a FFMPEG di creare rappresentazioni. Poi segui i passaggi descritti di seguito per aggiungere il tuo profilo video personalizzato all&#39;elenco dei profili.
>
>Inoltre, consulta [Risoluzione problemi video](troubleshoot-videos.md) per il debug e la risoluzione dei problemi nella riproduzione video sul canale.

Segui i passaggi riportati di seguito per generare automaticamente rappresentazioni in Full HD:

1. Seleziona il collegamento ad Adobe Experience Manager (in alto a sinistra) e fai clic sull&#39;icona a martello per accedere agli strumenti e poi a **Flusso di lavoro**.

   Fare clic su **Modelli** per accedere alla gestione dei modelli di workflow.

   ![screen_shot_2018-02-01 alle123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Selezionate il modello **DAM Update Asset** e fate clic su Modifica nella barra delle azioni per aprire la finestra **DAM Update Asset**.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Fai doppio clic su **Transcodifica FFmpeg**.

   ![screen_shot_2018-02-01 alle124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Seleziona la scheda **Processo** per modificare gli argomenti del processo. Immettere i profili HD completi nell&#39;elenco in **Argomenti** come: ***,profile:fullhd-bp,profile:fullhd-hp*** e fare clic su **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Fai clic su **Salva** in alto a sinistra della schermata **Aggiorna risorse DAM**.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Accedi a **Risorse** e carica un nuovo video. Fate clic sul video e aprite la barra laterale Rappresentazioni per visualizzare i due video HD completi.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Aprire **Rendering** dalla barra laterale.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Noterai due nuove rappresentazioni in Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generazione manuale di rappresentazioni in Full HD {#manually-generating-full-hd-renditions}

Segui i passaggi riportati di seguito per generare manualmente le rappresentazioni in Full HD:

1. Seleziona il collegamento ad Adobe Experience Manager (in alto a sinistra) e fai clic sull&#39;icona a martello per accedere agli strumenti e poi a **Flusso di lavoro**.

   Fare clic su **Modelli** per accedere alla gestione dei modelli di workflow.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Selezionare il modello **Screens Update Asset** e fare clic sul **Avvia flusso di lavoro** per aprire la finestra di dialogo **Esegui flusso di lavoro**.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Selezionare il video desiderato nel **Payload** e fare clic su **Run**.

   ![step6_-_select_theDESredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Accedi a **Risorse**, trova e fai click sulla tua risorsa.

   ![step7_-_open_theideoasset](assets/step7_-_open_thevideoasset.png)

1. Apri la barra laterale **Rappresentazioni** e potrai vedere le nuove rappresentazioni in Full HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

