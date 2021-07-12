---
title: Configurazione di Adobe Analytics con AEM Screens
seo-title: Configurazione di Adobe Analytics con AEM Screens
description: Leggi questa sezione per ulteriori informazioni sulla sequenza e l’invio di eventi personalizzati tramite Offline Adobe Analytics
seo-description: Leggi questa sezione per ulteriori informazioni sulla sequenza e l’invio di eventi personalizzati tramite Offline Adobe Analytics
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
feature: Amministrazione di schermi
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 11%

---

# Configurazione di Adobe Analytics con AEM Screens {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se hai installato AEM Feature Pack 2 6.4.2 e AEM Feature Pack 4 6.3.3.
>
>Per accedere a uno di questi Feature Pack, è necessario contattare il supporto Adobe e richiedere l’accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

Questa sezione tratta i seguenti argomenti:

* **Sequenza in Adobe Analytics con AEM Screens**
* **Invio di eventi personalizzati tramite Adobe Analytics offline**

## Sequenza in Adobe Analytics con AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

Il ***processo di sequenziamento*** inizia con il servizio di archiviazione dati che attiva il servizio Adobe Analytics. Il contenuto del canale invia gli eventi Adobe Analytics con il ciclo paghe, ovvero l&#39;acquisizione del test dei dati a Windows I/O e gli eventi di soggiorno vengono attivati. Gli eventi vengono salvati nel database dell&#39;indice e vengono ulteriormente inseriti nell&#39;archivio oggetti. In base alla pianificazione, l&#39;amministratore imposta, taglia i dati dall&#39;archivio oggetti e li trasferisce ulteriormente nell&#39;archivio blocchi. Cerca di inviare la quantità massima di dati, quando connesso.

### Diagramma di sequenza {#sequencing-diagram}

Il seguente diagramma di sequenza spiega l’integrazione di Adobe Analytics con AEM Screens:

![analytics_chunking](assets/analytics_chunking.png)

## Invio di eventi personalizzati tramite Adobe Analytics offline {#sending-custom-events-using-offline-adobe-analytics}

La tabella seguente riepiloga il modello dati standard per gli eventi. Elenca tutti i campi inviati ad Adobe Analytics:

<table>
 <tbody>
  <tr>
   <td><strong>Sezione</strong></td> 
   <td><strong>Etichetta proprietà</strong></td> 
   <td><strong>Nome proprietà/chiave</strong></td> 
   <td><strong>Obbligatorio</strong></td> 
   <td><strong>Tipo di dati</strong></td> 
   <td><strong>Tipo di proprietà</strong><br /> </td> 
   <td><strong>Descrizione</strong></td> 
  </tr>
  <tr>
   <td><strong><em>Core/Event</em></strong></td> 
   <td>GUID evento</td> 
   <td>event.guid</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>ID univoco che identifica l'istanza di un evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data della raccolta dell'evento</td> 
   <td>event.coll_dts</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td>timestamp - UTC</td> 
   <td>Data e ora di raccolta</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e ora dell’evento (inizio)</td> 
   <td>event.dts_start</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td>timestamp - UTC</td> 
   <td>Data e ora di inizio evento, se NON si specifica questa opzione, l'ora dell'evento verrà considerata come l'ora in cui è stata ricevuta dal server</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e ora dell’evento (fine)</td> 
   <td>event.dts_end</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td>timestamp - UTC</td> 
   <td>Data e ora di completamento eventi</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Flusso di lavoro</td> 
   <td>event.workflow</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome del flusso di lavoro (Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoria principale DMe</td> 
   <td>event.category</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Categoria principale (DESKTOP, MOBILE, WEB, PROCESS, SDK, SERVICE, ECOSISTEMA) - Raggruppamento di tipi di evento - <strong>Inviiamo Player</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoria secondaria</td> 
   <td>event.subcategory</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Sottocategoria: sezione di un flusso di lavoro o area di una schermata, ecc. (File recenti, file CC, creazioni mobili e così via)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo evento/azione</td> 
   <td>event.type</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo evento (rendering, clic, pizzico, zoom) - Azione utente principale</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sottotipo</td> 
   <td>event.subtype</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo secondario evento (creazione, aggiornamento, eliminazione, pubblicazione, ecc.) - Ulteriori dettagli sull'azione dell'utente</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Offline</td> 
   <td>event.offline</td> 
   <td>facoltativo</td> 
   <td>booleano</td> 
   <td> </td> 
   <td>Evento generato mentre l'azione era offline/online (true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agente utente</td> 
   <td>event.user_agent</td> 
   <td>consigliato (proprietà web)</td> 
   <td>string</td> 
   <td> </td> 
   <td>Agente utente</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Lingua/Impostazioni internazionali</td> 
   <td>event.language</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Le impostazioni internazionali utente sono una stringa basata sulle convenzioni di assegnazione tag della lingua della RFC 3066 (ad esempio, en-US, fr-FR o es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID dispositivo</td> 
   <td>event.device_guid</td> 
   <td>facoltativo</td> 
   <td>stringa<br /> </td> 
   <td>UUID</td> 
   <td>Identifica il GUID del dispositivo (ad esempio ID macchina o hash dell'indirizzo IP + subnet mask + ID rete + user agent) - Qui invieremo il nome utente del lettore generato al momento della registrazione.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Conteggio</td> 
   <td>event.count</td> 
   <td>facoltativo</td> 
   <td>numero</td> 
   <td> </td> 
   <td>Numero di volte in cui si è verificato l’evento - Qui si invia la durata del video</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Valore</td> 
   <td>event.value</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td> </td> 
   <td>Valore dell’evento (ad esempio, impostazioni attive/disattivate)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>richiesto per AA</td> 
   <td>string</td> 
   <td> </td> 
   <td>Supporto Adobe Analytics per Nome pagina personalizzato</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL della proprietà Web o dello schema mobile: deve includere un URL completo</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Codice di errore</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Codice di errore</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo errore</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo di errore</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrizione errore</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Descrizione errore<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Prodotto di origine</em></strong></td> 
   <td>Nome</td> 
   <td>source.name</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome app (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versione</td> 
   <td>source.version</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td> </td> 
   <td>Versione firmware</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Platform</td> 
   <td>source.platform</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Dispositivo</td> 
   <td>source.device</td> 
   <td>con eccezioni richieste</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome del lettore</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versione sistema operativo</td> 
   <td>source.os_version</td> 
   <td>con eccezioni richieste</td> 
   <td>string</td> 
   <td> </td> 
   <td>Versione O/S</td> 
  </tr>
  <tr>
   <td><strong><em>Contenuto</em></strong></td> 
   <td>Azione</td> 
   <td>content.action</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL della risorsa, compreso il rendering effettivamente riprodotto</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo MIME</td> 
   <td>content.mimetype</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo di MIME del contenuto</td> 
  </tr>
  <tr>
   <td><strong><em>Transazione</em></strong></td> 
   <td>Numero della transazione</td> 
   <td>trn.number</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>ID univoco che preferibilmente aderisce a UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrizione del prodotto</td> 
   <td>trn.product</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL della risorsa (rendering escluso)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Quantità</td> 
   <td>trn.quantity</td> 
   <td>obbligatorio</td> 
   <td>string</td> 
   <td> </td> 
   <td>Durata della riproduzione</td> 
  </tr>
 </tbody>
</table>
