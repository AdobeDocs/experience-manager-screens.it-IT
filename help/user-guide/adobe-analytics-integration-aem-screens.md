---
title: ' Integrazione Adobe Analytics con  AEM Screens'
seo-title: ' Integrazione Adobe Analytics con  AEM Screens'
description: Segui questa pagina per saperne di più sull'integrazione di  AEM Screens con  Adobe Analytics e ti fornisce una prova di gioco.
seo-description: Segui questa pagina per saperne di più sull'integrazione di  AEM Screens con  Adobe Analytics e ti fornisce una prova di gioco.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 2%

---


#  Integrazione Adobe Analytics con  AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Questa funzionalità  AEM Screens è disponibile solo se sono stati installati AEM Feature Pack 2 e AEM Feature Pack 4 6.3.3.

>[!NOTE]
>
>Per accedere a uno di questi Feature Pack, è necessario contattare  Adobe di assistenza e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

Questa sezione illustra i seguenti argomenti:

* **Panoramica**
* **Dettagli architettonici**
* **Configurazione delle proprietà**

## Panoramica {#overview}

***AEM*** Screenssfrutta  Adobe Analytics e consente di ottenere risultati unici sul mercato: analisi cross-channel che aiutano a correlare i contenuti visualizzati nella posizione con altre origini dati.

 AEM Screens offre un&#39;integrazione standard con  Adobe Analytics e fornisce una prova della riproduzione.

Questa sezione descrive le seguenti funzionalità relative alla connessione di un progetto AEM Screens  con  Adobe Analytics:

* Consente la generazione di rapporti della prova di riproduzione per dispositivo
* Consente la generazione di rapporti della prova di riproduzione per risorsa
* Assicurarsi che tutti gli eventi del lettore siano catturati e con marca temporale
* Assicurarsi che tutti gli eventi del lettore siano memorizzati localmente se la riproduzione non è collegata a una rete
* Consente di creare cicli di feedback per il tracciamento degli eventi di riproduzione nel tempo
* Consente al sistema di modificare contenuto e layout in base ai criteri di successo definiti dall&#39;autore del contenuto

 l&#39;integrazione Adobe Analytics con  AEM Screens applica quindi i seguenti *obiettivi*:

* Ottimizzazione del ROI dalle implementazioni di digital signage
* Integrare Analytics come base per l&#39;abilitazione futura della raccolta e dell&#39;analisi delle informazioni di utilizzo

## Dettagli architettonici {#architectural-details}

I clienti di AEM Screens  desiderano comprendere a che punto e per quanto tempo (aggregato) è stato visualizzato il contenuto. Questa è la funzionalità comune della soluzione di digital signage. Invece di creare le nostre analisi,  AEM Screens sfrutterà  Adobe Analytics, e con questo potremo realizzare qualcosa di unico sul mercato: analisi cross-channel che aiutino a correlare i contenuti visualizzati nella posizione con altre origini dati.

Nel diagramma seguente viene illustrato il  Integrazione Adobe Analytics con  AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Abilitazione  Adobe Analytics in  AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Le  impostazioni Adobe Analytics possono essere configurate dalla console OSGi.

Andate a **Configurazione console Web Adobe Experience Manager** per configurare  Adobe Analytics per  AEM Screens, come illustrato nella figura seguente:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Analisi delle schermate: Flusso di abilitazione {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Prima di configurare le proprietà, contatta il tuo  Adobe Relationship Manager per creare un ticket per ottenere una **chiave API di Analytics** e un **progetto di Analytics** da utilizzare con  AEM Screens.

![]()

### Configurazione delle proprietà {#configuring-the-properties}

>[!CAUTION]
>
>Prima di configurare le proprietà, contatta il tuo  Adobe Relationship Manager per creare un ticket per ottenere una **chiave API di Analytics** e un **progetto di Analytics** da utilizzare con  AEM Screens.

Nella tabella seguente sono evidenziate le proprietà con la relativa descrizione per la configurazione  Adobe Analytics per  AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong>URL analisi</strong></td>
   <td>URL per pubblicare i dati di analisi dal lettore. <br>
   Per lo sviluppo/stage</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Per la produzione</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Chiave API di Analytics</strong></td>
   <td>Chiave API per l'autenticazione al server Adobe Analytics  (fornita da Gestione account).</td>
  </tr>
  <tr>
   <td><strong>Progetto di Analytics</strong></td>
   <td> progetto AEM Screens configurato nell'analisi per ricevere i dati (fornito da Gestione account).</td>
  </tr>
  <tr>
   <td><strong>di authoring</strong></td>
   <td><p>Fase o ambiente di produzione (scegliere Fase o Produzione).</p></td>
  </tr>
  <tr>
   <td><strong>Frequenza di invio di Analytics</strong></td>
   <td>Frequenza in minuti per l'invio di dati di analisi dai lettori. Per impostazione predefinita, è impostata su 15 minuti.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Per impostazione predefinita, la **frequenza di invio di Analytics** è di 15 minuti.

#### Utilizzo di  Adobe Analytics Service in  AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Questo scenario richiama l&#39;API di Analytics tramite le chiamate REST da un servizio di analisi nel firmware e nei componenti core degli schermi strumenti per creare e inviare in modo esplicito eventi specifici per un particolare caso di utilizzo, consentendo al contempo l&#39;estensibilità in cui qualsiasi messaggio personalizzato può essere inviato ad Analytics da un canale sviluppato personalizzato.

Gli eventi di Analytics vengono memorizzati offline in indicxedDB e successivamente troncati e inviati al cloud.

>[!NOTE]
>
>Per ulteriori informazioni su ***Sequencing*** e ***Standard Data Model for Events***, fare riferimento a **[Configurazione  Adobe Analytics per  AEM Screens](configuring-adobe-analytics-aem-screens.md)**.

