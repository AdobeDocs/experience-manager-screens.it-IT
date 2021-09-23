---
title: Rapporto assegnazione contenuti
description: Questa pagina descrive il download e l’utilizzo del rapporto sull’assegnazione dei contenuti.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 9e750b874253a5d1786e5ef78fc41d96e72b702d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 6%

---

# Rapporto assegnazione contenuti {#content-assignment-report}

La funzione Rapporto assegnazione contenuto consente a un amministratore AEM Screens o a un autore di esportare un *Rapporto assegnazione contenuto* in un formato foglio di calcolo.

## Utilizzo del rapporto Assegnazione contenuto {#using-content-assignment-report}

Il rapporto Assegnazione contenuto consente all’autore o all’amministratore di AEM Screens di scaricare il rapporto contenente tutte le risorse, ad esempio immagini e video, in tutti i canali creati in un progetto AEM Screens. Inoltre, include le informazioni dell&#39;intero canale assegnato a tutti i display designati e quindi a tutti i dispositivi assegnati ai relativi display designati.

Il rapporto Assegnazione contenuto non solo consente di visualizzare un’anteprima di tutti i canali, le risorse, i display e i dispositivi nel progetto AEM Screens selezionato, ma fornisce anche una struttura di alto livello del progetto.


### Prerequisiti {#pre-reqs}

Prima di scaricare il Rapporto sull’assegnazione del contenuto, accertati di aver impostato un progetto AEM Screens con canali, posizioni e dispositivi.
Per ulteriori informazioni, consulta le seguenti risorse:

1. [Creazione e gestione di progetti](/help/user-guide/creating-a-screens-project.md)
1. [Creazione e gestione dei canali](/help/user-guide/managing-channels.md)
1. [Creazione e gestione delle posizioni](/help/user-guide/managing-locations.md)
1. [Creazione e gestione delle visualizzazioni](/help/user-guide/managing-displays.md)
1. [Creazione di dispositivi](/help/user-guide/managing-devices.md)
1. [Assegnazione dei canali ](/help/user-guide/channel-assignment-latest-fp.md)


## Download del rapporto sull’assegnazione del contenuto {#downloading-content-assignment-report-fp}

Dopo aver configurato il progetto AEM Screens e aver assegnato le visualizzazioni a ciascuna delle posizioni come mostrato nei passaggi precedenti, puoi scaricare il rapporto Assegnazione contenuto .

>[!NOTE]
>È possibile accedere alla funzione Rapporto assegnazione contenuto solo a livello di progetto.

Segui le istruzioni riportate di seguito per scaricare il rapporto sull’assegnazione del contenuto:

1. Passa al progetto AEM Screens e seleziona il progetto **DemoScreens**.

1. Fai clic su **Rapporto assegnazione contenuto** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/content-assignment-report/can-download.png)

1. Il foglio di calcolo scaricato è costituito da due schede quali **Posizioni** e **Contenuto**. La scheda Posizione visualizza quattro colonne quali **Posizioni**, **Visualizzazioni**, **Canali** e **Dispositivi** che possono essere utilizzate per approfondire l&#39;analisi di queste quattro entità relative al progetto AEM Screens.

   ![immagine](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >I dati visualizzati nel foglio di calcolo sono ordinati alfabeticamente in un formato di facile lettura.

1. Puoi fare clic su uno dei canali dalla colonna **Canali** per aprire la scheda **Contenuto** che ti permetterà di accedere direttamente a quel canale e ti fornirà anche informazioni sulle risorse (immagini e video) associate a quel canale specifico, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
