---
title: Aggiornamento dei contenuti tramite Screens Launch
seo-title: Content Update using Screens Launch
description: Gli autori dei contenuti possono creare versioni future dei canali, note come Launch; un’ulteriore impostazione della data di pubblicazione consente di riprodurre i contenuti su dispositivi o lettori.
seo-description: Content authors can create future version of the channel(s), known as Launch and further setting live date for this launch allows content to be live in devices or players.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: 2cc613454d0d20a42871858e3d754e1b0e161dc3
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# Aggiornamento dei contenuti tramite Screens Launch {#launches}

Gli autori dei contenuti possono creare versioni future dei canali, note come **Lancio di Screens** e imposta ulteriormente la data di pubblicazione per questo lancio. Questo consente di riprodurre il contenuto in tempo reale su dispositivi o lettori alla data di pubblicazione specificata.

Con l&#39;aiuto di ***Lancio di Screens***, gli autori possono visualizzare in anteprima ogni canale nel lancio e dovrebbero essere in grado di avviare una richiesta di revisione. Il gruppo di approvatori riceverà una notifica e potrà approvare o rifiutare la richiesta. Una volta raggiunta la data di attivazione, il contenuto viene riprodotto nei dispositivi.

Ad esempio, se l’autore desidera creare versioni future di c1, c2 (canali), viene creato un lancio e viene impostata una data di attivazione (ad esempio, 10 novembre alle 8.00). Eventuali ulteriori aggiornamenti nel contenuto vengono inviati per la revisione.

Dopo l’approvazione e la data di attivazione (10 novembre, 08:00), questo lancio riproduce il contenuto sui dispositivi o sui lettori.

## Requisiti {#requirements}

Prima di iniziare a sfruttare *Lancio di Screens* in un progetto AEM Screens, accertati di comprendere il concetto di Periodo di tolleranza e la sua rilevanza.

L&#39;esecuzione di un&#39;esperienza nella data di attivazione impostata sul lettore comporta:

* promozione del lancio (in genere richiede qualche secondo)

* la pubblicazione delle risorse nelle istanze di pubblicazione (in genere richiede qualche minuto, a seconda delle dimensioni dei canali o delle risorse da pubblicare)

* tempo impiegato dal completamento dell’aggiornamento del contenuto offline (in genere richiede qualche minuto)

* tempo impiegato dai lettori per scaricare il contenuto dall’istanza di pubblicazione (in genere richiede minuti a seconda della larghezza di banda e delle dimensioni delle risorse da scaricare)

* differenze di orario tra server e lettore

### Informazioni sul periodo di tolleranza {#understanding-grace-period}

Affinché il lettore possa iniziare a riprodurre il contenuto nella data di pubblicazione impostata, è necessario avviare le attività precedenti prima della data di pubblicazione.

Se la data di attivazione è *24 novembre, 09:00* e il periodo di tolleranza è *24 ore*, la sequenza di azioni precedente inizierà a (data pubblicazione - periodo di tolleranza), ovvero il 23 novembre alle 9:00 ora del server. Questo dà 24 ore di tempo per completare tutte le azioni di cui sopra e il contenuto raggiungerà i giocatori. I lettori capiranno che si tratta di un contenuto di lancio, quindi il contenuto non verrà riprodotto immediatamente, ma i lettori memorizzeranno questo contenuto come versione futura e inizieranno a riprodurre esattamente alla data di trasmissione impostata sul fuso orario del lettore.

Ad esempio, supponiamo che il server sia in PST e che i dispositivi siano in EST; in questo caso la differenza di tempo massima è di 3 ore e si supponga che la promozione richieda 1 minuto e che la pubblicazione dall’autore alla pubblicazione richieda 10 minuti e che il lettore possa scaricare le risorse in genere in 10-15 minuti. Quindi periodo di tolleranza = differenza di tempo (3 ore) + tempo per promuovere il lancio (1 min) + tempo per pubblicare il lancio (10 min) + tempo per scaricare al lettore (10-15 min) + buffer (per sicurezza, diciamo 30 min) = 3 ore 56 min = 14160 secondi.

Ogni volta che pianifichiamo un lancio in diretta, la promozione inizierà prima di questo offset. Nell&#39;equazione precedente, la maggior parte degli elementi non richiede molto tempo, possiamo utilizzare una stima decente per questo offset una volta che conosciamo la massima differenza di tempo tra il server e qualsiasi lettore.

>[!NOTE]
>
>Pronto all’uso, il periodo di tolleranza per Screens Launch è impostato su 24 ore, il che significa che quando impostiamo la data di attivazione per qualsiasi lancio per le risorse in */content/screens*, la promozione inizierà con questo offset.

### Aggiornamento del periodo di tolleranza predefinito {#updating-out-of-the-box-grace-period}

In questa sezione viene illustrato come aggiornare a 10 minuti un periodo di tolleranza predefinito.

1. Passa a CRXDE Lite e quindi a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Fai clic con il pulsante destro del mouse e copia il file.
3. Accedi a `/apps/system/config` e fare clic con il pulsante destro del mouse e incollare.
4. Doppio clic su `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` per aprire il file nell’editor in CRXDE Lite. Deve mostrare il periodo di tolleranza per il percorso */content/screens/* as **86400**. Cambia il valore in **600**.

Ora il contenuto nel file di testo dovrebbe essere simile a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Poiché nell&#39;esempio precedente il periodo di tolleranza è stato impostato su 10 minuti, quando si imposta la data di attivazione per qualsiasi avvio per le risorse in */content/screens*, la promozione inizierà con questo offset.

Ad esempio, se la data di attivazione è impostata su 24 novembre, 09:00 e il periodo di tolleranza è di 600 secondi, il processo di promozione inizierà il 24 novembre alle 08:50.

## Utilizzo di Screens Launch {#using-launches}

Questa sezione illustra come implementare Screens Launch nel progetto AEM Screens.

### Creazione di un lancio Screens {#creating-a-launch}

Per implementare la funzionalità di avvio di Screens nel tuo progetto AEM Screens, segui i passaggi seguenti:

1. Crea un canale di sequenza nel progetto AEM Screens, ad esempio **DemoLanci** —> **Canali** —> **FutureLaunch**, come illustrato di seguito.

   >[!CAUTION]
   >
   >Devi creare un lancio da un canale preesistente nel progetto AEM Screens.

   ![Immagine](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleziona il canale **FutureLaunch** e fai clic su **Crea lancio** dalla barra delle azioni.

   ![Immagine](/help/user-guide/assets/launches-images/launches-12.png)

1. Il **Crea lancio** viene aperta la procedura guidata. È possibile selezionare il canale già visibile nella procedura guidata oppure fare clic su **+ Aggiungi canali** per aggiungere il canale per il quale desideri creare il lancio.

1. Clic **Successivo** dal **Crea lancio** procedura guidata. Il **Includi pagine secondarie** è selezionata per impostazione predefinita.

   ![immagine](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >È possibile utilizzare **+ Aggiungi canali** per aggiungere un altro canale per il quale desideri creare il lancio.

   Da utilizzare **Aggiungi canali** , passa al canale per il quale vuoi creare il lancio e fai clic su **Seleziona**.

   Il **Seleziona** l’opzione sarà disabilitata se tenti di selezionare più canali o una cartella per l’aggiunta del lancio.

   ![immagine](/help/user-guide/assets/launches-images/launches-14.png)

   Dopo aver selezionato i canali, fai clic su **Successivo**.


1. Inserisci il **Titolo lancio** as **SummerPromotions** e non è necessario impostare **Data lancio**, come illustrato nella figura seguente. Fai clic su **Crea**.

   >[!NOTE]
   >
   >*Abilitazione o controllo* l&#39;opzione **Eredita i dati live della pagina sorgente** consente di creare i canali come Live Copy nel lancio. Se vengono apportate modifiche al canale originale, queste vengono applicate automaticamente ai canali di avvio.
   >
   >
   >*Disattivazione o deselezione* **Eredita i dati live della pagina sorgente** consente di copiare i canali senza alcuna relazione live nel lancio. Pertanto, se vengono apportate modifiche al canale originale, tali modifiche non vengono applicate ai canali di lancio.

   ![Immagine](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Puoi impostare la data di lancio live in questo passaggio o in un secondo momento durante la modifica delle proprietà del lancio, una volta creato.

   **Informazioni sull’ambito della promozione di Launch**

   * **Promuovi lancio completo**: tutti i canali del lancio vengono promossi alla data live impostata.
   * **Promuovi pagine modificate**: verranno promosse solo le risorse di lancio modificate. Si consiglia di utilizzare questa opzione quando non è richiesta la revisione del lancio.
   * **Promuovi pagine approvate**: questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito sui canali del lancio. Solo le pagine approvate verranno promosse alla data di attivazione impostata.

      >[!CAUTION]
      >
      >La data di lancio live rispetta il fuso orario del lettore/dispositivo anziché quello del server.

1. Vedrai che il lancio è stato creato. Puoi fare clic su **Apri** per visualizzare le pagine nell’editor o fai clic su **Fine** per tornare al progetto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clic **Fine** consente di tornare al **FutureLaunch** canale.

   ![Immagine](/help/user-guide/assets/launches-images/launches-16.png)


### Modifica delle proprietà di Launch per impostare la data e l&#39;ambito di attivazione {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Dopo la creazione del lancio, puoi aggiornare proprietà quali data di attivazione, titolo del lancio e ambito della promozione utilizzando **Proprietà lancio**.

* **Data lancio**, si riferisce alla data e all’ora di riproduzione del contenuto nel lettore Screens in base al fuso orario del lettore.
* **Produzione pronta**, consente di pubblicare i canali dopo averli promossi; questa opzione è abilitata per impostazione predefinita, quindi non è necessario modificarla.
* **Ambito**, decide quali canali verranno promossi durante la promozione del lancio.


Per modificare le proprietà del lancio, segui i passaggi seguenti:

1. Accedi al canale **FutureLaunch**, *(questo è il lancio in sospeso)* e selezionare il canale, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/launches-images/launches-17.png)

1. Fai clic su **Dashboard** dalla barra delle azioni e viene visualizzata la **LANCI IN SOSPESO** dal dashboard dei canali.

   ![immagine](/help/user-guide/assets/launches-images/launches-18.png)

1. Seleziona il lancio e fai clic su **Proprietà lancio** dal **LANCI IN SOSPESO** pannello.

   ![immagine](/help/user-guide/assets/launches-images/launches-19.png)

### Modifica di Screens Launch per aggiungere o rimuovere canali  {#editing-the-screens-launch-to-add-or-remove-channels}

Dopo aver creato il lancio, puoi aggiungere o rimuovere canali dal lancio esistente utilizzando **Modifica lancio** opzione.

Al termine, fai clic su **Salva** per tornare a **FutureLaunch** canale.

### Promozione manuale del lancio di Screens{#promote-the-screens-launch-manually}

Puoi promuovere il lancio manualmente utilizzando **Promuovi lancio** opzione dalla **LANCI IN SOSPESO** pannello.

Puoi scegliere le risorse da promuovere nell&#39;ambito di questa promozione manuale nel **Avvia promozione guidata**.

![immagine](/help/user-guide/assets/launches-images/launches-e.png)

1. Puoi abilitare o disabilitare l’opzione per eliminare il lancio dopo la produzione.
1. È possibile impostare **Ambito** del lancio, con le seguenti opzioni:
   1. **Promuovi lancio completo**: tutti i canali del lancio vengono promossi alla data live impostata.
   1. **Promuovi pagine modificate**: verranno promosse solo le risorse di lancio modificate. Si consiglia di utilizzare questa opzione quando non è richiesta la revisione del lancio.
   1. **Promuovi pagine approvate**: questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito sui canali del lancio. Solo le pagine approvate verranno promosse alla data di attivazione impostata.
   1. **Promuovi la pagina corrente**: questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito solo per la pagina corrente.
1. Clic **Successivo** nel **Promuovi lancio** procedura guidata.
1. Clic **Promuovi** per promuovere il lancio.

### Eliminazione del lancio Screens {#deleting-the-screens-launch}

Puoi eliminare il lancio utilizzando **Elimina lancio** opzione dalla **LANCI IN SOSPESO** pannello.

>[!CAUTION]
>
>Questa azione eliminerà anche tutti i discendenti (lanci nidificati).
