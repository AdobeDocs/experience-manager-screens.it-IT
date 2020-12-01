---
title: Aggiornamento del contenuto come servizio
seo-title: Aggiornamento del contenuto come servizio
description: Segui questa pagina per saperne di più su Content Update As a Service.
seo-description: Segui questa pagina per saperne di più su Content Update As a Service.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
translation-type: tm+mt
source-git-commit: 323e2df2419cc65de7bfe88648ffd1dbd3a91aec
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 8%

---


# Aggiornamento dei contenuti come servizio {#content-update-as-a-service}

Questa sezione illustra i seguenti argomenti relativi all’aggiornamento del contenuto come servizio:

* **Panoramica**
* **Utilizzo dell&#39;aggiornamento offline in blocco**

>[!CAUTION]
>
>Questa funzionalità  AEM Screens è disponibile solo se è stato installato AEM Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

Aggiornamento offline in blocco, consente di aggiornare tutti i canali in massa. Consente di evitare la difficoltà di spostarsi su un canale specifico e di aggiornare il contenuto. Potete invece aggiornare tutti i contenuti dei canali per un progetto specifico in un istante.

Potete anche pianificare questa attività per un periodo di tempo con traffico di rete inferiore.

>[!NOTE]
>
>La funzione Aggiornamento offline in blocco è ottimizzata per aggiornare solo i canali che sono stati modificati.

## Utilizzo dell&#39;aggiornamento offline in blocco {#using-bulk-offline-update}

Potete utilizzare manualmente l’aggiornamento offline in blocco dall’interfaccia utente o pianificare l’aggiornamento in blocco dai servizi OSGi.

### Utilizzo  interfaccia utente AEM Screens {#using-aem-screens-user-interface}

Per utilizzare l&#39;aggiornamento offline in blocco per un progetto AEM Screens , effettuate le seguenti operazioni:

1. Andate al progetto AEM Screens .
1. Selezionate il progetto e fate clic su **Aggiorna contenuto offline** nella barra delle azioni per aggiornare manualmente il contenuto del canale.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configurazione della console Web Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Per utilizzare l&#39;aggiornamento offline in blocco per un progetto AEM Screens , effettuate le seguenti operazioni:

1. Configurazione della console Web di Adobe Experience Manager.
1. Cercare servizi di aggiornamento offline in massa.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Aggiungete le seguenti proprietà:

   **Percorso** progetto: consente di specificare il percorso del progetto AEM Screens . In genere il percorso è `/content/screens/<Name of your project>`.

   *Esempio*, `/content/screens/we-retail`. Potete trovare questo percorso nell’URL selezionando un progetto qualsiasi in  AEM Screens (non fate clic sull’icona).

   >[!NOTE]
   >
   >Specificate il percorso del progetto relativo al canale.

   **Pianificazione** frequenza: specificate l&#39;ora, ad esempio, alle 17:00 o alle 17:00 in cui il servizio deve aggiornare il contenuto offline.

1. Fare clic su **Salva** per salvare le impostazioni e il contenuto verrà aggiornato al momento specificato.

