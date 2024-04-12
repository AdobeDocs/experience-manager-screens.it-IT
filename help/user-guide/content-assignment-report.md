---
title: Rapporto assegnazione contenuti
description: Scopri come scaricare e utilizzare il rapporto Assegnazione contenuti relativo ad AEM Screens.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: ba5327077e4a2d30cc7b77f02123da5a240c67ae
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 2%

---

# Rapporto assegnazione contenuti {#content-assignment-report}

La funzione Content Assignment Report (Report assegnazione contenuti) consente a un amministratore di AEM Screens o a un autore di esportare un *Rapporto assegnazione contenuti* in un foglio di calcolo.

## Utilizzo del rapporto di assegnazione dei contenuti {#using-content-assignment-report}

Il rapporto sull’assegnazione dei contenuti consente all’autore o all’amministratore di AEM Screens di scaricare un rapporto contenente tutte le risorse, come immagini e video, in tutti i canali creati in un progetto AEM Screens. Inoltre, include le informazioni sugli interi canali assegnati a tutti i display designati e, d&#39;ora in avanti, su tutti i dispositivi assegnati ai loro display designati.

Il rapporto Assegnazione contenuto non solo consente di visualizzare in anteprima tutti i canali, le risorse, le visualizzazioni e i dispositivi nel progetto AEM Screens selezionato, ma fornisce anche una struttura di alto livello del progetto.


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

Dopo aver configurato il progetto AEM Screens e aver assegnato le visualizzazioni a ciascuna delle posizioni come mostrato nei passaggi precedenti, è possibile scaricare il rapporto Assegnazione contenuto.

>[!NOTE]
>È possibile accedere alla funzione Report assegnazione contenuto solo a livello di progetto.

Segui le istruzioni riportate di seguito per scaricare il rapporto Assegnazione contenuti:

1. Passa al progetto AEM Screens e seleziona il progetto **DemoScreens**.

1. Clic **Rapporto assegnazione contenuti** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/content-assignment-report/can-download.png)

1. Il foglio di calcolo scaricato è costituito da due schede, ad esempio **Posizioni** e **Contenuto**. Nella scheda Posizione vengono visualizzate quattro colonne, ad esempio **Posizioni**, **Display**, **Canali**, e **Dispositivi** che possono essere utilizzate per analizzare ulteriormente queste quattro entità relative al progetto AEM Screens.

   ![immagine](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >I dati visualizzati nel foglio di calcolo sono ordinati alfabeticamente in un formato di facile lettura.

1. Facendo clic su uno dei canali dalla **Canali** apre la colonna **Contenuto** scheda. A sua volta, naviga direttamente in quel canale e ti fornisce informazioni sulle risorse (immagini e video) associate a quel canale specifico.

   ![immagine](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
