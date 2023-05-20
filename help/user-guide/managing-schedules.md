---
title: Creazione e gestione delle pianificazioni
seo-title: Managing Schedules
description: Segui questa pagina per scoprire le Pianificazioni, che ti consentono di organizzare i canali in gruppi riutilizzabili in modo da non dover ripetere la loro assegnazione individualmente per ogni visualizzazione in cui desideri mostrare il contenuto.
seo-description: Follow this page to learn about Schedules, that lets you organize channels into re-usable groups so that you do not have to repeat their assignment individually for each display on which you want to show your content.
uuid: c05328a0-620a-4597-b7b3-f4433e78d4e9
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 75ed3c42-4be9-42ae-9d76-e0343af81516
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Creazione e gestione delle pianificazioni {#creating-and-managing-schedules}

**Schedules**, in AEM Screens, consente di organizzare i canali in gruppi riutilizzabili in modo da non dover ripetere singolarmente l’assegnazione per ogni visualizzazione in cui desideri visualizzare il contenuto.

Schedules quando combinati con ***DayParting***, consente di impostare una pianificazione globale con più canali in esecuzione in orari specifici della giornata e di riutilizzare tale configurazione per tutti i display contemporaneamente.

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3 Sites Feature Pack 1. Per accedere a questo Feature Pack, contatta il supporto Adobe e richiedi l’accesso. Una volta ricevute le autorizzazioni, puoi scaricarle da Condivisione pacchetti.

## Creazione di una pianificazione {#creating-a-schedule}

Puoi creare una pianificazione per il progetto Screens che gestirà tutte le attività per il tuo caso d’uso.

Per creare una pianificazione per il tuo canale, segui la procedura riportata di seguito:

1. Seleziona il collegamento Adobe Experience Manager (in alto a sinistra), quindi Screens. In alternativa, puoi passare direttamente a: `http://localhost:4502/screens.html/content/screens`.
1. Passa al progetto Schermi e fai clic su **Schedules**.
1. Clic **Crea** dalla barra delle azioni.
1. Seleziona **Pianificazione** dal **Crea** e fai clic su **Successivo**.

1. Inserisci il **Nome** e **Titolo** e fai clic su **Crea**.

Nel progetto verrà visualizzata una cartella delle pianificazioni con il nome e il titolo designati.


## Visualizzazione del dashboard {#viewing-dashboard}

Dopo aver creato la cartella Schedules nel progetto, puoi visualizzarne i dettagli dal dashboard Schedules.

Per visualizzare il dashboard delle pianificazioni, segui la procedura riportata di seguito. L&#39;esempio seguente mostra il dashboard del progetto We.Retail:

1. Accedi a **Schedules** cartella del progetto Screens (ad esempio, We.Retail).

   ![chlimage_1](assets/chlimage_1.png)

1. Clic **Dashboard** dalla barra delle azioni per aprire il dashboard della pianificazione.

   Puoi visualizzare tre pannelli diversi, ad esempio **INFORMAZIONI SULLA PIANIFICAZIONE**, **CANALI ASSEGNATI**, e **VISUALIZZAZIONI ASSEGNATE**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Riquadro informazioni pianificazione** Fare clic su Proprietà nell&#39;angolo superiore destro del riquadro INFORMAZIONI PIANIFICAZIONE per visualizzare/modificare le proprietà della pianificazione.

   **Pannello Canali assegnati** Fate clic su +Assegna canale (Assign Channel) nell&#39;angolo superiore destro del pannello CANALI ASSEGNATI (ASSIGNED CHANNELS) per aprire la finestra di dialogo Assegnazione canale (Channel Assignment).

   **Pannello visualizzazioni assegnate** Selezionate una delle visualizzazioni dal pannello VISUALIZZAZIONI ASSEGNATE per aprire la dashboard di visualizzazione.
