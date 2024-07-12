---
title: 'Caso di utilizzo: transizioni da MultiZone a SingleZone'
description: Segui questa pagina per scoprire il caso d’uso MultiZone sulle transizioni SingleZone.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# Transizione da più zone a zona singola {#multizone-to-singlezone-use-case}

## Descrizione del caso d’uso {#use-case-description}

Questa sezione descrive un esempio di caso d’uso che evidenzia come impostare un canale di layout multizona alternativo a un canale di layout a zona singola. Il canale multizona dispone di risorse video/immagini di sequenziamento e mostra come impostare un progetto che si alterni da più zone a una singola zona e viceversa.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di aver compreso come:

* **[Crea e gestisci canali](managing-channels.md)**
* **[Crea e gestisci posizioni](managing-locations.md)**
* **[Crea e gestisci pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Configurazione del progetto {#setting-up-the-project}

Per impostare un progetto, segui i passaggi seguenti:

1. Crea un progetto AEM Screens denominato **TakeoverLoop**, come illustrato di seguito.

   ![risorsa](assets/mz-to-sz1.png)


1. **Creazione di un canale Screens con più zone**

   1. Fai clic sulla cartella **Canali** e fai clic su **Crea** nella barra delle azioni, quindi apri la procedura guidata per creare un canale.
   1. Fare clic su **Canale schermo diviso barra sinistra** dalla procedura guidata e creare il canale con titolo **MultiZoneLayout**.
   1. Aggiungi contenuto al canale. Trascina e rilascia le risorse in ciascuna zona. L&#39;esempio seguente mostra un canale **MultiZoneLayout** che include un video, un&#39;immagine e un banner di testo (in una sequenza incorporata), come illustrato di seguito.

   ![risorsa](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un layout multizona nel canale, vedere [Layout multizona](multi-zone-layout-aem-screens.md).


1. Crea un altro canale con titolo **Canale di acquisto** nella cartella **Canali**.

   ![risorsa](assets/mz-to-sz3.png)

1. Fai clic su **Modifica** nella barra delle azioni per aggiungere contenuti a questo canale. Aggiungi un componente **Canale** e una risorsa immagine a cui vuoi passare per questo canale, come illustrato nella figura seguente:

   ![risorsa](assets/mz-to-sz4.png)

1. Aprire le impostazioni del componente Canale e puntarlo al canale **MultiZoneLayout** creato in *passaggio 2*.

   ![risorsa](assets/mz-to-sz5.png)

1. Imposta la durata del campo **Sequenza** su **10000 millisecondi**.

   ![risorsa](assets/mz-to-sz6.png)

1. Allo stesso modo, apri le impostazioni per l&#39;immagine (risorsa aggiunta) e impostane la durata dal campo **Sequenza** a **3000 millisecondi**.

   ![risorsa](assets/mz-to-sz7.png)

## Controllo dell’anteprima {#checking-the-preview}

Puoi visualizzare l&#39;output desiderato dal lettore o semplicemente selezionando **Anteprima** dall&#39;editor.

L&#39;output mostra come viene eseguito un layout multizona per *10000 millisecondi*. Quindi, passa a un layout a zona singola con una durata di riproduzione di *3000 millisecondi*. Infine, torna al layout multizona.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>È possibile personalizzare la transizione dei canali (dal layout multizona a quello a zona singola o viceversa) in base alle proprie esigenze.
