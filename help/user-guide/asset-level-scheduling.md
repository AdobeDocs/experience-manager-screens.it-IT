---
title: Attivazione a livello di risorsa
seo-title: Attivazione a livello di risorsa
description: Segui questa pagina per scoprire come attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore.
seo-description: Segui questa pagina per scoprire come attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore.
translation-type: tm+mt
source-git-commit: 74b0a98e3123f703db7f353685aed69d6012709d

---


# Attivazione a livello di risorsa {#asset-level-scheduling}

Questa pagina descrive l’attivazione del livello delle risorse per le risorse utilizzate nei canali.

Gli argomenti seguenti sono trattati in questa sezione:

* Panoramica
* Finestra Attivazione
* Riproduzione Di Singoli Eventi
* Gestione della ricorrenza nelle risorse
   * Frazionamento del giorno
   * Scomposizione Settimana
   * Mese di suddivisione
* Attivazione di più risorse

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3 Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

***Attivazione*** a livello di risorsa, consente di attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore. È disponibile per immagini, video, transizioni, pagine e canali incorporati (dinamici o statici).

*Ad esempio*, per visualizzare una promozione speciale solo durante l’ora di piacere (dalle 2 alle 17:00) il lunedì e il mercoledì.

Con questa funzione, potete specificare non solo la data e l&#39;ora di inizio e fine, ma anche un pattern di ricorrenza.

## Finestra Attivazione {#single-event-playback}

Attivazione a livello di risorsa viene eseguita configurando la scheda **Attivazione** durante l&#39;accesso alle proprietà di una risorsa.

Per eseguire la pianificazione a livello di risorsa, effettuate le seguenti operazioni:

1. Selezionate un canale e fate clic su **Modifica** dalla barra delle azioni per aggiungere o modificare il contenuto del canale.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Per informazioni dettagliate su come
   >
   >* Create un progetto, consultate [Creazione di un nuovo progetto](creating-a-screens-project.md).
   >* Create e aggiungete contenuto a un canale, consultate [Gestione dei canali](managing-channels.md).


1. Fai clic su **Modifica** per aprire l’editor dei canali e selezionare una risorsa a cui applicare la pianificazione.

   ![image](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Selezionate la risorsa e fate clic in alto a sinistra **Configura** (icona chiave inglese) per aprire le proprietà dell’immagine.

   Click the **Activation** tab.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Puoi specificare la data dal selettore data utilizzando i campi **Attivo da** e **Attivo fino** a.

   Se selezionate **Attivo da** e **Attivo fino** alla data e all’ora, la risorsa verrà visualizzata e loop solo tra la data/ora di inizio e la data/ora di fine rispettivamente.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestione della ricorrenza nelle risorse {#handling-recurrence-in-assets}

È possibile pianificare la ripetizione delle risorse a determinati intervalli su base giornaliera, settimanale o mensile, in base alle proprie esigenze.

Supponete di voler visualizzare un’immagine solo il venerdì dall’1:00 alle 10:00. Potete utilizzare la scheda **Attivazione** per impostare l&#39;intervallo periodico desiderato per la risorsa.

### Frazionamento del giorno {#day-parting}

1. Selezionate la risorsa e fate clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver immesso la data/ora di inizio e l’ora di fine/data, potete utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   > [!NOTE]
   > Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la suddivisione del giorno {#example-one}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| prima delle 8:00 | la risorsa nel canale viene riprodotta prima delle 8:00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 14:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa nel canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | la risorsa nel canale viene riprodotta prima delle 12:15 di ogni giorno e poi anche dopo le 12:45 di sera |


>[!NOTE]
>È inoltre possibile utilizzare la notazione _militare dell&#39;ora_ (ovvero, 14:00) invece della notazione *AM/pm* (ovvero, 2:00 pm).

### Scomposizione Settimana {#week-parting}

1. Selezionate la risorsa e fate clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver immesso la data/ora di inizio e l’ora di fine/data, potete utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   > [!NOTE]
   > Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la suddivisione settimanale {#example-two}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| Lun,Wed,Vri | la risorsa viene riprodotta nel canale da lunedì, mercoledì e venerdì |
| Mon-Thu | la risorsa viene riprodotta nel canale dal lunedì al giovedì |

>[!NOTE]
>È inoltre possibile utilizzare la notazione _completa_ (cioè, Lunedì,Mercoledì,Venerdì) invece della notazione a mano _corta_ (ovvero, Lun,Wed,Vri).


### Mese di suddivisione {#month-parting}

1. Selezionate la risorsa e fate clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver immesso la data/ora di inizio e l’ora di fine/data, potete utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   > [!NOTE]
   > Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la suddivisione del mese {#example-three}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| di febbraio,maggio,agosto,novembre | la risorsa viene riprodotta nel canale in febbraio, maggio, agosto e novembre |
| di febbraio-luglio | la risorsa viene riprodotta nel canale da febbraio fino alla fine di luglio |

> [!NOTE]
> Quando definite i giorni della settimana e dei mesi, potete utilizzare sia le note a mano breve che quelle a nome intero, ad esempio, Luna/Lunedì e Gen/Gennaio.

### Combinazioni di partizioni {#combined-parting}

1. Selezionate la risorsa e fate clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver immesso la data/ora di inizio e l’ora di fine/data, potete utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   > [!NOTE]
   > Potete saltare o includere i campi **Attivo da** e **Attivo fino** e aggiungere l&#39;espressione al campo Pianificazioni, in base alle vostre esigenze.

1. Immettere l&#39;espressione nella **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per combinazioni di partizioni {#example-four}

Nella tabella seguente sono riepilogate alcune espressioni di esempio che è possibile aggiungere alla pianificazione durante l&#39;assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| dopo le 6:00 e prima delle 18:00 il lun,Wed di gen-mar | la risorsa viene riprodotta nel canale tra le 6 del mattino e le 6 del pomeriggio del lunedì e del mercoledì da gennaio a fine marzo |
| il 1° gennaio dopo le 14:00 anche il 2° giorno di gennaio anche il 3 gennaio prima delle 3:00 | la risorsa nel canale inizia a giocare dopo le 14:00 del 1° gennaio, continua a giocare per l&#39;intera giornata il 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 giorno di gennaio dopo le 2:00 pm anche il 2-3 giorno di gennaio prima delle 3:00 | la risorsa nel canale avvia il lettore dopo le 14:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 del pomeriggio e continua a giocare fino alle 3:00 del 3 gennaio |

> [!NOTE]
> Quando definite i giorni della settimana e dei mesi, potete utilizzare sia le note a mano breve che quelle a nome intero, ad esempio, Luna/Lunedì e Gen/Gennaio.  Inoltre, è possibile utilizzare la notazione _militare dell&#39;ora_ (ovvero, 14:00) invece della notazione *AM/pm* (ovvero, 2:00 pm).


## Attivazione di più risorse {#multi-asset-scheduling}

>[!CAUTION]
>
>La funzione Attivazione **risorse** multiple è disponibile solo se è stato installato AEM 6.3 Feature Pack 5 o AEM 6.4 Feature Pack 3.

***Attivazione*** per più risorse consente all’utente di selezionare più risorse e di applicare una pianificazione di riproduzione a tutte le risorse selezionate.

### Prerequisiti {#prerequisites}

Per utilizzare l’attivazione a livello di risorse multiple per le risorse, create un progetto AEM Screens con un canale di sequenza. Ad esempio, il seguente caso d’uso illustra l’implementazione della funzione:

* Creare un progetto AEM Screens denominato **MultiAssetDemo**
* Create un canale denominato **MultiAssetChannel** e aggiungete contenuto al canale, come mostrato nella figura seguente

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Per selezionare più risorse e pianificarne la visualizzazione in un progetto AEM Screens, procedi come segue:

1. Select **MultiAssetChannel** and click **Edit** from the action bar to open the editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Selezionate più risorse dall’editor e fate clic su **Modifica attivazione** (icona in alto a sinistra).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Selezionare la data e l&#39;ora in **Attivo da** e **Attivo fino** alla finestra di dialogo Attivazione **** componente. Fate clic sull&#39;icona del segno di spunta al termine della selezione delle pianificazioni.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Fate clic su Aggiorna per controllare le risorse a cui viene applicata la pianificazione per più risorse.

   >[!NOTE]
   >
   >L’icona di pianificazione è visibile nell’angolo in alto a destra per le risorse che attivano più risorse.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

