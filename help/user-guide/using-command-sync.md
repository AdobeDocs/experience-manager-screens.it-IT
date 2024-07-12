---
title: Utilizzo di Command Sync
description: Scopri come utilizzare la sincronizzazione dei comandi in AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# Sincronizzazione comandi {#command-sync}

Nella pagina seguente viene descritto come utilizzare Sincronizzazione comandi. Command Sync consente la riproduzione sincronizzata tra diversi lettori. I lettori possono riprodurre contenuti diversi, ma ogni risorsa deve avere la stessa durata.

>[!IMPORTANT]
>
>Questa funzione non supporta le sequenze incorporate, le sequenze incorporate dinamiche, i canali dell&#39;applicazione o le transizioni.

## Panoramica {#overview}

Le soluzioni di digital signage devono supportare pareti video e riproduzione sincronizzata. Questo scenario è valido se stai tentando di supportare scenari come il conto alla rovescia di Capodanno o un video di grandi dimensioni suddiviso in più sezioni da riprodurre su più schermi. In tali scenari entra in gioco la sincronizzazione dei comandi.

Per utilizzare la sincronizzazione dei comandi, un lettore agisce come *primario* e invia il comando e tutti gli altri lettori agiscono come *client* e vengono riprodotti quando ricevono il comando.

*primary* invia un comando a tutti i client registrati quando sta per avviare la riproduzione di un elemento. Il payload di questa azione può essere l’indice dell’elemento da riprodurre, l’html esterno dell’elemento da riprodurre o entrambi.

## Implementazione sincronizzazione comandi {#using-command-sync}

La sezione seguente descrive come utilizzare la sincronizzazione dei comandi in un progetto AEM Screens.

>[!NOTE]
>
>Per la riproduzione sincronizzata, è necessario che tutti i dispositivi hardware abbiano le stesse specifiche hardware e preferibilmente lo stesso sistema operativo. La sincronizzazione tra hardware e sistemi operativi diversi non è consigliata.

### Configurazione del progetto {#setting-up}

Prima di utilizzare la funzione di sincronizzazione dei comandi, accertati di disporre di un progetto e di un canale con contenuti impostati per il progetto.

1. Nell&#39;esempio seguente viene illustrato un progetto demo denominato **CommandSyncDemo** e un canale di sequenza **ChannelLobby**.

   ![immagine1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Per informazioni su come creare un canale o aggiungere contenuto a un canale, vedere [Creazione e gestione di canali](/help/user-guide/managing-channels.md)

   Il canale contiene il seguente contenuto, come illustrato nella figura riportata di seguito.

   ![immagine1](assets/command-sync/command-sync2-1.png)

1. Creare una posizione **Lobby** e quindi una visualizzazione con titolo **LobbyDisplay** nella cartella **Locations**, come illustrato nella figura seguente.
   ![immagine1](assets/command-sync/command-sync3-1.png)

1. Assegna il canale **ChannelLobby** al tuo **LobbyDisplay**. Ora puoi visualizzare il canale assegnato alla visualizzazione dal dashboard di visualizzazione.
   ![immagine1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Per informazioni su come assegnare un canale a una visualizzazione, vedere [Creazione e gestione di visualizzazioni](/help/user-guide/managing-displays.md).

1. Passare alla cartella **Dispositivi**.
1. Fare clic su **Gestione periferiche** nella barra delle azioni.

   ![immagine1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Per informazioni su come registrare un dispositivo, vedere [Registrazione dispositivo](/help/user-guide/device-registration.md)

1. A scopo dimostrativo, in questo esempio vengono illustrati un dispositivo Chrome e un lettore Windows come due dispositivi separati. Entrambi i dispositivi puntano allo stesso schermo.
   ![immagine1](assets/command-sync6.png)

### Aggiornamento impostazioni canale

1. Passa a **ChannelLobby**.
1. Fai clic su **Modifica** nella barra delle azioni.
1. Fate clic sull&#39;intero canale come illustrato nella figura riportata di seguito.
   ![immagine1](assets/command-sync/command-sync7-1.png)

1. Fai clic sull’icona a forma di chiave inglese.
   ![immagine1](assets/command-sync/command-sync8-1.png)

1. Nella finestra di dialogo **Pagina** immettere la parola chiave *sincronizzata* nel campo **Strategia**.
   ![immagine1](assets/command-sync/command-sync9-1.png)


### Configurazione di un primario {#setting-up-primary}

1. Passa alla dashboard di visualizzazione da **CommandSyncDemo** > **Percorsi** > **Lobby** > **LobbyDisplay**. Quindi fai clic su **Dashboard** nella barra delle azioni.
Osserva i due dispositivi (Chrome e Windows Player) nel pannello **DISPOSITIVI**, come illustrato di seguito:
   ![immagine1](assets/command-sync/command-sync10-1.png)

1. Nel pannello **DISPOSITIVI**, fare clic sul dispositivo che si desidera impostare come primario. Nell&#39;esempio seguente viene illustrata la configurazione del dispositivo Chrome come dispositivo principale. Fare clic su **Imposta come dispositivo principale**.

   ![immagine1](assets/command-sync/command-sync11-1.png)

1. Immettere l&#39;indirizzo IP in **Imposta come dispositivo principale** e fare clic su **Salva**.

   ![immagine1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>È possibile impostare più dispositivi come dispositivi principali.

### Sincronizzazione con primario {#sync-up-primary}

1. Dopo aver impostato il dispositivo Chrome come principale, sincronizzare l&#39;altro dispositivo (in questo caso Windows Player) con quello principale.
Fare clic sull&#39;altro dispositivo (in questo caso Windows Player) dal pannello **DISPOSITIVI** e fare clic su **Sincronizza con dispositivo principale**.

   ![immagine1](assets/command-sync/command-sync13-1.png)

1. Fare clic sul dispositivo nell&#39;elenco e fare clic su **Salva**.

   >[NOTA:]
   > Nella finestra di dialogo **Sincronizza con dispositivo principale** viene visualizzato l&#39;elenco dei dispositivi principali. Seleziona quella preferita.

1. Quando il dispositivo (Windows Player) viene sincronizzato con quello primario (Chrome Player), è possibile vedere il dispositivo sincronizzato nel pannello **DISPOSITIVI**.

   ![immagine1](assets/command-sync/command-sync14-1.png)

### Desincronizzazione con il primario {#desync-up-primary}

Dopo aver sincronizzato uno o più dispositivi in un dispositivo primario, è possibile desincronizzare l&#39;assegnazione da tale dispositivo.

>[!NOTE]
>
>Se si desincronizza un dispositivo principale, verranno scollegati anche tutti i dispositivi client associati a tale dispositivo principale.

Per rimuovere la sincronizzazione dal dispositivo principale, effettua le seguenti operazioni:

1. Passare al pannello **DISPOSITIVI** e fare clic sul dispositivo.

1. Fare clic su **Desincronizza dispositivi** per desincronizzare il client dal dispositivo principale.

   ![immagine1](assets/command-sync/command-sync15-1.png)

1. Fai clic su **Conferma** per desincronizzare il dispositivo selezionato dal primario.

   >[NOTA:]
   > Se si fa clic sul dispositivo principale e si utilizza l&#39;opzione di desincronizzazione, tutti i dispositivi connessi al dispositivo principale vengono desincronizzati in un unico passaggio.
