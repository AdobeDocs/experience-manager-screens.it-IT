---
title: Aggiornamento offline in blocco
seo-title: Aggiornamento offline in blocco
description: Segui questa pagina per scoprire come aggiornare tutti i canali in blocco.
seo-description: Segui questa pagina per scoprire come aggiornare tutti i canali in blocco.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Aggiornamento offline in blocco {#bulk-offline-update}

Questa sezione illustra i seguenti argomenti relativi all'aggiornamento offline in blocco:

* **Panoramica**
* **Utilizzo dell'aggiornamento offline in blocco**

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3 Feature Pack 3 o AEM 6.4 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l'accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

Aggiornamento offline in blocco, consente di aggiornare tutti i canali in massa. Consente di evitare la difficoltà di spostarsi su un canale specifico e di aggiornare il contenuto. Potete invece aggiornare tutti i contenuti dei canali per un progetto specifico in un istante.

Potete anche pianificare questa attività per un periodo di tempo con traffico di rete inferiore.

>[!NOTE]
>
>La funzione Aggiornamento offline in blocco è ottimizzata per aggiornare solo i canali che sono stati modificati.

## Utilizzo dell'aggiornamento offline in blocco {#using-bulk-offline-update}

Potete utilizzare manualmente l’aggiornamento offline in blocco dall’interfaccia utente o pianificare l’aggiornamento in blocco dai servizi OSGi.

### Utilizzo dell’interfaccia utente di AEM Screens {#using-aem-screens-user-interface}

Per utilizzare l'aggiornamento offline in blocco per un progetto AEM Screens, procedi come segue:

1. Passa al progetto AEM Screens.
1. Selezionate il progetto e fate clic su **Aggiorna contenuto** offline nella barra delle azioni per aggiornare manualmente il contenuto del canale.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configurazione della console Web di Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Per utilizzare l'aggiornamento offline in blocco per un progetto AEM Screens, procedi come segue:

1. Configurazione della console Web di Adobe Experience Manager.
1. Cerca servizi di aggiornamento offline in massa.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Aggiungete le seguenti proprietà:

   **Percorso** progetto Specificate il percorso del progetto AEM Screens. Di solito il percorso è `/content/screens/<Name of your project>`.

   *Esempio*, `/content/screens/we-retail`. Per trovare questo percorso nell’URL, seleziona qualsiasi progetto in AEM Screens (non fai clic sull’icona).

   >[!NOTE]
   >
   >Specificate il percorso del progetto relativo al canale.

   **Frequenza** pianificazione Specificate un'ora, ad esempio le 17:00 o le 17:00, in cui il servizio deve aggiornare il contenuto offline.

1. Fai clic su **Salva** per salvare le impostazioni e il contenuto verrà aggiornato al momento specificato.

