---
title: Applicazione delle transizioni
description: Scopri come applicare le transizioni ai progetti AEM Screens.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
TQID: https://experienceleague.adobe.com/t4JTCyQhe7kb5v-dveK4Np9dAAGLBeatCN2kyTM6ELc
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: e8696a6a-4caa-4059-b0b2-3fbb66f5ab7e
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 0%

---

# Applicazione delle transizioni {#applying-transitions}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Questa sezione descrive come applicare il componente **Transizione** tra risorse diverse (immagini e video) e sequenze incorporate in un canale.

>[!CAUTION]
>
>Per informazioni dettagliate sulle proprietà del componente **Transizione**, vedere [Transizioni](adding-components-to-a-channel.md#transition).

## Aggiunta di un componente di transizione ad Assets in un canale {#adding-transition}

Per aggiungere un componente di transizione al progetto AEM Screens, segui i passaggi seguenti:

>[!NOTE]
>
>**Prerequisiti**
>
>Crea un progetto AEM Screens **TestProject** con un canale **TestTransition**. Inoltre, imposta una posizione e una visualizzazione per visualizzare l’output.

1. Passa al canale **TestTransition** e fai clic su **Modifica** nella barra delle azioni.

   ![immagine1](assets/transitions1.png)

   >[!NOTE]
   >
   >Il canale **TestTransition** contiene già alcune risorse (immagini e video). Ad esempio, il canale **TestTransition** include tre immagini e due video, come illustrato di seguito:

   ![immagine2](assets/transitions2.png)


1. Trascina e rilascia il componente **Transizione** nell&#39;editor.

   >[!CAUTION]
   >
   >Prima di aggiungere la transizione alle risorse nel canale, accertati di non aggiungere la transizione prima della prima risorsa nel canale sequenziale. Il primo elemento nel canale deve essere una risorsa e non una transizione.

   ![immagine3](assets/transitions3.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, le proprietà del componente di transizione come **Tipo** sono impostate su **Dissolvenza** e la **Durata** su *1600 millisecondi*. Inoltre, non è consigliabile impostare una durata di transizione più lunga della risorsa a cui viene applicata.

1. Inoltre, se aggiungi un componente **Sequenza incorporata** (che include un canale di sequenza) a questo editor canali, puoi aggiungere un componente di transizione alla fine. In questo modo il contenuto viene riprodotto nell’ordine corretto, come illustrato nell’immagine seguente:

   ![immagine3](assets/transitions5.png)

