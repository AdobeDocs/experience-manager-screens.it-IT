---
title: Integrazione di Adobe  Analytics con AEM Screens
seo-title: Integrazione di Adobe  Analytics con AEM Screens
description: Seguite questa pagina per apprendere l'integrazione immediata dei AEM Screens con Adobe  Analytics e per ottenere una prova della riproduzione.
seo-description: Seguite questa pagina per apprendere l'integrazione immediata dei AEM Screens con Adobe  Analytics e per ottenere una prova della riproduzione.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 2%

---


# Integrazione di Adobe  Analytics con AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Questa funzionalità AEM Screens è disponibile solo se sono stati installati AEM 6.4.2 Feature Pack 2 e AEM 6.3.3 Feature Pack 4.

>[!NOTE]
>
>Per accedere a uno di questi Feature Pack, contattate il supporto Adobe e richiedete l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

Questa sezione illustra i seguenti argomenti:

* **Panoramica**
* **Dettagli architettonici**
* **Configurazione delle proprietà**

## Panoramica {#overview}

***I AEM Screens*** sfruttano Adobe  Analytics e consentono di ottenere risultati unici sul mercato: analisi cross-channel che consentono di correlare i contenuti visualizzati nella posizione con altre origini dati.

I AEM Screens forniscono un&#39;integrazione immediata con Adobe  Analytics e una prova del gioco.

Questa sezione descrive le seguenti funzionalità relative alla connessione di un progetto AEM Screens con Adobe  Analytics:

* Consente la generazione di rapporti della prova di riproduzione per dispositivo
* Consente la generazione di rapporti della prova di riproduzione per risorsa
* Assicurarsi che tutti gli eventi del lettore siano catturati e con marca temporale
* Assicurarsi che tutti gli eventi del lettore siano memorizzati localmente se la riproduzione non è collegata a una rete
* Consente di creare cicli di feedback per il tracciamento degli eventi di riproduzione nel tempo
* Consente al sistema di modificare contenuto e layout in base ai criteri di successo definiti dall&#39;autore del contenuto

L&#39;integrazione di Adobe  Analytics con i AEM Screens applica quindi i seguenti *obiettivi*:

* Ottimizzazione del ROI dalle implementazioni di digital signage
* Integrare  Analytics come base per la futura abilitazione della raccolta e dell&#39;analisi delle informazioni di utilizzo

## Dettagli architettonici {#architectural-details}

I clienti di AEM Screens vogliono comprendere il contenuto visualizzato in che momento e per quanto tempo (aggregato). Questa è la funzionalità comune della soluzione di digital signage. Invece di creare le nostre analisi, gli AEM Screens sfrutteranno Adobe  Analytics e con questo potremo ottenere risultati unici sul mercato: analisi multicanale che aiutano a correlare i contenuti visualizzati nella posizione con altre origini dati.

Nel diagramma di architettura seguente viene illustrato Adobe  Analytics Integration with AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Abilitazione di Adobe  Analytics nei AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Le impostazioni Adobe  Analytics possono essere configurate dalla console OSGi.

Andate a **Configurazione** console Web di Adobe Experience Manager per configurare Adobe  Analytics per AEM Screens, come illustrato nella figura seguente:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Schermi  Analytics: Flusso abilitazione {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Prima di configurare le proprietà, contattate Adobe Relationship Manager per creare un ticket per ottenere una chiave **API** Analytics e un progetto **** Analytics da utilizzare con AEM Screens.

![]()

### Configurazione delle proprietà {#configuring-the-properties}

>[!CAUTION]
>
>Prima di configurare le proprietà, contattate Adobe Relationship Manager per creare un ticket per ottenere una chiave **API** Analytics e un progetto **** Analytics da utilizzare con AEM Screens.

La tabella seguente evidenzia le proprietà con la relativa descrizione per configurare Adobe  Analytics per AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong> URL Analytics</strong></td>
   <td>URL per pubblicare i dati di analisi dal lettore. <br>
   Per lo sviluppo/lo stage</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Per la produzione</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong> Chiave API Analytics</strong></td>
   <td>Chiave API per l'autenticazione al server Adobe  Analytics (fornita da Gestione account).</td>
  </tr>
  <tr>
   <td><strong> progetto Analytics</strong></td>
   <td>Progetto AEM Screens configurato nell'analisi per ricevere i dati (fornito dal Gestore account).</td>
  </tr>
  <tr>
   <td><strong>di authoring</strong></td>
   <td><p>Fase o ambiente di produzione (scegliere Fase o Produzione).</p></td>
  </tr>
  <tr>
   <td><strong> Analytics Send Frequency</strong></td>
   <td>Frequenza in minuti per l'invio di dati di analisi dai lettori. Per impostazione predefinita, è impostata su 15 minuti.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Per impostazione predefinita, la **frequenza** di invio Analytics è di 15 minuti.

#### Utilizzo di Adobe  Analytics Service nei AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Questo scenario richiama  API Analytics tramite chiamate REST da un servizio di analisi nel firmware e nei componenti core dello schermo strumenti per creare e inviare in modo esplicito eventi specifici per un particolare caso di utilizzo, consentendo al contempo l&#39;estensibilità in cui qualsiasi messaggio personalizzato può essere inviato a  Analytics da un canale sviluppato personalizzato.

 gli eventi Analytics vengono memorizzati offline in un database indicizzato e successivamente bloccati e inviati al cloud.

>[!NOTE]
>
>Per ulteriori informazioni su ***Sequencing*** e ***Standard Data Model for Events***, consultare **[Configuring Adobe  Analytics for AEM Screens](configuring-adobe-analytics-aem-screens.md)**.

