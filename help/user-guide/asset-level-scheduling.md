---
title: Pianificazione a livello di risorsa
seo-title: Pianificazione a livello di risorsa
description: Segui questa pagina per scoprire come attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore.
seo-description: Segui questa pagina per scoprire come attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: da25cdc7-c814-493e-8d8e-b6191fee2831
noindex: true
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Pianificazione a livello di risorsa {#asset-level-scheduling}

In questa sezione viene descritta la pianificazione a livello di risorsa per le risorse utilizzate nei canali.

Gli argomenti seguenti sono trattati in questa sezione:

* Panoramica
* Utilizzo della pianificazione a livello di risorsa
* Gestione della ricorrenza nelle risorse
* Pianificazione di più risorse


>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3 Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l'accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

***Asset Level Scheduling (Pianificazione*** livello risorsa) consente di attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore. È disponibile per immagini, video, transizioni, pagine e canali incorporati (dinamici o statici).

*Ad esempio*, per visualizzare una promozione speciale solo durante l’ora di piacere (dalle 2 alle 17:00) il lunedì e il mercoledì.

Con questa funzione, potete specificare non solo la data e l'ora di inizio e fine, ma anche un pattern di ricorrenza.

## Utilizzo della pianificazione a livello di risorsa {#using-asset-level-scheduling}

La pianificazione a livello di risorsa viene eseguita configurando la scheda **Attivazione** durante l'accesso alle proprietà di una risorsa.

Per eseguire la pianificazione a livello di risorsa, effettuate le seguenti operazioni:

1. Selezionate un canale e fate clic su **Modifica** dalla barra delle azioni per aggiungere o modificare il contenuto del canale.

   ![screen_shot_2018-04-23at111422am](assets/screen_shot_2018-04-23at111422am.png)

   >[!NOTE]
   >
   >Per informazioni dettagliate su come
   >
   >* Create un progetto, consultate [Creazione di un nuovo progetto](creating-a-screens-project.md).
   >* Create e aggiungete contenuto a un canale, consultate [Gestione dei canali](managing-channels.md).


1. Fai clic su **Modifica** per aprire l’editor dei canali e selezionare una risorsa a cui applicare la pianificazione.

   ![screen_shot_2018-04-24at90434pm](assets/screen_shot_2018-04-24at90434pm.png)

1. Selezionate la risorsa e fate clic sull’icona **Configura** in alto a sinistra per aprire le proprietà dell’immagine.

   Click the **Activation** tab.

   ![screen_shot_2018-04-23at112348am](assets/screen_shot_2018-04-23at112348am.png)

1. Puoi specificare la data dal selettore data dai campi **Attivo da** e **Attivo fino** ai campi.

   Se selezionate **Attivo da** e **Attivo fino** alla data e all’ora, la risorsa verrà visualizzata e loop solo tra la data/ora di inizio e la data/ora di fine rispettivamente.

   ![screen_shot_2018-04-23at113545am](assets/screen_shot_2018-04-23at113545am.png)

## Gestione della ricorrenza nelle risorse {#handling-recurrence-in-assets}

È possibile pianificare la ripetizione delle risorse a determinati intervalli su base giornaliera, settimanale o mensile, in base alle proprie esigenze.

Supponete di voler visualizzare un’immagine solo il venerdì dall’1:00 alle 10:00. Potete utilizzare la scheda Attivazione per impostare l'intervallo periodico desiderato per la risorsa.

### Aggiunta di un evento ricorrente per la risorsa {#adding-a-recurring-event-for-your-asset}

1. Selezionate la risorsa e fate clic sull'icona **Configura** per aprire la finestra di dialogo delle proprietà.
1. Dopo aver immesso la data/ora di inizio e l’ora di fine/data, potete utilizzare un’espressione cron o una versione di testo naturale per specificare il programma di ricorrenza.

   Potete cercare sul Web un generatore di espressioni cron gratuite, quindi copiare e incollare l’espressione cron nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

   *In alternativa*, invece di utilizzare l'espressione cron, potete utilizzare la versione di testo naturale, ad esempio *dopo le 6:00 e prima delle 18:00* di venerdì per eseguire l'attività. Immettete il testo in **Pianificazione** per visualizzare la risorsa.

## Pianificazione di più risorse {#multi-asset-scheduling}

>[!CAUTION]
>
>La funzione **Pianificazione** risorse multiple è disponibile solo se è stato installato AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

***Pianificazione*** per più risorse consente all’utente di selezionare più risorse e di applicare una pianificazione di riproduzione a tutte le risorse selezionate.

### Prerequisiti {#prerequisites}

Per utilizzare la pianificazione a livello di risorse multiple per le risorse, create un progetto AEM Screens con un canale di sequenza. Ad esempio, il seguente caso d’uso illustra l’implementazione della funzione:

* Creare un progetto AEM Screens denominato **MultiAssetDemo**
* Create un canale denominato **MultiAssetChannel** e aggiungete contenuto al canale, come mostrato nella figura seguente

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Per selezionare più risorse e pianificarne la visualizzazione in un progetto AEM Screens, procedi come segue:

1. Select **MultiAssetChannel** and click **Edit** from the action bar to open the editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Selezionate più risorse dall’editor e fate clic su **Modifica attivazione** (icona in alto a sinistra).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Selezionare la data e l'ora in **Attivo da** e **Attivo fino** alla finestra di dialogo Attivazione **** componente. Fate clic sull'icona del segno di spunta al termine della selezione delle pianificazioni.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Fate clic su Aggiorna per controllare le risorse a cui viene applicata la pianificazione per più risorse.

   >[!NOTE]
   >
   >L’icona di pianificazione è visibile nell’angolo in alto a destra per le risorse per le quali è attiva la pianificazione di più risorse.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

