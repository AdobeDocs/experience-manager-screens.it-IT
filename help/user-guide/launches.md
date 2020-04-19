---
title: Aggiornamento dei contenuti tramite il lancio dello schermo
seo-title: Aggiornamento dei contenuti tramite il lancio dello schermo
description: Gli autori dei contenuti possono creare versioni future dei canali, noti come Launch, e l'ulteriore impostazione della data di inizio per il lancio consente al contenuto di essere live nei dispositivi o lettori.
seo-description: Gli autori dei contenuti possono creare versioni future dei canali, noti come Launch, e l'ulteriore impostazione della data di inizio per il lancio consente al contenuto di essere live nei dispositivi o lettori.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
translation-type: tm+mt
source-git-commit: 9cc4b31ecd66530a85a7a526e306faf1ec371b2e

---


# Aggiornamento dei contenuti tramite il lancio dello schermo {#launches}

Gli autori dei contenuti possono creare una versione futura dei canali, nota come lancio **** delle schermate, e l&#39;ulteriore impostazione della data di inizio per questo lancio consente al contenuto di essere live nei dispositivi o lettori.

Con l’aiuto di una pubblicazione futura, gli autori possono visualizzare l’anteprima di ogni canale nel lancio e devono essere in grado di avviare una richiesta di revisione. Il gruppo di approvatori riceve la notifica e può approvare o rifiutare la richiesta. Quando viene raggiunta la data di inizio, il contenuto viene riprodotto nei dispositivi.

Ad esempio, se l’autore desidera creare versioni future di c1, c2 (canali), viene creato un lancio e viene impostata una data dal vivo (ad esempio, 10 novembre 8:00 AM). Eventuali ulteriori aggiornamenti nel contenuto vengono inviati per la revisione. Una volta approvato e in data dal vivo (10 novembre, 8:00 AM), questo lancio riproduce il contenuto sui dispositivi o lettori.

## Requisiti {#requirements}

Prima di avviare l’implementazione della pubblicazione futura in un progetto AEM Screens, verifica di comprendere il concetto di periodo di tolleranza e la sua rilevanza.

Nella sezione seguente viene illustrato il periodo di tolleranza e come configurarlo come out-of-the-box. Potete anche scaricare una configurazione di prova di esempio per comprenderne l’utilizzo.

### Periodo di tolleranza {#understanding-grace-period}

La seguente configurazione consente all’amministratore di configurare il periodo ***di*** tolleranza, richiesto per la pubblicazione futura.

**Periodo** di tolleranza, include:

* promozione del lancio
* pubblicazione delle risorse per pubblicare le istanze
* tempo impiegato dai dispositivi per scaricare il contenuto dall’istanza di pubblicazione e le eventuali differenze di ora del server e del lettore

Ad esempio, supponiamo che il server sia in PST e che i dispositivi siano in EST, la differenza di tempo massima è di 3 ore in questo caso e che la promozione richieda 1 minuto e che la pubblicazione dall&#39;autore richieda 10 minuti e che il lettore possa scaricare le risorse in genere tra 10-15 minuti. Quindi periodo di tolleranza = differenza di tempo (3 ore) + tempo per promuovere il lancio (1 min) + tempo per pubblicare il lancio (10 min) + tempo per scaricare al lettore (10-15 min) + buffer (per essere sicuro, ad esempio 30 min) = 3 ore 56 min = 14160 secondi. Per cui, quando programmeremo un lancio live, la promozione inizierà presto con questo offset. Nell&#39;equazione di cui sopra, la maggior parte degli elementi non richiede molto tempo, possiamo utilizzare una stima decente per questo offset una volta che conosciamo la differenza di tempo max b/w il server e qualsiasi giocatore.

### Configurazione del periodo di tolleranza out-of-the-box {#configuring-out-of-the-box-grace-period}

In dotazione, il periodo di tolleranza per un lancio è impostato su 24 ore, il che significa che quando si imposta la data dal vivo per qualsiasi avvio per le risorse in */content/screens*, la promozione inizierà con questo offset. Ad esempio, se liveDate è impostato su nov 24, 9:00 AM e il periodo di tolleranza è di 24 ore, il processo di promozione inizierà a novembre 23, 09:00 AM.

### Download delle configurazioni {#downloading-configurations}

Scaricate le seguenti configurazioni di test:

[Ottieni file](assets/launches_event_handlerconfig-10.zip)

>[!NOTE]
>
>La configurazione di cui sopra ha 600 secondi come periodo di tolleranza in questa configurazione di test.

#### Aggiornamento delle configurazioni {#updating-the-configurations}

Se desiderate modificare la configurazione precedente, seguite le istruzioni riportate di seguito:

* create il file ***sling:OsgiConfig/ nt:file in /apps/system/config*** con nome **com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config** e contenuto

   *launches.eventhandler.updatelastmodified=B&quot;false&quot;launches.eventhandler.launch.Promotion.graceperiod=[&quot;/content/screens(/.*):600&quot;]launches.eventhandler.threadpool.maxsize=I&quot;5&quot;launches.eventhandler.threadpool.priority=&quot;MIN&quot;*

* `launches.eventhandler.launch.promotion.graceperiod=["/content/screens(/.&#42;):600"`, consente di impostare un periodo di tolleranza di 600 secondi nel percorso */contenuto/schermi*.

Questo significa che quando imposti una data di inizio per qualsiasi lancio per le risorse sotto */content/screens*, la promozione inizierà con questo offset. Ad esempio, se la data di inizio è impostata su 24 novembre, 9:00 AM e il periodo di tolleranza è di 600 secondi, il processo di promozione inizierà il 24 novembre, 8:50 AM.

## Utilizzo del lancio dello schermo {#using-launches}

Segui la sezione seguente per implementare i lanci nel progetto AEM Screens. Questa sezione illustra i seguenti argomenti:

1. **Creazione di un lancio dello schermo**
1. **Modifica di un lancio di schermate per impostare data e ambito live**

### Creazione di un lancio dello schermo {#creating-a-launch}

Per implementare la funzionalità di avvio nel progetto AEM Screens, procedi come segue:

1. Crea un canale di sequenza nel progetto AEM Screens, ad esempio **LaunchesDemo** —> **Channels** —> **FutureLaunch**, come mostrato di seguito.

   >[!CAUTION]
   >
   >È necessario creare un lancio da un canale preesistente nel progetto AEM Screens.

   ![Immagine](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleziona il canale **FutureLaunch** e fai clic su **Crea lancio** nella barra delle azioni.

   ![Immagine](/help/user-guide/assets/launches-images/launches-12.png)

1. Viene aperta la procedura guidata **Crea lancio** . Potete selezionare il canale già visibile nella procedura guidata oppure fare clic su **+ Aggiungi canali** per aggiungere il canale per il quale desiderate creare il lancio.


#### Utilizzo del canale esistente {#existing-channel-launch}

1. Selezionate il canale già esistente nella procedura guidata **Crea lancio** e fate clic su **Avanti**.

   ![image](/help/user-guide/assets/launches-images/launches-b.png)

1. Selezionate il canale e fate clic su **Avanti** dalla barra delle azioni.

   >[!NOTE]
   >**Per impostazione predefinita, l’opzione Includi sottopagine** è selezionata.

   ![Immagine](/help/user-guide/assets/launches-images/launches-b.png)

1. Inserisci il Titolo **del** lancio come **EstatePromozioni** e non è necessario impostare la Data **del** lancio, come illustrato nella figura riportata di seguito. Fai clic su **Crea**.

   >[!NOTE]
   >
   >*Abilitando o selezionando* l’opzione **Eredita dati** live della pagina di origine, i canali possono essere creati come Live Copy nel lancio. Se vengono apportate modifiche al canale originale, tali modifiche vengono applicate automaticamente ai canali di avvio.
   >
   >
   >*Disattivando o deselezionando* Eredita dati **dal vivo della pagina** di origine, i canali possono essere copiati senza alcuna relazione dal vivo all’avvio. Pertanto, se vengono apportate modifiche al canale originale, tali modifiche non vengono applicate ai canali di lancio.

   ![Immagine](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >In questo passaggio potete impostare la data del lancio live o impostarla in seguito mentre modificate le proprietà del lancio una volta che è già stato creato.

1. Il lancio verrà creato. Potete fare clic su **Apri** per visualizzare le pagine nell’editor oppure su **Fine** per tornare al progetto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Facendo clic su **Fine** puoi tornare al canale **FutureLaunch** .

   ![Immagine](/help/user-guide/assets/launches-images/launches-16.png)


#### Utilizzo dell’opzione Aggiungi canali {#add-channel-launch}

1. Fate clic su **+ Aggiungi canali** per aggiungere il canale per il quale desiderate creare il lancio.

   ![image](/help/user-guide/assets/launches-images/launches-13.png)

   >[!NOTE]
   >Se tentate di selezionare più canali o una cartella per l’aggiunta del lancio, l’opzione **Seleziona** verrà disattivata.

1. Andate al canale per il quale desiderate creare il lancio e fate clic su **Seleziona**.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

1. Ora puoi selezionare il canale aggiunto per creare un lancio e fare clic su **Avanti**.

   ![image](/help/user-guide/assets/launches-images/launches-15.png)

1. Inserisci il Titolo **del** lancio come **EstatePromozioni** e non è necessario impostare la Data **del** lancio, come illustrato nella figura riportata di seguito. Fai clic su **Crea**.

   >[!NOTE]
   >
   >*Abilitando o selezionando* l’opzione **Eredita dati** live della pagina di origine, i canali possono essere creati come Live Copy nel lancio. Se vengono apportate modifiche al canale originale, tali modifiche vengono applicate automaticamente ai canali di avvio.
   >
   >
   >*Disattivando o deselezionando* Eredita dati **dal vivo della pagina** di origine, i canali possono essere copiati senza alcuna relazione dal vivo all’avvio. Pertanto, se vengono apportate modifiche al canale originale, tali modifiche non vengono applicate ai canali di lancio.

   ![Immagine](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >In questo passaggio potete impostare la data del lancio live o impostarla in seguito mentre modificate le proprietà del lancio una volta che è già stato creato.

1. Il lancio verrà creato. Potete fare clic su **Apri** per visualizzare le pagine nell’editor oppure su **Fine** per tornare al progetto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Facendo clic su **Fine** puoi tornare al canale **FutureLaunch** .

   ![Immagine](/help/user-guide/assets/launches-images/launches-16.png)

### Modifica delle proprietà del lancio per impostare la data e l&#39;ambito di attività {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Dopo aver creato il lancio, è necessario modificare le proprietà del lancio per impostare la data in diretta con l’ambito del lancio.

Per modificare le proprietà del lancio, effettuate le seguenti operazioni:

1. Andate al canale **FutureLaunch**, *(ovvero il lancio in sospeso)* e selezionate il canale, come mostrato nella figura seguente.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Fate clic sul **dashboard** dalla barra delle azioni e visualizzate il pannello AVVII **** IN SOSPESO dal dashboard del canale.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Selezionate il lancio e fate clic sulle azioni desiderate nel pannello **LANCI** IN ATTESA.

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

1. Ad esempio, fai clic su Proprietà **** lancio per modificare le proprietà per il lancio **SummerPromotions**.

   ![image](/help/user-guide/assets/launches-images/launches-20.png)

1. Potete modificare il Titolo **** lancio e compilare i campi seguenti:

   * Seleziona la data di **avvio**
   * Verifica **produzione pronta**
   * Seleziona pagine **approvate** Promote da **ambito**
   **Informazioni sulle voci Lanci in Promozione automatica:**

   * **Data** lancio, si riferisce alla data in cui il contenuto viene riprodotto nel lettore Screens, ovvero alla data/ora in base al fuso orario del lettore.
   * **Production Ready** consente di promuovere i canali e di utilizzare il lancio.
   * **Ambito**, si riferisce ai canali che possono essere promossi durante un lancio.
   Sono disponibili le tre opzioni seguenti per impostare l&#39;ambito:

   * **Promuovi lancio** completo: Tutti i canali del lancio vengono promossi alla data impostata.
   * **Promuovi pagine** modificate: Verranno promosse solo le risorse di lancio modificate. Si consiglia di utilizzare questa opzione quando la revisione del lancio non è obbligatoria. Consente di promuovere le modifiche nei canali di lancio.
   * **Promuovi pagine** approvate: Solo le pagine approvate vengono promosse alla data di disponibilità impostata.

      >[!CAUTION]
      >
      >La promozione di avvio rispetta il fuso orario del lettore/dispositivo anziché quello del server.



1. Fai clic su **Salva e chiudi** per tornare al canale **FutureLaunch** .

