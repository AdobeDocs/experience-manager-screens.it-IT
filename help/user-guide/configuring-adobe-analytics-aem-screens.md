---
title: Configurazione di Adobe Analytics con AEM Screens
seo-title: Configurazione di Adobe Analytics con AEM Screens
description: 'Seguite questa sezione per ulteriori informazioni sulla sequenza e l''invio di eventi personalizzati tramite offline Adobe Analytics '
seo-description: 'Seguite questa sezione per ulteriori informazioni sulla sequenza e l''invio di eventi personalizzati tramite offline Adobe Analytics '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configurazione di Adobe Analytics con AEM Screens {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se sono stati installati AEM 6.4.2 Feature Pack 2 e AEM 6.3.3 Feature Pack 4.

>Per accedere a uno di questi Feature Pack, contattate il supporto Adobe e richiedete l'accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.
>
Questa sezione illustra i seguenti argomenti:

* **Sequenza in Adobe Analytics con AEM Screens**
* **Invio di eventi personalizzati tramite Adobe Analytics offline**

## Sequenza in Adobe Analytics con AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

Il processo ***di*** sequenziamento inizia con il servizio di memorizzazione dei dati che attiva il servizio Adobe Analytics. Il contenuto del canale invia eventi Adobe Analytics con payroll, ovvero l'acquisizione di test dei dati a Windows I/O e gli eventi di permanenza vengono attivati. Gli eventi vengono salvati nel database di indice e vengono quindi inseriti nell'archivio oggetti. In base alla pianificazione, l'amministratore imposta, taglia i dati dall'archivio oggetti e li trasferisce ulteriormente nell'archivio blocchi. Cerca di inviare la quantità massima di dati quando è connesso.

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
   <td><strong>Nome proprietà/Chiave</strong></td> 
   <td><strong>Obbligatorio</strong></td> 
   <td><strong>Tipo di dati</strong></td> 
   <td><strong>Tipo proprietà</strong><br /> </td> 
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
   <td>Data e ora della raccolta dell’evento</td> 
   <td>event.coll_dts</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td>marca temporale - UTC</td> 
   <td>Data raccolta</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e ora dell'evento (inizio)</td> 
   <td>event.dts_start</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td>marca temporale - UTC</td> 
   <td>Data e ora di inizio evento, se NON si specifica questa opzione, l'ora dell'evento verrà considerata l'ora in cui è stata ricevuta dal server</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e ora dell’evento (fine)</td> 
   <td>event.dts_end</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td>marca temporale - UTC</td> 
   <td>Ora completamento evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Flusso di lavoro</td> 
   <td>event.workflow</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome flusso di lavoro (schermate)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoria DM principale</td> 
   <td>event.category</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Categoria principale (DESKTOP, MOBILE, WEB, PROCESS, SDK, SERVICE, ECOSYSTEM) - Raggruppamento di tipi di evento - <strong>Viene inviato il lettore</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sottocategoria</td> 
   <td>event.subcategory</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Sottocategoria - Sezione di un flusso di lavoro o Area di uno schermo, ecc. (File recenti, file CC, creazioni per dispositivi mobili e così via)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo di evento/azione</td> 
   <td>event.type</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo evento (rendering, clic, avvicinamento delle dita, zoom) - Azione utente principale</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sottotipo</td> 
   <td>event.subtype</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Sottotipo evento (creazione, aggiornamento, eliminazione, pubblicazione ecc.) - Ulteriori dettagli sull'azione dell'utente</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Offline</td> 
   <td>event.offline</td> 
   <td>facoltativo</td> 
   <td>booleano</td> 
   <td> </td> 
   <td>L'evento è stato generato mentre l'azione era offline/online (true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agente utente</td> 
   <td>event.user_agent</td> 
   <td>consigliato (proprietà Web)</td> 
   <td>string</td> 
   <td> </td> 
   <td>Agente utente</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Lingua/lingua</td> 
   <td>event.language</td> 
   <td>consigliato</td> 
   <td>string</td> 
   <td> </td> 
   <td>Le impostazioni internazionali dell'utente sono una stringa basata sulle convenzioni per l'assegnazione di tag nella lingua di RFC 3066 (ad esempio, en-US, fr-FR o es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID dispositivo</td> 
   <td>event.device_guid</td> 
   <td>facoltativo</td> 
   <td>stringa<br /> </td> 
   <td>UUID</td> 
   <td>Identifica il GUID del dispositivo (ad esempio, ID computer o hash dell'indirizzo IP + subnet mask + ID rete + agente utente) - Qui verrà inviato il nome utente del lettore generato al momento della registrazione.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Conteggio</td> 
   <td>event.count</td> 
   <td>facoltativo</td> 
   <td>numero</td> 
   <td> </td> 
   <td>Numero di volte in cui si è verificato l’evento - Qui viene inviata la durata del video</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Valore</td> 
   <td>event.value</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td> </td> 
   <td>Valore dell’evento (ad esempio, impostazioni attivate/disattivate)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>richiesto per AA</td> 
   <td>string</td> 
   <td> </td> 
   <td>Supporto di Adobe Analytics per Nome pagina personalizzato</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td> </td> 
   <td>L'URL della proprietà Web o dello schema mobile deve includere l'URL completo</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Codice errore</td> 
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
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome app (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versione</td> 
   <td>source.version</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Versione firmware</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Piattaforma</td> 
   <td>source.platform</td> 
   <td>required</td> 
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
   <td>Nome lettore</td> 
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
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL della risorsa, inclusa la rappresentazione effettivamente riprodotta</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo mime</td> 
   <td>content.mimetype</td> 
   <td>facoltativo</td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo mime del contenuto</td> 
  </tr>
  <tr>
   <td><strong><em>Transazione</em></strong></td> 
   <td>Numero transazione</td> 
   <td>trn.number</td> 
   <td>required</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>ID univoco che preferibilmente aderisce a UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrizione prodotto</td> 
   <td>trn.product</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL della risorsa (esclusa la rappresentazione)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Quantità</td> 
   <td>trn.Quantity</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Durata della riproduzione</td> 
  </tr>
 </tbody>
</table>
