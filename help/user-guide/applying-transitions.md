---
title: Applicazione delle transizioni
seo-title: Applying Transitions
description: Segui questa pagina per scoprire come applicare le transizioni ai progetti Screens.
seo-description: Follow this page to learn how to apply transitions to your Screens projects.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---

# Applicazione delle transizioni {#applying-transitions}

Questa sezione descrive come applicare **Transizione** componente intermedio tra risorse diverse (immagini e video) e sequenze incorporate in un canale.


>[!CAUTION]
>
>Per informazioni dettagliate sulle proprietà di **Transizione** componente, fare riferimento a [Transizioni](adding-components-to-a-channel.md#transition).

## Aggiunta di un componente di transizione alle risorse in un canale {#adding-transition}

Per aggiungere un componente di transizione al progetto AEM Screens, segui i passaggi seguenti:

>[!NOTE]
>
>**Prerequisiti**
>
>Creazione di un progetto AEM Screens **TestProject** con un canale **TestTransition**. Inoltre, impostate una posizione e una visualizzazione per visualizzare l&#39;output.

1. Passa al canale **TestTransition** e fai clic su **Modifica** dalla barra delle azioni.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >Il **TestTransition** il canale contiene già poche risorse (immagini e video). Ad esempio, il **TestTransition** il canale include tre immagini e due video, come illustrato di seguito:

   ![image2](assets/transitions2.png)


1. Trascina la **Transizione** all&#39;editor.
   >[!CAUTION]
   >
   >Prima di aggiungere la transizione alle risorse nel canale, accertati di non aggiungere la transizione prima della prima risorsa nel canale sequenziale. Il primo elemento nel canale deve essere una risorsa e non una transizione.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, le proprietà del componente Transizione come **Tipo** è impostato su **Dissolvenza** e **Durata** è impostato su *1600 ms*.  Inoltre, non è consigliabile impostare una durata di transizione superiore a quella della risorsa a cui viene applicata.

1. Inoltre, se aggiungi un’ **Sequenza incorporata** componente (che include un canale di sequenza) di questo editor di canali, puoi aggiungere un componente di transizione alla fine, in modo che il contenuto venga riprodotto in ordine, come illustrato nella figura seguente:

   ![image3](assets/transitions5.png)
