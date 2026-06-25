---
title: Rapporto assegnazione contenuti
description: Scopri come scaricare e utilizzare il rapporto Assegnazione contenuti relativo ad AEM Screens.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
TQID: https://experienceleague.adobe.com/Pwq3ebRrbCufXFMk7R-FJj90xq4b7gLOcLvslch2L5o
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 397
ht-degree: 2%

---

# Rapporto assegnazione contenuti {#content-assignment-report}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

La funzionalità Report assegnazione contenuto consente a un amministratore AEM Screens o a un autore di esportare un *Report assegnazione contenuto* in un formato foglio di calcolo.

## Utilizzo del rapporto di assegnazione dei contenuti {#using-content-assignment-report}

Il rapporto sull’assegnazione dei contenuti consente all’autore o all’amministratore di AEM Screens di scaricare un rapporto contenente tutte le risorse, come immagini e video, in tutti i canali creati in un progetto AEM Screens. Inoltre, include le informazioni sugli interi canali assegnati a tutti i display designati e, d&#39;ora in avanti, su tutti i dispositivi assegnati ai loro display designati.

Il rapporto sull’assegnazione dei contenuti non solo consente di visualizzare in anteprima tutti i canali, Assets, display e dispositivi nel progetto AEM Screens selezionato, ma fornisce anche una struttura di alto livello del progetto.


### Prerequisiti {#pre-reqs}

Prima di scaricare il report sull’assegnazione dei contenuti, accertati di aver impostato un progetto AEM Screens con canali, posizioni e dispositivi.
Per ulteriori informazioni, consulta le seguenti risorse:

1. [Creazione e gestione di progetti](/help/user-guide/creating-a-screens-project.md)
1. [Creazione e gestione dei canali](/help/user-guide/managing-channels.md)
1. [Creazione e gestione delle posizioni](/help/user-guide/managing-locations.md)
1. [Creazione e gestione delle visualizzazioni](/help/user-guide/managing-displays.md)
1. [Creazione di dispositivi](/help/user-guide/managing-devices.md)
1. [Assegnazione dei canali](/help/user-guide/channel-assignment-latest-fp.md)


## Download del report di assegnazione contenuti {#downloading-content-assignment-report-fp}

Dopo aver configurato il progetto AEM Screens e aver assegnato le visualizzazioni a ciascuna delle posizioni come illustrato nei passaggi precedenti, scarica il rapporto Assegnazione contenuto.

>[!NOTE]
>È possibile accedere alla funzione Report assegnazione contenuto solo a livello di progetto.

Segui le istruzioni riportate di seguito per scaricare il rapporto Assegnazione contenuti:

1. Passa al progetto AEM Screens e fai clic sul progetto **DemoScreens**.

1. Fare clic su **Report assegnazione contenuto** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/content-assignment-report/can-download.png)

1. Il foglio di calcolo scaricato è costituito da due schede, ad esempio **Percorsi** e **Contenuto**. Nella scheda Posizione vengono visualizzate quattro colonne, ad esempio **Percorsi**, **Visualizzazioni**, **Canali** e **Dispositivi**, che possono essere utilizzate per analizzare queste quattro entità relative al progetto AEM Screens.

   ![immagine](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >I dati visualizzati nel foglio di calcolo sono ordinati alfabeticamente in un formato di facile lettura.

1. Selezionando uno dei canali dalla colonna **Canali** si apre la scheda **Contenuto**. A sua volta, naviga direttamente in quel canale e ti fornisce informazioni sulle risorse (immagini e video) associate a quel canale specifico.

   ![immagine](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
