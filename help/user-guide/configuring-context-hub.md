---
title: Configurazione di ContextHub in AEM Screens
description: Scopri ContextHub nel motore di targeting per definire un archivio dati per la modifica del contenuto dell’attivatore dei dati.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 1%

---

# Configurazione di ContextHub in AEM Screens {#configuring-contexthub-in-aem-screens}

In questa sezione viene posto l’accento sulla creazione e la gestione delle modifiche alle risorse basate sui dati tramite un archivio dati.

## Termini chiave {#key-terms}

Prima di entrare nei dettagli della creazione e della gestione dei canali basati sull’inventario nel progetto AEM Screens, scopri alcuni dei termini chiave dei diversi scenari.

**Marchio** - Descrizione del progetto di alto livello.

**Area** - Il nome del progetto AEM Screens, ad esempio Digital Ad Signage

**Attività** - Definisce le regole di categoria, ad esempio Basate su inventario, Meteo o Basate sulla disponibilità del reparto.

**Pubblico** - Definisce la regola.

**Segmento**: versione di una risorsa da riprodurre per la regola specificata. Ad esempio, se la temperatura è inferiore a 50 gradi Fahrenheit, sullo schermo viene visualizzata l’immagine di una bevanda calda, altrimenti di una bevanda fredda.

Il diagramma seguente fornisce una rappresentazione visiva del modo in cui le configurazioni di ContextHub coincidono con attività, pubblico e canali.

![schermata_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Precondizioni {#preconditions}

Prima di iniziare a configurare le configurazioni ContextHub per un progetto AEM Screens, imposta i fogli Google (a scopo dimostrativo).

>[!IMPORTANT]
>
>Nell’esempio seguente, i fogli di Google vengono utilizzati come database di esempio dal quale vengono recuperati i valori, a scopo puramente didattico. L’Adobe non prevede l’utilizzo di Google Sheets per ambienti di produzione.
>
>Per ulteriori informazioni, consulta [Ottenere la chiave API](https://developers.google.com/maps/documentation/javascript/get-api-key) nella documentazione di Google.

## Passaggio 1: configurazione di un archivio dati {#step-setting-up-a-data-store}

È possibile impostare l&#39;archivio dati come evento di I/O locale o come evento di database locale.

L’esempio seguente, relativo ai trigger di dati a livello di risorsa, mostra un evento di database locale. L’evento configura un archivio dati, ad esempio un foglio Excel, che consente di utilizzare le configurazioni ContextHub e il percorso dei segmenti per il canale AEM Screens.

Dopo aver configurato correttamente il foglio `google`, come illustrato nell&#39;esempio seguente:

![immagine](/help/user-guide/assets/context-hub/context-hub1.png)

La convalida seguente è quella visualizzata quando si controlla la connessione immettendo i due valori `*google sheet ID*` e `*API key*` nel formato seguente:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![immagine](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>L’esempio specifico seguente mostra i fogli di Google come archivio dati che attiva una modifica della risorsa se il valore è maggiore di 100 o minore di 50.

## Passaggio 2: configurazione dell’archivio {#step-setting-store-configurations}

1. **Accesso a ContextHub**

   Passa all’istanza AEM e fai clic sull’icona Strumenti nella barra laterale a sinistra. Fai clic su **Sites** > **ContextHub**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Creazione di una configurazione archivio ContextHub**

   1. Passa al contenitore di configurazione con titolo **schermate**.

   1. Fai clic su **Crea** > **Crea contenitore configurazione** e immetti il titolo come **ContextHubDemo**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Passa** a **ContextHubDemo** > **Crea** **Configurazione ContentHub** e fai clic su **Salva**.

      >[!NOTE]
      > Dopo aver fatto clic su **Salva**, sei nella schermata **Configurazione ContextHub**.

   1. Dalla schermata **Configurazione ContextHub**, fai clic su **Crea** > **Configurazione archivio ContentHub**

   ![immagine](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Come parte del Feature Pack 4 per AEM 6.5 o del Feature Pack 8 per AEM 6.4, i clienti devono aggiornare `/conf/screens/settings/cloudsettings` a `sling:Folder`.
   >
   >Effettua le seguenti operazioni:
   >
   >1. Passare a CRXDE Lite e quindi a `/conf/screens/settings/cloudsettings`.
   >1. Verifica se `cloudsettings jcr:primaryType` si trova in `sling:Folder`. Se `jcr:primaryType` non è in `sling:folder`, procedere con i passaggi successivi.
   >1. Fare clic con il pulsante destro del mouse su `/conf/screens/settings`, creare un nodo con *name* come **`cloudsettings1`** e *Type* come **`sling:Folder`** e salvare le modifiche.
   >1. Sposta tutti i nodi in `/conf/screens/settings/cloudsettings` in `cloudsettings1`.
   >1. Elimina `cloudsettings` e salva.
   >1. Rinomina `cloudsettings1` in `cloudsettings` e salva.
   >1. Osservare che `/conf/screens/settings/cloudsettings` ha `jcr:primaryType` come `sling:Folder`.
   >
   >Segui questi passaggi in Author e Publish prima o dopo l’aggiornamento.

   1. Immetti il **Titolo** come **Fogli Google**, **Nome archivio** come **`googlesheets`** e **Tipo archivio** come **c`ontexthub.generic-jsonp`** e fai clic su **Avanti**.

      >[!CAUTION]
      >Se si utilizza Adobe Experience Manager (AEM) 6.4, immettere **Titolo configurazione** come **`googlesheets`** e **Tipo archivio** come **c`ontexthub.generic-jsonp`**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Immetti la configurazione JSON specifica. Ad esempio, puoi utilizzare il seguente codice JSON a scopo dimostrativo e fare clic su **Salva**. Nella configurazione ContextHub è presente la configurazione dell&#39;archivio con titolo **Fogli Google**.

      >[!IMPORTANT]
      >Assicurarsi di sostituire il codice con `*<Sheet ID>*` e `*<API Key>*` recuperati durante la configurazione dei fogli di Google.

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
      >Nel codice di esempio precedente, **pollInterval** definisce la frequenza di aggiornamento dei valori (in millisecondi).
      >
      >Sostituisci il codice con `*<Sheet ID>*` e `*<API Key>*` recuperati durante la configurazione dei fogli di Google.

      >[!CAUTION]
      >
      >Se crei i fogli Google per memorizzare le configurazioni al di fuori della cartella globale (ad esempio, nella tua cartella di progetto), il targeting non funziona come previsto.

1. **Impostazione della segmentazione dell&#39;archivio**

   1. Passa a **Configurazione archivio ContentHub** e crea un&#39;altra configurazione archivio nel contenitore di configurazione AEM Screens e imposta **Titolo** come **segmentation-contexthub**, **Nome archivio** come **segmentation** e **Tipo archivio** come **aem.segmentation**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Fai clic su **Avanti** e quindi su **Salva**.

      >[!NOTE]
      >Ignora il processo di definizione del codice JSON e lascialo vuoto.


## Passaggio 3: Impostazione dei segmenti in Audience {#setting-up-audience}

1. **Creazione di segmenti in tipi di pubblico**

   1. Passa dall&#39;istanza AEM a **Personalization** > **Tipi di pubblico** > **Schermi**.

   1. Fai clic su **Crea** > **Crea segmento ContextHub.** Viene visualizzata la finestra di dialogo **Nuovo segmento ContextHub**.

   1. Immetti **Titolo** come `**Higherthan50**` e fai clic su **Crea**. Allo stesso modo, crea un altro segmento con titolo `**Lowerthan50**`.

      ![immagine](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Fai clic sul segmento `**Higherthan50**` e fai clic su **Proprietà** nella barra delle azioni.

      ![immagine](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Fai clic sulla scheda **Personalization** dalle **Proprietà segmento**. Imposta **Percorso ContextHub** su `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Percorso segmenti** su `/conf/screens/settings/wcm/segments` e fai clic su **Salva**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Analogamente, impostare **Percorso ContextHub** e **Percorso segmenti** anche per il segmento `**Lowerthan50**`.

## Passaggio 4: configurazione di marchio e area {#setting-brand-area}

Segui i passaggi seguenti per creare un marchio nelle attività e nelle aree sotto il marchio:

1. **Creazione di un marchio nelle attività**

   1. Passa dall&#39;istanza AEM a **Personalization** > **Attività**.

   1. Fai clic su **Crea** > **Crea marchio**.

   1. Fare clic su **Marchio** dalla procedura guidata **Crea pagina** e fare clic su **Avanti**.

   1. Immetti **Titolo** come **ScreensBrand** e fai clic su **Crea**. Il brand viene ora creato come mostrato di seguito.

      ![immagine](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Problema noto:
      >Per aggiungere un’area, rimuovi l’elemento principale dall’URL, ad esempio
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Creazione di un&#39;area nel tuo marchio**

   Per creare un’area nel brand, segui i passaggi seguenti:

   1. Fare clic su **Crea** e quindi su **Crea area**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Fare clic su **Area** dalla procedura guidata **Crea pagina** e fare clic su **Avanti**.

   1. Immetti **Titolo** come **ValoreSchermi** e fai clic su **Crea**.
Nel tuo marchio viene creata un’area.

## Passaggio 5: Creazione dei segmenti in un’attività {#step-setting-up-audience-segmentation}

Dopo aver configurato un archivio dati e definito l’attività (marchio e area), segui i passaggi riportati di seguito per creare segmenti nell’attività.

1. **Creazione di segmenti nelle attività**

   1. Passa dall&#39;istanza AEM a **Personalization** > **Attività** > **ScreensBrand** >**ScreensValue**.

   1. Fai clic su **Crea** > **Crea attività.** Viene aperta la **Configurazione guidata attività**.

   1. Immetti il **Titolo** come **ValueCheck50** e **Nome** come **valuecheck50**. Fai clic sul **motore di targeting** come **ContextHub (AEM)** dal menu a discesa e fai clic su **Avanti**.

      ![immagine](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Fare clic su **Aggiungi esperienza** dalla procedura guidata `**Configure Activity**`.

   1. Da **Tipi di pubblico**, fai clic su `**Higherthan50**`, quindi su **Aggiungi esperienza** e immetti **Titolo** come `**higherthan50**` **Nome** come `**higherthan50**`. Fare clic su **Ok**.

   1. Da **Tipi di pubblico**, fai clic su `**Lowerthan50**`, quindi su **Aggiungi esperienza** e immetti **Titolo** come `**lowerthan50**` **Nome** come `**lowerthan50**`. Fare clic su **Ok**.

   ![immagine](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Fai clic su **Avanti** e quindi su **Salva**. L&#39;attività `**ValueCheck50**` è stata creata e configurata.

      ![immagine](/help/user-guide/assets/context-hub/context-hub16.png)

## Passaggio 5: modificare i segmenti in Audiences{#editing-audience-segmentation}

1. **Modifica dei segmenti**

   1. Passa dall&#39;istanza AEM a **Personalization** > **Tipi di pubblico** > **Schermi**.

   1. Fai clic sul segmento `**Higherthan50**` e fai clic su **Modifica** nella barra delle azioni.

   1. Trascina e rilascia il componente **Comparison: Property - Value** nell&#39;editor.

   1. Fare clic sull&#39;icona chiave inglese per aprire la finestra di dialogo **Confronto di una proprietà con il valore**.

   1. Fare clic su **googlesheets/value/1/0** dal menu a discesa in **Nome proprietà**.

      >[!NOTE]
      > I **fogli di Google Analytics/value/1/0** fanno riferimento alla riga 2 e alla colonna compilate in `google` fogli nella figura seguente:

      ![immagine](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Fare clic su **Operatore** come **maggiore di** dal menu a discesa.

   1. Immetti **Valore** come **70**.

      >[!NOTE]
      >
      >L’AEM convalida i dati dal foglio Google mostrando il segmento in verde.

      ![immagine](/help/user-guide/assets/context-hub/context-hub18.png)

   Analogamente, modificare i valori della proprietà in `**Lowerthan50**`.

   1. Trascina e rilascia il componente **Comparison: Property - Value** nell&#39;editor.

   1. Fai clic sull’icona a forma di chiave inglese.

   1. Nella finestra di dialogo **Confronto di una proprietà con valore**, fare clic su **googlesheets/value/1/0** dall&#39;elenco a discesa in **Nome proprietà**.

   1. Fare clic su **Operatore** come **minore di** dal menu a discesa.

   1. Immetti **Valore** come **50**.


## Abilitazione del targeting nei canali {#step-enabling-targeting-in-channels}

Segui i passaggi seguenti per abilitare il targeting nei tuoi canali.

1. Passa a uno dei canali di AEM Screens. Nei passaggi seguenti viene illustrato come abilitare il targeting utilizzando **DataDrivenChannel** creato in un canale AEM Screens.

1. Fai clic sul canale **TargetChannel** e fai clic su **Proprietà** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/context-hub/context-hub19.png)

1. Fai clic sulla scheda **Personalization** per configurare le configurazioni di ContextHub.

   1. Impostare **Percorso ContextHub** su `/conf/screens/settings/wcm/segments` e **Percorso segmenti** su `/conf/screens/settings/wcm/segments`.
   1. Imposta brand su **ScreensBrand** dal menu a discesa e **Imposta riferimento area** su **ScreensValue**.

   1. Fai clic su **Salva e chiudi**.

      >[!NOTE]
      >
      >Utilizza ContextHub e il percorso Segmenti, dove hai inizialmente salvato le configurazioni e i segmenti ContextHub.

      ![immagine](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Passa al canale **TargetChannel** e fai clic su **Modifica** nella barra delle azioni.

      >[!NOTE]
      >
      >Se hai impostato tutto correttamente, puoi visualizzare l&#39;opzione **Targeting** nell&#39;elenco a discesa dall&#39;editor, come illustrato nella figura seguente.

      ![immagine](/help/user-guide/assets/context-hub/context-hub21.png)

## Ulteriori informazioni: casi di utilizzo di esempio {#learn-more-example-use-cases}

Dopo aver configurato ContextHub per il progetto AEM Screens, puoi seguire i diversi casi d’uso per comprendere in che modo le risorse attivate dai dati svolgono un ruolo fondamentale in diversi settori:

1. **[Attivazione con targeting inventario vendita al dettaglio](retail-inventory-activation.md)**
1. **[Attivazione temperatura centro di viaggio](local-temperature-activation.md)**
1. **[Attivazione prenotazione ospitalità](hospitality-reservation-activation.md)**
