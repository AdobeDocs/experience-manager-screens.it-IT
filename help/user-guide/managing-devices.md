---
title: Gestione dei dispositivi
seo-title: Managing Devices
description: Questa pagina descrive l'assegnazione dei dispositivi.
seo-description: Follow this page to learn about device assignment. The Devices console allows you to access the device manager to assign your device to a display.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 4%

---

# Gestione dei dispositivi {#managing-devices}

Questa pagina descrive l&#39;assegnazione dei dispositivi.

La console Dispositivi consente di accedere al gestore di dispositivi per assegnare il dispositivo a uno schermo.

>[!CAUTION]
>
>Prima di assegnare il dispositivo, è necessario registrarlo. Per ulteriori informazioni, consulta [Registrazione dispositivo](device-registration.md).

## Assegnazione dispositivo {#device-assignment}

Per assegnare un dispositivo a uno schermo, attenersi alla procedura descritta di seguito.

1. Vai alla cartella Dispositivi del progetto, ad esempio

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Seleziona il **Dispositivi** cartella e tocca o fai clic su **Gestione dispositivi** nella barra delle azioni. Vengono visualizzati i dispositivi assegnati e non assegnati.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Seleziona un dispositivo non assegnato dall’elenco, quindi tocca o fai clic sul pulsante **Assegna dispositivo** nella barra delle azioni.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Seleziona dall’elenco la visualizzazione a cui assegnare il dispositivo, quindi tocca o fai clic sul pulsante **Assegna**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Tocca o fai clic sul pulsante **Fine** per completare il processo di assegnazione.


   Il dashboard di visualizzazione mostra il dispositivo assegnato nel **DISPOSITIVI** pannello.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Fai clic su (**...**) nell&#39;angolo in alto a destra del **DISPOSITIVI** per aggiungere la configurazione del dispositivo o aggiornare i dispositivi.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Ogni volta che il primo dispositivo viene aggiunto a un nuovo progetto Screens, viene creato un gruppo di utenti.
>Ad esempio, se il nome del nodo del progetto è *we-retail*, il nome del gruppo di utenti è *screens-we-retail-devices*.
>Questo gruppo verrà aggiunto come membro del **Collaboratori** come illustrato nella figura seguente:

![chlimage_1-39](assets/chlimage_1-39.png)

### Passaggi successivi {#the-next-steps}

Una volta acquisita familiarità con l’assegnazione di un canale a una visualizzazione, consulta le risorse seguenti:

* [Monitoraggio e risoluzione dei problemi](monitoring-screens.md)
