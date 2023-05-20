---
title: Creazione e gestione delle visualizzazioni
seo-title: Managing Displays
description: Segui questa pagina per scoprire come creare una nuova configurazione di display e dispositivi. Inoltre, scopri il dashboard di visualizzazione.
seo-description: Follow this page to learn about creating a new display and device config. Additionally, learn about the display dashboard.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# Creazione e gestione delle visualizzazioni {#creating-and-managing-displays}

Un display è un raggruppamento virtuale di schermi solitamente posizionati uno accanto all’altro. Il display è di solito permanente rispetto a un&#39;installazione. Questo sarà l’oggetto con cui gli autori di contenuto lavoreranno e a cui faranno sempre riferimento come visualizzazione logica piuttosto che le loro parti contatore fisiche.

Una volta creata una posizione, è necessario crearne una nuova per la posizione.

Questa pagina mostra come creare e gestire le visualizzazioni di Screens.

**Prerequisiti**:

* [Configurazione e distribuzione di Screens](configuring-screens-introduction.md)
* [Creare e gestire un progetto Screens](creating-a-screens-project.md)
* [Creare e gestire i canali](managing-channels.md)
* [Creare e gestire le posizioni](managing-locations.md)

## Creazione di una nuova visualizzazione {#creating-a-new-display}

>[!NOTE]
>
>È necessario creare una posizione prima di creare una visualizzazione. Per informazioni su come creare una posizione, consulta [Creare e gestire le posizioni](managing-locations.md) per ulteriori informazioni.

Per creare una nuova visualizzazione nella tua posizione, segui i passaggi seguenti:

1. Passa alla posizione appropriata, ad esempio `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Seleziona la cartella della posizione e tocca o fai clic su **Crea** accanto all’icona più nella barra delle azioni. Verrà aperta una procedura guidata.
1. Seleziona **Visualizzazione** dal **Crea** e fai clic su **Successivo**.

1. Invio **Nome** e **Titolo** per la posizione di visualizzazione.

1. Sotto **Visualizzazione** , scegliere i dettagli del layout. Scegli il **Risoluzione** (ad esempio come, come **Full HD**). Inoltre, è possibile scegliere il numero di dispositivi in orizzontale e in verticale.

1. Fai clic su **Crea**.

Visualizzazione (*StoreDisplay*) viene creato e aggiunto alla posizione (*SanJose*).

![visualizzare](assets/display.gif)

Una volta che lo schermo è in posizione, il passaggio successivo consisterà nel creare una configurazione dispositivo per quel particolare display. Segui la sezione seguente per creare una nuova configurazione dispositivo.

>[!NOTE]
>
>**Passaggio successivo**:
>
>Dopo aver creato una visualizzazione per la posizione, è necessario assegnare un canale alla visualizzazione per sfruttare il contenuto.
>
>Consulta [Assegna canali](channel-assignment.md) per scoprire come assegnare un canale alla visualizzazione.

## Creazione di una nuova configurazione dispositivo {#creating-a-new-device-config}

La configurazione di un dispositivo funge da segnaposto per un dispositivo di digital signage non ancora installato.

Per creare una nuova configurazione dispositivo, segui i passaggi seguenti:

1. Passa alla visualizzazione appropriata, ad esempio: `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Seleziona la cartella di visualizzazione e tocca o fai clic su **Visualizza dashboard** nella barra delle azioni.
1. Tocca o fai clic sul pulsante **+ Aggiungi configurazione dispositivo** in alto a destra nella **Dispositivi** pannello.

1. Seleziona la **Configurazione dispositivo** come modello richiesto come e tocca o fai clic su **Successivo**.

1. Inserisci le proprietà richieste e tocca o fai clic su **Crea**.

La configurazione del dispositivo viene creata e aggiunta alla visualizzazione corrente (nella seguente dimostrazione, la nuova configurazione del dispositivo è *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Una volta che la configurazione del dispositivo è impostata sul display nella posizione, il passaggio successivo consisterà nell’assegnare un canale al display.

>[!NOTE]
>
>Una volta che la configurazione del dispositivo è impostata sul display nella posizione, il passaggio successivo consisterà nell’assegnare un canale al display.
>
>Come mostrato nella figura seguente, se la configurazione del dispositivo viene visualizzata come non assegnata nel **DISPOSITIVI** nel caso in cui nessun canale venga assegnato a quella particolare configurazione dispositivo.
>
>Devi conoscere in anticipo i concetti relativi alla creazione e alla gestione dei canali. Consulta [Creare e gestire i canali](managing-channels.md) per ulteriori dettagli.

![chlimage_1-9](assets/chlimage_1-9.png)

## Dashboard di visualizzazione {#display-dashboard}

La dashboard di visualizzazione offre diversi pannelli per la gestione dei dispositivi di visualizzazione e delle configurazioni dei dispositivi per il dispositivo.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Puoi selezionare gli elenchi del dashboard e attivare azioni in blocco sugli elementi, invece di esaminare ogni elemento singolarmente.
>
>Ad esempio, l&#39;immagine seguente mostra come selezionare più canali dal dashboard di visualizzazione.

![cqdoc9456](assets/cqdoc9456.gif)

### Schermo pannello informazioni {#display-information-panel}

Il **INFORMAZIONI SULLA VISUALIZZAZIONE** Il pannello fornisce le proprietà di visualizzazione.

Fai clic sul pulsante (**...**) in alto a destra nella **INFORMAZIONI SULLA VISUALIZZAZIONE** per visualizzare le proprietà e visualizzare l&#39;anteprima della visualizzazione.


#### Visualizzazione delle proprietà {#viewing-properties}

Clic **Proprietà** per visualizzare o modificare le proprietà della visualizzazione.

Inoltre, puoi regolare il valore del timer dell’evento per il canale interattivo in **Timeout di inattività** proprietà in **Visualizzazione** scheda. Il valore predefinito è impostato su *300 secondi*.

Utilizzare **CRXDE Lite**, per accedere al **idleTimeout** proprietà, ovvero `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### Pannello Canali assegnati {#assigned-channels-panel}

Il **CANALI ASSEGNATI** nel pannello vengono visualizzati i canali assegnati al dispositivo.


### Pannello Dispositivi {#devices-panel}

Il **DISPOSITIVI** Il pannello fornisce informazioni sulle configurazioni del dispositivo.

Fai clic sul pulsante (**...**) in alto a destra nella **DISPOSITIVI** per aggiungere configurazioni di dispositivi e aggiornare i dispositivi.

Inoltre, fai clic sulla configurazione del dispositivo per visualizzare le proprietà, assegnare un dispositivo o eliminarlo completamente.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Passaggi successivi {#the-next-steps}

Una volta completata la creazione di una visualizzazione per la posizione, è necessario assegnare un canale per la visualizzazione.

Consulta [Assegna canali](channel-assignment.md) per ulteriori dettagli.
