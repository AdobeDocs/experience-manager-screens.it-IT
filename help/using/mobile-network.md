---
title: Rete mobile diretta
description: La pagina descrive l’impostazione della rete mobile diretta
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# Rete mobile diretta {#mobile-network-setup}

I giocatori di AEM Screens possono anche essere collegati tramite reti mobili o cellulari che eseguono almeno una rete 3G.

All&#39;interno dei AEM Screens, il contenuto richiesto viene scaricato fisicamente nel controller del lettore o nel computer e memorizzato correttamente all&#39;interno del sistema operativo sottostante. Di conseguenza, la larghezza di banda specificata influisce solo sui tempi di download iniziali e non sulle prestazioni dei display.

Connessione dei lettori AEM Screens con Cellulare 3/4/5G al provider di dati Mobile Service. Il vantaggio di questa configurazione è che Mobile Router può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è solitamente in posizione elevata e aperta con il più possibile la costruzione di calcestruzzo o metallo circostante.

Questa configurazione consente agli utenti di AEM Screen una grande flessibilità, in quanto non è necessaria alcuna connessione fissa per connettersi ai AEM Screens.

Il diagramma seguente mostra l&#39;impostazione della rete mobile diretta ed è composto da un segmento di connessione di rete singolo, la connessione di ciascun lettore alla rete dati mobile/cellulare.

![](/help/using/assets/direct-mobile-1.png)

## Collegamento del lettore AEM Screens alla rete mobile diretta {#connecting-aem-screens-players}

Per collegare i lettori AEM Screens in questa configurazione, effettuate le seguenti operazioni:

1. Accertatevi che ciascuno dei lettori dello schermo AEM sia collegato alla rete Routers.

1. Verificate la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Nel caso in cui venga visualizzato un messaggio di errore, controllare le impostazioni di rete. Esistono sostanzialmente due opzioni per una connessione di rete adeguata:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurarsi che l&#39;impostazione della scheda di rete corrisponda all&#39;impostazione del router.

1. Verificare che il router sia collegato correttamente alla rete Internet Wide Area Network (Internet Link). Questo può essere identificato anche utilizzando un LED di segnale su router standard.

1. Se la chiamata URL ha esito positivo, potete continuare a installare gli AEM Screens e registrarvi. AEM Screens iniziali.

   >[!NOTE]
   >**Suggerimenti per la risoluzione dei problemi**
   >Se i AEM Screens non si connettono correttamente e non mostrano il contenuto previsto:
   >
   >1. Se sono presenti restrizioni, controllate il firewall Internet Router `TCP/IP Port 80/443`.
   >1. Accertatevi che tutte le porte necessarie siano consentite.



## Requisiti per la configurazione della rete mobile {#requirements-direct}

La configurazione della rete può essere logicamente separata in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet oltre alla raggiungibilità della rete forniscono una larghezza di banda sufficiente per il corretto funzionamento dei AEM Screens.

*Sufficiente* dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti WiFi per gli ospiti.

>[!NOTE]
>Tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce in modo lineare aggiungendo alla rete più utenti o computer.

Le reti dati forniscono una larghezza di banda standard con:

**3G**
* 42 Mbps

**4G**
* 150 Mbps

**5G**
* 1000 Mbps-10000 Mbps

Mentre considera quale rete dati utilizzare, si consiglia di rispondere alle seguenti domande:

* Quanti client sono collegati al router?

* Quante modifiche ai contenuti sono previste e quali sono tali dimensioni medie dei file?

>[!NOTE]
>Il pacchetto dati necessario deve essere almeno:
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Accertatevi che sia presente un buffer sufficiente.
>Per il caricamento iniziale di file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una quantità maggiore di dati e un tempo di download maggiore, che si riflette nelle ipotesi sopra riportate.Una rete 4G con una *buona* copertura e dati *illimitati* dovrebbe corrispondere alle installazioni più comuni di questa configurazione di rete.


### Rete locale {#lan-connection}

Le prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, consentono di disporre di una larghezza di banda sufficiente a garantire un funzionamento fluido dei AEM Screens. La rete LAN è in genere almeno uguale a una rete a 100 Mbps, per cui dovrebbe esserci una larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema.

Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti questi corrispondano ai requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalla specifica Internet Access/Router.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. Consente di scaricare e salvare localmente tutti i file multimediali necessari, come immagini e video. A causa di ciò, si verifica un traffico di rete rilevante nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio, una playlist definita che non viene aggiornata frequentemente durante il giorno, offre un funzionamento indipendente dalla rete, una volta che tutti i file sono stati salvati sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.

La tabella seguente fornisce una panoramica dei dati chiave della connettività di rete responsabili delle prestazioni che possono essere previste e dei potenziali tempi di attesa.

>[!NOTE]
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/download-times-mobile.png)



