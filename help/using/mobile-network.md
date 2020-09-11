---
title: Rete mobile diretta
description: La pagina descrive l’impostazione della rete mobile diretta
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Rete mobile diretta {#mobile-network-setup}

 AEM Screens Players può essere collegato utilizzando reti mobili o cellulari che eseguono almeno una rete 3G.

All&#39;interno  AEM Screens, il contenuto richiesto viene scaricato fisicamente nel controller del lettore o nel computer e archiviato correttamente all&#39;interno del sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali, nonché sugli aggiornamenti dei contenuti, e non influenza le prestazioni della riproduzione regolare dei display.

Il vantaggio di collegare  lettori AEM Screens Cellulare 3/4/5G al provider di dati Mobile Service è che il router Mobile può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è solitamente in posizione elevata e aperta con il minor numero possibile di costruzione di cemento o metallo circostante.

Questa configurazione consente agli utenti AEM schermo una grande flessibilità, in quanto non è necessaria una connessione fissa per  AEM Screens. Questo è particolarmente interessante per le impostazioni effimere o mobili.

Il diagramma seguente mostra l&#39;impostazione della rete mobile diretta ed è costituito da un segmento di connessione di rete singolo e dalla connessione di ciascun lettore alla rete di dati mobile o cellulare.

![](/help/using/assets/direct-mobile-1.png)

## Collegamento  AEM Screens Player alla rete mobile diretta {#connecting-aem-screens-players}

Seguire i passaggi indicati di seguito per garantire la corretta connessione dei lettori AEM dello schermo in questa configurazione:

1. Assicurarsi che ciascuno dei lettori AEM dello schermo sia collegato alla rete del router.

1. Verificate la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Se ricevi un messaggio di errore, controlla le impostazioni di rete e verifica se è presente un collegamento di rete sufficiente e se il firewall del sistema operativo è configurato per consentire l&#39;accesso di rete utilizzando le porte di comunicazione AEM Screens  configurate.

1. Se la chiamata URL ha esito positivo, potete continuare a installare l’AEM Screens  e registrarvi. Avviate  AEM Screens.

## Impostazione di una rete mobile diretta {#requirements-direct}

La configurazione della rete può essere logicamente separata in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet oltre alla raggiungibilità della rete forniscono una larghezza di banda sufficiente per funzionare  AEM Screens senza problemi.

In Direct Mobile Network, ogni lettore è collegato a una singola scheda dati mobile alla rete dati del provider.

Nella tabella seguente sono evidenziate le reti di dati con larghezza di banda standard:

| Rete dati | Larghezza di banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Mentre considera quale rete dati utilizzare, si consiglia di rispondere alle seguenti domande:

La velocità di rete disponibile dipende dal piano specifico del provider di dati mobili e con la copertura disponibile che viene raggiunta nella posizione del controller AEM Screens .
Dopo questa configurazione, è anche necessario tenere presente che oltre alla larghezza di banda disponibile, alcuni piani Mobile Data Provider limitano la quantità di dati disponibili che si trovano attraverso la connessione entro un periodo di tempo specifico. Occorre garantire che la capacità in quantità di dati e larghezza di banda sia sufficiente.
Come follow-up il pacchetto dati necessario deve essere almeno:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Per il caricamento iniziale dei file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una maggiore quantità di dati e un maggiore tempo di scaricamento, che si rifletta nelle ipotesi di cui sopra. Una rete 4G con una *buona* copertura e dati *illimitati* dovrebbe corrispondere alle installazioni più comuni di questa configurazione di rete.

>[!NOTE]
>Un piano 3G minimo con una buona copertura di rete dovrebbe portare a prestazioni di download accettabili per un lettore AEM Screens . Se esiste solo una copertura equa disponibile in una posizione specifica, è necessario considerare la possibilità di passare dall&#39;impostazione della rete alla rete [mobile con Mobile Data Router e Active Network Components](/help/using/mobile-network-router.md).


### Rete locale {#lan-connection}

I problemi di prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, sono di fornire una larghezza di banda sufficiente per operare  AEM Screens senza problemi. La raccomandazione per le velocità di rete LAN è di avviare le reti a 100 Mbps almeno, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema.

Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti questi corrispondano ai requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalla specifica di accesso a Internet o Router. In caso contrario, la larghezza di banda totale sarà limitata dal collegamento più debole nella catena di rete.

## Download di file multimediali e risorse {#download}

 AEM Screens offre un grande vantaggio agli utenti del digital signage. Consente di scaricare e salvare localmente tutti i file multimediali necessari, come immagini e video. Il traffico di rete principale si verifica in presenza di nuovo contenuto da visualizzare su un display specifico.

Per le normali operazioni, ad esempio, una playlist definita che si aggiorna frequentemente durante il giorno, offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore.

Per gli scenari in cui ci sono più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza del cliente.

La tabella seguente fornisce una panoramica sui dati chiave della connettività di rete.

>[!NOTE]
>
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/download-times-mobile.png)



