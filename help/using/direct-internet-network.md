---
title: Accesso diretto a Internet
description: Accesso diretto a Internet
translation-type: tm+mt
source-git-commit: 77cf87cbce39a00528b2690d9689861b91e61fc5
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---


# Rete Internet diretta (via cavo/wireless) {#direct-internet-access}

La rete Internet diretta contiene un punto di accesso per l&#39;accesso a Internet al fine di raggiungere i AEM cloud services a cui i AEM Screens devono connettersi.

Le porte standard per la comunicazione AEM Screens sono:
* `http (TCP Port 80)`
Oppure,
* `ssl-secured https (TCP Port 443)`

Le porte possono variare a causa della configurazione della configurazione AEM. In questa configurazione, tutti i dispositivi sono direttamente collegati al router Internet come mostrato nella figura seguente.

![](/help/assets/direct-access-2.png)

La configurazione include anche un accesso a Internet da parte di un provider di servizi Internet (ISP) e una linea Internet. La maggior parte dei provider Internet fornisce un router Internet che copre il modem Internet, lo switch di rete, il punto di accesso WIFI, il firewall e altre funzionalità di rete (a seconda del produttore e del modello).

## Collegamento del lettore AEM Screens a Direct Internet Access {#connecting-aem-screens-players}

Segui i passaggi indicati di seguito per collegare i lettori di schermo AEM in questa configurazione:

1. Accertatevi che ciascuno dei lettori dello schermo AEM sia collegato alla rete Routers.
1. Verificate la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Nel caso in cui venga visualizzato un messaggio di errore, controllare le impostazioni di rete. Esistono sostanzialmente due opzioni per una connessione di rete adeguata:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurarsi che l&#39;impostazione della scheda di rete corrisponda all&#39;impostazione del router e verificare che la quantità massima di indirizzi IP disponibili nella rete non sia raggiunta.

1. Verificare che il router sia connesso correttamente alla rete Internet Wide Area Network (Internet Link). Questo può essere identificato anche utilizzando un LED di segnale su router standard.
1. Se la chiamata URL ha esito positivo, potete continuare a installare gli AEM Screens e registrarvi. AEM Screens iniziali.

   >[!NOTE]
   >**Suggerimenti per la risoluzione dei problemi**
   >Se i AEM Screens non si connettono correttamente e non mostrano il contenuto previsto:
   >
   >1. Se sono presenti restrizioni, controllate il firewall Internet Router `TCP/IP Port 80/443`.
   >1. Accertatevi che tutte le porte necessarie siano consentite.


## Requisiti per la configurazione della rete di accesso diretto {#requirements-direct}

La rete Internet diretta può essere logicamente separata in due blocchi:

* Ampia rete di reti

* Rete locale

### Ampia rete di reti {#wan-connection}

Oltre alla raggiungibilità della rete, le prestazioni della connessione Internet consentono di fornire una larghezza di banda sufficiente per il funzionamento dei AEM Screens.

*Sufficiente* dipende dalla quantità di schermi AEM connessi e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassiere, computer o reti WIFI guest.

>[!NOTE]
>Tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce in modo lineare quando si aggiungono più utenti o computer alla rete.

### Rete locale {#lan-connection}

Le prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, forniscono una larghezza di banda sufficiente per il funzionamento dei AEM Screens.

La rete LAN solitamente corrisponde ad almeno una rete a 100 Mbps, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema.
Nel caso in cui sia prevista una soluzione WIFI per collegare AEM Screens a Internet Link, si consiglia di utilizzare standard WIFI moderni come `IEEE 802.11g` minimo. Questo standard supporta connessioni fino a 54 Mbps. Tutti gli standard *più recenti* come `802.11h-n` sono di migliore qualità.

>[!NOTE]
>Se è richiesto un Ripetitore WIFI, consigliamo vivamente le tecnologie Mesh WIFI Access-point come Google Nest Mesh WIFI o simili. Altre tecnologie ripetute WiFi finiscono con una massiccia perdita di larghezza di banda nella rete.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. Consente di scaricare e salvare localmente tutti i file multimediali necessari, come immagini e video. Il traffico di rete principale si verifica in presenza di nuovo contenuto da visualizzare su un display specifico.

Per le normali operazioni, ad esempio, con una playlist definita che si aggiorna frequentemente durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta che tutti i file sono stati salvati sul lettore.

Per quei casi d&#39;uso in cui ci sono più interazioni con sensori o altri attivatori e il contenuto è molto dinamico, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo per garantire la migliore esperienza del cliente.

La tabella seguente fornisce una panoramica sui dati chiave della connettività di rete.

>[!NOTE]
>Le informazioni consentono di visualizzare il consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/assets/download-times-direct.png)
