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
TQID: https://experienceleague.adobe.com/orHLShhCxLB8T9Dm8Vvihvy7GNGrmJQZt8toCPs5c3k
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: d8e42837-75d7-4e4e-accd-d0cdd8efe1f4id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 710
ht-degree: 1%

---

# Creazione e gestione delle visualizzazioni {#creating-and-managing-displays}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Un display è un raggruppamento virtuale di schermi posizionati uno accanto all’altro. Il display è fisso rispetto a un&#39;installazione. Si tratta degli autori di contenuti oggetto che lavorano con e a cui fanno sempre riferimento come visualizzazione logica piuttosto che come parti contatore fisiche.

Quando crei una posizione, devi crearne una visualizzazione specifica.

Questa pagina mostra come creare e gestire le visualizzazioni per Screens.

**Prerequisiti**:

* [Configurazione e distribuzione di Screens](configuring-screens-introduction.md)
* [Creazione e gestione di un progetto Screens](creating-a-screens-project.md)
* [Creare e gestire i canali](managing-channels.md)
* [Creare e gestire le posizioni](managing-locations.md)

## Creazione di una nuova visualizzazione {#creating-a-new-display}

>[!NOTE]
>
>Create una posizione prima di creare una visualizzazione. Per ulteriori informazioni, vedere [Crea e gestisci percorsi](managing-locations.md).

1. Passare alla posizione appropriata, ad esempio `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Fai clic sulla cartella del percorso e fai clic su **Crea** accanto all&#39;icona più (+) nella barra delle azioni.
1. Fai clic su **Visualizzazione** nella procedura guidata **Crea**, quindi fai clic su **Avanti**.
1. Immetti **Name** e **Title** per la posizione di visualizzazione.
1. Nella scheda **Visualizzazione** scegliere i dettagli del layout. Scegli la **Risoluzione** desiderata, ad esempio **Full HD**. Scegli il numero di dispositivi in orizzontale e in verticale.
1. Fai clic su **Crea**.

La visualizzazione (*StoreDisplay*) è stata creata e aggiunta al percorso (*SanJose*).

![visualizzazione](assets/display.gif)

Quando si dispone di una visualizzazione in posizione, il passaggio successivo consiste nel creare una configurazione di dispositivo per quella particolare visualizzazione.

>[!NOTE]
>
>**Passaggio successivo**:
>
>Quando crei una visualizzazione per la tua posizione, assegna un canale alla visualizzazione per utilizzare il contenuto.
>
>Consulta la sezione [Assegnare canali](channel-assignment.md) per scoprire come assegnare un canale alla visualizzazione.

## Creazione di una nuova configurazione dispositivo {#creating-a-new-device-config}

La configurazione di un dispositivo funge da segnaposto per un dispositivo di digital signage non ancora installato.

1. Passare alla visualizzazione appropriata, ad esempio `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Fai clic sulla cartella di visualizzazione e fai clic su **Visualizza dashboard** nella barra delle azioni.
1. Fai clic su **+ Aggiungi configurazione dispositivo** in alto a destra nel pannello **Dispositivi**.

1. Fare clic su **Configurazione dispositivo** come modello richiesto e fare clic su **Avanti**.

1. Immetti le proprietà richieste e fai clic su **Crea**.

La configurazione dispositivo viene creata e aggiunta alla visualizzazione corrente (nella seguente dimostrazione, la nuova configurazione dispositivo è *DeviceConfig*).

![configurazione dispositivo](assets/deviceconfig.gif)

>[!NOTE]
>
>Quando una configurazione dispositivo è impostata sulla visualizzazione nella posizione, il passaggio successivo consiste nell’assegnare un canale alla visualizzazione.
>
>Come mostrato nella figura seguente, se la configurazione del dispositivo viene visualizzata come non assegnata nel pannello **DEVICES**, nessun canale viene assegnato a quella particolare configurazione del dispositivo.
>
>Devi conoscere in anticipo i concetti relativi alla creazione e alla gestione dei canali. Per ulteriori dettagli, consulta [Creare e gestire i canali](managing-channels.md).

![chlimage_1-9](assets/chlimage_1-9.png)

## Dashboard di visualizzazione {#display-dashboard}

Il dashboard di visualizzazione offre diversi pannelli per la gestione dei dispositivi di visualizzazione. Consente inoltre di configurare il dispositivo.

![schermata_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Puoi fare clic sugli elenchi del dashboard e attivare azioni in blocco sugli elementi, invece di esaminare ogni elemento singolarmente.
>
>Ad esempio, l&#39;immagine seguente mostra come fare clic su più canali dal dashboard di visualizzazione.

![cqdoc9456](assets/cqdoc9456.gif)

### Schermo pannello informazioni {#display-information-panel}

Il pannello **INFORMAZIONI DI VISUALIZZAZIONE** fornisce le proprietà di visualizzazione.

Fare clic su (**...**) nell&#39;angolo in alto a destra nel pannello **VISUALIZZA INFORMAZIONI** per visualizzare le proprietà e l&#39;anteprima della visualizzazione.


#### Visualizzazione delle proprietà {#viewing-properties}

Fai clic su **Proprietà** per visualizzare o modificare le proprietà della visualizzazione.

Inoltre, puoi regolare il valore del timer dell&#39;evento per il tuo canale interattivo nella scheda **Visualizzazione**. Il valore predefinito è *300 secondi*.

Utilizza **CRXDE Lite** per accedere alla proprietà **idleTimeout**, ovvero `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### Pannello Canali assegnati {#assigned-channels-panel}

Nel pannello **CANALI ASSEGNATI** vengono visualizzati i canali assegnati a questo dispositivo.


### Pannello Dispositivi {#devices-panel}

Il pannello **DISPOSITIVI** fornisce informazioni sulle configurazioni dei dispositivi.

Fare clic su (**...**) nell&#39;angolo in alto a destra nel pannello **DISPOSITIVI**, in modo da poter aggiungere configurazioni di dispositivi e aggiornarli.

Inoltre, fai clic sulla configurazione del dispositivo per visualizzare le proprietà, assegnare un dispositivo o eliminarlo completamente.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Passaggi successivi {#the-next-steps}

Una volta completata la creazione di una visualizzazione per la posizione, assegnate un canale per la visualizzazione.

Vedi [Assegna canali](channel-assignment.md) per ulteriori dettagli.
