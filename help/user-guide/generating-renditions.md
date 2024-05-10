---
title: Rappresentazioni video
description: Scopri come generare rappresentazioni Full HD per il tuo progetto AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Rappresentazioni video {#video-renditions}

È possibile generare copie trasformate Full HD manuali e automatiche. La sezione seguente descrive il flusso di lavoro per aggiungere rappresentazioni alle risorse.

## Generazione automatica di rappresentazioni Full HD {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Se le rappresentazioni video di AEM Screens non vengono riprodotte in modo ottimale sul dispositivo, contatta il fornitore dell’hardware per le specifiche del video. In questo modo è possibile ottenere le migliori prestazioni sul dispositivo. Consente di creare un profilo video personalizzato con i parametri appropriati affinché FFMPEG possa generare la rappresentazione. Quindi, utilizza i passaggi seguenti per aggiungere il tuo profilo video personalizzato all’elenco dei profili.
>
>Vedi anche [Video sulla risoluzione dei problemi](troubleshoot-videos.md) per eseguire il debug e risolvere i problemi relativi alla riproduzione di video nel canale.

Per generare automaticamente le rappresentazioni Full HD, effettua le seguenti operazioni:

1. Fai clic sul collegamento Adobe Experience Manager (in alto a sinistra) e fai clic sull’icona del martello in modo da poter fare clic su **Flusso di lavoro**.

   Clic **Modelli**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Nella gestione del modello di flusso di lavoro, fai clic su **Aggiorna risorsa DAM** e fai clic su **Modifica** dalla barra delle azioni.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. In **Aggiorna risorsa DAM** fare doppio clic sulla **Transcodifica FFmpeg** passaggio.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Fai clic su **Processo** scheda.
1. Inserire i profili Full HD nell&#39;elenco in **Argomenti** come segue:
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Fai clic su **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Clic **Salva** in alto a sinistra nella **Aggiorna risorsa DAM** schermo.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Accedi a **Risorse** e carica un nuovo video. Fai clic sul video e apri la barra laterale Rappresentazioni. Osservate i due video Full HD.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Apri **Rappresentazioni** dalla barra laterale.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Notate due nuove rappresentazioni Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generazione manuale di rappresentazioni Full HD {#manually-generating-full-hd-renditions}

Per generare manualmente le rappresentazioni Full HD, effettua le seguenti operazioni:

1. Fai clic sul collegamento Adobe Experience Manager (in alto a sinistra) e fai clic sull’icona del martello in modo da poter fare clic su Strumenti e poi su **Flusso di lavoro**.

   Clic **Modelli**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Nella gestione dei modelli di flusso di lavoro, fai clic su **Risorsa per aggiornamento schermi** e fare clic sul pulsante **Avvia flusso di lavoro** per aprire **Esegui flusso di lavoro** .

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Fai clic sul video desiderato nella sezione **Payload** e fai clic su **Esegui**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Accedi a **Risorse**, espandi la risorsa e fai clic su di essa.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Apri **Rappresentazioni** barra laterale. Osservate le nuove rappresentazioni Full HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
