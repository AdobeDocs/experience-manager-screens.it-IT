---
title: Caso di utilizzo di transizioni tra zona singola e zona multipla
description: Segui questa pagina per saperne di più sul caso d’uso MultiZone to SingleZone Transitions.
seo-description: Caso di utilizzo delle transizioni da MultiZone a SingleZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 2%

---


# Transizione da zona a zona singola {#multizone-to-singlezone-use-case}


## Descrizione di un caso d’uso {#use-case-description}

In questa sezione viene illustrato un esempio di utilizzo che mette in evidenza come impostare un canale di layout con più zone che si alterna con un canale di layout a zona singola. Il canale multizona dispone di risorse video/immagine in sequenza e mostra come impostare un progetto che si alterni da una zona a più zone a una singola zona e viceversa.

### Precondizioni {#preconditions}

Prima di iniziare questo caso di utilizzo, accertatevi di comprendere come:

* **[Creazione e gestione di canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori primari {#primary-actors}

Autori contenuto

## Impostazione del progetto {#setting-up-the-project}

Per impostare un progetto, effettuate le seguenti operazioni:

1. Create un progetto AEM Screens  denominato **TakeoverLoop**, come illustrato di seguito.

   ![risorsa](assets/mz-to-sz1.png)


1. **Creazione di un canale per schermi con più aree**

   1. Selezionate la cartella **Channels** e fate clic su **Create** dalla barra delle azioni per aprire la procedura guidata e creare un canale.
   1. Selezionare **Left-L Bar Split Screen Channel** dalla procedura guidata e creare il canale denominato **MultiZoneLayout**.
   1. Aggiungete contenuti al canale. Trascinate e rilasciate le risorse in ciascuna area. L&#39;esempio seguente mostra un canale **MultiZoneLayout** composto da un video, un&#39;immagine e un banner di testo (in una sequenza incorporata), come mostrato di seguito.

   ![risorsa](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un layout a più zone nel canale, fare riferimento a [Layout a più zone](multi-zone-layout-aem-screens.md).


1. Create un altro canale denominato **TakeoverChannel** nella cartella **Channels**.

   ![risorsa](assets/mz-to-sz3.png)

1. Fare clic su **Modifica** dalla barra delle azioni per aggiungere contenuti a questo canale. Aggiungete a questo canale un componente **Canale** e una risorsa immagine a cui desiderate passare, come illustrato nella figura seguente:

   ![risorsa](assets/mz-to-sz4.png)

1. Aprite le impostazioni per il componente Canale e puntatelo al canale **MultiZoneLayout** creato in *passaggio 2*.

   ![risorsa](assets/mz-to-sz5.png)

1. Impostare la durata dal campo **Sequence** su **10000 ms**.

   ![risorsa](assets/mz-to-sz6.png)

1. Allo stesso modo, aprite le impostazioni per l&#39;immagine (risorsa aggiunta) e impostate la durata del campo **Sequence** su **3000 ms**.

   ![risorsa](assets/mz-to-sz7.png)

## Controllo dell&#39;anteprima {#checking-the-preview}

È possibile visualizzare l&#39;output desiderato dal lettore o semplicemente facendo clic su **Preview** dall&#39;editor.

L&#39;output mostra come viene riprodotto un layout a più zone per *10000 ms*, quindi passa al layout a zona singola con una durata di riproduzione di *3000 ms* e quindi al layout a più zone.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Potete personalizzare la transizione del canale (da un layout con più zone a un layout a zona singola o viceversa) in base alle vostre esigenze.