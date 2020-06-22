---
title: Accesso diretto a Internet
description: Accesso diretto a Internet
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Accesso diretto a Internet {#direct-internet-access}

La configurazione Accesso diretto a Internet contiene un punto di accesso per l&#39;accesso a Internet al fine di raggiungere i AEM cloud services a cui i AEM Screens devono connettersi.

Le porte standard per la comunicazione AEM Screens sono:
* `http (TCP Port 80)`
Oppure,
* `ssl-secured https (TCP Port 443)`

Le porte possono variare a causa della configurazione della configurazione AEM. In questa configurazione, tutti i dispositivi sono direttamente collegati al router Internet come mostrato nella figura seguente.

![](/help/assets/direct-access-2.png)

La configurazione include anche un accesso a Internet da parte di un provider di servizi Internet (ISP) e una linea Internet. La maggior parte dei provider Internet fornisce un router Internet che copre il modem Internet, lo switch di rete, il punto di accesso WIFI, il firewall e altre funzionalità di rete (a seconda del produttore e del modello).

>[!NOTE]
>**Suggerimenti per la risoluzione dei problemi **>Se i AEM Screens non si connettono correttamente e mostra il contenuto previsto:
>
>1. Se sono presenti restrizioni, controllate il firewall Internet Router `TCP/IP Port 80/443`.
>1. Verificate che tutte le porte necessarie siano consentite e riprovate.


## Requisiti per la configurazione della rete di accesso diretto {#requirements-direct}

L&#39;impostazione della rete di accesso diretto può essere logicamente separata in due blocchi. Il blocco di connessione Internet/mondo WAN/esterno e la rete LAN/locale interna.

### WAN / Connessione Internet {#wan-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete già descritta, devono fornire una larghezza di banda sufficiente per utilizzare AEM Screens in modo ordinato e ordinato. In dettaglio, &quot;sufficiente&quot; dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti WiFi per gli ospiti.
Tenere presente che tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda è generalmente in diminuzione lineare, mentre l&#39;aggiunta di più consumatori/computer alla rete.

### Connessione LAN {#lan-connection}

Le prestazioni della LAN, oltre alla raggiungibilità della rete già descritta, garantiscono una larghezza di banda sufficiente per il funzionamento dei AEM Screens in modo ordinato e ordinato. In questi giorni la rete LAN corrisponde almeno a una rete da 100 MBit/sec, in modo che ci dovrebbe essere larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema.
Nel caso in cui sia prevista una soluzione WIFI per collegare lo schermo a Internet Link, si consiglia di utilizzare come minimo standard WIFI moderni come IEEE 802.11g. Questo standard supporta connessioni fino a 54 Mbit. Tutti gli standard *più recenti* come 802.11h-n sono di qualità migliore. Se è richiesto un Ripetitore WIFI, consigliamo vivamente le tecnologie Mesh WIFI Access-point come Google Nest Mesh WIFI o simili.
Altre tecnologie ripetute WiFi finiscono con una massiccia perdita di larghezza di banda nella rete.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. È in corso il download e il salvataggio locale di tutti i file multimediali necessari, come immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio, avendo definito una playlist che non cambia molto spesso durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta che tutti i file sono stati salvati sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con sensori o altri attivatori e il contenuto è molto dinamico, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo per garantire la migliore esperienza cliente.

La tabella seguente fornisce una panoramica sui dati chiave di connettività di rete:

![](/help/assets/download-times-direct.png)

>[!NOTE]
>Le informazioni consentono di visualizzare il consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.