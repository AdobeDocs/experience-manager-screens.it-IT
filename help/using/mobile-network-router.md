---
title: Rete mobile con router dati mobile e componenti di rete attivi
description: La pagina descrive Mobile Network con Mobile Data Router e Componenti Active Network
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---


# Rete mobile con router dati mobile e componenti di rete attivi {#mobile-network-setup}

Adobe AEM Screens Player può essere collegato anche utilizzando reti mobili o cellulari con almeno una rete 3G.

All&#39;interno di AEM Screens, il contenuto richiesto viene fisicamente scaricato nel controller o nel computer del lettore e archiviato correttamente nel sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali, nonché sugli aggiornamenti dei contenuti, e non influisce sulle prestazioni della riproduzione regolare dei display.

Il vantaggio di questa configurazione è che il router mobile può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è di solito in posizione elevata e aperta con il minor numero possibile di costruzione di cemento o metallo circostante.
Questa configurazione consente agli utenti di AEM Screen di essere flessibili in quanto non è necessaria una linea fissa per connettersi ad AEM Screens. Questo è particolarmente interessante per le configurazioni effimere o mobili.

Il diagramma seguente mostra la configurazione Mobile Network con Mobile Data Router e Active Network Components e contiene un accesso a Internet di uno qualsiasi dei controller AEM Screens tramite accesso diretto a Internet utilizzando un proprio Data Link 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Collegamento di AEM Screens Player alla rete mobile con il router dati mobile e i componenti di rete attivi {#connecting-aem-screens-players}

Segui i passaggi riportati di seguito per garantire la connessione corretta dei lettori AEM dello schermo in questa configurazione:

La configurazione assegna un accesso a Internet per ogni controller AEM Screens tramite accesso diretto a Internet utilizzando un collegamento dati 3/4/5G dedicato.

1. Assicurati che il Router dati mobile sia correttamente collegato alla rete dati cellulare come indicato nel Sistema operativo e che ciascuno dei lettori dello schermo AEM sia collegato alla rete router.
1. Verifica la connessione Internet richiamando un URL nel browser dei sistemi.
   >[!NOTE]
   >In caso di errore, controllare le impostazioni di rete.Esistono fondamentalmente due opzioni per una connessione di rete corretta:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurati che l&#39;impostazione della scheda di rete corrisponda all&#39;impostazione del router.

1. Controllare se il router è collegato correttamente all&#39;ISP Wide Area Network (Internet Link) Questo può anche essere identificato utilizzando un LED di segnale su router standard.
1. Se la chiamata URL ha esito positivo, puoi continuare a installare AEM Screens e registrarti. Avvia AEM Screens.

   >[!NOTE]
   >**Suggerimento per la risoluzione dei problemi**
   >Se AEM Screens non si connette correttamente e il contenuto previsto non viene visualizzato, controlla nel firewall del router Internet se sono presenti restrizioni relative a `TCP/IP Port 80/443`.


## Configurazione di Mobile Network con Mobile Data Router e Componenti di rete attivi {#requirements-direct}

La configurazione della rete può essere separata in modo logico in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità di rete già descritta, devono fornire una larghezza di banda sufficiente per eseguire in modo scorrevole il download dei contenuti AEM Screens.

** Sufficiente dipende dalla quantità di dispositivi AEM schermi collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come Smartphone, Tablet, Cashiers, Computer o reti Wi-Fi guest.
Tenere presente che tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda è generalmente in diminuzione lineare, mentre l&#39;aggiunta di più utenti/computer alla rete.
Oltre alla specifica connessione teorica di rete, è necessario garantire che la copertura del Router mobile sia almeno &quot;buona&quot;. Inoltre, il piano mensile sottostante deve coprire una capacità dati sufficiente e una larghezza di banda sufficiente per servire tutti i client collegati all&#39;interno della LAN collegata.

La tabella seguente evidenzia le reti dati con la larghezza di banda standard:

| Rete dati | Larghezza di banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Quando consideri quale Data Network deve essere utilizzato, ti consigliamo di rispondere alle seguenti domande:

* Quanti client sono connessi al Router?

* Quante modifiche sono attese e quali sono le dimensioni medie dei file?

>[!NOTE]
>
>Il pacchetto dati necessario deve essere almeno:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Per il caricamento iniziale di file multimediali, ad esempio, durante l&#39;integrazione di nuovi lettori, è necessario prevedere una maggiore quantità di dati e un maggiore tempo di download, che si rifletta nei presupposti di cui sopra. Una rete 4G con copertura *buona* e dati illimitati deve corrispondere alle installazioni più comuni in questa configurazione di rete.


### Rete locale {#lan-connection}

Le prestazioni della LAN, oltre alla raggiungibilità della rete già descritta, devono fornire una larghezza di banda sufficiente per consentire il corretto download dei contenuti AEM Screens. In questi giorni la rete LAN corrisponde di solito almeno a una rete a 100 Mbps, in modo che ci dovrebbe essere una larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Quando si utilizza un altro componente di rete attivo, è obbligatorio che tutti gli elementi corrispondano ai requisiti di larghezza di banda della rete.

Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalle specifiche Internet Access/Router.

Nel caso in cui sia prevista una soluzione Wi-Fi per collegare lo schermo a Internet Link, si consiglia di utilizzare almeno standard Wi-Fi moderni come IEEE 802.11g. Questo standard supporta connessioni fino a 54 Mbps. Tutti gli standard *più recenti* come 802.11h-n sono di migliore qualità. Se è necessario un ripetitore Wi-Fi, consigliamo vivamente le tecnologie Mesh Wi-Fi Access-Point come la rete Wi-Fi di Google Nest Mesh o simili.

## Download di file multimediali e risorse {#download}

AEM Screens offre un grande vantaggio agli utenti del digital signage. Scarica e salva localmente tutti i file multimediali necessari, come immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui vi siano nuovi contenuti da visualizzare su uno schermo specifico.
Per il normale funzionamento, ad esempio, dopo aver definito la playlist che non viene aggiornata frequentemente durante il giorno, questo offre un funzionamento simile a quello indipendente dalla rete, una volta salvati tutti i file sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con Sensor o altri Triggers e il contenuto è molto dinamico, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo per garantire la migliore esperienza cliente possibile.
Le tabelle seguenti offrono una buona panoramica del significato dei dati chiave per la connettività di rete per le prestazioni previste e i potenziali tempi di attesa.

>[!NOTE]
>
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo della rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/using/assets/mobile-router-download.png)
