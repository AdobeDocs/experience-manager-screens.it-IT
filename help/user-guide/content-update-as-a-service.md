---
title: Aggiornamento dei contenuti come servizio
seo-title: Aggiornamento dei contenuti come servizio
description: Segui questa pagina per informazioni su Aggiornamento dei contenuti come servizio.
seo-description: Segui questa pagina per informazioni su Aggiornamento dei contenuti come servizio.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
feature: Creazione di esperienze in Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 8%

---

# Aggiornamento dei contenuti come servizio {#content-update-as-a-service}

Questa sezione tratta i seguenti argomenti sull’aggiornamento di content-as-a-service:

* **Panoramica**
* **Utilizzo dell&#39;aggiornamento offline in blocco**

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se hai installato AEM Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

Aggiornamento offline bulk, ti consente di aggiornare tutti i canali in blocco. Evita la difficoltà di navigare in un particolare canale e di aggiornare il contenuto. Puoi invece aggiornare tutti i contenuti nei canali per un progetto specifico in un solo istante.

Puoi anche pianificare questa attività per un periodo di traffico di rete inferiore.

>[!NOTE]
>
>La funzione Aggiornamento offline in blocco è ottimizzata per aggiornare solo i canali modificati.

## Utilizzo dell&#39;aggiornamento offline in blocco {#using-bulk-offline-update}

Puoi utilizzare manualmente l’aggiornamento offline in blocco dall’interfaccia utente o pianificare l’aggiornamento in blocco dai servizi OSGi.

### Utilizzo dell’interfaccia utente di AEM Screens {#using-aem-screens-user-interface}

Per utilizzare l’aggiornamento offline in blocco per un progetto AEM Screens, effettua le seguenti operazioni:

1. Passa al progetto AEM Screens.
1. Seleziona il progetto e fai clic su **Aggiorna contenuto offline** nella barra delle azioni per aggiornare manualmente il contenuto del canale.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configurazione della console Web di Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Per utilizzare l’aggiornamento offline in blocco per un progetto AEM Screens, effettua le seguenti operazioni:

1. Configurazione della console Web Adobe Experience Manager.
1. Cerca servizi di aggiornamento offline in blocco.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Aggiungi le seguenti proprietà:

   **Percorso** progettoSpecifica il percorso del progetto AEM Screens. In genere il percorso è `/content/screens/<Name of your project>`.

   *Esempio*, `/content/screens/we-retail`. Puoi trovare questo percorso nell’URL selezionando qualsiasi progetto in AEM Screens (non fare clic sull’icona).

   >[!NOTE]
   >
   >Specifica il percorso del progetto relativo al canale.

   **Pianificazione** FrequenzaSpecifica un&#39;ora, ad esempio le 17:00 o le 17:00, in cui il servizio deve aggiornare il contenuto offline.

1. Fai clic su **Salva** per salvare le impostazioni e il contenuto verrà aggiornato all&#39;ora specificata.
