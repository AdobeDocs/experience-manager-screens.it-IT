---
title: Creazione e gestione delle visualizzazioni
description: Scopri come creare una configurazione di display e dispositivi in AEM Screens. Inoltre, scopri il dashboard di visualizzazione.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Creazione e gestione delle visualizzazioni {#creating-and-managing-displays}

Un display è un raggruppamento virtuale di schermi posizionati uno accanto all’altro. Il display è fisso rispetto a un&#39;installazione. Si tratta degli autori di contenuti oggetto che lavorano con e a cui fanno sempre riferimento come visualizzazione logica piuttosto che come parti contatore fisiche.

Quando crei una posizione, devi crearne una visualizzazione specifica.

Questa pagina mostra come creare e gestire le visualizzazioni di Screens.

**Prerequisiti**:

* [Configurazione e distribuzione di Screens](configuring-screens-introduction.md)
* [Creare e gestire un progetto Screens](creating-a-screens-project.md)
* [Creare e gestire i canali](managing-channels.md)
* [Creare e gestire le posizioni](managing-locations.md)

## Creazione di una nuova visualizzazione {#creating-a-new-display}

>[!NOTE]
>
>Create una posizione prima di creare una visualizzazione. Consulta [Creare e gestire le posizioni](managing-locations.md) per ulteriori informazioni.

1. Passa alla posizione appropriata, ad esempio `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Fai clic sulla cartella del percorso e fai clic su **Crea** che si trova accanto all’icona più nella barra delle azioni.
1. Clic **Visualizzazione** dal **Crea** procedura guidata, quindi fai clic su **Successivo**.
1. Immetti il **Nome** e **Titolo** per la posizione di visualizzazione.
1. Sotto **Visualizzazione** , scegliere i dettagli del layout. Scegli il **Risoluzione**, ad esempio **Full HD**. Scegli il numero di dispositivi in orizzontale e in verticale.
1. Fai clic su **Crea**.

Visualizzazione (*StoreDisplay*) viene creato e aggiunto alla posizione (*SanJose*).

![visualizzare](assets/display.gif)

Quando si dispone di una visualizzazione in posizione, il passaggio successivo consiste nel creare una configurazione di dispositivo per quella particolare visualizzazione.

>[!NOTE]
>
>**Passaggio successivo**:
>
>Quando crei una visualizzazione per la tua posizione, assegna un canale alla visualizzazione per utilizzare il contenuto.
>
>Consulta la [Assegna canali](channel-assignment.md) per scoprire come assegnare un canale alla visualizzazione.

## Creazione di una nuova configurazione dispositivo {#creating-a-new-device-config}

La configurazione di un dispositivo funge da segnaposto per un dispositivo di digital signage non ancora installato.

1. Passa alla visualizzazione appropriata, ad esempio: `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Fai clic sulla cartella di visualizzazione e fai clic su **Visualizza dashboard** nella barra delle azioni.
1. Clic **+ Aggiungi configurazione dispositivo** in alto a destra nella **Dispositivi** pannello.

1. Fai clic su **Configurazione dispositivo** come modello richiesto, come e fai clic su **Successivo**.

1. Immetti le proprietà richieste e fai clic su **Crea**.

La configurazione del dispositivo viene creata e aggiunta alla visualizzazione corrente (nella seguente dimostrazione, la nuova configurazione del dispositivo è *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>Quando una configurazione dispositivo è impostata sulla visualizzazione nella posizione, il passaggio successivo consiste nell’assegnare un canale alla visualizzazione.
>
>Come mostrato nella figura seguente, se la configurazione del dispositivo viene visualizzata come non assegnata nel **DISPOSITIVI** nel caso in cui non sia stato assegnato alcun canale alla specifica configurazione del dispositivo.
>
>Devi conoscere in anticipo i concetti relativi alla creazione e alla gestione dei canali. Consulta [Creare e gestire i canali](managing-channels.md) per ulteriori dettagli.

![chlimage_1-9](assets/chlimage_1-9.png)

## Dashboard di visualizzazione {#display-dashboard}

Il dashboard di visualizzazione offre diversi pannelli per la gestione dei dispositivi di visualizzazione. Consente inoltre di configurare il dispositivo.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Puoi fare clic sugli elenchi del dashboard e attivare azioni in blocco sugli elementi, invece di esaminare ogni elemento singolarmente.
>
>Ad esempio, l&#39;immagine seguente mostra come fare clic su più canali dal dashboard di visualizzazione.

![cqdoc9456](assets/cqdoc9456.gif)

### Schermo pannello informazioni {#display-information-panel}

Il **INFORMAZIONI SULLA VISUALIZZAZIONE** Il pannello fornisce le proprietà di visualizzazione.

Fai clic su (**...**) nell&#39;angolo in alto a destra nella **INFORMAZIONI SULLA VISUALIZZAZIONE** per visualizzare le proprietà e visualizzare l&#39;anteprima della visualizzazione.


#### Visualizzazione delle proprietà {#viewing-properties}

Clic **Proprietà** in modo da poter visualizzare o modificare le proprietà dello schermo.

Inoltre, puoi regolare il valore del timer dell’evento per il canale interattivo sotto il **Visualizzazione** scheda. Il valore predefinito è impostato su *300 secondi*.

Utilizzare **CRXDE Liti**, per accedere al **idleTimeout** proprietà, ovvero `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### Pannello Canali assegnati {#assigned-channels-panel}

Il **CANALI ASSEGNATI** nel pannello vengono visualizzati i canali assegnati al dispositivo.


### Pannello Dispositivi {#devices-panel}

Il **DISPOSITIVI** Il pannello fornisce informazioni sulle configurazioni del dispositivo.

Fai clic su (**...**) nell&#39;angolo in alto a destra nella **DISPOSITIVI** per aggiungere configurazioni di dispositivi e aggiornare i dispositivi.

Inoltre, fai clic sulla configurazione del dispositivo per visualizzare le proprietà, assegnare un dispositivo o eliminarlo completamente.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Passaggi successivi {#the-next-steps}

Una volta completata la creazione di una visualizzazione per la posizione, assegnate un canale per la visualizzazione.

Consulta [Assegna canali](channel-assignment.md) per ulteriori dettagli.
