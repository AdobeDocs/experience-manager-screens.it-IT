---
title: Gestione dei dispositivi
seo-title: Gestione dei dispositivi
description: Questa pagina descrive l’assegnazione del dispositivo.
seo-description: Questa pagina contiene informazioni sull’assegnazione dei dispositivi. La console Dispositivi consente di accedere alla gestione dei dispositivi da assegnare alle visualizzazioni.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
translation-type: tm+mt
source-git-commit: 6d86710a5d0a4fd1cf6c0dc46961d231b0128f95
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 72%

---


# Gestione dei dispositivi {#managing-devices}

Questa pagina descrive l’assegnazione del dispositivo.

La console Dispositivi consente di accedere alla gestione dei dispositivi da assegnare alle visualizzazioni.

>[!CAUTION]
>
>Prima di assegnare il dispositivo, è necessario registrarlo. Per ulteriori informazioni, vedi [Registrazione dei dispositivi](device-registration.md).

## Assegnazione dei dispositivi {#device-assignment}

Segui i passaggi descritti di seguito per assegnare un dispositivo a una visualizzazione:

1. Individua la cartella dei dispositivi del progetto, ad esempio

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Select your **Devices** folder and tap/click **Device Manager** in the action bar. Vengono mostrati i dispositivi assegnati e non assegnati.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Select an unassigned device from the list, and tap/click the **Assign Device** in the action bar.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Select the display you want to assign the device to from the list, and tap/click the **Assign**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Tap/click the **Finish** to complete the assignment process.


   Il dashboard di visualizzazione mostra il dispositivo assegnato nel pannello **DISPOSITIVI**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Fai clic su **...** nell’angolo in alto a destra del pannello **DISPOSITIVI** per aggiungere la configurazione del dispositivo o per aggiornare i dispositivi.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Ogni volta che il primo dispositivo viene aggiunto a un nuovo progetto Screens, viene creato un gruppo utente.
>For instance, if the project node name is *we-retail*, then the user group name is *screens-we-retail-devices*.
>Questo gruppo viene aggiunto come membro del gruppo **Collaboratori**, come illustrato di seguito:

![chlimage_1-39](assets/chlimage_1-39.png)

### Passaggi successivi {#the-next-steps}

Dopo aver acquisito familiarità con l’assegnazione del canale a una visualizzazione, vedi le risorse seguenti:

* [Monitoraggio e risoluzione dei problemi](monitoring-screens.md)

