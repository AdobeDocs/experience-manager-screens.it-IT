---
title: Integrazione di Adobe Analytics con AEM Screens
description: Scopri l’integrazione preconfigurata di AEM Screens con Adobe Analytics e una bozza di gioco.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Integrazione di Adobe Analytics con AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stata installata la versione minima del Feature Pack 2 AEM 6.4.2 o del Feature Pack 4 AEM 6.3.3. Per i clienti del servizio AEM Screens Cloud, contatta il tuo Adobe Relationship Manager per abilitare Adobe Analytics in Screens Cloud.

>[!NOTE]
>
>Per accedere a uno di questi Feature Pack, contatta il supporto Adobe e richiedi l’accesso. Puoi scaricare il Feature Pack più recente per AEM Screens dalla sezione [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) utilizzando il tuo Adobe ID.

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Dettagli dell’architettura**
* **Configurazione delle proprietà**

## Panoramica {#overview}

***AEM Screens*** utilizza Adobe Analytics e con questo puoi ottenere qualcosa di unico nel mercato: analisi cross-channel che consentono di correlare i contenuti mostrati nella posizione con altre origini dati.

AEM Screens fornisce un’integrazione standard con Adobe Analytics e una bozza di riproduzione.

Questa sezione descrive le seguenti funzionalità relative alla connessione di un progetto AEM Screens con Adobe Analytics:

* Consente di creare report di prova di riproduzione per dispositivo
* Consente di creare report proof of play per risorsa
* Garantisce che tutti gli eventi del lettore vengano acquisiti e contrassegnati con marca temporale
* Garantisce che tutti gli eventi del lettore siano archiviati localmente se la riproduzione non è collegata a una rete
* È possibile creare cicli di feedback per tenere traccia degli eventi di riproduzione nel tempo
* Consente al sistema di modificare il contenuto e i layout in base ai criteri di successo definiti dall’autore del contenuto

L’integrazione di Adobe Analytics con AEM Screens applica quindi quanto segue *obiettivi*:

* Abilitare il ROI dalle implementazioni di digital signage
* Integrare Analytics come base per l’abilitazione futura della raccolta e dell’analisi delle informazioni sull’utilizzo

## Dettagli dell’architettura {#architectural-details}

Un cliente AEM Screens vuole capire quale contenuto è stato mostrato in che momento e per quanto tempo (aggregato). Questa necessità è una capacità comune di una soluzione di digital signage. Invece di creare un’applicazione di analisi separata, AEM Screens utilizza Adobe Analytics. La combinazione consente di ottenere qualcosa di unico nel mercato: analisi cross-channel che consentono di correlare i contenuti mostrati localmente con altre origini dati.

Il diagramma architetturale seguente spiega l’integrazione di Adobe Analytics con AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Abilitazione di Adobe Analytics in AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Le impostazioni di Adobe Analytics possono essere configurate dalla console OSGi.

Accedi a **Configurazione console Web Adobe Experience Manager** in modo da poter configurare Adobe Analytics per AEM Screens.

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics: Flusso di abilitazione {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Prima di configurare le proprietà, contatta l’Adobe Relationship Manager per creare un ticket per ottenere un **Chiave API di Analytics** e **Progetto Analytics** da utilizzare con AEM Screens.

### Configurazione delle proprietà {#configuring-the-properties}

>[!CAUTION]
>
>Prima di configurare le proprietà, contatta l’Adobe Relationship Manager per creare un ticket per ottenere un **Chiave API di Analytics** e **Progetto Analytics** da utilizzare con AEM Screens.

La tabella seguente evidenzia le proprietà con la relativa descrizione per la configurazione di Adobe Analytics per AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong>URL di Analytics</strong></td>
   <td>URL per pubblicare i dati di analisi dal lettore. <br>
   Per sviluppo/fase</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Per la produzione</em> - https://cc-api-data.adobe.io/ingest/<br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Chiave API di Analytics</strong></td>
   <td>Chiave API per l’autenticazione al server Adobe Analytics (fornita da Accounts Manager).</td>
  </tr>
  <tr>
   <td><strong>Progetto Analytics</strong></td>
   <td>Progetto AEM Screens configurato nell’analisi per ricevere i dati (forniti da Accounts Manager).</td>
  </tr>
  <tr>
   <td><strong>Ambiente</strong></td>
   <td><p>Ambiente stage o produzione (scegliere Stage o Produzione).</p></td>
  </tr>
  <tr>
   <td><strong>Frequenza di invio di Analytics</strong></td>
   <td>Frequenza in minuti per l’invio dei dati di analisi dai lettori. Per impostazione predefinita, è impostato su 15 minuti.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Per impostazione predefinita, il **Frequenza di invio di Analytics** è di 15 minuti.

#### Utilizzo del servizio Adobe Analytics in AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Questo scenario richiama l’API di Analytics tramite chiamate REST da un servizio di analisi nel firmware. Inoltre, strumenti i componenti core Screens dell’AEM per creare e inviare eventi specifici per un caso d’uso particolare. Tutte queste funzionalità consentono l’estensibilità di inviare messaggi personalizzati ad Analytics da un canale personalizzato.

Gli eventi di Analytics vengono archiviati offline in indexedDB e successivamente bloccati e inviati al cloud.

>[!NOTE]
>
>Per ulteriori informazioni su ***Sequenziamento*** e ***Modello dati standard per eventi***, vedi **[Configurazione di Adobe Analytics per AEM Screens](configuring-adobe-analytics-aem-screens.md)**.
