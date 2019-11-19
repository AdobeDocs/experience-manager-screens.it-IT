---
title: Integrazione di Adobe Analytics con AEM Screens
seo-title: Integrazione di Adobe Analytics con AEM Screens
description: Segui questa pagina per scoprire l’integrazione standard di AEM Screens con Adobe Analytics e fornire una prova della riproduzione.
seo-description: Segui questa pagina per scoprire l’integrazione standard di AEM Screens con Adobe Analytics e fornire una prova della riproduzione.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Integrazione di Adobe Analytics con AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se sono stati installati AEM 6.4.2 Feature Pack 2 e AEM 6.3.3 Feature Pack 4.

>Per accedere a uno di questi Feature Pack, contattate il supporto Adobe e richiedete l'accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.
>
Questa sezione illustra i seguenti argomenti:

* **Panoramica**
* **Dettagli architettonici**
* **Configurazione delle proprietà**

## Panoramica {#overview}

***AEM Screens*** sfrutta Adobe Analytics e consente di ottenere risultati unici sul mercato: analisi cross-channel che aiutano a correlare i contenuti visualizzati nella posizione ad altre origini dati.

AEM Screens offre un’integrazione completa con Adobe Analytics e fornisce una prova della riproduzione.

Questa sezione descrive le seguenti funzionalità relative alla connessione di un progetto AEM Screens con Adobe Analytics:

* Consente la generazione di rapporti della prova di riproduzione per dispositivo
* Consente la generazione di rapporti della prova di riproduzione per risorsa
* Assicurarsi che tutti gli eventi del lettore siano catturati e con marca temporale
* Assicurarsi che tutti gli eventi del lettore siano memorizzati localmente se la riproduzione non è collegata a una rete
* Consente di creare cicli di feedback per monitorare gli eventi di riproduzione nel tempo
* Consente al sistema di modificare contenuto e layout in base ai criteri di successo definiti dall'autore del contenuto

L'integrazione di Adobe Analytics con AEM Screens applica quindi i seguenti *obiettivi*:

* Ottimizzazione del ROI dalle implementazioni di digital signage
* Integrare Analytics come base per l'abilitazione futura della raccolta e dell'analisi delle informazioni di utilizzo

## Dettagli architettonici {#architectural-details}

I clienti di AEM Screens desiderano conoscere il contenuto visualizzato in che momento e per quanto tempo (aggregato). Questa è la funzionalità comune della soluzione di digital signage. Invece di creare le nostre analisi, AEM Screens sfrutterà Adobe Analytics e con questo potremo ottenere risultati unici sul mercato: analisi multicanale che aiutano a correlare i contenuti visualizzati nella posizione con altre origini dati.

Il seguente diagramma architettonico spiega l’integrazione di Adobe Analytics con AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Abilitazione di Adobe Analytics in AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Le impostazioni di Adobe Analytics possono essere configurate dalla console OSGi.

Andate alla configurazione **della console Web di** Adobe Experience Manager per configurare Adobe Analytics per AEM Screens, come illustrato nella figura seguente:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Analisi delle schermate: Flusso abilitazione {#screens-analytics-enablement-flow}

>[!CAUTION]
Prima di configurare le proprietà, contatta Adobe Relationship Manager per creare un ticket per ottenere una chiave **API** Analytics e un progetto **** Analytics da utilizzare con AEM Screens.

![]()

### Configurazione delle proprietà {#configuring-the-properties}

>[!CAUTION]
Prima di configurare le proprietà, contatta Adobe Relationship Manager per creare un ticket per ottenere una chiave **API** Analytics e un progetto **** Analytics da utilizzare con AEM Screens.

La tabella seguente evidenzia le proprietà con la relativa descrizione per la configurazione di Adobe Analytics per AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong>URL analisi</strong></td>
   <td>URL per pubblicare i dati di analisi dal lettore<br /> </td>
  </tr>
  <tr>
   <td><strong>Chiave API di Analytics</strong></td>
   <td>Chiave API per l'autenticazione al server Adobe Analytics (fornita da Gestione account)</td>
  </tr>
  <tr>
   <td><strong>Progetto di Analytics</strong></td>
   <td>Progetto AEM Screens configurato nell’analisi per la ricezione di dati (fornito dal manager account)</td>
  </tr>
  <tr>
   <td><strong>di authoring</strong></td>
   <td><p>Fase o ambiente di produzione.</p> <p><em>Per lo sviluppo/lo stage</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Per la produzione</em> - https://cc-api-data.adobe.io/ingest/</p> </td>
  </tr>
  <tr>
   <td><strong>Frequenza di invio di Analytics</strong></td>
   <td>Frequenza in minuti per l'invio di dati di analisi dai lettori. Per impostazione predefinita, è impostata su 15 minuti.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
Per impostazione predefinita, la **Analytics Send Frequency **è di 15 minuti.

#### Utilizzo di Adobe Analytics Service in AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Questo scenario richiama l'API di Analytics tramite le chiamate REST da un servizio di analisi nel firmware e nei componenti core degli schermi strumenti per creare e inviare in modo esplicito eventi specifici per un particolare caso d'uso, consentendo al contempo l'estensibilità in cui qualsiasi messaggio personalizzato può essere inviato ad Analytics da un canale sviluppato personalizzato.

Gli eventi di Analytics vengono memorizzati offline in indicxedDB e successivamente troncati e inviati al cloud.

>[!NOTE]
Per ulteriori informazioni su ***Sequencing*** e ***Standard Data Model for Events***, consultate **[Configurazione di Adobe Analytics per AEM Screens](configuring-adobe-analytics-aem-screens.md)**.

