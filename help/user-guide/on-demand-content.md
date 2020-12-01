---
title: Aggiornamento dei contenuti on-demand
seo-title: Aggiornamento dei contenuti on-demand
description: 'Seguite questa pagina per informazioni su On-Demand Content Update.  '
seo-description: 'Seguite questa pagina per informazioni su On-Demand Content Update.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 8492bdd071ae029a68ec4a4983c79ce326cac38b
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---


# Aggiornamento dei contenuti on-demand {#on-demand}

Questa sezione descrive il contenuto on-demand per la gestione delle pubblicazioni.

## Gestione della pubblicazione: Distribuzione di aggiornamenti di contenuto dall&#39;autore alla pubblicazione sul dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Potete pubblicare e annullare la pubblicazione del contenuto da  AEM Screens. La funzione Gestisci pubblicazione consente di distribuire gli aggiornamenti di contenuto dall’autore alla pubblicazione sul dispositivo. Potete pubblicare/annullare la pubblicazione del contenuto per l’intero progetto AEM Screens  o solo per un canale, un percorso, un dispositivo, un’applicazione o una pianificazione.

### Gestione della pubblicazione per un progetto AEM Screens  {#managing-publication-for-an-aem-screens-project}

Per distribuire gli aggiornamenti di contenuto dall’istanza di creazione alla pubblicazione sul dispositivo per un progetto AEM Screens , effettuate le seguenti operazioni:

1. Andate al progetto AEM Screens .
1. Fate clic su **Gestisci pubblicazione** nella barra delle azioni per pubblicare l&#39;istanza del progetto da pubblicare.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. Viene aperta la procedura guidata **Gestisci pubblicazione**. Potete selezionare **Action** e pianificare l&#39;ora di pubblicazione per ora o in seguito. Fai clic su **Avanti**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Selezionare la casella per selezionare l&#39;intero progetto dalla procedura guidata **Gestisci pubblicazione**.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Fate clic su **+ Include Children** dalla barra delle azioni e deselezionate tutte le opzioni per pubblicare tutti i moduli nel progetto, quindi fate clic su **Aggiungi** per pubblicare.

   >[!NOTE]
   >
   >Per impostazione predefinita, tutte le caselle sono selezionate e sarà necessario deselezionare manualmente le caselle per pubblicare tutti i moduli nel progetto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Informazioni sulla finestra di dialogo Includi elementi figlio**

   Il passaggio sopra riportato mostra come pubblicare l’intero contenuto. Se si desidera utilizzare le altre tre alternative disponibili, sarà necessario verificare quella particolare opzione.
Ad esempio, la seguente immagine consente di gestire e aggiornare solo le pagine modificate del progetto:
   ![immagine](assets/author-publish-manage.png)

   Seguite le spiegazioni riportate di seguito per comprendere le opzioni disponibili:

   1. **Include solo elementi figlio** immediati: Questa opzione consente di gestire gli aggiornamenti solo per i nodi secondari della struttura del progetto.
   1. **Includi solo pagine** modificate: Questa opzione consente di gestire gli aggiornamenti solo per le pagine modificate del progetto in cui si trovano le modifiche nella struttura del progetto.
   1. **Solo pagine** già pubblicate: Questa opzione consente di gestire gli aggiornamenti solo per le pagine pubblicate in precedenza.


1. Fare clic su **Pubblica** dalla **Gestione guidata pubblicazione.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Attendete alcuni secondi/minuti in modo che il contenuto raggiunga l’istanza di pubblicazione.
   >
   >
   >    1. Il flusso di lavoro non funzionerà se il progetto non contiene modifiche e se non sono presenti modifiche per **Aggiorna contenuto offline**.
   >    1. Il flusso di lavoro non funzionerà se l&#39;autore non completa il processo di replica (i contenuti continuano a caricare nell&#39;istanza di pubblicazione) dopo aver fatto clic sul pulsante **Pubblica** nel flusso di lavoro di gestione della pubblicazione.


   >[!CAUTION]
   >Se in qualità di autore o creatore di contenuti, desiderate visualizzare le modifiche nei dispositivi collegati all’istanza di creazione, fate clic su **Aggiorna contenuto offline** nel dashboard di canale o selezionando il progetto. In questo caso, il contenuto aggiornato offline viene eseguito solo nell&#39;istanza di creazione.

1. Andate al progetto e fate clic su **Aggiorna contenuto offline** nella barra delle azioni. Questa azione inoltra lo stesso comando per pubblicare l’istanza, in modo che le zip offline vengano create anche nell’istanza di pubblicazione.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Dopo aver completato il flusso di lavoro di gestione della pubblicazione e se esiste un lettore che punta all’istanza di creazione, è necessario attivare l’aggiornamento del contenuto offline in corso di creazione, che creerà l’aggiornamento offline nell’istanza di creazione.

   >[!CAUTION]
   >
   >È necessario attivare l’aggiornamento del contenuto offline nell’istanza di creazione, se al server di creazione è registrato un lettore. L&#39;aggiornamento del contenuto offline non è richiesto per il lettore registrato nell&#39;istanza di pubblicazione.

### Gestione della pubblicazione per un canale {#managing-publication-for-a-channel}

Per distribuire gli aggiornamenti di contenuto dall’istanza di creazione alla pubblicazione sul dispositivo per un canale in un progetto AEM Screens , effettuate le seguenti operazioni:

>[!NOTE]
>
>Seguite questa sezione solo se vi sono modifiche in un canale. Se un canale non contiene modifiche dopo il contenuto offline del precedente aggiornamento, il flusso di lavoro di gestione della pubblicazione per un singolo canale non funzionerà.

1. Andate al progetto Screens e selezionate il canale.
1. Fate clic su **Gestisci pubblicazione** nella barra delle azioni per pubblicare l&#39;istanza del canale da pubblicare.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. Viene aperta la procedura guidata **Gestisci pubblicazione**. Potete selezionare **Action** e pianificare l&#39;ora di pubblicazione per ora o in seguito. Fai clic su **Avanti**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Fare clic su **Pubblica** dalla **Gestione guidata pubblicazione.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Attendete alcuni secondi/minuti in modo che il contenuto raggiunga l’istanza di pubblicazione.

1. Attivatore **Aggiorna contenuto offline** nel dashboard canale eseguirà il push del contenuto offline solo per l&#39;istanza di creazione ma non per l&#39;istanza di pubblicazione. I passaggi da 1 a 4 prevedono l’invio di contenuto offline per pubblicare l’istanza.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >È prima necessario pubblicare e quindi attivare l&#39;aggiornamento del contenuto offline, come riepilogato nei passaggi precedenti.

### Assegnazione canale e dispositivo: {#channel-and-device-re-assignment}

Se avete riassegnato un dispositivo, dovete pubblicare sia la visualizzazione iniziale che la nuova visualizzazione, una volta che il dispositivo è stato assegnato nuovamente al nuovo display.

Analogamente, se avete riassegnato un canale, dovete pubblicare sia il display iniziale che il nuovo display, una volta che il canale è stato riassegnato al nuovo display.