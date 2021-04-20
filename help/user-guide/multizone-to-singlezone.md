---
title: Caso di utilizzo delle transizioni da MultiZone a SingleZone
description: Segui questa pagina per scoprire il caso d’uso MultiZone to SingleZone Transitions.
seo-description: 'Caso di utilizzo: Transizioni da MultiZone a SingleZone.'
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, Business Practitioner
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 3%

---


# Transizione da più aree a più aree {#multizone-to-singlezone-use-case}


## Descrizione di un caso d’uso {#use-case-description}

Questa sezione descrive un esempio di caso d’uso che sottolinea come impostare un canale di layout con più aree che si alterna con un canale di layout a una sola zona. Il canale con più aree ha la sequenza di risorse immagine/video e mostra come impostare un progetto che si alterna da più aree a una singola zona e viceversa.

### Precondizioni {#preconditions}

Prima di iniziare questo caso d’uso, assicurati di comprendere come:

* **[Creare e gestire i canali](managing-channels.md)**
* **[Creare e gestire posizioni](managing-locations.md)**
* **[Creare e gestire le pianificazioni](managing-schedules.md)**
* **[Registrazione dispositivo](device-registration.md)**

### Attori principali {#primary-actors}

Autori di contenuti

## Configurazione del progetto {#setting-up-the-project}

Per impostare un progetto, effettua le seguenti operazioni:

1. Crea un progetto AEM Screens denominato **TakeoverLoop**, come mostrato di seguito.

   ![risorsa](assets/mz-to-sz1.png)


1. **Creazione di un canale per schermi multi-aree**

   1. Seleziona la cartella **Canali** e fai clic su **Crea** nella barra delle azioni per aprire la procedura guidata per creare un canale.
   1. Seleziona **Canale schermo diviso a barre sinistro-L** dalla procedura guidata e crea il canale denominato **MultiZoneLayout**.
   1. Aggiungi il contenuto al canale. Trascina e rilascia le risorse in ciascuna zona. L&#39;esempio seguente mostra un canale **MultiZoneLayout** composto da un video, un&#39;immagine e un banner di testo (in una sequenza incorporata), come mostrato di seguito.

   ![risorsa](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un layout a più aree nel canale, consulta [Layout a più aree](multi-zone-layout-aem-screens.md).


1. Crea un altro canale denominato **TakeoverChannel** nella cartella **Canali**.

   ![risorsa](assets/mz-to-sz3.png)

1. Fai clic su **Modifica** nella barra delle azioni per aggiungere contenuto a questo canale. Aggiungi a questo canale un componente **Canale** e una risorsa immagine a cui desideri passare, come illustrato nella figura seguente:

   ![risorsa](assets/mz-to-sz4.png)

1. Apri le impostazioni del componente Canale e puntale al canale **MultiZoneLayout** creato in *passaggio 2*.

   ![risorsa](assets/mz-to-sz5.png)

1. Imposta la durata dal campo **Sequenza** su **10000 ms**.

   ![risorsa](assets/mz-to-sz6.png)

1. Allo stesso modo, apri le impostazioni per l’immagine (risorsa aggiunta) e imposta la sua durata dal campo **Sequenza** a **3000 ms**.

   ![risorsa](assets/mz-to-sz7.png)

## Controllo dell&#39;anteprima {#checking-the-preview}

Puoi visualizzare l&#39;output desiderato dal lettore o semplicemente facendo clic su **Anteprima** dall&#39;editor.

L&#39;output mostrerà come viene riprodotto un layout a più zone per *10000 ms* e quindi passa al layout a zona singola con una durata di riproduzione di *3000 ms* e quindi torna al layout a più zone.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Puoi personalizzare la transizione del canale (dal layout a più aree al layout a zona singola o viceversa) in base alle tue esigenze.