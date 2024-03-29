---
title: 'Caso di utilizzo: transizione da MultiZone a SingleZone'
description: Segui questa pagina per scoprire il caso d’uso MultiZone sulle transizioni SingleZone.
seo-description: MultiZone to SingleZone Transitions use case.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 3%

---

# Transizione da più zone a zona singola {#multizone-to-singlezone-use-case}


## Descrizione del caso d’uso {#use-case-description}

Questa sezione descrive un esempio di caso d’uso che evidenzia come impostare un canale di layout multizona alternativo a un canale di layout a zona singola. Il canale multizona dispone di risorse immagine/video in sequenza e mostra come impostare un progetto che si alterna da più zone a una singola zona e viceversa.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di aver compreso come:

* **[Creare e gestire i canali](managing-channels.md)**
* **[Creare e gestire le posizioni](managing-locations.md)**
* **[Creare e gestire gli Schedules](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Configurazione del progetto {#setting-up-the-project}

Per impostare un progetto, segui i passaggi seguenti:

1. Creare un progetto AEM Screens denominato come **TakeoverLoop**, come illustrato di seguito.

   ![risorsa](assets/mz-to-sz1.png)


1. **Creazione di un canale schermi con più zone**

   1. Seleziona la **Canali** cartella e fai clic su **Crea** dalla barra delle azioni per aprire la procedura guidata per creare un canale.
   1. Seleziona **Canale schermo diviso barra sinistra-L** dalla procedura guidata e crea il canale con titolo **LayoutZonaMultiplo**.
   1. Aggiungi contenuto al canale. Trascina e rilascia le risorse in ciascuna zona. L’esempio seguente mostra una **LayoutZonaMultiplo** canale composto da un video, un’immagine e un banner di testo (in una sequenza incorporata), come mostrato di seguito.

   ![risorsa](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un layout multizona nel canale, consulta [Layout multizona](multi-zone-layout-aem-screens.md).


1. Crea un altro canale con titolo **TakeoverChannel** al tuo **Canali** cartella.

   ![risorsa](assets/mz-to-sz3.png)

1. Clic **Modifica** dalla barra delle azioni per aggiungere contenuto a questo canale. Aggiungi un **Canale** e una risorsa di immagine a cui passare, a questo canale, come illustrato nella figura seguente:

   ![risorsa](assets/mz-to-sz4.png)

1. Apri le impostazioni del componente Canale e puntale al **LayoutZonaMultiplo** canale creato in *passaggio 2*.

   ![risorsa](assets/mz-to-sz5.png)

1. Imposta la durata da **Sequenza** campo a **10000 ms**.

   ![risorsa](assets/mz-to-sz6.png)

1. Allo stesso modo, apri le impostazioni per l’immagine (risorsa aggiunta) e impostane la durata dal campo **Sequenza** campo a **3000 ms**.

   ![risorsa](assets/mz-to-sz7.png)

## Controllo dell’anteprima {#checking-the-preview}

Puoi visualizzare l’output desiderato dal lettore o semplicemente facendo clic sul pulsante **Anteprima** dall’editor.

L’output mostra come viene riprodotto un layout multizona per *10000 ms* e quindi passa al layout a zona singola con durata di riproduzione di *3000 ms* e quindi torna al layout multizona.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>È possibile personalizzare la transizione dei canali (dal layout multisito a quello a zona singola o viceversa) in base alle proprie esigenze.
