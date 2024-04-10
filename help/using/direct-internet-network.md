---
title: Accesso diretto a Internet
description: Accesso diretto a Internet
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# Rete Internet diretta (cablata/wireless) {#direct-internet-access}

La rete Internet diretta contiene un punto di accesso a Internet per raggiungere i Cloud Service AEM ai quali AEM Screens deve connettersi.

Le porte standard per la comunicazione AEM Screens sono:

* `ssl-secured https (TCP Port 443)`
  <br>Oppure</br>

* `http (TCP Port 80)`, se il tuo caso d’uso particolare non richiede quel livello di sicurezza.

Le porte possono variare a causa della configurazione della configurazione dedicata dell’AEM. All&#39;interno di questa configurazione, tutte le periferiche sono collegate direttamente al router Internet, come illustrato nella figura seguente.

![](/help/assets/direct-access-2.png)

La configurazione include anche l&#39;accesso a Internet da parte di qualsiasi provider di servizi Internet (ISP) e la relativa linea Internet. La maggior parte degli ISP fornisce un router Internet che copre modem Internet, switch di rete, punto di accesso Wi-Fi, firewall e altre funzionalità di rete (a seconda del produttore e del modello).

## Connessione di AEM Screens Player all&#39;accesso diretto a Internet

Segui i passaggi seguenti per garantire la corretta connessione dei lettori AEM Screen in questa configurazione:

1. Verificare che ogni lettore di schermo AEM sia collegato alla rete del router.
1. Verificare la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >In caso di errore, controllare le impostazioni di rete. Esistono fondamentalmente due opzioni per una connessione di rete corretta:
   >* DHCP
   >* Configurazione IP manuale

1. Verificare che l&#39;impostazione della scheda di rete corrisponda alle impostazioni del router; verificare che non sia stato raggiunto il numero massimo di indirizzi IP disponibili nella rete.
1. Verificare che il router sia connesso correttamente all&#39;ISP Wide Area Network (collegamento Internet). Questo può anche essere identificato utilizzando un LED di segnale sui router standard.
1. Se la chiamata URL ha esito positivo, puoi continuare a installare AEM Screens e registrarti. Avvia AEM Screens.

   >[!NOTE]
   >**Suggerimento per la risoluzione dei problemi**
   >Se AEM Screens non si connette correttamente e il contenuto previsto non viene visualizzato:
   >
   >1. Se sono presenti restrizioni relative a, controlla nel firewall del router Internet `TCP/IP Port 80/443`.
   >1. Verificare che tutte le porte richieste siano consentite.

## Configurazione di una rete Internet diretta {#requirements-direct}

La rete Internet diretta è logicamente suddivisa in due blocchi:

* Wide Area Network

* Local Area Network

### Wide Area Network {#wan-connection}

Oltre alla raggiungibilità della rete, la connessione Internet fornisce una larghezza di banda sufficiente per il funzionamento di AEM Screens.

*Sufficiente* dipende dal numero di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi guest.

>[!NOTE]
>
>I dispositivi sopra menzionati hanno un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce in modo lineare quando si aggiungono più utenti o computer alla rete.

### Local Area Network {#lan-connection}

Le prestazioni della rete LAN (Local Area Network), oltre alla raggiungibilità della rete, forniscono una larghezza di banda sufficiente per il funzionamento di AEM Screens.

La rete LAN di solito corrisponde almeno a una rete a 100 Mbps, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema.
Nel caso in cui sia prevista una soluzione Wi-Fi per collegare AEM Screens al collegamento Internet, si consiglia di utilizzare standard Wi-Fi moderni come `IEEE 802.11g` come minimo. Questo standard supporta connessioni fino a 54 Mbps. Qualsiasi *più recente* Standard come `802.11h-n` sono di migliore qualità.

>[!NOTE]
>
>Se è necessario un ripetitore Wi-Fi, Adobe consiglia un punto di accesso Wi-Fi Mesh come Google Nest Mesh Wi-Fi o simile. Altre tecnologie di ripetizione Wi-Fi finiscono in una massiccia perdita di larghezza di banda nella rete globale.

## Download di contenuti multimediali e risorse {#download}

AEM Screens offre un vantaggio significativo agli utenti di digital signage. Scarica e salva localmente tutti i file multimediali necessari, ad esempio immagini e video. Il traffico di rete principale si verifica quando è presente un nuovo contenuto da visualizzare su una visualizzazione specifica.

Per le normali operazioni, ad esempio una playlist definita che si aggiorna frequentemente durante il giorno - offre un funzionamento simile a quello della rete, dopo che tutti i file sono stati salvati sul lettore.

Negli scenari in cui sono presenti più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata allo schermo al fine di garantire la migliore esperienza possibile per il cliente.

Nella tabella seguente viene fornita una panoramica sui dati chiave della connettività di rete.

>[!NOTE]
>
>Le informazioni consentono di visualizzare il consumo di ogni dispositivo nella rete che richiede e scarica un&#39;origine Internet. Ognuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/assets/download-times-direct.png)
