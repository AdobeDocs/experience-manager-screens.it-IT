---
title: Aggiornamento contenuti come servizio
description: Scopri come Aggiornare i contenuti come servizio.
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
TQID: https://experienceleague.adobe.com/p-13F7oySwiZfXHItW8zTIJRWiab5dOKxx-iU99vE9w
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 340
ht-degree: 0%

---

# Aggiornamento contenuti come servizio {#content-update-as-a-service}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Questa sezione tratta i seguenti argomenti sull’aggiornamento del contenuto come servizio:

* **Panoramica**
* **Utilizzo dell&#39;aggiornamento offline in blocco**

<!--
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission you can download it from Package Share. 
-->

## Panoramica {#overview}

L’aggiornamento in blocco offline consente di aggiornare tutti i canali in blocco. Evita il problema di navigare su un canale particolare e di aggiornare il contenuto. Piuttosto, puoi aggiornare tutti i contenuti in canali per un progetto specifico in un istante.

Puoi anche pianificare questa attività per un periodo di traffico di rete ridotto.

>[!NOTE]
>
>La funzione Aggiornamento offline in blocco è ottimizzata per aggiornare solo i canali che sono stati modificati.

## Utilizzo dell’aggiornamento offline in blocco {#using-bulk-offline-update}

Puoi utilizzare manualmente l’aggiornamento in blocco offline dall’interfaccia utente o pianificare l’aggiornamento in blocco dai servizi OSGi.

### Utilizzo dell’interfaccia utente di AEM Screens {#using-aem-screens-user-interface}

Per utilizzare l’aggiornamento offline in blocco per un progetto AEM Screens, effettua le seguenti operazioni:

1. Passa al progetto AEM Screens.
1. Fare clic sul progetto e fare clic su **Aggiorna contenuto offline** nella barra delle azioni per aggiornare manualmente il contenuto del canale.

   ![schermata_shot_2018-04-24alle122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configurazione console Web Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Per utilizzare l’aggiornamento offline in blocco per un progetto AEM Screens, effettua le seguenti operazioni:

1. Configurazione della console Web Adobe Experience Manager.
1. Cercare i servizi di aggiornamento offline in blocco.

   ![schermata_shot_2018-04-24alle121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Aggiungi le seguenti proprietà:

   **Percorso progetto** - Specifica il percorso del progetto AEM Screens. Il percorso è in genere `/content/screens/<Name of your project>`.

   *Ad esempio*, `/content/screens/we-retail`. Per trovare questo percorso nell’URL, seleziona qualsiasi progetto in AEM Screens (non fare clic sull’icona ).

   >[!NOTE]
   >
   >Specifica il percorso del progetto relativo al canale.

   **Frequenza pianificazione** - Specifica un&#39;ora, ad esempio 5:00 P.M. o 17:00, in cui il servizio deve aggiornare il contenuto offline.

1. Fai clic su **Salva** per salvare le impostazioni. Tutto il contenuto viene aggiornato all’ora specificata.

