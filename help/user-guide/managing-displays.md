---
title: Creazione e gestione delle visualizzazioni
seo-title: Gestione delle visualizzazioni
description: Segui questa pagina per scoprire come creare una nuova configurazione dispositivo e di visualizzazione. Inoltre, scopri la dashboard di visualizzazione.
seo-description: Segui questa pagina per scoprire come creare una nuova configurazione dispositivo e di visualizzazione. Inoltre, scopri la dashboard di visualizzazione.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: Creazione di esperienze in Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 59%

---


# Creazione e gestione delle visualizzazioni {#creating-and-managing-displays}

Una visualizzazione è un raggruppamento virtuale di schermate che sono solitamente posizionate l’una accanto all’altra. La visualizzazione è solitamente permanente per quanto riguarda l’installazione. Questo sarà l’oggetto con il quale gli autori di contenuti lavoreranno e al quale faranno sempre riferimento come visualizzazione logica piuttosto che le controparti fisiche.

Dopo aver creato una posizione, è necessario creare una nuova visualizzazione per la posizione.

Questa pagina illustra la creazione e la gestione di visualizzazioni per le schermate.

**Prerequisiti**:

* [Configurazione e distribuzione di Screens](configuring-screens-introduction.md)
* [Creare e gestire un progetto Screens](creating-a-screens-project.md)
* [Creare e gestire i canali](managing-channels.md)
* [Creare e gestire posizioni](managing-locations.md)

## Creazione di una nuova visualizzazione {#creating-a-new-display}

>[!NOTE]
>
>È necessario creare una posizione prima di creare una visualizzazione. Per informazioni su come creare una posizione, consulta [Creare e gestire posizioni](managing-locations.md) .

Per creare una nuova visualizzazione nella posizione, effettua le seguenti operazioni:

1. Passa alla posizione appropriata, ad esempio `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Seleziona la cartella della posizione e tocca o fai clic su **Crea** accanto all&#39;icona del segno più nella barra delle azioni. Si apre una procedura guidata.
1. Seleziona **Display** dalla procedura guidata **Crea** e fai clic su **Avanti**.

1. Immetti **Nome** e **Titolo** per la posizione di visualizzazione.

1. Nella scheda **Visualizzazione** , scegli i dettagli del layout. Scegli la **Risoluzione** desiderata (ad esempio, come **Full HD**). Inoltre, è possibile scegliere il numero di dispositivi orizzontalmente e verticalmente.

1. Fai clic su **Crea**.

Il display (*StoreDisplay*) viene creato e aggiunto al percorso (*SanJose*).

![display](assets/display.gif)

Quando la visualizzazione è in posizione, il passaggio successivo è la creazione di una configurazione dispositivo per quella specifica visualizzazione. Segui la sezione seguente per creare una nuova configurazione dispositivo.

>[!NOTE]
>
>**Passaggio successivo**:
>
>Dopo aver creato una visualizzazione per la posizione, è necessario assegnarle un canale affinché la visualizzazione sfrutti i contenuti.
>
>Per informazioni su come assegnare un canale alla visualizzazione, consulta la sezione [Assegna canali](channel-assignment.md) .

## Creazione di una nuova configurazione dispositivo {#creating-a-new-device-config}

Una configurazione dispositivo funge da segnaposto per un dispositivo di segnaletica digitale che non è non ancora stato installato.

Effettua le seguenti operazioni per creare una nuova configurazione dispositivo:

1. Passa alla visualizzazione appropriata, ad esempio `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Seleziona la cartella di visualizzazione e tocca o fai clic su **Visualizza dashboard** nella barra delle azioni.
1. Tocca o fai clic su **+ Aggiungi configurazione dispositivo** in alto a destra nel pannello **Dispositivi**.

1. Seleziona il modello **Configurazione dispositivo** come richiesto e tocca o fai clic su **Avanti**.

1. Immetti le proprietà desiderate e tocca o fai clic su **Crea**.

La configurazione dispositivo viene creata e aggiunta alla visualizzazione corrente (nella seguente dimostrazione, la nuova configurazione dispositivo è *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Una volta impostata la configurazione dispositivo per la visualizzazione nella posizione, il passaggio successivo prevede l’assegnazione di un canale alla visualizzazione.

>[!NOTE]
>
>Una volta impostata la configurazione dispositivo per la visualizzazione nella posizione, il passaggio successivo prevede l’assegnazione di un canale alla visualizzazione.
>
>Come mostrato nella figura seguente, se la configurazione del dispositivo viene visualizzata come non assegnata nel pannello **DISPOSITIVI**, se non viene assegnato alcun canale a quella specifica configurazione del dispositivo.
>
>È necessario avere familiarità con le procedure di creazione e gestione di canali. Per ulteriori informazioni, consulta [Creare e gestire i canali](managing-channels.md) .

![chlimage_1-9](assets/chlimage_1-9.png)

## Dashboard di visualizzazione {#display-dashboard}

La dashboard di visualizzazione fornisce diversi pannelli per la gestione di dispositivi di visualizzazione e configurazioni dispositivo per il dispositivo.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Puoi selezionare gli elenchi della dashboard e avviare azioni collettive sugli elementi, invece di passare in rassegna individualmente ogni singolo elemento.
>
>Ad esempio, l’immagine seguente mostra come selezionare più canali dalla dashboard di visualizzazione.

![cqdoc9456](assets/cqdoc9456.gif)

### Pannello Informazioni sulla visualizzazione {#display-information-panel}

Il pannello **INFORMAZIONI SULLA VISUALIZZAZIONE** fornisce le proprietà di visualizzazione.

Fai clic su **...** nell’angolo in alto a destra del pannello **INFORMAZIONI SULLA VISUALIZZAZIONE** per visualizzare le proprietà e vedere la visualizzazione in anteprima.


#### Visualizzazione delle proprietà {#viewing-properties}

Fai clic su **Proprietà** per visualizzare o modificare le proprietà della visualizzazione.

Inoltre, è possibile regolare il valore del timer evento per il canale interattivo nella proprietà **Timeout inattività** nella scheda **Visualizzazione**. Il valore predefinito è impostato su *300 secondi*.

Utilizza **CRXDE Lite** per accedere alla proprietà **idleTimeout** , ovvero `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### Pannello Canali Assegnati {#assigned-channels-panel}

Il pannello **CANALI ASSEGNATI** visualizza i canali assegnati a questo dispositivo.


### Pannello Dispositivi {#devices-panel}

Il pannello **DISPOSITIVI** fornisce informazioni sulle configurazioni dispositivo.

Fai clic su (**...**) nell&#39;angolo in alto a destra del pannello **DISPOSITIVI** per aggiungere configurazioni dispositivo e aggiornare dispositivi.

Inoltre, fai clic sulla configurazione del dispositivo per visualizzare le proprietà, assegnare un dispositivo o eliminarlo completamente.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Passaggi successivi {#the-next-steps}

Dopo aver completato la creazione di una visualizzazione per la posizione, è necessario assegnare un canale alla visualizzazione.

Per ulteriori informazioni, consulta [Assegna canali](channel-assignment.md) .
