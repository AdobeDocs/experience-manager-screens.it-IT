---
title: Attivazione a livello di risorsa
seo-title: Attivazione a livello di risorsa
description: Segui questa pagina per scoprire come attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore.
seo-description: Segui questa pagina per scoprire come attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore.
feature: Creazione di schermi, Attivazione a livello di risorsa
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 2%

---

# Attivazione a livello di risorsa {#asset-level-scheduling}

Questa pagina descrive l’attivazione a livello di risorsa per le risorse utilizzate in Canali.

I seguenti argomenti sono trattati in questa sezione:

* Panoramica
* Finestra di attivazione
* Riproduzione di eventi singoli
* Gestione della ricorrenza nelle risorse
   * DayParting
   * WeekParting
   * MonthParting
   * Combinazione di partizioni
* Attivazione di più risorse

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se hai installato AEM Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

***Attivazione a livello di risorsa***, consente di attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore. Questa funzione è disponibile per immagini, video, transizioni, pagine e canali incorporati (dinamici o statici).

*Ad esempio*, vuoi che una promozione speciale venga visualizzata solo durante l&#39;ora felice (dalle 2 alle 17:00) il lunedì e il mercoledì.

Questa funzione consente non solo di specificare la data e l’ora di inizio e fine, ma anche un pattern di ricorrenza.

## Finestra di attivazione {#single-event-playback}

L’attivazione a livello di risorsa viene eseguita configurando la scheda **Attivazione** durante l’accesso alle proprietà di una risorsa.

Segui i passaggi seguenti per eseguire la pianificazione a livello di risorsa:

1. Seleziona un canale e fai clic su **Modifica** nella barra delle azioni per aggiungere o modificare il contenuto del canale.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Per saperne di più su come
   >
   >* Crea un progetto. Consulta [Creazione di un nuovo progetto](creating-a-screens-project.md).
   >* Crea e aggiungi contenuto a un canale, consulta [Gestione dei canali](managing-channels.md).


1. Fai clic su **Modifica** per aprire l&#39;editor di canali e seleziona una risorsa a cui applicare la pianificazione.

   ![immagine](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Seleziona la risorsa e fai clic su in alto a sinistra **Configura** (icona a forma di chiave inglese) per aprire le proprietà dell&#39;immagine.

   Fare clic sulla scheda **Attivazione**.

   ![immagine](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Puoi specificare la data dal selettore data utilizzando i campi **Attivo da** e **Attivo fino a** .

   Se selezioni la data e l’ora **Attivo da** e **Attivo fino a**, la risorsa verrà visualizzata e loop solo tra la data/ora di inizio e la data/ora di fine rispettivamente.

   ![immagine](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestione della ricorrenza nelle risorse {#handling-recurrence-in-assets}

È possibile pianificare le risorse in modo che ricorrano a determinati intervalli giornalieri, settimanali o mensili, in base alle proprie esigenze.

Supponiamo di voler visualizzare un&#39;immagine solo il venerdì dalle 13:00 alle 10:00. Puoi utilizzare la scheda **Activation** per impostare l’intervallo ricorrente desiderato per la risorsa.

### Ripartizione giornaliera {#day-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per ripartizione giornaliera {#example-one}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| prima delle 8:00 | la risorsa del canale viene riprodotta prima delle 8:00 di ogni giorno |
| dopo le 14:00 | la risorsa nel canale viene riprodotta dopo le 2:00 di ogni giorno |
| dopo le 12:15 e prima delle 12:45 | la risorsa del canale viene riprodotta dopo le 12:15 di ogni giorno per 30 minuti |
| prima delle 12:15 anche dopo le 12:45 | la risorsa nel canale viene riprodotta prima delle 12:15 di ogni giorno e poi anche dopo le 12:45 di sera |


>[!NOTE]
>
>È inoltre possibile utilizzare la notazione _tempo militare_ (ovvero, 14:00) invece della notazione *am/pm* (ovvero 2:00 pm).

### WeekParting {#week-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per WeekParting {#example-two}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| Lun,Wed,Ven | la risorsa gioca nel canale da lunedì, mercoledì e venerdì |
| Mon-Thu | la risorsa viene riprodotta nel canale dal lunedì al giovedì |

>[!NOTE]
>
>È inoltre possibile utilizzare la notazione _full_ (cioè, Lunedì, Mercoledì, Venerdì) invece della notazione _short-hand_ (ovvero, Luna, Wed, Vri).


### MonthParting {#month-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per MonthParting {#example-three}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| di febbraio,maggio,agosto,novembre | la risorsa viene riprodotta nel canale in febbraio, maggio, agosto e novembre |
| di febbraio-luglio | la risorsa viene riprodotta sul canale da febbraio fino a fine luglio |

>[!NOTE]
>Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le note a mano breve che a nome completo, ad esempio, lunedì/lunedì e gennaio/gennaio.

### Combinazione di partizioni {#combined-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere i campi **Attivo da** e **Attivo fino a** e aggiungere l’espressione al campo Pianificazioni, in base alle tue esigenze.

1. Immetti l’espressione nel **Programma** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la combinazione di partizioni {#example-four}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| dopo le 6:00 e prima delle 18:00 su lun,Wed di gen-mar | il asset gioca nel canale tra le 6 del mattino e le 18 del pomeriggio del lunedì e del mercoledì da gennaio a fine marzo |
| il 1° gennaio dopo le 14.00 anche il 2° giorno di gennaio anche il 3° giorno di gennaio prima delle 3.00 | la risorsa del canale inizia a giocare dopo le 2:00 del 1° gennaio, continua a giocare per tutta la giornata del 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 gennaio dopo le 2:00 del pomeriggio anche il 2-3 di gennaio prima delle 3:00 | la risorsa del canale inizia il lettore dopo le 2:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 pm e continua a giocare fino alle 3:00 del 3 gennaio |

>[!NOTE]
>Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le note a mano breve che a nome completo, ad esempio, lunedì/lunedì e gennaio/gennaio.  Inoltre, è possibile utilizzare la notazione _tempo militare_ (ovvero, 14:00) invece della notazione *am/pm* (ovvero 2:00 pm).


## Attivazione di più risorse {#multi-asset-scheduling}

>[!CAUTION]
>
>La funzione **Attivazione multi-risorsa** è disponibile solo se è stato installato AEM Feature Pack 5 6.3 o AEM Feature Pack 3 6.4.

***L’*** attivazione di più risorse consente all’utente di selezionare più risorse e di applicare una pianificazione di riproduzione a tutte le risorse selezionate.

### Prerequisiti {#prerequisites}

Per utilizzare l’attivazione a livello di risorse multiple per le risorse, crea un progetto AEM Screens con un canale per sequenza. Ad esempio, il seguente caso d’uso illustra l’implementazione della funzione:

* Crea un progetto AEM Screens denominato **MultiAssetDemo**
* Crea un canale denominato **MultiAssetChannel** e aggiungi contenuto al canale, come illustrato nella figura seguente

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Per selezionare più risorse e pianificarne la visualizzazione in un progetto AEM Screens, effettua le seguenti operazioni:

1. Seleziona **MultiAssetChannel** e fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Seleziona più risorse dall&#39;editor e fai clic su **Modifica attivazione** (icona in alto a sinistra).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Selezionare la data e l&#39;ora in **Attivo da** e **Attivo fino a** dalla finestra di dialogo **Attivazione componente**. Fai clic sull’icona del segno di spunta al termine della selezione delle pianificazioni.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Fai clic su aggiorna per controllare le risorse alle quali viene applicata la pianificazione per più risorse.

   >[!NOTE]
   >
   >L’icona di pianificazione è visibile nell’angolo in alto a destra per le risorse per le quali è attiva più risorse.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)
