---
title: Configurazione di Adobe Analytics con AEM Screens
description: Ulteriori informazioni sulla sequenza e l’invio di eventi personalizzati utilizzando Offline Adobe Analytics.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 10%

---

# Configurazione di Adobe Analytics con AEM Screens {#configuring-adobe-analytics-with-aem-screens}

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.4.2 Feature Pack 2 and AEM 6.3.3 Feature Pack 4.
>
>To get access to either of these Feature Packs, contact Adobe Support and request access. When you have permissions, download it from Package Share. -->

Questa sezione tratta i seguenti argomenti:

* **Sequenza in Adobe Analytics con AEM Screens**
* **Invio di eventi personalizzati tramite Adobe Analytics offline**

## Ordinamento in Adobe Analytics con AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

Il ***processo di sequenziamento*** inizia con un servizio di archiviazione dati che attiva il servizio Adobe Analytics. Il contenuto del canale invia gli eventi di Adobe Analytics con il ciclo paghe, ovvero l’acquisizione dei test dei dati a Windows I/O e gli eventi stay vengono attivati. Gli eventi vengono salvati nel database dell&#39;indice e successivamente inseriti nell&#39;archivio oggetti. In base alla pianificazione impostata dall&#39;amministratore, i dati vengono tagliati dall&#39;archivio oggetti e ulteriormente trasferiti nell&#39;archivio blocchi. Tenta di inviare la quantità massima di dati quando si è connessi.

### Diagramma di sequenziamento {#sequencing-diagram}

Il seguente diagramma di sequenziamento spiega l’integrazione di Adobe Analytics con AEM Screens:

![analisi_chunking](assets/analytics_chunking.png)

## Invio Di Eventi Personalizzati Tramite Offline Adobe Analytics {#sending-custom-events-using-offline-adobe-analytics}

Nella tabella seguente viene riepilogato il modello dati standard per gli eventi. Elenca tutti i campi inviati ad Adobe Analytics:

<table>
 <tbody>
  <tr>
   <td><strong>Sezione</strong></td> 
   <td><strong>Etichetta proprietà</strong></td> 
   <td><strong>Nome/Chiave proprietà</strong></td> 
   <td><strong>Obbligatorio</strong></td> 
   <td><strong>Tipo di dati</strong></td> 
   <td><strong>Tipo di proprietà</strong><br /> </td> 
   <td><strong>Descrizione</strong></td> 
  </tr>
  <tr>
   <td><strong><em>Core/Evento</em></strong></td> 
   <td>GUID evento</td> 
   <td>event.guid</td> 
   <td>consigliato</td> 
   <td>stringa</td> 
   <td>UUID</td> 
   <td>ID univoco che identifica un’istanza di un evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e ora di raccolta dell’evento</td> 
   <td>event.coll_dts</td> 
   <td>facoltativo</td> 
   <td>stringa</td> 
   <td>timestamp - UTC</td> 
   <td>Data e ora raccolta</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e ora dell’evento (inizio)</td> 
   <td>event.dts_start</td> 
   <td>consigliato</td> 
   <td>stringa</td> 
   <td>timestamp - UTC</td> 
   <td>Data e ora di inizio evento. Se non è stata specificata questa ora, l'ora dell'evento verrà considerata come l'ora di ricezione del server.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e ora dell’evento (fine)</td> 
   <td>event.dts_end</td> 
   <td>facoltativo</td> 
   <td>stringa</td> 
   <td>timestamp - UTC</td> 
   <td>Data e ora di completamento evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Flusso di lavoro</td> 
   <td>event.workflow</td> 
   <td>consigliato</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Nome flusso di lavoro (Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoria DMe principale</td> 
   <td>event.category</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Categoria principale (DESKTOP, MOBILE, WEB, PROCESS, SDK, SERVICE, ECOSYSTEM) - Raggruppamento di tipi di evento - <strong>Lettore inviato</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sottocategoria</td> 
   <td>event.subcategory</td> 
   <td>consigliato</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Sottocategoria: sezione di un flusso di lavoro o area di uno schermo e così via. (File recenti, file CC, creazioni per dispositivi mobili e così via).</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo evento/azione</td> 
   <td>event.type</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Tipo evento (rendering, clic, pizzico, zoom) - Azione utente principale</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sottotipo</td> 
   <td>event.subtype</td> 
   <td>consigliato</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Sottotipo evento (crea, aggiorna, elimina, pubblica e così via) - Ulteriori dettagli sull’azione dell’utente</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Offline</td> 
   <td>event.offline</td> 
   <td>facoltativo</td> 
   <td>booleano</td> 
   <td> </td> 
   <td>L’evento è stato generato mentre l’azione era offline/online (true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agente utente</td> 
   <td>event.user_agent</td> 
   <td>consigliato (proprietà web)</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Agente utente</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Lingua/Paese</td> 
   <td>event.language</td> 
   <td>consigliato</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Le impostazioni locali dell’utente sono stringhe basate sulle convenzioni di assegnazione tag della lingua della RFC 3066 (ad esempio, en-US, fr-FR o es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID dispositivo</td> 
   <td>event.device_guid</td> 
   <td>facoltativo</td> 
   <td>stringa<br /> </td> 
   <td>UUID</td> 
   <td>Identifica il GUID del dispositivo (ad esempio, ID computer o hash dell'indirizzo IP + subnet mask + ID di rete + agente utente) - Qui viene inviato il nome utente del lettore generato al momento della registrazione.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Conteggio</td> 
   <td>event.count</td> 
   <td>facoltativo</td> 
   <td>numero</td> 
   <td> </td> 
   <td>Numero di volte in cui si è verificato l’evento: viene inviata la durata del video</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Valore</td> 
   <td>event.value</td> 
   <td>facoltativo</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Valore dell’evento (ad esempio impostazioni attivate/disattivate)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>richiesto per AA</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Supporto per il nome pagina personalizzato in Adobe Analytics</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>facoltativo</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>URL della proprietà web o dello schema mobile: deve includere un URL completo</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Codice di errore</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Codice errore</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo di errore</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Tipo di errore</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrizione errore</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Descrizione errore<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Source/Prodotto originario</em></strong></td> 
   <td>Nome</td> 
   <td>source.name</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Nome app (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versione</td> 
   <td>source.version</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Versione firmware</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Platform</td> 
   <td>source.platform</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Dispositivo</td> 
   <td>source.device</td> 
   <td>obbligatorio con eccezioni</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Nome lettore</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versione sistema operativo</td> 
   <td>source.os_version</td> 
   <td>obbligatorio con eccezioni</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Versione sistema operativo</td> 
  </tr>
  <tr>
   <td><strong><em>Contenuto</em></strong></td> 
   <td>Azione</td> 
   <td>content.action</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>URL della risorsa, inclusa la rappresentazione riprodotta</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo MIME</td> 
   <td>content.mimetype</td> 
   <td>facoltativo</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Tipo MIME del contenuto</td> 
  </tr>
  <tr>
   <td><strong><em>Transazione</em></strong></td> 
   <td>Numero transazione</td> 
   <td>trn.number</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td>UUID</td> 
   <td>ID univoco preferibilmente conforme a UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrizione del prodotto</td> 
   <td>trn.product</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>URL della risorsa (esclusa la rappresentazione)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Quantità</td> 
   <td>trn.quantity</td> 
   <td>obbligatorio</td> 
   <td>stringa</td> 
   <td> </td> 
   <td>Durata della riproduzione</td> 
  </tr>
 </tbody>
</table>
