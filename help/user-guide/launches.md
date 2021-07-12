---
title: Aggiornamento dei contenuti tramite Screens Launch
seo-title: Aggiornamento dei contenuti tramite Screens Launch
description: Gli autori dei contenuti possono creare una versione futura dei canali, nota come Launch, e l’ulteriore impostazione della data di inizio per questo lancio consente al contenuto di essere live nei dispositivi o nei lettori.
seo-description: Gli autori dei contenuti possono creare una versione futura dei canali, nota come Launch, e l’ulteriore impostazione della data di inizio per questo lancio consente al contenuto di essere live nei dispositivi o nei lettori.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: Creazione di schermi, avvii
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 0%

---

# Aggiornamento dei contenuti tramite Screens Launch {#launches}

Gli autori dei contenuti possono creare una versione futura dei canali, noti come **Screens Launch** e impostare ulteriormente la data di inizio del lancio. Questo consente al contenuto di essere live nei dispositivi o nei lettori alla data live specificata.

Con l’aiuto di ***Screens Launch***, gli autori possono visualizzare in anteprima ogni canale del lancio e devono essere in grado di avviare una richiesta di revisione. Il gruppo di approvatori riceverà la notifica e potrà approvare o rifiutare la richiesta. Una volta raggiunta la data di inizio, il contenuto viene riprodotto nei dispositivi.

Ad esempio, se l’autore desidera creare versioni future di c1, c2 (canali), viene creato un lancio e viene impostata una data di inizio (ad esempio, 10 novembre alle 8.00). Eventuali ulteriori aggiornamenti nel contenuto vengono inviati per la revisione.

Una volta approvato e in data dal vivo (10 novembre, 8:00), questo lancio riproduce il contenuto sui dispositivi o lettori.

## Requisiti {#requirements}

Prima di iniziare a utilizzare *Screens Launch* in un progetto AEM Screens, assicurati di comprendere il concetto di periodo di tolleranza e la sua rilevanza.

L&#39;esecuzione di un&#39;esperienza sulla data di inizio impostata sul lettore comporta:

* promozione del lancio (in genere richiede alcuni secondi)

* la pubblicazione delle risorse per pubblicare le istanze (in genere richiede alcuni minuti, a seconda delle dimensioni dei canali o delle risorse che devono essere pubblicate)

* tempo impiegato dall&#39;aggiornamento del contenuto offline per il completamento (in genere richiede alcuni minuti)

* tempo impiegato dai lettori per scaricare il contenuto dall’istanza di pubblicazione (in genere ci vogliono minuti a seconda della larghezza di banda e della dimensione delle risorse da scaricare)

* eventuali differenze di tempo tra il server e il lettore

### Informazioni sul periodo di tolleranza {#understanding-grace-period}

Affinché il lettore possa iniziare a riprodurre il contenuto nella data di inizio impostata, è necessario avviare le attività precedenti prima della data di inizio.

Se la data in tempo reale è *24 nov, 9:00* e il periodo di tolleranza è *24 ore*, la sequenza di azioni di cui sopra inizia a (data in tempo reale - periodo di tolleranza), ovvero il 23 novembre, ore 9:00 del server. Questo offre 24 ore di tempo per completare tutte le azioni di cui sopra e il contenuto raggiungerà i giocatori. I giocatori comprenderanno che si tratta di un contenuto di lancio, quindi il contenuto non verrà riprodotto immediatamente, ma i giocatori memorizzeranno questo contenuto come versione futura e inizieranno a giocare esattamente alla data di inizio impostata sul fuso orario del lettore.

Ad esempio, supponiamo che il server sia in PST e che i dispositivi siano in EST, la differenza di tempo massima è di 3 ore in questo caso e si supponga che la promozione richiederà 1 minuto e che la pubblicazione dall&#39;autore richieda 10 minuti e che il lettore possa scaricare le risorse tipicamente in 10-15 minuti. Quindi periodo di tolleranza = differenza di tempo (3 ore) + tempo per promuovere il lancio (1 min) + tempo per pubblicare il lancio (10 min) + tempo per scaricare al giocatore (10-15 min) + buffer (per essere sicuro, diciamo 30 min) = 3 ore 56 min = 14160 secondi.

Quindi, ogni volta che pianifichiamo un lancio in diretta, la promozione inizierà presto con questo offset. Nell&#39;equazione di cui sopra, la maggior parte degli elementi non richiede molto tempo, possiamo utilizzare una stima decente per questo offset una volta che conosciamo la differenza di tempo massima tra il server e qualsiasi giocatore.

>[!NOTE]
>
>Con l’impostazione predefinita, il periodo di tolleranza per Screens Launch è impostato su 24 ore, il che significa che quando si imposta la data di inizio per un lancio delle risorse in */content/screens*, la promozione inizia con questo offset.

### Aggiornamento del periodo di tolleranza predefinito {#updating-out-of-the-box-grace-period}

Questa sezione spiega come aggiornare un periodo di tolleranza predefinito a 10 minuti.

1. Passa a CRXDE Lite e quindi a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Fai clic con il pulsante destro del mouse e copia il file.
3. Passa a `/apps/system/config` e fai clic con il pulsante destro del mouse e incolla.
4. Fai doppio clic su `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` per aprire il file nell’editor in CRXDE Lite. Deve mostrare il periodo di tolleranza per il percorso */content/screens/* come **86400**. Modifica tale valore in **600**.

Ora il contenuto del file di testo deve essere simile al seguente:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Poiché nell’esempio precedente è stato impostato il periodo di tolleranza su 10 minuti, quando si imposta la data di lancio per qualsiasi lancio per le risorse in */content/screens*, la promozione inizierà con questo offset.

Ad esempio, se la data di inizio è impostata sul 24 novembre, alle 9:00 e il periodo di tolleranza è di 600 secondi, il processo di promozione inizierà il 24 novembre alle 8:50.

## Utilizzo di Screens Launch {#using-launches}

Questa sezione illustra come implementare Screens Launch nel progetto AEM Screens.

### Creazione di un lancio Screens {#creating-a-launch}

Per implementare la funzionalità Launch di Screens nel progetto AEM Screens, effettua le seguenti operazioni:

1. Crea un canale per sequenza nel progetto AEM Screens, ad esempio **LaunchesDemo** —> **Canali** —> **FutureLaunch**, come mostrato di seguito.

   >[!CAUTION]
   >
   >Devi creare un lancio da un canale preesistente nel tuo progetto AEM Screens.

   ![Immagine](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleziona il canale **FutureLaunch** e fai clic su **Crea lancio** dalla barra delle azioni.

   ![Immagine](/help/user-guide/assets/launches-images/launches-12.png)

1. Viene visualizzata la procedura guidata **Crea lancio** . Puoi selezionare il canale già visibile nella procedura guidata oppure fare clic su **+ Aggiungi canali** per aggiungere il canale per il quale desideri creare il lancio.

1. Fai clic su **Avanti** dalla procedura guidata **Crea lancio**. L’opzione **Includi pagine secondarie** è selezionata per impostazione predefinita.

   ![immagine](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Puoi utilizzare l&#39;opzione **+ Aggiungi canali** per aggiungere un altro canale per il quale desideri creare il lancio.

   Per utilizzare l&#39;opzione **Aggiungi canali**, accedi al canale per il quale desideri creare il lancio e fai clic su **Seleziona**.

   L&#39;opzione **Seleziona** verrà disabilitata se tenti di selezionare più canali o una cartella per aggiungere il lancio.

   ![immagine](/help/user-guide/assets/launches-images/launches-14.png)

   Dopo aver selezionato il canale/i canali, fare clic su **Avanti**.


1. Inserisci il **Titolo lancio** come **Promozioni estive** e non è necessario impostare la **Data lancio**, come illustrato nella figura seguente. Fai clic su **Crea**.

   >[!NOTE]
   >
   >*L’abilitazione o* il controllo dell’opzione  **Eredita i** dati live della pagina sorgente consente di creare i canali come Live Copy nel lancio. Se vengono apportate modifiche nel canale originale, queste vengono applicate automaticamente ai canali di lancio.
   >
   >
   >*La disattivazione o* **la deselezione dei** dati live della pagina di origine Eredita consente di copiare i canali senza alcuna relazione live nel lancio. Pertanto, se vengono apportate modifiche al canale originale, tali modifiche non vengono applicate ai canali di lancio.

   ![Immagine](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >In questo passaggio puoi impostare la data del lancio live oppure configurarla in un secondo momento mentre modifichi le proprietà del lancio una volta creato.

   **Ambito della promozione Launch**

   * **Promuovi il lancio** completo: Tutti i canali del lancio vengono promossi alla data di pubblicazione impostata.
   * **Promuovi pagine** modificate: Verranno promosse solo le risorse di lancio modificate. Si consiglia di utilizzare questa opzione quando non è richiesta la revisione del lancio.
   * **Promuovi pagine** approvate: Questa opzione richiede l’esecuzione del flusso di lavoro di approvazione del lancio sui canali di lancio. Solo le pagine approvate verranno promosse alla data di attivazione impostata.

      >[!CAUTION]
      >
      >La data in tempo reale di Launch rispetta il fuso orario del lettore/dispositivo anziché quello del server.

1. Il lancio verrà creato. Puoi fare clic su **Apri** per visualizzare le pagine nell&#39;editor oppure fare clic su **Fine** per tornare al progetto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Facendo clic su **Fine** è possibile tornare al canale **FutureLaunch**.

   ![Immagine](/help/user-guide/assets/launches-images/launches-16.png)


### Modifica delle proprietà di Launch per impostare la data e l’ambito live {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Dopo aver creato il lancio, puoi aggiornare le proprietà come data di lancio, titolo del lancio e ambito di promozione utilizzando **Proprietà lancio**.

* **Data lancio**: si riferisce alla data in tempo reale, ovvero alla data o all’ora in cui il contenuto verrà riprodotto nel lettore Screens in base al fuso orario del lettore.
* **Production Ready** consente di pubblicare i canali dopo la promozione di questi, impostazione predefinita abilitata, quindi non è necessario apportare modifiche.
* **Ambito**: determina quali canali verranno promossi durante la promozione del lancio.


Per modificare le proprietà del lancio, effettua le seguenti operazioni:

1. Passa al canale **FutureLaunch**, *(ovvero il lancio in sospeso)* e seleziona il canale, come mostrato nella figura seguente.

   ![immagine](/help/user-guide/assets/launches-images/launches-17.png)

1. Fai clic su **Dashboard** dalla barra delle azioni e vedrai il pannello **LANCI IN ATTESA** dal dashboard del canale.

   ![immagine](/help/user-guide/assets/launches-images/launches-18.png)

1. Seleziona il lancio e fai clic su **Proprietà lancio** dal pannello **LANCI IN ATTESA**.

   ![immagine](/help/user-guide/assets/launches-images/launches-19.png)

### Modifica del lancio di Screens per aggiungere o rimuovere canali  {#editing-the-screens-launch-to-add-or-remove-channels}

Dopo aver creato il lancio, puoi aggiungere o rimuovere canali al lancio esistente utilizzando l&#39;opzione **Modifica lancio**.

Al termine, fai clic su **Salva** per tornare al canale **FutureLaunch**.

### Promozione manuale del lancio di Screens{#promote-the-screens-launch-manually}

Puoi promuovere il lancio manualmente utilizzando l&#39;opzione **Promuovi lancio** dal pannello **LANCI IN ATTESA** .

Puoi scegliere le risorse da promuovere come parte di questa promozione manuale nella **Promozione guidata Launch**.

![immagine](/help/user-guide/assets/launches-images/launches-e.png)

1. Puoi abilitare o disabilitare l’opzione per eliminare il lancio dopo la produzione.
1. Puoi impostare **Ambito** del lancio, con le seguenti opzioni:
   1. **Promuovi il lancio** completo: Tutti i canali del lancio vengono promossi alla data di pubblicazione impostata.
   1. **Promuovi pagine** modificate: Verranno promosse solo le risorse di lancio modificate. Si consiglia di utilizzare questa opzione quando non è richiesta la revisione del lancio.
   1. **Promuovi pagine** approvate: Questa opzione richiede l’esecuzione del flusso di lavoro di approvazione del lancio sui canali di lancio. Solo le pagine approvate verranno promosse alla data di attivazione impostata.
   1. **Promuovi la pagina** corrente: Questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito solo per la pagina corrente.
1. Fai clic su **Avanti** nella procedura guidata **Promuovi lancio**.
1. Fai clic su **Promuovi** per promuovere il lancio.

### Eliminazione di Screens Launch {#deleting-the-screens-launch}

Puoi eliminare il lancio utilizzando l’opzione **Elimina lancio** dal pannello **LANCI IN SOSPESO** .

>[!CAUTION]
>
>Questa azione eliminerà anche tutti i discendenti (lanci nidificati).
