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
TQID: https://experienceleague.adobe.com/4xxCtO5lD71kiS-dSbTjTgycZDiWkQlHPdJOCVDrv38
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 378
ht-degree: 0%

---

# Rappresentazioni video {#video-renditions}

È possibile generare copie trasformate Full HD manuali e automatiche. La sezione seguente descrive il flusso di lavoro per aggiungere rappresentazioni alle risorse.

## Generazione automatica di rappresentazioni Full HD {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Se le rappresentazioni video di AEM Screens non vengono riprodotte in modo ottimale sul dispositivo, contatta il fornitore dell’hardware per le specifiche del video. In questo modo è possibile ottenere le migliori prestazioni sul dispositivo. Consente di creare un profilo video personalizzato con i parametri appropriati affinché FFMPEG possa generare la rappresentazione. Quindi, utilizza i passaggi seguenti per aggiungere il tuo profilo video personalizzato all’elenco dei profili.
>
>Consulta anche [Risoluzione dei problemi relativi ai video](troubleshoot-videos.md) per eseguire il debug e risolvere i problemi relativi alla riproduzione di video nel tuo canale.

Per generare automaticamente le rappresentazioni Full HD, effettua le seguenti operazioni:

1. Fai clic sul collegamento Adobe Experience Manager (in alto a sinistra) e sull&#39;icona del martello in modo da poter fare clic su **Flusso di lavoro**.

   Fare clic su **Modelli**.

   ![schermata_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Nella gestione del modello del flusso di lavoro, fai clic sul modello **Risorsa di aggiornamento DAM** e fai clic su **Modifica** nella barra delle azioni.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Nella finestra **Risorsa di aggiornamento DAM**, fai doppio clic sul passaggio **Trascodifica FFmpeg**.

   ![schermata_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Fare clic sulla scheda **Processo**.
1. Immetti i profili Full HD nell&#39;elenco in **Argomenti** come segue:
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Fai clic su **OK**.

   ![schermata_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Fai clic su **Salva** in alto a sinistra nella schermata **Aggiorna risorsa DAM**.

   ![schermata_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Passa a **Assets** e carica un nuovo video. Fai clic sul video e apri la barra laterale Rappresentazioni. Osservate i due video Full HD.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Apri **Rappresentazioni** dalla barra laterale.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Notate due nuove rappresentazioni Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Generazione manuale di rappresentazioni Full HD {#manually-generating-full-hd-renditions}

Per generare manualmente le rappresentazioni Full HD, effettua le seguenti operazioni:

1. Fai clic sul collegamento Adobe Experience Manager (in alto a sinistra) e sull&#39;icona del martello in modo da poter fare clic su Strumenti e poi su **Flusso di lavoro**.

   Fare clic su **Modelli**.

   ![schermata_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Nella gestione del modello di flusso di lavoro, fai clic sul modello **Risorsa di aggiornamento Screens** e poi sul **Avvia flusso di lavoro** per aprire la finestra di dialogo **Esegui flusso di lavoro**.

   ![passaggio5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Fai clic sul video desiderato nel **Payload** e fai clic su **Esegui**.

   ![passaggio6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Passa a **Assets**, approfondisci la risorsa e fai clic su di essa.

   ![passaggio7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Apri la barra laterale **Rendering**. Osservate le nuove rappresentazioni Full HD.

   ![passaggio8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
