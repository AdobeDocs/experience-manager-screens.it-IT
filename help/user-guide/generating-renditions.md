---
title: Rappresentazioni video
seo-title: Video Renditions
description: Segui questa pagina per scoprire come generare rappresentazioni Full HD per il tuo progetto Screens.
seo-description: Follow this page to learn about generating full HD renditions for your Screens project.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Rappresentazioni video {#video-renditions}

È possibile generare copie trasformate Full HD manuali e automatiche. La sezione seguente descrive il flusso di lavoro per aggiungere rappresentazioni alle risorse.

## Generazione automatica di rappresentazioni Full HD  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Se le rappresentazioni video di AEM Screens non vengono riprodotte in modo ottimale sul dispositivo, contatta il fornitore dell’hardware per le specifiche del video. Questo ti aiuterà a ottenere le migliori prestazioni sul dispositivo e quindi a creare un tuo profilo video personalizzato in cui fornisci i parametri appropriati affinché FFMPEG possa generare la tua rappresentazione. Successivamente, utilizza i passaggi seguenti per aggiungere il tuo profilo video personalizzato all’elenco dei profili.
>
>Inoltre, vedi [Video sulla risoluzione dei problemi](troubleshoot-videos.md) per eseguire il debug e risolvere i problemi relativi alla riproduzione di video nel canale.

Per generare automaticamente rappresentazioni Full HD, segui la procedura indicata di seguito:

1. Seleziona il collegamento Adobe Experience Manager (in alto a sinistra) e fai clic sull’icona a forma di martello per selezionare gli strumenti da selezionare **Flusso di lavoro**.

   Clic **Modelli** per accedere alla gestione dei modelli di workflow.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Seleziona la **Aggiorna risorsa DAM** e fare clic su Modifica nella barra delle azioni per aprire **Aggiorna risorsa DAM** finestra.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Fai doppio clic su **Transcodifica FFmpeg** passaggio.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Seleziona la **Processo** per modificare gli argomenti del processo. Inserire i profili Full HD nell&#39;elenco in **Argomenti** come: ***,profile:fullhd-bp,profile:fullhd-hp*** e fai clic su **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Clic **Salva** in alto a sinistra nella **Aggiorna risorsa DAM** schermo.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Accedi a **Risorse** e carica un nuovo video. Fai clic sul video e apri la barra laterale Rappresentazioni per visualizzare i due video Full HD.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Apri **Rappresentazioni** dalla barra laterale.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Vedrete due nuovi rendering Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generazione manuale di rappresentazioni Full HD {#manually-generating-full-hd-renditions}

Per generare manualmente le rappresentazioni Full HD, effettua le seguenti operazioni:

1. Seleziona il collegamento Adobe Experience Manager (in alto a sinistra) e fai clic sull’icona a forma di martello per selezionare gli strumenti da selezionare **Flusso di lavoro**.

   Clic **Modelli** per accedere alla gestione dei modelli di workflow.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Seleziona la **Risorsa per aggiornamento schermi** e fare clic sul pulsante **Avvia flusso di lavoro** per aprire **Esegui flusso di lavoro** .

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Seleziona il video desiderato nella **Payload** e fai clic su **Esegui**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Accedi a **Risorse**, espandi la risorsa e fai clic su di essa.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Apri **Rappresentazioni** nella barra laterale, noterete le nuove rappresentazioni Full HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
