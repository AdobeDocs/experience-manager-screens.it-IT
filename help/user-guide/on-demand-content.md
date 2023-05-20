---
title: Aggiornamento dei contenuti on-demand
seo-title: On-Demand Content Update
description: Segui questa pagina per scoprire di più sull’aggiornamento dei contenuti on-demand.
seo-description: Follow this page to learn about On-Demand Content Update.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Aggiornamento dei contenuti on-demand {#on-demand}

Questa sezione descrive i contenuti on-demand per la gestione delle pubblicazioni.

## Gestione della pubblicazione: distribuzione degli aggiornamenti dei contenuti dall’ambiente di authoring a quello di pubblicazione sul dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Puoi pubblicare e annullare la pubblicazione dei contenuti da AEM Screens. La funzione Gestisci pubblicazione consente di distribuire aggiornamenti di contenuto dall’ambiente di authoring a quello di pubblicazione su dispositivo. Puoi pubblicare/annullare la pubblicazione dei contenuti per l’intero progetto AEM Screens o solo per un canale, una posizione, un dispositivo, un’applicazione o una pianificazione.

### Gestione della pubblicazione per un progetto AEM Screens {#managing-publication-for-an-aem-screens-project}

Per distribuire gli aggiornamenti di contenuto dall’ambiente di authoring a quello di pubblicazione su dispositivo per un progetto AEM Screens, segui i passaggi seguenti:

1. Passa al progetto AEM Screens.
1. Clic **Gestisci pubblicazione** dalla barra delle azioni per pubblicare il progetto nell’istanza Publish.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. Il **Gestisci pubblicazione** viene aperta la procedura guidata. È possibile selezionare **Azione** e pianifica anche il tempo di pubblicazione per il momento o in un secondo momento. Fai clic su **Avanti**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Seleziona la casella da cui selezionare l’intero progetto **Gestisci pubblicazione** procedura guidata.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Clic **+ Includi elementi figlio** dalla barra delle azioni, deseleziona tutte le opzioni per pubblicare tutti i moduli del progetto e fai clic su **Aggiungi** per la pubblicazione.

   >[!NOTE]
   >
   >Per impostazione predefinita, tutte le caselle sono selezionate e dovrai deselezionarle manualmente per pubblicare tutti i moduli del progetto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Finestra di dialogo Includi elementi figlio**

   Il passaggio indicato sopra mostra come pubblicare l’intero contenuto. Nel caso in cui si desideri utilizzare le altre tre alternative disponibili, è necessario selezionare quella particolare opzione.
Ad esempio, l’immagine seguente ti consente di gestire e aggiornare solo le pagine modificate del progetto:
   ![immagine](assets/author-publish-manage.png)

   Per comprendere le opzioni disponibili, segui le spiegazioni riportate di seguito:

   1. **Includi solo gli elementi figlio di primo livello**: questa opzione consente di gestire gli aggiornamenti solo ai sottonodi nella struttura del progetto.
   1. **Solo pagine modificate**: questa opzione consente di gestire gli aggiornamenti solo alle pagine modificate del progetto in cui le modifiche si trovano nella struttura del progetto.
   1. **Solo pagine già pubblicate**: questa opzione consente di gestire gli aggiornamenti solo per le pagine pubblicate in precedenza.


1. Clic **Pubblica** dal **Procedura guidata Gestisci pubblicazione.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Attendi alcuni secondi/minuti in modo che il contenuto raggiunga l’istanza di pubblicazione.
   >
   >
   >    1. Il flusso di lavoro non funziona se nel progetto non sono presenti modifiche e non viene eseguita alcuna operazione per **Aggiorna contenuto offline**.
   >    1. Il flusso di lavoro non funziona se l’autore non completa il processo di replica (i contenuti vengono ancora caricati nell’istanza Publish) dopo aver fatto clic su **Pubblica** nel flusso di lavoro di gestione della pubblicazione.


   >[!CAUTION]
   >Se in qualità di autore o creatore di contenuti desideri visualizzare le modifiche nei dispositivi collegati all’istanza di authoring, fai clic su **Aggiorna contenuto offline** dal dashboard del canale o selezionando il progetto. In questo caso, l’aggiornamento del contenuto offline viene eseguito solo nell’istanza di authoring.

1. Passa al progetto e fai clic su **Aggiorna contenuto offline** dalla barra delle azioni. Questa azione inoltra lo stesso comando all’istanza Publish, in modo che i file ZIP non in linea vengano creati anche sull’istanza Publish.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Dopo aver completato il flusso di lavoro di gestione della pubblicazione e se un lettore punta all’istanza di authoring, devi attivare l’aggiornamento dei contenuti offline in authoring, che creerà l’aggiornamento offline nell’istanza di authoring.

   >[!CAUTION]
   >
   >Se hai un lettore registrato nel server di authoring, devi attivare l’aggiornamento dei contenuti offline nell’istanza di authoring. Non è necessario aggiornare il contenuto offline per il lettore registrato nell’istanza Publish.

### Gestione della pubblicazione per un canale {#managing-publication-for-a-channel}

Per distribuire gli aggiornamenti di contenuto dall’ambiente di authoring a quello di pubblicazione su dispositivo per un canale in un progetto AEM Screens, segui i passaggi seguenti:

>[!NOTE]
>
>Segui questa sezione solo se ci sono modifiche in un canale. Se un canale non presenta modifiche dopo il precedente aggiornamento del contenuto offline, il flusso di lavoro di gestione della pubblicazione per un singolo canale non funzionerà.

1. Passa al progetto Screens e seleziona il canale.
1. Clic **Gestisci pubblicazione** dalla barra delle azioni per pubblicare il canale nell’istanza Publish.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. Il **Gestisci pubblicazione** viene aperta la procedura guidata. È possibile selezionare **Azione** e pianifica anche il tempo di pubblicazione per il momento o in un secondo momento. Fai clic su **Avanti**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Clic **Pubblica** dal **Procedura guidata Gestisci pubblicazione.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Attendi alcuni secondi/minuti in modo che il contenuto raggiunga l’istanza di pubblicazione.

1. Trigger **Aggiorna contenuto offline** in channel dashboard invierà il contenuto offline solo all’istanza di authoring, ma non a quella di pubblicazione. I passaggi 1-4 consistono nel push dei contenuti offline all’istanza Publish.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Devi innanzitutto pubblicare e quindi attivare l’aggiornamento del contenuto offline, come riepilogato nei passaggi precedenti.

### Riassegnazione di canali e dispositivi: {#channel-and-device-re-assignment}

Se il dispositivo è stato riassegnato, è necessario pubblicare sia la visualizzazione iniziale che quella nuova, una volta che il dispositivo è stato riassegnato alla nuova visualizzazione.

Allo stesso modo, se avete riassegnato un canale, dovete pubblicare sia la visualizzazione iniziale che quella nuova, una volta che il canale è stato riassegnato alla nuova visualizzazione.
