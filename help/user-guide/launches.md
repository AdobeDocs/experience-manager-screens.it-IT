---
title: Aggiornamento dei contenuti tramite Screens Launch
description: Scopri come creare una versione futura dei canali, nota come Launch, e come impostare una data di pubblicazione del lancio in modo che il contenuto venga reso live su dispositivi o lettori.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 0%

---

# Aggiornamento dei contenuti tramite Screens Launch {#launches}

Gli autori dei contenuti possono creare versioni future dei canali, note come **Lancio di Screens** e imposta ulteriormente la data di pubblicazione per questo lancio. Questo consente di riprodurre il contenuto in tempo reale su dispositivi o lettori alla data di pubblicazione specificata.

Con l&#39;aiuto di ***Lancio di Screens***, gli autori possono visualizzare in anteprima ogni canale nel lancio e dovrebbero essere in grado di avviare una richiesta di revisione. Il gruppo di approvatori riceve una notifica e può approvare o rifiutare la richiesta. Una volta raggiunta la data di attivazione, il contenuto viene riprodotto nei dispositivi.

Ad esempio, se l’autore desidera creare versioni future di c1, c2 (canali), viene creato un lancio e viene impostata una data di attivazione (ad esempio, 10 novembre alle 8.00). Eventuali altri aggiornamenti nel contenuto vengono inviati per la revisione.

Una volta approvato e in data live (10 novembre, 8:00), questo lancio riproduce il contenuto sui dispositivi o sui lettori.

## Requisiti {#requirements}

Prima di iniziare a utilizzare *Lancio di Screens* in un progetto AEM Screens, accertati di comprendere il concetto di Periodo di tolleranza e la sua rilevanza.

L&#39;esecuzione di un&#39;esperienza nella data di attivazione impostata sul lettore comporta:

* La promozione del lancio (in genere richiede alcuni secondi).

* La pubblicazione delle risorse nelle istanze di pubblicazione (in genere richiede alcuni minuti, a seconda delle dimensioni dei canali o delle risorse da pubblicare).

* Tempo impiegato dal completamento dell’aggiornamento del contenuto offline (in genere richiede qualche minuto).

* Tempo impiegato dai lettori per scaricare il contenuto dall’istanza di pubblicazione (in genere richiede minuti a seconda della larghezza di banda e delle dimensioni delle risorse da scaricare).

* Differenze in qualsiasi momento tra server e lettore.

### Informazioni sul periodo di tolleranza {#understanding-grace-period}

Affinché il lettore possa iniziare a riprodurre il contenuto nella data di pubblicazione impostata, devi avviare le attività precedenti prima della data di pubblicazione.

Se la data di attivazione è *24 novembre, 09:00* e il periodo di tolleranza è *24 ore*, quindi la sequenza di azioni precedente inizierà a (data pubblicazione - periodo di tolleranza), ovvero il 23 novembre alle 09:00 ora del server. Questo offre 24 ore per completare tutte le azioni sopra menzionate affinché il contenuto raggiunga i lettori. I giocatori capiscono che questo è un contenuto di lancio. Di conseguenza, il contenuto non viene riprodotto immediatamente, ma i lettori possono memorizzarlo come versione futura e farne iniziare la riproduzione esattamente alla data di trasmissione impostata sul fuso orario del lettore.

Ad esempio, il server è in PST e i dispositivi sono in EST. In questo caso, la differenza di tempo massima è di tre ore e presuppone che la promozione richieda 1 minuto, che la pubblicazione dall’ambiente di authoring a quello di pubblicazione richieda 10 minuti e che il lettore possa scaricare le risorse in genere in 10-15 minuti. Quindi il periodo di tolleranza = differenza di tempo (tre ore):

* Più tempo per promuovere il lancio (1 minuto)
* Più tempo per pubblicare il lancio (10 minuti)
* Più tempo per scaricare sul lettore (10-15 minuti)
* Più buffer (30 minuti)

È uguale a 3 ore e 56 minuti (14160 secondi).

Pertanto, ogni volta che pianifichi un lancio in diretta, la promozione inizia prima di questo offset. Nell&#39;equazione precedente, la maggior parte degli elementi non richiede molto tempo. È possibile utilizzare una stima ragionata per questo scostamento quando si conosce la differenza di tempo massima tra il server e qualsiasi lettore.

>[!NOTE]
>
>Pronto all’uso, il periodo di tolleranza per Screens Launch è impostato su 24 ore. Ciò significa che quando imposti la data di attivazione per qualsiasi lancio per le risorse in */content/screens*, la promozione inizia con questo offset.

### Aggiornamento del periodo di tolleranza predefinito {#updating-out-of-the-box-grace-period}

In questa sezione viene illustrato come aggiornare a 10 minuti un periodo di tolleranza predefinito.

1. Passa a CRXDE Liti e quindi a `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Fare clic con il pulsante destro del mouse e copiare il file.
1. Accedi a `/apps/system/config` e fare clic con il pulsante destro del mouse e incollare.
1. Doppio clic `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` in modo da poter aprire il file nell’editor in CRXDE Liti. Deve mostrare il periodo di tolleranza per il percorso */content/screens/* as **86400**. Cambia il valore in **600**.

Ora il contenuto nel file di testo dovrebbe essere simile a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Poiché nell&#39;esempio precedente il periodo di tolleranza era stato impostato su 10 minuti, quando si imposta la data di attivazione per un avvio delle risorse in */content/screens*, la promozione inizia con questo offset.

Ad esempio, se la data di attivazione è impostata sul 24 novembre alle 9.00 e il periodo di tolleranza è di 600 secondi, il processo di promozione inizia il 24 novembre alle 8.50.

## Utilizzo di Screens Launch {#using-launches}

Questa sezione illustra come implementare Screens Launch nel progetto AEM Screens.

### Creazione di un lancio Screens {#creating-a-launch}

Per implementare la funzionalità di avvio di Screens nel tuo progetto AEM Screens, segui i passaggi seguenti:

1. Crea un canale di sequenza nel progetto AEM Screens, ad esempio **DemoLanci** > **Canali** > **FutureLaunch**, come illustrato di seguito.

   >[!CAUTION]
   >
   >Crea un lancio da un canale preesistente nel progetto AEM Screens.

   ![Immagine](/help/user-guide/assets/launches-images/launches-11.png)

1. Seleziona il canale **FutureLaunch** e fai clic su **Crea lancio** dalla barra delle azioni.

   ![Immagine](/help/user-guide/assets/launches-images/launches-12.png)

1. Il **Crea lancio** viene aperta la procedura guidata. È possibile selezionare il canale già visibile nella procedura guidata oppure fare clic su **+ Aggiungi canali** per aggiungere il canale per il quale desideri creare il lancio.

1. Clic **Successivo** dal **Crea lancio** procedura guidata. Il **Includi pagine secondarie** è selezionata per impostazione predefinita.

   ![immagine](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >È possibile utilizzare **+ Aggiungi canali** per aggiungere un altro canale per il quale desideri creare il lancio.

   Da utilizzare **Aggiungi canali** , passa al canale per il quale vuoi creare il lancio e fai clic su **Seleziona**.

   Il **Seleziona** l’opzione è disabilitata se tenti di selezionare più canali o una cartella per l’aggiunta del lancio.

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

   * **Promuovi lancio completo** - Tutti i canali del lancio vengono promossi alla data impostata per la messa in onda.
   * **Promuovi pagine modificate** - Vengono promosse solo le risorse di lancio modificate. Utilizza questa opzione quando non è richiesta la revisione del lancio.
   * **Promuovi pagine approvate** - Questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito sui canali del lancio. Solo le pagine approvate vengono promosse alla data di attivazione impostata.

     >[!CAUTION]
     >
     >La data di lancio live rispetta il fuso orario del lettore/dispositivo anziché quello del server.

1. Tieni presente che il lancio viene creato. Puoi selezionare **Apri** per visualizzare le pagine nell’editor o seleziona **Fine** per tornare al progetto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Selezione **Fine** ti consente di tornare al **FutureLaunch** canale.

   ![Immagine](/help/user-guide/assets/launches-images/launches-16.png)


### Modifica delle proprietà di Launch per impostare la data e l&#39;ambito di attivazione {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Dopo la creazione del lancio, puoi aggiornare proprietà quali data di attivazione, titolo del lancio e ambito della promozione utilizzando **Proprietà lancio**.

* **Data lancio** - La data e l’ora di riproduzione del contenuto nel lettore Screens in base al fuso orario del lettore.
* **Produzione pronta** : consente la pubblicazione dei canali dopo la promozione di questi, abilitata per impostazione predefinita, quindi non è necessario modificarla.
* **Ambito** - Decide quali canali promuovere durante la promozione del lancio.

Per modificare le proprietà del lancio, segui i passaggi seguenti:

1. Passare al canale **FutureLaunch** *(il lancio in sospeso)* e selezionare il canale come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/launches-images/launches-17.png)

1. Seleziona **Dashboard** dalla barra delle azioni e viene visualizzata la **LANCI IN SOSPESO** dal dashboard dei canali.

   ![immagine](/help/user-guide/assets/launches-images/launches-18.png)

1. Seleziona il lancio e fai clic su **Proprietà lancio** dal **LANCI IN SOSPESO** pannello.

   ![immagine](/help/user-guide/assets/launches-images/launches-19.png)

### Modifica di Screens Launch per aggiungere o rimuovere canali  {#editing-the-screens-launch-to-add-or-remove-channels}

Dopo aver creato il lancio, puoi aggiungere o rimuovere canali dal lancio esistente utilizzando **Modifica lancio** opzione.

Al termine, seleziona **Salva** per tornare a **FutureLaunch** canale.

### Promozione manuale del lancio di Screens{#promote-the-screens-launch-manually}

Puoi promuovere il lancio manualmente utilizzando **`Promote Launch`** opzione dalla **LANCI IN SOSPESO** pannello.

Puoi scegliere le risorse da promuovere nell&#39;ambito di questa promozione manuale nel **Avvia promozione guidata**.

![immagine](/help/user-guide/assets/launches-images/launches-e.png)

1. Puoi abilitare o disabilitare l’opzione per eliminare il lancio dopo la produzione.
1. È possibile impostare **Ambito** del lancio con le seguenti opzioni:
   * **Promuovi lancio completo** - Tutti i canali del lancio vengono promossi alla data impostata per la messa in onda.
   * **Promuovi pagine modificate** - Vengono promosse solo le risorse di lancio modificate. Utilizza questa opzione quando non è richiesta la revisione del lancio.
   * **Promuovi pagine approvate** - Questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito sui canali del lancio. Solo le pagine approvate vengono promosse alla data di attivazione impostata.
   * **Promuovi la pagina corrente** - Questa opzione richiede che il flusso di lavoro di approvazione del lancio venga eseguito solo per la pagina corrente.
1. Seleziona **Successivo** nel **Promuovi lancio** procedura guidata.
1. Seleziona **Promuovi** per promuovere il lancio.

### Eliminazione del lancio Screens

Puoi eliminare il lancio utilizzando **Elimina lancio** opzione dalla **LANCI IN SOSPESO** pannello.

>[!CAUTION]
>
>Questa azione elimina anche tutti i discendenti (lanci nidificati).
