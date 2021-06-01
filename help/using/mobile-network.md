---
title: Rete mobile diretta
description: La pagina descrive l’impostazione della rete mobile diretta
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Rete mobile diretta {#mobile-network-setup}

I lettori AEM Screens possono anche essere collegati tramite reti mobili o cellulari con almeno una rete 3G.

All&#39;interno di AEM Screens, il contenuto richiesto viene fisicamente scaricato nel controller o nel computer del lettore e archiviato correttamente nel sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali, nonché sugli aggiornamenti dei contenuti, e non influisce sulle prestazioni della riproduzione regolare dei display.

Il vantaggio di collegare i lettori AEM Screens su Cellular 3/4/5G al provider di dati di Mobile Services è che il router mobile può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è di solito in posizione elevata e aperta con il minor numero possibile di costruzione di cemento o metallo circostante.

Questa configurazione consente agli utenti di AEM Screen una grande flessibilità in quanto non è necessaria alcuna connessione fissa per connettersi ad AEM Screens. Questo è particolarmente interessante per le configurazioni effimere o mobili.

Il diagramma seguente mostra la Configurazione di rete mobile diretta ed è costituito da un unico segmento di connessione di rete e dalla connessione di ciascun lettore alla Rete dati mobile o cellulare.

![](/help/using/assets/direct-mobile-1.png)

## Collegamento di AEM Screens Player alla rete mobile diretta {#connecting-aem-screens-players}

Segui i passaggi riportati di seguito per garantire la connessione corretta dei lettori AEM dello schermo in questa configurazione:

1. Assicurati che ciascuno dei lettori dello schermo AEM sia collegato alla rete del router.

1. Verifica la connessione Internet richiamando un URL nel browser dei sistemi.

   >[!NOTE]
   >Se ricevi un messaggio di errore, controlla le impostazioni di rete e verifica se è presente un collegamento di rete sufficiente e se il firewall del sistema operativo è configurato per consentire l’accesso di rete utilizzando le porte di comunicazione AEM Screens configurate.

1. Se la chiamata URL ha esito positivo puoi continuare a installare AEM Screens e registrarti. Avvia AEM Screens.

## Configurazione della rete mobile diretta {#requirements-direct}

La configurazione della rete può essere separata in modo logico in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet oltre alla raggiungibilità della rete consentono di disporre di una larghezza di banda sufficiente per il corretto funzionamento di AEM Screens.

In Direct Mobile Network, ogni lettore è collegato a una singola scheda dati mobile alla rete dati dei fornitori.

La tabella seguente evidenzia le reti dati con la larghezza di banda standard:

| Rete dati | Larghezza di banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Quando consideri quale Data Network deve essere utilizzato, ti consigliamo di rispondere alle seguenti domande:

La velocità di rete disponibile dipende dal piano specifico del provider di dati mobili e dalla copertura disponibile raggiunta nel percorso del controller AEM Screens.
Durante questa configurazione, è necessario tenere presente che oltre alla larghezza di banda disponibile alcuni piani dei fornitori di dati mobili limitano la quantità di dati disponibili che attraversano la connessione entro un periodo di tempo specifico. È necessario garantire che vi sia sufficiente capacità nella quantità di dati e larghezza di banda.
Come follow-up del pacchetto dati necessario deve essere almeno:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Per il caricamento iniziale di file multimediali, ad esempio durante l&#39;integrazione di nuovi lettori, è necessario prevedere una maggiore quantità di dati e un maggiore tempo di download, che si rifletta nelle ipotesi di cui sopra. Una rete 4G con una copertura *buona* e dati *illimitati* deve corrispondere alle installazioni più comuni in questa configurazione di rete.

>[!NOTE]
>Un piano 3G minimo con una buona copertura di rete dovrebbe portare a prestazioni di download accettabili per un lettore AEM Screens. Se è disponibile solo una copertura equa in una posizione specifica, è necessario prendere in considerazione l&#39;impostazione complessiva della rete su [Rete mobile con router dati mobile e componenti di rete attivi](/help/using/mobile-network-router.md).


### Rete locale {#lan-connection}

I problemi di prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, sono di fornire una larghezza di banda sufficiente per funzionare AEM Screens senza problemi. La raccomandazione per la velocità di rete LAN è di partire almeno da reti a 100 Mbps, in modo che vi sia una larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema.

Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti corrispondano ai requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalle specifiche di accesso a Internet o Router. In caso contrario, la larghezza di banda totale sarà limitata dal collegamento più debole della catena di rete.

## Download di file multimediali e risorse {#download}

AEM Screens offre un grande vantaggio agli utenti del digital signage. Scarica e salva localmente tutti i file multimediali necessari, come immagini e video. Il traffico di rete principale si verifica quando su una visualizzazione specifica è presente un nuovo contenuto da visualizzare.

Per le operazioni normali, ad esempio, una playlist definita che si aggiorna frequentemente durante il giorno, offre un funzionamento simile a quello della rete, una volta salvati tutti i file sul lettore.

Per gli scenari in cui vi sono più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza del cliente possibile.

La tabella seguente fornisce una panoramica dei dati chiave della connettività di rete.

>[!NOTE]
>
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo della rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/using/assets/download-times-mobile.png)



