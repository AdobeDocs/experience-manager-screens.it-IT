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
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Creazione e gestione delle visualizzazioni {#creating-and-managing-displays}

Una visualizzazione è un raggruppamento virtuale di schermate che sono solitamente posizionate l’una accanto all’altra. La visualizzazione è solitamente permanente per quanto riguarda l’installazione. Questo sarà l’oggetto con il quale gli autori di contenuti lavoreranno e al quale faranno sempre riferimento come visualizzazione logica piuttosto che le controparti fisiche.

Dopo aver creato una posizione, è necessario creare una nuova visualizzazione per la posizione.

Questa pagina illustra la creazione e la gestione di visualizzazioni per le schermate.

**Prerequisiti**:

* [Configurazione e distribuzione di Screens](configuring-screens-introduction.md)
* [Creare e gestire il progetto Screens](creating-a-screens-project.md)
* [Creare e gestire canali](managing-channels.md)
* [Creare e gestire le posizioni](managing-locations.md)

## Creazione di una nuova visualizzazione {#creating-a-new-display}

>[!NOTE]
>
>È necessario creare una posizione prima di creare una visualizzazione. To see how to create a location, see [Create and Manage Locations](managing-locations.md) for more information.

Per creare una nuova visualizzazione nella posizione, effettua le seguenti operazioni:

1. Navigate to the appropriate location, for example `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Select your location folder and tap/click **Create** next to the plus icon in the action bar. Si apre una procedura guidata.
1. Select **Display** from the **Create** wizard and click **Next**.

1. Enter **Name** and **Title** for your display location.

1. Under the **Display** tab, choose the details of the Layout. Choose the desired **Resolution** (example as, as **Full HD**). Inoltre, potete scegliere il numero di dispositivi in orizzontale e verticale.

1. Fai clic su **Crea**. 

The display (*StoreDisplay*) is created and added to the location (*SanJose*).

![display](assets/display.gif)

Quando la visualizzazione è in posizione, il passaggio successivo è la creazione di una configurazione dispositivo per quella specifica visualizzazione. Segui la sezione seguente per creare una nuova configurazione dispositivo.

>[!NOTE]
>
>**Passaggio successivo**:
>
>Dopo aver creato una visualizzazione per la posizione, è necessario assegnarle un canale affinché la visualizzazione sfrutti i contenuti.
>
>See [Assign Channels](channel-assignment.md) section to learn how to assign a channel to the display.

## Creazione di una nuova configurazione dispositivo {#creating-a-new-device-config}

Una configurazione dispositivo funge da segnaposto per un dispositivo di segnaletica digitale che non è non ancora stato installato.

Effettua le seguenti operazioni per creare una nuova configurazione dispositivo:

1. Andate alla visualizzazione appropriata, ad esempio `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Select your display folder and tap/click **View Dashboard** in the action bar.
1. Tap/click the **+ Add Device Config** on the top right of the **Devices** panel.

1. Select the **Device Config** as the required template as and tap/click **Next**.

1. Enter the properties as required and tap/click **Create**.

The device config is created and added to the current display (in the following demonstration, the new device config is *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Una volta impostata la configurazione dispositivo per la visualizzazione nella posizione, il passaggio successivo prevede l’assegnazione di un canale alla visualizzazione.

>[!NOTE]
>
>Una volta impostata la configurazione dispositivo per la visualizzazione nella posizione, il passaggio successivo prevede l’assegnazione di un canale alla visualizzazione.
>
>As shown in the figure below, if the device config is displayed as unassigned in the **DEVICES** pannel, if no channel is assigned to that particular device config.
>
>È necessario avere familiarità con le procedure di creazione e gestione di canali. Per ulteriori informazioni, consulta [Creazione e gestione di canali](managing-channels.md) .

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

Click on the (**...**) in the top right corner in the **DISPLAY INFORMATION **panel to view the properties and preview the display.

![chlimage_1-10](assets/chlimage_1-10.png)

#### Visualizzazione delle proprietà {#viewing-properties}

Fai clic su **Proprietà** per visualizzare o modificare le proprietà della visualizzazione.

Additionally, you can adjust the event timer value for your interactive channel in **Idle timeout **property under **Display** tab. Il valore predefinito è impostato su *300 secondi*.

Use **CRXDE Lite**, to access the **idleTimeout** property, that is, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .

![chlimage_1-1](assets/chlimage_1-1.gif)

### Pannello Canali Assegnati {#assigned-channels-panel}

Il pannello **CANALI ASSEGNATI** visualizza i canali assegnati a questo dispositivo.

![chlimage_1-11](assets/chlimage_1-11.png)

### Pannello Dispositivi {#devices-panel}

Il pannello **DISPOSITIVI** fornisce informazioni sulle configurazioni dispositivo.

Click on the (**...**) in the top right corner in the **DEVICES **panel to add device configs and update devices.

![chlimage_1-12](assets/chlimage_1-12.png)

Inoltre, fare clic sulla configurazione del dispositivo per visualizzare le proprietà, assegnare un dispositivo o eliminarlo completamente.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Passaggi successivi {#the-next-steps}

Dopo aver completato la creazione di una visualizzazione per la posizione, è necessario assegnare un canale alla visualizzazione.

See [Assign Channels](channel-assignment.md) for more details.
