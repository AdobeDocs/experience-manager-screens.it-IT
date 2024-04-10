---
title: Configurazione di ContextHub in AEM Screens
description: Scopri ContextHub nel motore di targeting per definire l’archivio dati per la modifica del contenuto dell’attivatore dei dati.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 1%

---

# Configurazione di ContextHub in AEM Screens {#configuring-contexthub-in-aem-screens}

In questa sezione viene posto l’accento sulla creazione e la gestione delle modifiche alle risorse basate sui dati tramite un archivio dati.

## Termini chiave {#key-terms}

Prima di entrare nei dettagli della creazione e della gestione dei canali basati sull’inventario nel progetto AEM Screens, scopri alcuni dei termini chiave dei diversi scenari.

**Marchio** - Descrizione del progetto di alto livello.

**Superfici** - il nome del progetto AEM Screens, ad esempio Digital Ad Signage

**Attività** - Definisce le regole di categoria, ad esempio Basate su inventario, Basate su meteo o Basate sulla disponibilità del reparto.

**Pubblico** - Definisce la regola.

**Segmento** : versione della risorsa da riprodurre per la regola specificata. Ad esempio, se la temperatura è inferiore a 50 gradi Fahrenheit, sullo schermo viene visualizzata l’immagine di una bevanda calda, altrimenti di una bevanda fredda.

Il diagramma seguente fornisce una rappresentazione visiva del modo in cui le configurazioni ContextHub coincidono con attività, pubblico e canali.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Precondizioni {#preconditions}

Prima di iniziare a configurare le configurazioni Context Hub per un progetto AEM Screens, devi impostare i fogli Google (a scopo dimostrativo).

>[!IMPORTANT]
>
>Nell’esempio seguente, i fogli di Google vengono utilizzati come database di esempio dal quale vengono recuperati i valori, a scopo puramente didattico. L’Adobe non prevede l’utilizzo di Google Sheets per ambienti di produzione.
>
>Per ulteriori informazioni, consulta [Ottieni chiave API](https://developers.google.com/maps/documentation/javascript/get-api-key) nella documentazione di Google.

## Passaggio 1: configurazione di un archivio dati {#step-setting-up-a-data-store}

È possibile impostare l&#39;archivio dati come evento di I/O locale o come evento di database locale.

L’esempio seguente di trigger di dati a livello di risorsa mostra un evento di database locale che imposta un archivio dati come un foglio di Excel che consente di utilizzare le configurazioni ContextHub e il percorso dei segmenti per il canale AEM Screens.

Dopo aver configurato `google` correttamente, come illustrato nell&#39;esempio seguente:

![immagine](/help/user-guide/assets/context-hub/context-hub1.png)

La seguente convalida è ciò che viene visualizzato quando si controlla la connessione immettendo i due valori, `*google sheet ID*` e `*API key*` nel formato seguente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![immagine](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>L’esempio specifico seguente mostra i fogli di google come archivio dati che attiva un cambiamento di risorsa se il valore è maggiore di 100 o minore di 50.

## Passaggio 2: configurazione dell’archivio {#step-setting-store-configurations}

1. **Navigazione a ContextHub**

   Passa all’istanza AEM e fai clic sull’icona Strumenti nella barra laterale a sinistra. Clic **Sites** > **ContextHub**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creazione di una configurazione archivio ContextHub**

   1. Passa al contenitore di configurazione con titolo **schermi**.

   1. Seleziona **Crea** > **Crea contenitore configurazione** e inserisci il titolo come **DemoContextHub**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Naviga** a **DemoContextHub** > **Crea** **Configurazione ContentHub** e fai clic su **Salva**.

      >[!NOTE]
      > Dopo aver selezionato **Salva**, sei nel **Configurazione ContextHub** schermo.

   1. Dalla sezione **Configurazione ContextHub** schermata, seleziona **Crea** > **Configurazione archivio ContentHub**

   ![immagine](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Come parte del Feature Pack 4 per AEM 6.5 o del Feature Pack 8 per AEM 6.4, i clienti devono aggiornare `/conf/screens/settings/cloudsettings` a `sling:Folder`.
   >
   >Effettua le seguenti operazioni:
   >
   >1. Passa a CRXDE Liti e quindi a `/conf/screens/settings/cloudsettings`.
   >1. Controlla se `cloudsettings jcr:primaryType` è in `sling:Folder`. Se il `jcr:primaryType` non è in `sling:folder`, procedere ai passaggi successivi.
   >1. Clic con il pulsante destro `/conf/screens/settings` e creare un nodo con *nome* as **`cloudsettings1`** e *Tipo* as **`sling:Folder`** e salva le modifiche.
   >1. Sposta tutti i nodi in `/conf/screens/settings/cloudsettings` a `cloudsettings1`.
   >1. Elimina `cloudsettings` e salva.
   >1. Rinomina `cloudsettings1` a `cloudsettings` e salva.
   >1. Osserva che `/conf/screens/settings/cloudsettings` ha `jcr:primaryType` as `sling:Folder`.
   >
   >Segui questi passaggi in Creazione e pubblicazione prima o dopo l’aggiornamento.

   1. Inserisci il **Titolo** as **Fogli Google**, **Nome store** as **`googlesheets`**, e **Tipo di archivio** as **c`ontexthub.generic-jsonp`** e fai clic su **Successivo**.

      >[!CAUTION]
      >Se si utilizza Adobe Experience Manager (AEM) 6.4, immettere il **Titolo configurazione** as **`googlesheets`** e **Tipo di archivio** as **c`ontexthub.generic-jsonp`**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Immetti la configurazione JSON specifica. Ad esempio, puoi utilizzare il seguente codice json a scopo dimostrativo e selezionare **Salva**. Vedi la configurazione dell’archivio con titolo **Fogli Google** nella configurazione ContextHub.

      >[!IMPORTANT]
      >Assicurati di sostituire il codice con il `*<Sheet ID>*` e `*<API Key>*`, recuperato durante la configurazione dei fogli Google.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      >
      >Nel codice di esempio di cui sopra, **pollInterval** definisce la frequenza di aggiornamento dei valori (in millisecondi).
      >
      >Sostituisci il codice con il `*<Sheet ID>*` e `*<API Key>*`, recuperato durante la configurazione dei fogli Google.

      >[!CAUTION]
      >
      >Se crei le configurazioni dell’archivio dei fogli di Google al di fuori della cartella globale (ad esempio, nella tua cartella di progetto), il targeting non funziona come previsto.

1. **Impostazione della segmentazione dell’archivio**

   1. Accedi a **Configurazione archivio ContentHub** e creare un’altra configurazione di archivio nel contenitore di configurazione di AEM Screens e impostare **Titolo** as **segmentation-contexthub**, **Nome store** as **segmentazione** e **Tipo di archivio** as **aem.segmentation**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Clic **Successivo** e poi **Salva**.

      >[!NOTE]
      >Ignora il processo di definizione del codice JSON e lascialo vuoto.


## Passaggio 3: Impostazione dei segmenti in Audience {#setting-up-audience}

1. **Creazione di segmenti in Audiences**

   1. Passa dall’istanza AEM a **Personalizzazione** > **Tipi di pubblico** > **schermi**.

   1. Clic **Crea** > **Crea un segmento ContextHub.** Il **Nuovo segmento ContextHub** viene visualizzata.

   1. Inserisci il **Titolo** as `**Higherthan50**` e fai clic su **Crea**. Allo stesso modo, crea un altro segmento denominato come `**Lowerthan50**`.

      ![immagine](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Seleziona il segmento `**Higherthan50**` e fai clic su **Proprietà** dalla barra delle azioni.
      ![immagine](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Seleziona la **Personalizzazione** scheda da **Proprietà segmento**. Imposta il **Percorso ContextHub** a `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Percorso segmenti** a `/conf/screens/settings/wcm/segments` e fai clic su **Salva**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Analogamente, impostare **Percorso ContextHub** e **Percorso segmenti** per `**Lowerthan50**` anche il segmento.

## Passaggio 4: configurazione di marchio e area {#setting-brand-area}

Segui i passaggi seguenti per creare un marchio nelle attività e nelle aree sotto il marchio:

1. **Creazione di un marchio nelle attività**

   1. Passa dall’istanza AEM a **Personalizzazione** > **Attività**.

   1. Seleziona **Crea** > **Crea marchio**.

   1. Seleziona **Marchio** dal **Crea pagina** e fai clic su **Successivo**.

   1. Inserisci il **Titolo** as **ScreensBrand** e fai clic su **Crea**. Il brand viene ora creato come mostrato di seguito.

      ![immagine](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Problema noto:
      >Per aggiungere un’area, rimuovi l’elemento principale dall’URL, ad esempio
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creazione di un’area nel marchio**

   Per creare un’area nel brand, segui i passaggi seguenti:

   1. Seleziona **Crea** e poi **Crea area**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Seleziona **Superfici** dal **Crea pagina** procedura guidata e seleziona **Successivo**.

   1. Inserisci il **Titolo** as **ScreensValue** e seleziona **Crea**.
Nel tuo marchio viene creata un’area.

## Passaggio 5: Creazione dei segmenti in un’attività {#step-setting-up-audience-segmentation}

Dopo aver configurato un archivio dati e definito l’attività (marchio e area), segui i passaggi riportati di seguito per creare segmenti nell’attività.

1. **Creazione di segmenti nelle attività**

   1. Passa dall’istanza AEM a **Personalizzazione** > **Attività** > **ScreensBrand** >**ScreensValue**.

   1. Seleziona **Crea** > **Crea attività.** Il **Configurazione guidata attività** viene aperto.

   1. Inserisci il **Titolo** as **ValueCheck50** e **Nome** as **valuecheck50**. Seleziona la **Motore di targeting** as **ContextHub (AEM)** dall’elenco a discesa e seleziona **Successivo**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Seleziona **Aggiungi esperienza** dal `**Configure Activity**` procedura guidata.

   1. Dalla sezione **Tipi di pubblico**, seleziona la `**Higherthan50**` e seleziona **Aggiungi esperienza** e immetti **Titolo** as `**higherthan50**` **Nome** as `**higherthan50**`. Seleziona **Ok**.

   1. Dalla sezione **Tipi di pubblico**, seleziona la `**Lowerthan50**` e seleziona **Aggiungi esperienza** e immetti **Titolo** as `**lowerthan50**` **Nome** as `**lowerthan50**`. Seleziona **Ok**.

   ![immagine](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Seleziona **Successivo** e poi **Salva**. `**ValueCheck50**` L’attività viene ora creata e configurata.

      ![immagine](/help/user-guide/assets/context-hub/context-hub16.png)

## Passaggio 5: modificare i segmenti in Audiences{#editing-audience-segmentation}

1. **Modifica dei segmenti**

   1. Passa dall’istanza AEM a **Personalizzazione** > **Tipi di pubblico** > **schermi**.

   1. Seleziona il segmento `**Higherthan50**`, e seleziona **Modifica** dalla barra delle azioni.

   1. Trascina la **Confronto: Proprietà - Valore** all&#39;editor.

   1. Fai clic sull’icona chiave inglese per aprire **Confronto di una proprietà con un valore** .

   1. Seleziona **googlesheets/value/1/0** dall’elenco a discesa in **Nome proprietà**.

      >[!NOTE]
      > Il **googlesheets/value/1/0** si riferisce alla riga 2 e alla colonna compilate in `google` fogli nella figura seguente:

      ![immagine](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Seleziona la **Operatore** as **maggiore di** dal menu a discesa.

   1. Inserisci il **Valore** as **70**.

      >[!NOTE]
      >
      >L’AEM convalida i dati dal foglio Google mostrando il segmento in verde.

      ![immagine](/help/user-guide/assets/context-hub/context-hub18.png)

   Allo stesso modo, modifica i valori delle proprietà in `**Lowerthan50**`.

   1. Trascina la **Confronto: Proprietà - Valore** all&#39;editor.

   1. Seleziona l’icona chiave inglese.

   1. In **Confronto di una proprietà con un valore** finestra di dialogo, seleziona **googlesheets/value/1/0** dall’elenco a discesa in **Nome proprietà**.

   1. Seleziona la **Operatore** as **less-than** dal menu a discesa.

   1. Inserisci il **Valore** as **50**.


## Abilitazione del targeting nei canali {#step-enabling-targeting-in-channels}

Segui i passaggi seguenti per abilitare il targeting nei tuoi canali.

1. Passa a uno dei canali di AEM Screens. I passaggi seguenti mostrano come abilitare il targeting utilizzando **DataDrivenChannel** creato in un canale AEM Screens.

1. Seleziona il canale **TargetChannel** e fai clic su **Proprietà** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/context-hub/context-hub19.png)

1. Seleziona la **Personalizzazione** in modo da poter impostare le configurazioni ContextHub.

   1. Imposta il **Percorso ContextHub** a `/conf/screens/settings/wcm/segments` e **Percorso segmenti** a `/conf/screens/settings/wcm/segments`.
   1. Imposta marchio su **ScreensBrand** dal menu a discesa e **Imposta riferimento area** a **ScreensValue**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      >
      >Utilizza ContextHub e il percorso Segmenti, dove hai inizialmente salvato le configurazioni e i segmenti dell’hub di contesto.

      ![immagine](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Naviga e seleziona la **TargetChannel** channel e click **Modifica** dalla barra delle azioni.

      >[!NOTE]
      >
      >Se hai impostato tutto correttamente, puoi vedere **Targeting** nell’elenco a discesa dall’editor, come illustrato nella figura riportata di seguito.

      ![immagine](/help/user-guide/assets/context-hub/context-hub21.png)

## Ulteriori informazioni: casi di utilizzo di esempio {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto AEM Screens, puoi seguire i diversi casi d’uso per comprendere in che modo le risorse attivate dai dati svolgono un ruolo fondamentale in diversi settori:

1. **[Attivazione con targeting magazzino vendita al dettaglio](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro di viaggio](local-temperature-activation.md)**
1. **[Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)**
