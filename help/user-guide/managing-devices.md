---
title: Gestione dei dispositivi
description: Scopri le funzioni di assegnazione e gestione dei dispositivi in AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 7%

---

# Gestione dei dispositivi {#managing-devices}

Questa pagina descrive l&#39;assegnazione del dispositivo.

La console Dispositivi consente di accedere al gestore di dispositivi per assegnare il dispositivo a uno schermo.

>[!CAUTION]
>
>Prima di assegnare il dispositivo, registrarlo. Consulta [Registrazione dispositivo](device-registration.md).

## Assegnazione dispositivo {#device-assignment}

Per assegnare un dispositivo a uno schermo, attenersi alla procedura descritta di seguito.

1. Vai alla cartella Dispositivi del progetto, ad esempio

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Fai clic sulla cartella **Dispositivi** e fai clic su **Gestione dispositivi** nella barra delle azioni. Vengono visualizzati i dispositivi assegnati e non assegnati.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Fare clic su un dispositivo non assegnato nell&#39;elenco e quindi fare clic su **Assegna dispositivo** nella barra delle azioni.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Fare clic sulla visualizzazione a cui si desidera assegnare il dispositivo dall&#39;elenco e quindi fare clic su **Assegna**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Fai clic su **Fine** per completare il processo di assegnazione.


   Il dashboard di visualizzazione visualizza il dispositivo assegnato nel pannello **DISPOSITIVI**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Fare clic su (**...**) nell&#39;angolo superiore destro del pannello **DISPOSITIVI** per aggiungere la configurazione del dispositivo o aggiornare i dispositivi.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Ogni volta che il primo dispositivo viene aggiunto a un nuovo progetto Screens, viene creato un gruppo di utenti.
>Ad esempio, se il nome del nodo del progetto è *we-retail*, il nome del gruppo di utenti è *screens-we-retail-devices*.
>Questo gruppo viene aggiunto come membro del gruppo **Collaboratori**, come illustrato nella figura seguente:

![chlimage_1-39](assets/chlimage_1-39.png)

### Passaggi successivi {#the-next-steps}

Dopo aver acquisito familiarità con l&#39;assegnazione di un canale a una visualizzazione, vedere t[Monitorare e risolvere i problemi](monitoring-screens.md).
