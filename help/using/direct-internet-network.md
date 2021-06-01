---
title: Accesso diretto a Internet
description: Accesso diretto a Internet
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Rete Internet diretta (cablata/wireless) {#direct-internet-access}

La rete Internet diretta contiene un punto di accesso per l’accesso a Internet al fine di raggiungere i servizi cloud AEM a cui AEM Screens deve connettersi.

Le porte standard per la comunicazione AEM Screens sono:
* `ssl-secured https (TCP Port 443)`

   <br>Oppure,</br>

* `http (TCP Port 80)`, se il tuo caso d’uso specifico non richiede quel livello di sicurezza.

Le porte possono variare a causa della configurazione della configurazione AEM dedicata. All&#39;interno di questo SetUp, tutti i dispositivi sono direttamente collegati al router Internet come mostrato nella figura riportata di seguito.

![](/help/assets/direct-access-2.png)

La configurazione include anche un accesso a Internet da parte di qualsiasi provider di servizi Internet (ISP) e la sua linea Internet. La maggior parte degli ISP fornisce un router Internet che copre il modem Internet, lo switch di rete, il punto di accesso Wi-Fi, il firewall e altre funzionalità di rete (a seconda del produttore e del modello).

## Connessione di AEM Screens Player all&#39;accesso diretto a Internet {#connecting-aem-screens-players}

Segui i passaggi riportati di seguito per garantire la connessione corretta dei lettori AEM dello schermo in questa configurazione:

1. Assicurati che ciascuno dei lettori dello schermo AEM sia collegato alla rete del router.
1. Verifica la connessione Internet richiamando un URL nel browser dei sistemi.

   >[!NOTE]
   >In caso di errore, controllare le impostazioni di rete.Esistono fondamentalmente due opzioni per una connessione di rete corretta:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurati che l&#39;impostazione della scheda di rete corrisponda alle impostazioni del router e controlla se la quantità massima di indirizzi IP disponibili nella rete non viene raggiunta.

1. Verificare che il router sia collegato correttamente all&#39;ISP Wide Area Network (Internet Link). Questo può essere identificato anche utilizzando un LED di segnale su router standard.
1. Se la chiamata URL ha esito positivo, puoi continuare a installare AEM Screens e registrarti. Avvia AEM Screens.

   >[!NOTE]
   >**Suggerimento per la risoluzione dei problemi**
   >Se AEM Screens non si connette correttamente e il contenuto previsto non viene visualizzato:
   >
   >1. Controlla il firewall per i router Internet in caso di restrizioni relative a `TCP/IP Port 80/443`.
   >1. Assicurati che tutte le porte richieste siano consentite.


## Configurazione della rete di accesso diretto {#requirements-direct}

La rete Internet diretta è logicamente separata in due blocchi:

* Rete ampia

* Rete locale

### Rete ampia {#wan-connection}

Oltre alla raggiungibilità della rete, le prestazioni della connessione Internet forniscono una larghezza di banda sufficiente per l&#39;utilizzo di AEM Screens.

** Sufficiente dipende dal numero di schermi AEM collegati e dall’utilizzo di altri consumatori all’interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi guest.

>[!NOTE]
>
>Tutti i dispositivi di cui sopra, hanno un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce linearmente quando si aggiungono più consumatori o computer alla rete.

### Rete locale {#lan-connection}

Le prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, offrono una larghezza di banda sufficiente per l&#39;utilizzo di AEM Screens.

La rete LAN solitamente corrisponde ad almeno una rete a 100 Mbps, in modo da disporre di una larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema.
Nel caso in cui sia prevista una soluzione Wi-Fi per collegare AEM Screens a Internet Link, si consiglia di utilizzare almeno standard Wi-Fi moderni come `IEEE 802.11g`. Questo standard supporta connessioni fino a 54 Mbps. Tutti gli standard *più recenti* come `802.11h-n` sono di migliore qualità.

>[!NOTE]
>
>Se è necessario un ripetitore Wi-Fi, si consiglia vivamente un punto di accesso Mesh Wi-Fi come la rete Wi-Fi di Google Nest Mesh o simile. Altre tecnologie ripetute Wi-Fi finiscono in una perdita massiccia di larghezza di banda nella rete complessiva.

## Download di file multimediali e risorse {#download}

AEM Screens offre un grande vantaggio agli utenti del digital signage. Scarica e salva localmente tutti i file multimediali necessari, come immagini e video. Il traffico di rete principale si verifica quando su una visualizzazione specifica è presente un nuovo contenuto da visualizzare.

Per le operazioni normali, ad esempio, una playlist definita che si aggiorna frequentemente durante il giorno, offre un funzionamento simile a quello della rete, una volta salvati tutti i file sul lettore.

Per gli scenari in cui vi sono più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza del cliente possibile.

La tabella seguente fornisce una panoramica dei dati chiave della connettività di rete.

>[!NOTE]
>
>Le informazioni consentono di visualizzare il consumo di ogni dispositivo della rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/assets/download-times-direct.png)

