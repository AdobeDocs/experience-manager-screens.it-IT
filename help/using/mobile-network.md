---
title: Direct Mobile Network
description: La pagina descrive l’installazione di Direct Mobile Network
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Direct Mobile Network {#mobile-network-setup}

I lettori AEM Screens possono anche essere collegati utilizzando reti mobili o cellulari che eseguono almeno una rete 3G.

All’interno di AEM Screens, il contenuto richiesto viene fisicamente scaricato sul controller o sul computer del lettore e memorizzato correttamente all’interno del sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali, nonché sugli aggiornamenti dei contenuti, e non influenza le prestazioni della riproduzione regolare dei display.

Il vantaggio di collegare i lettori AEM Screens tramite la rete cellulare 3/4/5G al provider di dati Mobile Services è che il router mobile può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo di solito è in una posizione elevata e aperta con il minor numero possibile di costruzioni circostanti in calcestruzzo o metallo.

Questa configurazione offre agli utenti di Schermo AEM una grande flessibilità in quanto non è necessaria alcuna connessione fissa per connettersi ad AEM Screens. Questo è particolarmente interessante per le configurazioni temporanee o mobili.

Il diagramma seguente mostra la configurazione della rete mobile diretta ed è costituito da un singolo segmento di connessione di rete e dalla connessione di ciascun lettore alla rete dati mobile o cellulare.

![](/help/using/assets/direct-mobile-1.png)

## Collegamento di AEM Screens Player a Direct Mobile Network {#connecting-aem-screens-players}

Segui i passaggi seguenti per garantire la corretta connessione dei lettori AEM Screen in questa configurazione:

1. Verificare che ogni lettore di schermo AEM sia collegato alla rete del router.

1. Verifica la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Se ricevi un messaggio di errore, controlla le impostazioni di rete e verifica se è presente un collegamento di rete sufficiente e se il firewall del sistema operativo è configurato per consentire l’accesso alla rete utilizzando le porte di comunicazione di AEM Screens configurate.

1. Se la chiamata URL ha esito positivo, puoi continuare a installare AEM Screens e registrarti. Avvia AEM Screens.

## Configurazione di una rete mobile diretta {#requirements-direct}

L&#39;installazione di rete può essere separata logicamente in due blocchi:

* Connessione Internet mobile

* Local Area Network

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet oltre alla raggiungibilità della rete forniscono una larghezza di banda sufficiente per il corretto funzionamento di AEM Screens.

In Direct Mobile Network (Rete mobile diretta), ogni lettore è collegato alla rete dati dei provider tramite una singola scheda dati mobile.

Nella tabella seguente vengono evidenziate le reti dati con la relativa larghezza di banda standard:

| Rete dati | Larghezza di banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Nel considerare quale rete dati utilizzare, si consiglia di rispondere alle seguenti domande:

La velocità di rete disponibile dipende dal piano specifico del provider di dati mobili e dalla copertura disponibile raggiunta nella posizione del controller di AEM Screens.
Durante questa configurazione, è anche necessario tenere in considerazione che oltre alla larghezza di banda disponibile alcuni piani dei provider di dati mobili limitano la quantità di dati disponibili che passano attraverso la connessione entro un periodo di tempo specifico. È necessario assicurarsi che vi sia sufficiente capacità nella quantità di dati e nella larghezza di banda.
Come follow-up il pacchetto di dati necessario deve essere almeno:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Per il caricamento iniziale dei file multimediali, ad esempio durante l’integrazione di nuovi lettori, è necessario attendersi una maggiore quantità di dati e un tempo di download maggiore, ipotesi che si riflettono in precedenza. Una rete 4G con *buono* copertura e *illimitato* I dati devono corrispondere alle installazioni più comuni in questa configurazione di rete.

>[!NOTE]
>Un piano 3G minimo con una buona copertura di rete dovrebbe portare a prestazioni di download accettabili per un lettore AEM Screens. Se in un luogo specifico è disponibile solo una copertura equa, occorre prendere in considerazione il passaggio dell&#39;impostazione generale della rete a [Rete mobile con router dati mobile e componenti di rete attivi](/help/using/mobile-network-router.md).


### Local Area Network {#lan-connection}

Oltre alla raggiungibilità della rete, i problemi di prestazioni della rete LAN sono quelli di fornire una larghezza di banda sufficiente per il corretto funzionamento di AEM Screens. Si consiglia di iniziare con una velocità di rete di almeno 100 Mbps, in modo da disporre di una larghezza di banda sufficiente per collegare al sistema molti dispositivi con buone prestazioni.

Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti i componenti corrispondano ai requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalle specifiche di accesso a Internet o router. In caso contrario, la larghezza di banda totale sarà limitata dall&#39;anello più debole della catena di rete.

## Download di contenuti multimediali e risorse {#download}

AEM Screens offre un grande vantaggio agli utenti di digital signage. Scarica e salva localmente tutti i file multimediali necessari, ad esempio immagini e video. Il traffico di rete principale si verifica quando è presente un nuovo contenuto da visualizzare su una visualizzazione specifica.

Per le normali operazioni, ad esempio, una playlist definita che si aggiorna frequentemente durante il giorno - offre un funzionamento simile a quello della rete, una volta che tutti i file sono stati salvati sul lettore.

Negli scenari in cui sono presenti più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata allo schermo al fine di garantire la migliore esperienza possibile per il cliente.

Nella tabella seguente viene fornita una panoramica sui dati chiave della connettività di rete.

>[!NOTE]
>
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una sorgente Internet. Ognuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/using/assets/download-times-mobile.png)
