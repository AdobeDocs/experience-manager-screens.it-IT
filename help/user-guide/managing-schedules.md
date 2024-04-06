---
title: Creazione e gestione delle pianificazioni
description: Scopri le pianificazioni che ti consentono di organizzare i canali in gruppi riutilizzabili in modo da non dover ripetere individualmente le assegnazioni per ogni visualizzazione in cui desideri visualizzare il contenuto.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Creazione e gestione delle pianificazioni {#creating-and-managing-schedules}

**Schedules** in AEM Screens puoi organizzare i canali in gruppi riutilizzabili in modo da non dover ripetere singolarmente l’assegnazione per ogni visualizzazione in cui desideri visualizzare il contenuto.

Schedules quando combinati con ***DayParting***, consente di impostare una pianificazione globale con più canali in esecuzione in orari specifici del giorno e di riutilizzare tale configurazione per tutti gli schermi contemporaneamente.

>[!NOTE]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3 Sites Feature Pack 1. Per accedere a questo Feature Pack, contatta il supporto Adobe e richiedi l’accesso. Dopo aver ottenuto le autorizzazioni necessarie, puoi scaricarlo da Condivisione pacchetti.

## Creazione di una pianificazione {#creating-a-schedule}

Puoi creare una pianificazione per il progetto Screens in grado di gestire tutte le attività relative al tuo caso d’uso.

Per creare una pianificazione per il tuo canale, segui la procedura riportata di seguito:

1. Seleziona il collegamento Adobe Experience Manager (in alto a sinistra) e quindi Screens. In alternativa, puoi passare direttamente a: `http://localhost:4502/screens.html/content/screens`.
1. Passa al progetto Schermi e fai clic su **Schedules**.
1. Clic **Crea** dalla barra delle azioni.
1. Seleziona **Pianificazione** dal **Crea** e fai clic su **Successivo**.

1. Inserisci il **Nome** e **Titolo** e fai clic su **Crea**.

Puoi visualizzare una cartella di pianificazione con il nome e il titolo indicati nel progetto.


## Visualizzazione del dashboard {#viewing-dashboard}

Dopo aver creato la cartella Schedules nel progetto, puoi visualizzarne i dettagli dal dashboard Schedules.

Per visualizzare il dashboard della pianificazione, segui la procedura riportata di seguito. L&#39;esempio seguente mostra il dashboard di `We.Retail` progetto:

1. Accedi a **Schedules** cartella di Screens (ad esempio, `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Seleziona **Dashboard** dalla barra delle azioni.

   Puoi visualizzare tre pannelli diversi, ad esempio **INFORMAZIONI SULLA PIANIFICAZIONE**, **CANALI ASSEGNATI**, e **VISUALIZZAZIONI ASSEGNATE**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Riquadro informazioni pianificazione** Fare clic su Proprietà nell&#39;angolo superiore destro del riquadro INFORMAZIONI PIANIFICAZIONE per visualizzare/modificare le proprietà della pianificazione.

   **Pannello Canali assegnati** Fate clic su +Assegna canale (Assign Channel) nell&#39;angolo superiore destro del pannello CANALI ASSEGNATI (ASSIGNED CHANNELS) per aprire la finestra di dialogo Assegnazione canale (Channel Assignment).

   **Pannello visualizzazioni assegnate** Selezionate una delle visualizzazioni dal pannello VISUALIZZAZIONI ASSEGNATE per aprire la dashboard di visualizzazione.
