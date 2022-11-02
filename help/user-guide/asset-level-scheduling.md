---
title: Attivazione a livello di risorsa
seo-title: Asset Level Activation
description: Segui questa pagina per scoprire come attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore.
seo-description: Follow this page to learn how to activate a specific asset in a channel for a scheduled time frame in the player's local timezone.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: 939d078def133e0db0e61ec80167f496c65ade46
workflow-type: tm+mt
source-wordcount: '1641'
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
* Override Globale Per Ora Di Inizio Universale

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se hai installato AEM Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

***Attivazione a livello di risorsa***, consente di attivare una risorsa specifica in un canale per un intervallo di tempo pianificato nel fuso orario locale del lettore. Questa funzione è disponibile per immagini, video, transizioni, pagine e canali incorporati (dinamici o statici).

*Esempio*, vuoi che una promozione speciale venga visualizzata solo durante l&#39;happy hour (dalle 2 del pomeriggio alle 17 del pomeriggio) il lunedì e il mercoledì.

Questa funzione consente non solo di specificare la data e l’ora di inizio e fine, ma anche un pattern di ricorrenza.

## Finestra di attivazione {#single-event-playback}

L’attivazione a livello di risorsa viene eseguita configurando la **Attivazione** durante l’accesso alle proprietà di una risorsa.

Segui i passaggi seguenti per eseguire la pianificazione a livello di risorsa:

1. Seleziona un canale e fai clic su **Modifica** dalla barra delle azioni per aggiungere o modificare il contenuto del canale.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Per saperne di più su come
   >
   >* Crea un progetto, vedi [Creazione di un nuovo progetto](creating-a-screens-project.md).
   >* Crea e aggiungi contenuto a un canale, vedi [Gestione dei canali](managing-channels.md).


1. Fai clic su **Modifica** per aprire l’editor canali e selezionare una risorsa a cui applicare la pianificazione.

   ![immagine](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Seleziona la risorsa e fai clic su in alto a sinistra **Configura** (icona a forma di chiave inglese) per aprire le proprietà dell’immagine.

   Fai clic sul pulsante **Attivazione** scheda .

   ![immagine](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Puoi specificare la data dal selettore data utilizzando **Attivo da** e **Attivo fino a** campi.

   Se selezioni la **Attivo da** e **Attivo fino a** data e ora, la risorsa verrà visualizzata e loop solo tra la data/ora di inizio e la data/ora di fine rispettivamente.

   ![immagine](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestione della ricorrenza nelle risorse {#handling-recurrence-in-assets}

È possibile pianificare le risorse in modo che ricorrano a determinati intervalli giornalieri, settimanali o mensili, in base alle proprie esigenze.

Supponiamo di voler visualizzare un&#39;immagine solo il venerdì dalle 13:00 alle 10:00. È possibile utilizzare **Attivazione** per impostare l’intervallo ricorrente desiderato per la risorsa.

### Ripartizione giornaliera {#day-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona a forma di chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere il **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Pianificazioni in base alle tue esigenze.

1. Immetti l’espressione nel **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

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
>È inoltre possibile utilizzare _ora militare_ notazione (ovvero 14:00) anziché *AM/pm* notazione (cioè, 2:00 pm).

### WeekParting {#week-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona a forma di chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere il **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Pianificazioni in base alle tue esigenze.

1. Immetti l’espressione nel **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per WeekParting {#example-two}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| Lun,Wed,Ven | la risorsa gioca nel canale da lunedì, mercoledì e venerdì |
| Mon-Thu | la risorsa viene riprodotta nel canale dal lunedì al giovedì |

>[!NOTE]
>
>È inoltre possibile utilizzare _pieno_ notazione (cioè, lunedì,mercoledì,venerdì) anziché _a mano corta_ notazione (cioè, lun, Wed, ven).


### MonthParting {#month-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona a forma di chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere il **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Pianificazioni in base alle tue esigenze.

1. Immetti l’espressione nel **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per MonthParting {#example-three}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| di febbraio,maggio,agosto,novembre | la risorsa viene riprodotta nel canale in febbraio, maggio, agosto e novembre |
| di febbraio-luglio | la risorsa viene riprodotta sul canale da febbraio fino a fine luglio |

>[!NOTE]
>Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le note a mano breve che a nome completo, ad esempio, lunedì/lunedì e gennaio/gennaio.

### Combinazione di partizioni {#combined-parting}

1. Seleziona la risorsa e fai clic su **Configura** (icona a forma di chiave inglese) per aprire la finestra di dialogo delle proprietà.

1. Dopo aver inserito la data/ora di inizio e l’ora di fine/data, puoi utilizzare un’espressione o una versione di testo naturale per specificare la pianificazione della ricorrenza.

   >[!NOTE]
   >Puoi saltare o includere il **Attivo da** e **Attivo fino a** e aggiungi l’espressione al campo Pianificazioni in base alle tue esigenze.

1. Immetti l’espressione nel **Pianificazione** e la risorsa verrà visualizzata per il particolare intervallo di giorno e ora.

#### Espressioni di esempio per la combinazione di partizioni {#example-four}

Nella tabella seguente sono riepilogati alcuni esempi di espressioni che è possibile aggiungere alla pianificazione durante l’assegnazione di un canale a una visualizzazione.

| **Espressione** | **Interpretazione** |
|---|---|
| dopo le 6:00 e prima delle 18:00 su lun,Wed di gen-mar | il asset gioca nel canale tra le 6 del mattino e le 18 del pomeriggio del lunedì e del mercoledì da gennaio a fine marzo |
| il 1° gennaio dopo le 14.00 anche il 2° giorno di gennaio anche il 3° giorno di gennaio prima delle 3.00 | la risorsa del canale inizia a giocare dopo le 2:00 del 1° gennaio, continua a giocare per tutta la giornata del 2 gennaio fino alle 3:00 del 3 gennaio |
| il 1-2 gennaio dopo le 2:00 del pomeriggio anche il 2-3 di gennaio prima delle 3:00 | la risorsa del canale inizia il lettore dopo le 2:00 del 1° gennaio, continua a giocare fino alle 3:00 del 2 gennaio, poi riparte il 2 gennaio alle 2:00 pm e continua a giocare fino alle 3:00 del 3 gennaio |

>[!NOTE]
>Quando definisci i giorni della settimana e i mesi, puoi utilizzare sia le note a mano breve che a nome completo, ad esempio, lunedì/lunedì e gennaio/gennaio.  Inoltre, puoi utilizzare _ora militare_ notazione (ovvero 14:00) anziché *AM/pm* notazione (cioè, 2:00 pm).


## Attivazione di più risorse {#multi-asset-scheduling}

>[!CAUTION]
>
>La **Attivazione di più risorse** Questa funzione è disponibile solo se è stato installato AEM Feature Pack 5 o AEM 6.4 Feature Pack 3 di 6.3.

***Attivazione di più risorse*** consente all’utente di selezionare più risorse e di applicare una pianificazione di riproduzione a tutte le risorse selezionate.

### Prerequisiti {#prerequisites}

Per utilizzare l’attivazione a livello di risorse multiple per le risorse, crea un progetto AEM Screens con un canale per sequenza. Ad esempio, il seguente caso d’uso illustra l’implementazione della funzione:

* Crea un progetto AEM Screens denominato come **DemoMultiAsset**
* Crea un canale denominato come **MultiAssetChannel** e aggiungere contenuti al canale, come illustrato nella figura riportata di seguito

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Per selezionare più risorse e pianificarne la visualizzazione in un progetto AEM Screens, effettua le seguenti operazioni:

1. Seleziona **MultiAssetChannel** e fai clic su **Modifica** dalla barra delle azioni per aprire l’editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Seleziona più risorse dall’editor e fai clic su **Modifica attivazione** (icona in alto a sinistra).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Seleziona la data e l’ora in **Attivo da** e **Attivo fino a** dal **Attivazione componente** finestra di dialogo. Fai clic sull’icona del segno di spunta al termine della selezione delle pianificazioni.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Fai clic su aggiorna per controllare le risorse alle quali viene applicata la pianificazione per più risorse.

   >[!NOTE]
   >
   >L’icona di pianificazione è visibile nell’angolo in alto a destra per le risorse per le quali è attiva più risorse.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Override Globale Per Ora Di Inizio Universale {#global-override-scheduling}

***Override globale per l&#39;ora di inizio universale***, è un’impostazione che consente all’autore del contenuto di definire la riproduzione di un’immagine o di una risorsa video in base a un’ora specifica. Non viene utilizzata l’impostazione di fuso orario o ora di un singolo lettore.

Normalmente, la riproduzione è determinata dall’ora locale di un determinato lettore, ma con l’override globale, è possibile utilizzare un tempo di inizio specifico e universale per avviare la riproduzione della risorsa.

Questo consente all’autore dei contenuti di designare la riproduzione di una risorsa specifica come avvenuta a una data/ora specifica, indipendentemente dall’orologio locale su qualsiasi lettore con il contenuto assegnato.

L’override globale per l’ora di inizio universale viene eseguito configurando l’ **Attivazione** durante l’accesso alle proprietà di una risorsa. Per eseguire un’override globale per la pianificazione delle risorse, effettua le seguenti operazioni:

1. Seleziona un canale e fai clic su **Modifica** dalla barra delle azioni per aggiungere o modificare il contenuto del canale.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Fai clic su **Modifica** per aprire l’editor canali e selezionare una risorsa a cui applicare la pianificazione.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Per un Override globale immettere il tempo di attivazione nel **Sostituzione del fuso orario** per la risorsa. Se non inserisci nulla in questa area, il fuso orario applicato sarà quello del lettore.


