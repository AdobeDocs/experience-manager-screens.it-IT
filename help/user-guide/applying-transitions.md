---
title: Applicazione delle transizioni
seo-title: Applicazione delle transizioni
description: Segui questa pagina per apprendere come applicare le transizioni ai tuoi progetti Screens.
seo-description: Segui questa pagina per apprendere come applicare le transizioni ai tuoi progetti Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 02acf7ffc447c92efb75d756071d2cd5f4aaf104

---


# Applicazione delle transizioni {#applying-transitions}

Questa sezione descrive come un componente **Transizione** consente di aggiungere una transizione al progetto Screens.


>[!CAUTION]
>
>Per informazioni dettagliate sulle proprietà del componente Transizione, vedere [Transizioni](adding-components-to-a-channel.md#transition)

## Aggiunta di un componente Transizione {#adding-transition}

Per aggiungere un componente di transizione al progetto AEM Screens, procedi come segue:

>[!NOTE]
>
>**Prerequisiti**
> Crea un progetto AEM Screens **TestProject** con un canale **TestTransition**. Inoltre, configurate una posizione e una visualizzazione per visualizzare l'output.

1. Andate al Channel **TestTransition** e fate clic su **Edit** dalla barra delle azioni.



   >[!NOTE]
   >
   >Il canale **TestTransition** contiene già poche risorse (immagini e video). Ad esempio, il canale **TestTransition** include cinque immagini e un video, come mostrato di seguito:



1. Trascinate e rilasciate il componente **Transizione** nell’editor.

   > [!NOTE]
   >
   >Per impostazione predefinita, il componente di transizione è impostato su Tipo come **Normale** con **Durata** impostata su *600 ms*.


   >[!CAUTION]
   >
   >Prima di aggiungere la transizione alle risorse del canale, accertatevi di:
Non si aggiunge la transizione prima della prima risorsa nel canale sequenziale. Il primo elemento nel canale deve essere una risorsa e non una transizione.
