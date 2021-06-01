---
title: Applicazione delle transizioni
seo-title: Applicazione delle transizioni
description: Segui questa pagina per scoprire come applicare le transizioni ai progetti Screens.
seo-description: Segui questa pagina per scoprire come applicare le transizioni ai progetti Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Creazione di esperienze in Screens
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 2%

---


# Applicazione delle transizioni {#applying-transitions}

Questa sezione descrive come applicare il componente **Transizione** tra diverse risorse (immagini e video) e sequenze incorporate in un canale.


>[!CAUTION]
>
>Per informazioni dettagliate sulle proprietà del componente **Transizione**, consulta [Transizioni](adding-components-to-a-channel.md#transition).

## Aggiunta di un componente di transizione alle risorse in un canale {#adding-transition}

Per aggiungere un componente di transizione al progetto AEM Screens, effettua le seguenti operazioni:

>[!NOTE]
>
>**Prerequisiti**
>
>Crea un progetto AEM Screens **TestProject** con un canale **TestTransition**. Inoltre, imposta una posizione e una visualizzazione per visualizzare l&#39;output.

1. Passa al Canale **TestTransition** e fai clic su **Modifica** dalla barra delle azioni.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >Il canale **TestTransition** contiene già poche risorse (immagini e video). Ad esempio, il canale **TestTransition** include tre immagini e due video, come mostrato di seguito:

   ![immagine2](assets/transitions2.png)


1. Trascina e rilascia il componente **Transizione** nell’editor.
   >[!CAUTION]
   >
   >Prima di aggiungere la transizione alle risorse nel canale, accertati di non aggiungere la transizione prima della prima risorsa nel canale sequenziale. Il primo elemento del canale deve essere una risorsa e non una transizione.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, le proprietà del componente di transizione come **Tipo** sono impostate su **Dissolvenza** e **Durata** sono impostate su *1600 ms*.  Inoltre, non è consigliabile impostare una durata di transizione maggiore della risorsa a cui viene applicata.

1. Inoltre, se aggiungi un componente **Sequenza incorporata** (che include un canale di sequenza) a questo editor di canali, puoi aggiungere un componente di transizione alla fine, in modo che il contenuto venga riprodotto in ordine, come illustrato nella figura seguente:

   ![image3](assets/transitions5.png)

