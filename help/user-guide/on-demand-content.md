---
title: Aggiornamento dei contenuti on-demand
seo-title: Aggiornamento dei contenuti on-demand
description: 'Segui questa pagina per informazioni sull’aggiornamento dei contenuti on-demand.  '
seo-description: 'Segui questa pagina per informazioni sull’aggiornamento dei contenuti on-demand.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
feature: Creazione di esperienze in Screens
role: Developer (Sviluppatore)
level: Intermedio
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---


# Aggiornamento dei contenuti on-demand {#on-demand}

Questa sezione descrive i contenuti on-demand per la gestione delle pubblicazioni.

## Gestione della pubblicazione: Distribuzione di aggiornamenti di contenuto da Autore a Pubblica sul dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Puoi pubblicare e annullare la pubblicazione dei contenuti da AEM Screens. La funzione Gestisci pubblicazione consente di distribuire aggiornamenti dei contenuti dall’autore alla pubblicazione sul dispositivo. Puoi pubblicare/annullare la pubblicazione dei contenuti per l’intero progetto AEM Screens o solo per uno dei canali, la posizione, il dispositivo, l’applicazione o una pianificazione.

### Gestione della pubblicazione per un progetto AEM Screens {#managing-publication-for-an-aem-screens-project}

Segui i passaggi riportati di seguito per fornire aggiornamenti dei contenuti dall’autore al dispositivo per la pubblicazione per un progetto AEM Screens:

1. Passa al progetto AEM Screens.
1. Fai clic su **Gestisci pubblicazione** nella barra delle azioni per pubblicare il progetto nell&#39;istanza di pubblicazione.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. Viene visualizzata la procedura guidata **Gestisci pubblicazione** . Puoi selezionare l’ **Azione** e anche pianificare l’ora di pubblicazione per il momento o in un secondo momento. Fai clic su **Avanti**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Seleziona la casella per selezionare l’intero progetto dalla procedura guidata **Gestisci pubblicazione** .

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Fai clic su **+ Include Children** nella barra delle azioni e deseleziona tutte le opzioni per pubblicare tutti i moduli nel progetto, quindi fai clic su **Aggiungi** per pubblicare.

   >[!NOTE]
   >
   >Per impostazione predefinita, tutte le caselle saranno selezionate e dovrai deselezionare manualmente le caselle per pubblicare tutti i moduli nel progetto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Finestra di dialogo Includi elementi figlio**

   Il passaggio precedente mostra come pubblicare l’intero contenuto. Nel caso in cui si desideri utilizzare le altre tre alternative disponibili, sarà necessario controllare quella particolare opzione.
Ad esempio, l’immagine seguente consente di gestire e aggiornare solo le pagine modificate del progetto:
   ![immagine](assets/author-publish-manage.png)

   Segui le spiegazioni riportate di seguito per comprendere le opzioni disponibili:

   1. **Includi solo elementi figlio** immediati: Questa opzione consente di gestire gli aggiornamenti solo ai sotto-nodi della struttura del progetto.
   1. **Include solo le pagine** modificate: Questa opzione consente di gestire gli aggiornamenti solo nelle pagine modificate del progetto in cui si trovano le modifiche nella struttura del progetto.
   1. **Solo le pagine** già pubblicate: Questa opzione consente di gestire gli aggiornamenti solo alle pagine pubblicate in precedenza.


1. Fai clic su **Pubblica** dalla procedura guidata **Gestisci pubblicazione.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Attendi alcuni secondi/minuti in modo che il contenuto raggiunga l’istanza di pubblicazione.
   >
   >
   >    1. Il flusso di lavoro non funzionerà se non ci sono modifiche nel progetto e se non ci sono modifiche per **Aggiorna contenuto offline**.
   >    1. Il flusso di lavoro non funziona se l’autore non completa il processo di replica (i contenuti vengono ancora caricati nell’istanza di pubblicazione) dopo aver fatto clic sul pulsante **Pubblica** nel flusso di lavoro di gestione della pubblicazione.


   >[!CAUTION]
   >Se in qualità di autore o creatore di contenuti, desideri visualizzare le modifiche nei dispositivi collegati all’istanza di authoring, fai clic su **Aggiorna contenuto offline** nel dashboard del canale o selezionando il progetto. In questo caso, l’aggiornamento del contenuto offline viene eseguito solo nell’istanza di authoring.

1. Passa al progetto e fai clic su **Aggiorna contenuto offline** nella barra delle azioni. Questa azione inoltra lo stesso comando per pubblicare l&#39;istanza, in modo che le zip offline vengano create anche sull&#39;istanza di pubblicazione.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Una volta completato il flusso di lavoro gestisci pubblicazione e se esiste un lettore che punta all’istanza di authoring, devi attivare l’aggiornamento del contenuto offline in autore, in modo da creare l’aggiornamento offline nell’istanza di authoring.

   >[!CAUTION]
   >
   >Devi attivare l’aggiornamento del contenuto offline nell’istanza di authoring, se hai un lettore registrato nel server di authoring. L’aggiornamento del contenuto offline non è necessario per il lettore registrato nell’istanza di pubblicazione.

### Gestione della pubblicazione per un canale {#managing-publication-for-a-channel}

Segui i passaggi riportati di seguito per distribuire aggiornamenti di contenuto dall’autore al dispositivo per la pubblicazione su un canale in un progetto AEM Screens:

>[!NOTE]
>
>Segui questa sezione solo se sono presenti modifiche in un canale. Se un canale non dispone di modifiche dopo il precedente aggiornamento del contenuto offline, il flusso di lavoro di gestione della pubblicazione per un singolo canale non funzionerà.

1. Passa al progetto Screens e seleziona il canale .
1. Fai clic su **Gestisci pubblicazione** nella barra delle azioni per pubblicare il canale per pubblicare l&#39;istanza.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. Viene visualizzata la procedura guidata **Gestisci pubblicazione** . Puoi selezionare l’ **Azione** e anche pianificare l’ora di pubblicazione per il momento o in un secondo momento. Fai clic su **Avanti**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Fai clic su **Pubblica** dalla procedura guidata **Gestisci pubblicazione.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Attendi alcuni secondi/minuti in modo che il contenuto raggiunga l’istanza di pubblicazione.

1. Attivatore **Aggiorna contenuto offline** nel dashboard dei canali invierà il contenuto offline solo all&#39;istanza di authoring ma non all&#39;istanza di pubblicazione. I passaggi 1-4 servono a spingere i contenuti offline per pubblicare l&#39;istanza.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Devi prima pubblicare e quindi attivare l’aggiornamento del contenuto offline, come riepilogato nei passaggi precedenti.

### Assegnazione di canali e dispositivi: {#channel-and-device-re-assignment}

Se hai riassegnato un dispositivo, devi pubblicare sia la visualizzazione iniziale che la nuova visualizzazione, una volta che il dispositivo è stato riassegnato al nuovo display.

Allo stesso modo, se hai riassegnato un canale, devi pubblicare sia la visualizzazione iniziale che la nuova visualizzazione, una volta che il canale è stato riassegnato alla nuova visualizzazione.