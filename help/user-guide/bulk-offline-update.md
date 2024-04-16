---
title: Aggiornamento offline in blocco
description: Scopri come aggiornare tutti i canali in blocco.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Aggiornamento offline in blocco {#bulk-offline-update}

Questa sezione tratta i seguenti argomenti relativi all’aggiornamento offline in blocco:

* **Panoramica**
* **Utilizzo dell’aggiornamento offline in blocco**

<!-- OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permissions you can download it from Package Share. -->

## Panoramica {#overview}

Bulk Offline Update (Aggiornamento offline in blocco) consente di aggiornare tutti i canali in blocco. Evita il problema di navigare su un canale particolare e di aggiornare il contenuto. Piuttosto, puoi aggiornare tutti i contenuti in canali per un progetto specifico in un istante.

Puoi anche pianificare questa attività per un periodo di traffico di rete ridotto.

>[!NOTE]
>
>La funzione Aggiornamento offline in blocco è ottimizzata per aggiornare solo i canali che sono stati modificati.

## Utilizzo dell’aggiornamento offline in blocco {#using-bulk-offline-update}

Puoi utilizzare manualmente l’aggiornamento offline in blocco dall’interfaccia utente o pianificare l’aggiornamento in blocco dai servizi OSGi.

### Utilizzo dell’interfaccia utente di AEM Screens {#using-aem-screens-user-interface}

Per utilizzare l’aggiornamento offline in blocco per un progetto AEM Screens, effettua le seguenti operazioni:

1. Passa al progetto AEM Screens.
1. Fai clic sul progetto, quindi su **Aggiorna contenuto offline** dalla barra delle azioni, in modo da poter aggiornare manualmente il contenuto del canale.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configurazione console Web Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Per utilizzare l’aggiornamento offline in blocco per un progetto AEM Screens, effettua le seguenti operazioni:

1. Configurazione della console Web Adobe Experience Manager.
1. Cerca servizi di aggiornamento offline in blocco.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Aggiungi le seguenti proprietà:

   **Percorso progetto** Specifica il percorso del progetto AEM Screens. Il percorso è in genere `/content/screens/<Name of your project>`.

   *Ad esempio*, `/content/screens/we-retail`. Per trovare questo percorso nell’URL, seleziona qualsiasi progetto in AEM Screens (non fare clic sull’icona ).

   >[!NOTE]
   >
   >Specifica il percorso del progetto relativo al canale.

   **Frequenza Schedule** Specifica un orario, ad esempio 17:00 o 17:00 in cui il servizio deve aggiornare il contenuto offline.

1. Clic **Salva** per salvare le impostazioni. Il contenuto viene aggiornato all&#39;ora specificata.
