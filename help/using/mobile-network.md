---
title: Rete mobile diretta
description: La pagina descrive l’impostazione della rete mobile diretta
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 0%

---


# Rete mobile diretta {#mobile-network-setup}

I giocatori di AEM Screens possono anche essere collegati utilizzando reti mobili o cellulari in esecuzione almeno su una rete 3G.

All&#39;interno dei AEM Screens, il contenuto richiesto viene scaricato fisicamente nel controller del lettore o nel computer e memorizzato correttamente all&#39;interno del sistema operativo sottostante. Di conseguenza, la larghezza di banda specificata influisce solo sui tempi di download iniziali e non sulle prestazioni dei display.

Il vantaggio di collegare i lettori AEM Screens con una connessione Cellulare 3/4/5G al provider di dati Mobile Service è che il router mobile può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è solitamente in posizione elevata e aperta con il più possibile la costruzione di calcestruzzo o metallo circostante.

Questa configurazione consente agli utenti di AEM Screen una grande flessibilità, in quanto non è necessaria alcuna connessione fissa per connettersi ai AEM Screens.

Il diagramma seguente mostra l&#39;impostazione della rete mobile diretta ed è costituito da un segmento di connessione di rete singolo e dalla connessione di ciascun lettore alla rete di dati mobile o cellulare.

![](/help/using/assets/direct-mobile-1.png)

## Collegamento del lettore AEM Screens alla rete mobile diretta {#connecting-aem-screens-players}

Segui i passaggi indicati di seguito per garantire la corretta connessione dei lettori dello schermo AEM in questa configurazione:

1. Accertatevi che ciascuno dei lettori dello schermo AEM sia collegato alla rete Routers.

1. Verificate la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Nel caso in cui venga visualizzato un messaggio di errore, verificare le impostazioni di rete e verificare se è presente un collegamento di rete sufficiente e se il firewall del sistema operativo è configurato per consentire l&#39;accesso di rete utilizzando le porte di comunicazione AEM Screens configurate.

1. Se la chiamata URL ha esito positivo, potete continuare a installare gli AEM Screens e registrarvi. AEM Screens iniziali.

## Impostazione di una rete mobile diretta {#requirements-direct}

La configurazione della rete può essere logicamente separata in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet oltre alla raggiungibilità della rete forniscono una larghezza di banda sufficiente per il corretto funzionamento dei AEM Screens.

In Direct Mobile Network, ogni lettore è collegato a una singola scheda dati mobile alla rete dati del provider.

Nella tabella seguente sono evidenziate le reti di dati con larghezza di banda standard:

| Rete dati | Larghezza di banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Mentre considera quale rete dati utilizzare, si consiglia di rispondere alle seguenti domande:

La velocità di rete disponibile dipende dal piano specifico Mobile Data Provider e con la copertura disponibile raggiunta nella posizione del controller AEM Screens.
Dopo questa configurazione, è anche necessario tenere presente che oltre alla larghezza di banda disponibile, alcuni piani Mobile Data Provider limitano la quantità di dati disponibili che si trovano attraverso la connessione entro un periodo di tempo specifico. Occorre garantire che la capacità in quantità di dati e larghezza di banda sia sufficiente.
Come follow-up il pacchetto dati necessario deve essere almeno:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>
>Per il caricamento iniziale di file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una quantità maggiore di dati e un tempo di download maggiore, che si riflette nelle ipotesi sopra riportate.Una rete 4G con una *buona* copertura e dati *illimitati* dovrebbe corrispondere alle installazioni più comuni di questa configurazione di rete.

>[!NOTE]
>
>Un piano 3G minimo con una buona copertura di rete dovrebbe portare a prestazioni di download accettabili per un lettore AEM Screens. Se esiste solo una copertura equa disponibile in una posizione specifica, è necessario considerare la possibilità di passare dall&#39;impostazione della rete alla rete [mobile con Mobile Data Router e Active Network Components](/help/using/mobile-network-router.md).


### Rete locale {#lan-connection}

Le prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, consentono di disporre di una larghezza di banda sufficiente a garantire un funzionamento fluido dei AEM Screens. La rete LAN solitamente corrisponde a una rete a 100 Mbps, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema.

Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti questi corrispondano ai requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalla specifica di accesso a Internet o Router.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. Consente di scaricare e salvare localmente tutti i file multimediali necessari, come immagini e video. Il traffico di rete principale si verifica in presenza di nuovo contenuto da visualizzare su un display specifico.

Per le normali operazioni, ad esempio, una playlist definita che si aggiorna frequentemente durante il giorno, offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore.

Per gli scenari in cui ci sono più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza del cliente.

La tabella seguente fornisce una panoramica sui dati chiave della connettività di rete.

>[!NOTE]
>
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/download-times-mobile.png)



