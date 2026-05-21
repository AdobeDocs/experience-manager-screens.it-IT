---
title: Creare e gestire gli Schedules
description: Scopri le pianificazioni che ti consentono di organizzare i canali in gruppi riutilizzabili in modo da non dover ripetere singolarmente la loro assegnazione.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
TQID: https://experienceleague.adobe.com/FJomd-Wz-r8vJZK7PH6wgL4LY3zRmOucBhIbTdjUmQ4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: ba4275ba-c29a-4197-90dc-5a633402ca3cid: cf6d61d1-acb6-4411-ad1b-25fb57e94db6id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 370
ht-degree: 0%

---

# Creare e gestire le pianificazioni {#creating-and-managing-schedules}

Le **Schedules** in AEM Screens consentono di organizzare i canali in gruppi riutilizzabili. In questo modo, non è necessario ripetere le singole assegnazioni per ogni visualizzazione in cui si desidera visualizzare il contenuto.

Le pianificazioni, se combinate con ***DayParting***, ti consentono di impostare una pianificazione globale con più canali in esecuzione in orari specifici del giorno e di riutilizzare tale configurazione per tutte le visualizzazioni contemporaneamente.

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3 Sites Feature Pack 1. Per accedere a questo Feature Pack, contatta il supporto Adobe e richiedi l’accesso. Dopo aver ottenuto le autorizzazioni necessarie, puoi scaricarlo da Condivisione pacchetti.

## Creare una pianificazione {#creating-a-schedule}

Puoi creare una pianificazione per il progetto Screens in grado di gestire tutte le attività per il tuo caso d’uso.

Per creare una pianificazione per il tuo canale, segui la procedura riportata di seguito:

1. Fai clic sul collegamento Adobe Experience Manager (in alto a sinistra) e quindi su Screens. In alternativa, è possibile passare direttamente a: `http://localhost:4502/screens.html/content/screens`.
1. Passa al progetto Screens e fai clic su **Pianificazioni**.
1. Fai clic su **Crea** nella barra delle azioni.
1. Fai clic su **Pianifica** nella procedura guidata **Crea** e fai clic su **Avanti**.

1. Immetti **Nome** e **Titolo** e fai clic su **Crea**.

Puoi visualizzare una cartella di pianificazione con il nome e il titolo indicati nel progetto.


## Visualizza dashboard {#viewing-dashboard}

Dopo aver creato una cartella delle pianificazioni nel progetto, è possibile visualizzarne i dettagli dal dashboard delle pianificazioni.

Per visualizzare il dashboard della pianificazione, segui la procedura riportata di seguito. Nell&#39;esempio seguente viene illustrato il dashboard del progetto `We.Retail`:

1. Passa alla cartella **Schedules** del progetto Screens (ad esempio, `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Fai clic su **Dashboard** nella barra delle azioni.

   Puoi visualizzare tre pannelli diversi, ad esempio **INFORMAZIONI SULLA PIANIFICAZIONE**, **CANALI ASSEGNATI** e **VISUALIZZAZIONI ASSEGNATE**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Riquadro informazioni pianificazione** - Fare clic su Proprietà nell&#39;angolo superiore destro del riquadro INFORMAZIONI PIANIFICAZIONE per visualizzare/modificare le proprietà della pianificazione.

   **Pannello canali assegnati** - Fare clic su +Assegna canale dall&#39;angolo superiore destro del pannello CANALI ASSEGNATI per aprire la finestra di dialogo Assegnazione canale.

   **Pannello visualizzazioni assegnate** - Fare clic su una delle visualizzazioni nel pannello VISUALIZZAZIONI ASSEGNATE per aprire il dashboard di visualizzazione.
