---
title: Applicazione delle transizioni
seo-title: Applicazione delle transizioni
description: Segui questa pagina per apprendere come applicare le transizioni ai tuoi progetti Screens.
seo-description: Segui questa pagina per apprendere come applicare le transizioni ai tuoi progetti Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f6ee043e41e46690e057758266f9adc5323001d2

---


# Applicazione delle transizioni {#applying-transitions}

Questa sezione descrive come applicare il componente **Transizione** tra risorse diverse (immagini e video) e sequenze incorporate in un canale.


>[!CAUTION]
>
>Per informazioni dettagliate sulle proprietà del componente **Transizione** , vedere [Transizioni](adding-components-to-a-channel.md#transition).

## Aggiunta di un componente di transizione alle risorse di un canale {#adding-transition}

Per aggiungere un componente di transizione al progetto AEM Screens, procedi come segue:

>[!NOTE]
>
>**Prerequisiti**
> Crea un progetto AEM Screens **TestProject** con un canale **TestTransition**. Inoltre, configurate una posizione e una visualizzazione per visualizzare l'output.

1. Andate al Channel **TestTransition** e fate clic su **Edit** dalla barra delle azioni.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >Il canale **TestTransition** contiene già poche risorse (immagini e video). Ad esempio, il canale **TestTransition** include tre immagini e due video, come mostrato di seguito:

   ![image2](assets/transitions2.png)


1. Trascinate e rilasciate il componente **Transizione** nell’editor.
   >[!CAUTION]
   >
   >Prima di aggiungere la transizione alle risorse del canale, accertatevi di non aggiungere la transizione prima della prima risorsa del canale sequenziale. Il primo elemento nel canale deve essere una risorsa e non una transizione.

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >Per impostazione predefinita, le proprietà del componente di transizione, ad esempio **Tipo** , sono impostate su **Normale** e la **Durata** è impostata su *600 ms*.  Inoltre, non è consigliabile impostare una durata di transizione maggiore della risorsa a cui viene applicata.

1. Inoltre, se aggiungete un componente Sequenza **** incorporata (che include un canale di sequenza) a questo editor canale, potete aggiungere un componente di transizione alla fine, in modo che il contenuto venga riprodotto in ordine, come illustrato nella figura seguente:

   ![image3](assets/transitions5.png)

## Aggiunta di un componente Transizione ai video in un canale {#adding-transition-videos}

Quando applicate un componente di transizione tra i video, si consiglia di impostare **Tipo** su **Dissolvenza** e Durata **** sequenza su **1600 ms**.

![image3](assets/transitions4.png)
