---
title: Rete mobile con Mobile Data Router e Componenti di rete attivi
description: La pagina descrive Mobile Network con Mobile Data Router e Active Network Components
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---


# Rete mobile con Mobile Data Router e Componenti di rete attivi {#mobile-network-setup}

È inoltre possibile collegare i lettori di AEM Screens Adobe utilizzando reti mobili o cellulari con almeno una rete 3G.

All&#39;interno dei AEM Screens, il contenuto richiesto viene scaricato fisicamente nel controller del lettore o nel computer e memorizzato correttamente all&#39;interno del sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali, nonché sugli aggiornamenti dei contenuti, e non influisce sulle prestazioni della riproduzione regolare dei display.

Il vantaggio di questa configurazione è che Mobile Router può essere collocato in una posizione ottimizzata per garantire la migliore copertura di rete disponibile. Questo è solitamente in posizione elevata e aperta con il minor numero possibile di costruzione di cemento o metallo circostante.
Questa configurazione consente agli utenti di AEM Screen la flessibilità, in quanto non è necessaria una linea fissa per connettersi ai AEM Screens. Questo è particolarmente interessante per le impostazioni effimere o mobili.

Il diagramma seguente mostra la configurazione Mobile Network con Mobile Data Router e Active Network Components e contiene l&#39;accesso a Internet di uno dei controller di AEM Screens tramite l&#39;accesso diretto a Internet tramite un proprio Data Link 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Collegamento del lettore AEM Screens alla rete mobile con il router dati mobile e i componenti di rete attivi {#connecting-aem-screens-players}

Segui i passaggi indicati di seguito per garantire la corretta connessione dei lettori dello schermo AEM in questa configurazione:

La configurazione alloca un Accesso Internet per ogni Controller AEM Screens tramite accesso Internet diretto utilizzando un Collegamento dati dedicato di 3/4/5G.

1. Assicurati che Mobile Data Router sia correttamente collegato alla rete dati cellulare come indicato nel sistema operativo e che ciascuno dei lettori dello schermo AEM sia collegato alla rete Routers.
1. Verificate la connessione Internet chiamando un URL nel browser del sistema.
   >[!NOTE]
   >Nel caso in cui si riceva un errore, controllare le impostazioni di rete. Esistono sostanzialmente due opzioni per una connessione di rete adeguata:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurarsi che l&#39;impostazione della scheda di rete corrisponda all&#39;impostazione del router.

1. Verificare che il router sia collegato correttamente alla rete Internet Wide Area Network (Internet Link). Questo può essere identificato anche utilizzando un LED di segnale su router standard.
1. Se la chiamata URL ha esito positivo, potete continuare a installare gli AEM Screens e registrarvi. AEM Screens iniziali.

   >[!NOTE]
   >**Suggerimenti per la risoluzione dei problemi**
   >Se i AEM Screens non si connettono correttamente e il contenuto previsto non viene visualizzato:
   >
   >1. Se sono presenti restrizioni, controllate il firewall Internet Router `TCP/IP Port 80/443`.



## Configurazione di Mobile Network con Mobile Data Router e componenti di rete attivi {#requirements-direct}

La configurazione della rete può essere logicamente separata in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità di rete già descritta, devono fornire una larghezza di banda sufficiente per eseguire in modo fluido i download dei contenuti AEM Screens.

*Sufficiente* dipende dalla quantità di schermi AEM connessi dispositivi e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi per gli ospiti.
Tenere presente che tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda è generalmente in diminuzione lineare, mentre l&#39;aggiunta di più consumatori/computer alla rete.
Oltre alla specifica connessione teorica di rete, occorre garantire che la copertura del router mobile sia almeno &quot;buona&quot;. Inoltre, il piano mensile sottostante deve coprire una capacità dati sufficiente e una larghezza di banda sufficiente per servire tutti i client connessi all&#39;interno della LAN collegata.

Nella tabella seguente sono evidenziate le reti di dati con larghezza di banda standard:

| Rete dati | Larghezza di banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Mentre considera quale rete dati utilizzare, si consiglia di rispondere alle seguenti domande:

* Quanti client sono collegati al router?

* Quante modifiche ai contenuti sono previste e quali sono tali dimensioni medie dei file?

>[!NOTE]
>
>Il pacchetto dati necessario deve essere almeno:
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Per il caricamento iniziale dei file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una maggiore quantità di dati e un maggiore tempo di scaricamento, che si riflette nelle ipotesi sopra riportate. Una rete 4G con una *buona* copertura e dati illimitati deve corrispondere alle installazioni più comuni di questa configurazione di rete.


### Rete locale {#lan-connection}

Le prestazioni della LAN, oltre alla raggiungibilità di rete già descritta, devono fornire una larghezza di banda sufficiente per consentire il corretto funzionamento dei download dei contenuti AEM Screens. In questi giorni la rete LAN corrisponde almeno a una rete a 100 Mbps, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Quando si utilizza un altro componente di rete attivo, è obbligatorio che tutti questi componenti corrispondano ai requisiti di larghezza di banda della rete.

Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalla specifica Internet Access/Router.

Nel caso in cui sia prevista una soluzione Wi-Fi per il collegamento dello schermo a Internet Link, si consiglia di utilizzare almeno standard Wi-Fi moderni come IEEE 802.11g. Questo standard supporta connessioni fino a 54 Mbps. Tutti gli standard *più recenti* come 802.11h-n sono di qualità migliore. Se è necessario un ripetitore Wi-Fi, consigliamo vivamente le tecnologie Mesh Wi-Fi Access-Point come Google Nest Mesh Wi-Fi o simili.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. Consente di scaricare e salvare localmente tutti i file multimediali necessari, ad esempio immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio con una playlist definita che non viene aggiornata frequentemente durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta che tutti i file sono stati salvati sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.
Le tabelle che seguono offrono una buona panoramica dei dati chiave di connettività di rete per le prestazioni che si possono prevedere e i potenziali tempi di attesa.

>[!NOTE]
>
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/mobile-router-download.png)



