---
title: Caso di utilizzo di transizioni tra zona singola e zona multipla
description: Segui questa pagina per saperne di più sul caso d’uso MultiZone to SingleZone Transitions.
seo-description: Caso di utilizzo delle transizioni da MultiZone a SingleZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3

---


# Transizione da zona a zona singola {#multizone-to-singlezone-use-case}


## Descrizione di un caso d’uso {#use-case-description}

In questa sezione viene illustrato un esempio di utilizzo che mette in evidenza come impostare un canale di layout con più zone che si alterna con un canale di layout a zona singola. Il canale multi-zona dispone di risorse immagine/video in sequenza e mostra come impostare un progetto che si alterna da una zona a più zone a una singola zona e viceversa.

### Premesse {#preconditions}

Prima di iniziare questo caso di utilizzo, accertatevi di comprendere come:

* **[Creare e gestire canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori primari {#primary-actors}

Autori contenuto

## Impostazione del progetto {#setting-up-the-project}

Per impostare un progetto, effettuate le seguenti operazioni:

1. Crea un progetto AEM Screens denominato **TakeoverLoop**, come mostrato di seguito.

   ![risorsa](assets/mz-to-sz1.png)


1. **Creazione di un canale per schermi con più aree**

   1. Selezionate la cartella **Canali** e fate clic su **Crea** dalla barra delle azioni per aprire la procedura guidata per creare un canale.
   1. Selezionate **Sinistra-L Barra Dividi canale** schermo dalla procedura guidata e create il canale denominato **MultiZoneLayout**.
   1. Aggiungete contenuti al canale. Trascinate e rilasciate le risorse in ciascuna area. L’esempio seguente mostra un canale **MultiZoneLayout** composto da un video, un’immagine e un banner di testo (in una sequenza incorporata), come mostrato di seguito.
   ![risorsa](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un layout a più zone nel canale, consultate Layout [a](multi-zone-layout-aem-screens.md)più aree.


1. Crea un altro canale denominato **TakeoverChannel** nella cartella **Channels (Canali** ).

   ![risorsa](assets/mz-to-sz3.png)

1. Fai clic su **Modifica** dalla barra delle azioni per aggiungere contenuto a questo canale. Aggiungete a questo canale un componente **Canale** e una risorsa immagine a cui desiderate passare, come illustrato nella figura seguente:

   ![risorsa](assets/mz-to-sz4.png)

1. Aprite le impostazioni per il componente Canale e puntatelo al canale **MultiZoneLayout** creato al *punto 2*.

   ![risorsa](assets/mz-to-sz5.png)

1. Impostate la durata dal campo **Sequenza** a **10000 ms**.

   ![risorsa](assets/mz-to-sz6.png)

1. Allo stesso modo, aprite le impostazioni per l’immagine (risorsa aggiunta) e impostatene la durata dal campo **Sequenza** a **3000 ms**.

   ![risorsa](assets/mz-to-sz7.png)

## Verifica dell’anteprima {#checking-the-preview}

È possibile visualizzare l&#39;output desiderato dal lettore o semplicemente facendo clic su **Anteprima** dall&#39;editor.

L&#39;output mostra come viene riprodotto un layout a più zone per *10000 ms* , quindi passa al layout a zona singola con una durata di riproduzione di *3000 ms* e quindi al layout a più zone.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Potete personalizzare la transizione del canale (da un layout con più zone a un layout a zona singola o viceversa) in base alle vostre esigenze.