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
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 0%

---


# Aggiornamento dei contenuti tramite il lancio dello schermo {#launches}

Gli autori dei contenuti possono creare versioni future dei canali, noti come lancio **** delle schermate, e impostare ulteriormente la data di inizio del lancio. Questo consente al contenuto di essere live nei dispositivi o lettori alla data di trasmissione specificata.

Con l&#39;aiuto di ***Screens Launch***, gli autori possono visualizzare l&#39;anteprima di ogni canale nel lancio e possono avviare una richiesta di revisione. Il gruppo di approvatori riceve la notifica e può approvare o rifiutare la richiesta. Quando viene raggiunta la data di inizio, il contenuto viene riprodotto nei dispositivi.

Ad esempio, se l’autore desidera creare versioni future di c1, c2 (canali), viene creato un lancio e viene impostata una data dal vivo (ad esempio, 10 novembre 8:00 AM). Eventuali ulteriori aggiornamenti nel contenuto vengono inviati per la revisione.

Una volta approvato e in data dal vivo (10 novembre, 8:00 AM), questo lancio riproduce il contenuto sui dispositivi o lettori.

## Requisiti {#requirements}

Prima di iniziare a utilizzare *Screens Launch* in un progetto AEM Screens , assicurati di comprendere il concetto di periodo di tolleranza e la sua rilevanza.

L&#39;esecuzione di un&#39;esperienza sulla data live impostata sul lettore comporta:

* promozione del lancio (in genere richiede alcuni secondi)

* la pubblicazione delle risorse per pubblicare le istanze (in genere richiede alcuni minuti, a seconda delle dimensioni dei canali o delle risorse da pubblicare)

* tempo impiegato dall&#39;aggiornamento del contenuto offline per il completamento (in genere richiede alcuni minuti)

* il tempo impiegato dai lettori per scaricare il contenuto dall’istanza di pubblicazione (in genere, il tempo richiesto dipende dalla larghezza di banda e dalla dimensione delle risorse da scaricare)

* eventuali differenze di tempo tra il server e il lettore

### Periodo di tolleranza {#understanding-grace-period}

Affinché il lettore possa iniziare a riprodurre il contenuto nella data di inizio impostata, è necessario avviare le attività precedenti prima della data di inizio.

Se la data in diretta è il 24 *novembre, le 9:00 AM* e il periodo di tolleranza è di *24 ore*, la sequenza di azioni di cui sopra inizierà a (data in diretta - periodo di tolleranza), vale a dire il 23 novembre, ore 9:00 del server. Questo offre 24 ore di tempo per completare tutte le azioni di cui sopra e il contenuto raggiungerà i giocatori. I giocatori comprenderanno che si tratta di un contenuto del lancio, quindi il contenuto non verrà riprodotto immediatamente, ma i giocatori memorizzeranno il contenuto come versione futura e inizieranno a giocare esattamente alla data dal vivo impostata sul fuso orario del giocatore.

Ad esempio, supponiamo che il server sia in PST e che i dispositivi siano in EST, la differenza di tempo massima è di 3 ore in questo caso e che la promozione richieda 1 minuto e che la pubblicazione dall&#39;autore richieda 10 minuti e che il lettore possa scaricare le risorse in genere tra 10-15 minuti. Quindi periodo di tolleranza = differenza di tempo (3 ore) + tempo per promuovere il lancio (1 min) + tempo per pubblicare il lancio (10 min) + tempo per scaricare al lettore (10-15 min) + buffer (per essere sicuro, ad esempio 30 min) = 3 ore 56 min = 14160 secondi.

Quindi, ogni volta che pianifichiamo un lancio live, la promozione inizierà presto con questo offset. Nell&#39;equazione di cui sopra, la maggior parte degli elementi non richiede molto tempo, possiamo utilizzare una stima decente per questo offset una volta che conosciamo la differenza di tempo massima tra il server e qualsiasi giocatore.

>[!NOTE]
>
>Il periodo di tolleranza previsto per il lancio dello schermo è impostato su 24 ore, il che significa che quando si imposta la data dal vivo per qualsiasi avvio per le risorse in */content/screens*, la promozione inizierà con questo offset.

### Aggiornamento del periodo di tolleranza out-of-the-box {#updating-out-of-the-box-grace-period}

In questa sezione viene illustrato come aggiornare un periodo di tolleranza predefinito a 10 minuti.

1. Passate al CRXDE Lite e quindi a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Fare clic con il pulsante destro del mouse e copiare il file.
3. Passate a fare clic con il pulsante destro del mouse `/apps/system/config` e incollare.
4. Fate doppio clic su `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` per aprire il file nell&#39;editor in CRXDE Lite. Deve mostrare il periodo di tolleranza per il percorso */contenuto/schermate/* come **86400**. Modificate tale valore in **600**.

Ora il contenuto del file di testo deve essere simile al seguente:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Poiché nell’esempio precedente è stato impostato il periodo di tolleranza su 10 minuti, quando si imposta la data di inizio per qualsiasi avvio per le risorse in */content/screens*, la promozione inizierà con questo offset.

Ad esempio, se la data di inizio è impostata su 24 novembre, 9:00 AM e il periodo di tolleranza è di 600 secondi, il processo di promozione inizierà il 24 novembre alle 08:50.

## Utilizzo del lancio dello schermo {#using-launches}

In questa sezione viene illustrato come implementare il lancio delle schermate nel progetto AEM Screens .

### Creazione di un lancio dello schermo {#creating-a-launch}

Per implementare la funzionalità Screens Launch nel progetto AEM Screens , effettuate le seguenti operazioni:

1. Create un canale di sequenza nel progetto AEM Screens , ad esempio **LaunchesDemo** —> **Channels** —> **FutureLaunch**, come mostrato di seguito.

   >[!CAUTION]
   >
   >È necessario creare un lancio da un canale preesistente nel progetto AEM Screens .

   ![Immagine](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleziona il canale **FutureLaunch** e fai clic su **Crea lancio** nella barra delle azioni.

   ![Immagine](/help/user-guide/assets/launches-images/launches-12.png)

1. Viene aperta la procedura guidata **Crea lancio** . Potete selezionare il canale già visibile nella procedura guidata oppure fare clic su **+ Aggiungi canali** per aggiungere il canale per il quale desiderate creare il lancio.

1. Fate clic su **Avanti** dalla procedura guidata **Crea lancio** . Per impostazione predefinita, l’opzione **Includi pagine** secondarie è selezionata.

   ![immagine](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Potete utilizzare l&#39;opzione **+ Aggiungi canali** per aggiungere un altro canale per il quale desiderate creare il lancio.

   Per utilizzare l&#39;opzione **Aggiungi canali** , andate al canale per il quale desiderate creare il lancio e fate clic su **Seleziona**.

   Se tentate di selezionare più canali o una cartella per l’aggiunta del lancio, l’opzione **Seleziona** verrà disattivata.

   ![immagine](/help/user-guide/assets/launches-images/launches-14.png)

   Dopo aver selezionato i canali, fai clic su **Avanti**.


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

   **Scopri l’ambito della promozione di Launch**

   * **Promuovi lancio** completo: Tutti i canali del lancio vengono promossi alla data impostata.
   * **Promuovi pagine** modificate: Verranno promosse solo le risorse di lancio modificate. Si consiglia di utilizzare questa opzione quando la revisione del lancio non è obbligatoria.
   * **Promuovi pagine** approvate: Questa opzione richiede l&#39;esecuzione del flusso di lavoro di approvazione del lancio sui canali di avvio. Solo le pagine approvate verranno promosse alla data impostata.

      >[!CAUTION]
      >
      >La data di lancio rispetta il fuso orario del lettore/dispositivo anziché quello del server.

1. Il lancio verrà creato. Potete fare clic su **Apri** per visualizzare le pagine nell’editor oppure su **Fine** per tornare al progetto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Facendo clic su **Fine** puoi tornare al canale **FutureLaunch** .

   ![Immagine](/help/user-guide/assets/launches-images/launches-16.png)


### Modifica delle proprietà del lancio per impostare la data e l&#39;ambito di attività {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Dopo aver creato il lancio, puoi aggiornare le proprietà come data di inizio, titolo del lancio e ambito della promozione utilizzando Proprietà **** lancio.

* **Data** lancio, si riferisce alla data in cui il contenuto viene riprodotto nel lettore Screens, ovvero alla data o all&#39;ora in cui viene riprodotto in base al fuso orario del lettore.
* **Production Ready**, consente di pubblicare i canali dopo la promozione di questi, è attivato out-of-the-box, quindi non è necessario modificare questo valore.
* **Ambito**, decide quali canali verranno promossi durante la promozione del lancio.


Per modificare le proprietà del lancio, effettuate le seguenti operazioni:

1. Andate al canale **FutureLaunch**, *(ovvero il lancio in sospeso)* e selezionate il canale, come mostrato nella figura seguente.

   ![immagine](/help/user-guide/assets/launches-images/launches-17.png)

1. Fate clic sul **dashboard** dalla barra delle azioni e visualizzate il pannello AVVII **** IN SOSPESO dal dashboard del canale.

   ![immagine](/help/user-guide/assets/launches-images/launches-18.png)

1. Selezionate il lancio e fate clic su **Avvia proprietà** dal pannello **LANCI** IN ATTESA.

   ![immagine](/help/user-guide/assets/launches-images/launches-19.png)

### Modifica del lancio dello schermo per aggiungere o rimuovere canali  {#editing-the-screens-launch-to-add-or-remove-channels}

Dopo aver creato il lancio, potete aggiungere o rimuovere canali al lancio esistente utilizzando l’opzione **Modifica lancio** .

Al termine, fai clic su **Salva** per tornare al canale **FutureLaunch** .

### Promozione manuale del lancio dello schermo{#promote-the-screens-launch-manually}

Potete promuovere il lancio manualmente utilizzando l&#39;opzione **Promuovi lancio** dal pannello AVVII **IN ATTESA** .

Puoi scegliere le risorse da promuovere nell&#39;ambito di questa promozione manuale in **Launch Promotion Wizard**.

![immagine](/help/user-guide/assets/launches-images/launches-e.png)

1. Potete attivare o disattivare l’opzione per eliminare il lancio dopo la produzione.
1. Puoi impostare l’ **ambito** del lancio, con le seguenti opzioni:
   1. **Promuovi lancio** completo: Tutti i canali del lancio vengono promossi alla data impostata.
   1. **Promuovi pagine** modificate: Verranno promosse solo le risorse di lancio modificate. Si consiglia di utilizzare questa opzione quando la revisione del lancio non è obbligatoria.
   1. **Promuovi pagine** approvate: Questa opzione richiede l&#39;esecuzione del flusso di lavoro di approvazione del lancio sui canali di avvio. Solo le pagine approvate verranno promosse alla data impostata.
   1. **Promuovi pagina** corrente: Questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito solo per la pagina corrente.
1. Fate clic su **Avanti** nella procedura guidata **Promuovi lancio** .
1. Fate clic su **Promuovi** per promuovere il lancio.

### Eliminazione del lancio dello schermo {#deleting-the-screens-launch}

Potete eliminare il lancio utilizzando l&#39;opzione **Elimina lancio** dal pannello **AVVII** IN ATTESA.

>[!CAUTION]
>
>Questa azione eliminerà anche tutti i discendenti (avvii nidificati).

