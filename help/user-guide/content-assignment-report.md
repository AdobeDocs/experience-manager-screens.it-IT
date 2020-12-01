---
title: Rapporto assegnazione contenuti
description: Questa pagina descrive il download e l'utilizzo del rapporto Assegnazione contenuto.
translation-type: tm+mt
source-git-commit: b93baeeb26e48b906ee1ddfc034112f8b73615af
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 2%

---


# Rapporto assegnazione contenuti {#content-assignment-report}

La funzione Rapporto assegnazione contenuto consente a un amministratore  AEM Screens o a un autore di esportare un report *Assegnazione contenuto* in un formato foglio di calcolo.

## Utilizzo del report Assegnazione contenuto {#using-content-assignment-report}

Il rapporto Assegnazione contenuto consente a un autore  AEM Screens o a un amministratore di scaricare il rapporto che contiene tutte le risorse come immagini e video in tutti i canali creati in un progetto  AEM Screens. Include inoltre le informazioni degli interi canali assegnati a tutti i display designati e, di conseguenza, a tutti i dispositivi assegnati ai rispettivi display designati.

Il rapporto Assegnazione contenuto non solo consente di visualizzare un&#39;anteprima di tutti i canali, le risorse, i display e i dispositivi nel progetto AEM Screens  selezionato, ma fornisce anche una struttura di alto livello del progetto.

### Utilizzo del report Assegnazione contenuto {#downloading-content-assignment-report-fp}

#### Impostazione del progetto {#setting-up-project}

Per scaricare il rapporto Assegnazione contenuto da un progetto AEM Screens , effettuate le seguenti operazioni:

1. Create un AEM Screens  denominato **DemoScreens**.

   ![immagine](/help/user-guide/assets/content-assignment-report/car-1.png)

1. Create due canali di sequenza in **DemoScreens** come **ChannelOne** e **ChannelTwo**.

   ![immagine](/help/user-guide/assets/content-assignment-report/car-2.png)

1. Selezionare **ChannelOne** e fare clic su **Edit** dalla barra delle azioni. Aggiungete alcune risorse (immagini/video) a questo canale. Allo stesso modo, aggiungete le risorse a **ChannelTwo**.

1. Andate alla cartella Locations da **DemoScreens** —> **Locations** e create tre diverse posizioni denominate come **SanJose**, **Dublino** e **SanFrancisco**.

   ![immagine](/help/user-guide/assets/content-assignment-report/car-3.png)

1. Andate a ciascuna posizione e create una visualizzazione per ciascuna posizione, ad esempio **SanJoseMain** in **SanJose**, **DublinMain** nella posizione **Dublin** e **SanFranciscoMain** in **Dublin Posizione di SanFrancisco**.

1. Assegnare un dispositivo a ciascun display.

   >[!NOTE]
   >Per informazioni sull&#39;assegnazione di un canale a uno schermo, fare riferimento a [Assegnazione canale](/help/user-guide/channel-assignment.md).

#### Download del report Assegnazione contenuto {#downloading-content-assignment-report}

Una volta configurato il progetto AEM Screens  e assegnato gli schermi a ciascuna delle posizioni come mostrato nei passaggi precedenti, potete scaricare il rapporto Assegnazione contenuto.

>[!NOTE]
>La funzione Rapporto assegnazione contenuto è accessibile solo a livello di progetto.

Seguite le istruzioni riportate di seguito per scaricare il rapporto Assegnazione contenuto:

1. Andate al progetto AEM Screens  e selezionate il progetto **DemoScreens**.

1. Fare clic su **Rapporto assegnazione contenuto** dalla barra delle azioni. È necessario scaricare un foglio Excel nel computer locale.

   ![immagine](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >Il foglio di calcolo scaricato è costituito da quattro colonne, ad esempio **Canali**, **Risorse**, **Display** e **Dispositivi**, che possono essere utilizzate per approfondire l&#39;analisi di queste quattro entità relative al progetto AEM Screens .





