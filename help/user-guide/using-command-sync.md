---
title: Utilizzo di Command Sync
description: Scopri come utilizzare la sincronizzazione dei comandi in AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Sincronizzazione comandi {#command-sync}

Nella pagina seguente viene descritto come utilizzare Sincronizzazione comandi. Command Sync consente la riproduzione sincronizzata tra diversi lettori. I lettori possono riprodurre contenuti diversi, ma ogni risorsa deve avere la stessa durata.

>[!IMPORTANT]
>
>Questa funzione non supporta le sequenze incorporate, le sequenze incorporate dinamiche, i canali dell&#39;applicazione o le transizioni.

## Panoramica {#overview}

Le soluzioni di digital signage devono supportare pareti video e riproduzione sincronizzata per supportare scenari come i conteggi di Capodanno o video di grandi dimensioni suddivisi per la riproduzione su più schermi ed è qui che entra in gioco Command Sync.

Per utilizzare Command Sync, un lettore agisce come un *primario* e invia il comando e tutti gli altri lettori agiscono come *client* e viene riprodotto quando riceve il comando.

Il *primario* invia un comando a tutti i client registrati quando sta per avviare la riproduzione di un elemento. Il payload di questo può essere l’indice dell’elemento da riprodurre e/o l’html esterno dell’elemento da riprodurre.

## Implementazione sincronizzazione comandi {#using-command-sync}

La sezione seguente descrive come utilizzare la sincronizzazione dei comandi in un progetto AEM Screens.

>[!NOTE]
>
>Per la riproduzione sincronizzata, è necessario che tutti i dispositivi hardware abbiano le stesse specifiche hardware e preferibilmente lo stesso sistema operativo. La sincronizzazione tra hardware e sistemi operativi diversi non è consigliata.

### Configurazione del progetto {#setting-up}

Prima di utilizzare la funzione di sincronizzazione dei comandi, accertati di disporre di un progetto e di un canale con contenuti impostati per il progetto.

1. L’esempio seguente mostra un progetto demo denominato **CommandSyncDemo** e un canale di sequenza **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuto a un canale, consulta [Creazione e gestione dei canali](/help/user-guide/managing-channels.md)

   Il canale contiene il seguente contenuto, come illustrato nella figura riportata di seguito.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Creare una posizione **Lobby** e quindi una visualizzazione con titolo **LobbyDisplay** nel **Posizioni** come illustrato nella figura seguente.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Assegna il canale, **ChannelLobby** al tuo **LobbyDisplay**. Ora puoi visualizzare il canale assegnato alla visualizzazione dal dashboard di visualizzazione.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a una visualizzazione, consulta [Creazione e gestione delle visualizzazioni](/help/user-guide/managing-displays.md).

1. Accedi a **Dispositivi** cartella.
1. Clic **Gestione dispositivi** dalla barra delle azioni.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Per informazioni su come registrare un dispositivo, consulta [Registrazione dispositivo](/help/user-guide/device-registration.md)

1. A scopo dimostrativo, questo esempio mostra un dispositivo Chrome e un lettore Windows come due dispositivi separati. Entrambi i dispositivi puntano allo stesso schermo.
   ![image1](assets/command-sync6.png)

### Aggiornamento impostazioni canale

1. Accedi a **ChannelLobby**.
1. Clic **Modifica** dalla barra delle azioni.
1. Fate clic sull&#39;intero canale come illustrato nella figura riportata di seguito.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Fai clic sull’icona a forma di chiave inglese.
   ![image1](assets/command-sync/command-sync8-1.png)

1. In **Pagina** , immetti il *sincronizzato* parola chiave in **Strategia** campo.
   ![image1](assets/command-sync/command-sync9-1.png)


### Configurazione di un primario {#setting-up-primary}

1. Passa al dashboard di visualizzazione da **CommandSyncDemo** > **Posizioni**  > **Lobby** > **LobbyDisplay** e fai clic su **Dashboard** dalla barra delle azioni.
Osserva i due dispositivi (chrome e Windows Player) in **DISPOSITIVI** come illustrato di seguito:
   ![image1](assets/command-sync/command-sync10-1.png)

1. Dalla sezione **DISPOSITIVI** fare clic sul dispositivo che si desidera impostare come principale. L’esempio seguente illustra come impostare il dispositivo Chrome come principale. Clic **Imposta come dispositivo principale**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Inserisci l’indirizzo IP in **Imposta come dispositivo principale** e fai clic su **Salva**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>È possibile impostare più dispositivi come principali.

### Sincronizzazione con primario {#sync-up-primary}

1. Dopo aver impostato il dispositivo Chrome come primario, sincronizzare l&#39;altro dispositivo (in questo caso, Windows Player) per la sincronizzazione con il principale.
Fare clic sull&#39;altro dispositivo (in questo caso Windows Player) dal **DISPOSITIVI** e fai clic su **Sincronizza con dispositivo principale**.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Selezionare il dispositivo dall&#39;elenco e fare clic su **Salva**.

   >[NOTA:]
   > Il **Sincronizza con dispositivo principale** mostra l&#39;elenco dei dispositivi principali. Seleziona quella preferita.

1. Quando il dispositivo (Windows Player) viene sincronizzato con il principale (Chrome Player), è possibile vedere il dispositivo sincronizzato in **DISPOSITIVI** pannello.

   ![image1](assets/command-sync/command-sync14-1.png)

### Desincronizzazione con il primario {#desync-up-primary}

Dopo aver sincronizzato uno o più dispositivi in un dispositivo primario, è possibile desincronizzare l&#39;assegnazione da tale dispositivo.

>[!NOTE]
>
>Se si desincronizza un dispositivo principale, verranno scollegati anche tutti i dispositivi client associati a tale dispositivo principale.

Per rimuovere la sincronizzazione dal dispositivo principale, effettua le seguenti operazioni:

1. Accedi a **DISPOSITIVI** e fare clic sul dispositivo.

1. Clic **Desincronizza dispositivi** in modo da poter desincronizzare il client dal dispositivo principale.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Clic **Conferma** per desincronizzare il dispositivo selezionato dal dispositivo primario.

   >[NOTA:]
   > Se si fa clic sul dispositivo principale e si utilizza l&#39;opzione di desincronizzazione, tutti i dispositivi connessi al dispositivo principale vengono desincronizzati in un unico passaggio.
