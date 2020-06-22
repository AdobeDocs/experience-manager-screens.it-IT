---
title: Configurazione della rete mobile
description: La pagina descrive Mobile Network Setup
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# Impostazioni di rete mobile {#mobile-network-setup}

I lettori di AEM Screens Adobe possono anche essere connessi utilizzando Mobile/Cellular Networks con almeno una rete 3G.
All&#39;interno dei AEM Screens, il contenuto necessario viene fisicamente scaricato nel controller/computer del lettore e archiviato correttamente all&#39;interno del sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali e non influenza affatto le prestazioni dei sistemi di visualizzazione.
Connessione dei lettori AEM Screens con Cellulare 3/4/5G ai provider di dati di Mobile Service. Il vantaggio di questa configurazione è che il router per dispositivi mobili può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è solitamente in posizione elevata e aperta con il meno possibile costruzione di cemento o metallo circostante.
Questa configurazione consente agli utenti dello schermo AEM una grande flessibilità, in quanto non è necessaria una linea fissa per connettere AEM Screens.


## Requisiti per la configurazione della rete di accesso diretto {#requirements-direct}

La configurazione della rete come descritto in 5.5 può essere separata in tre blocchi. Il WAN/Outer World/Internet Connection Block (qui mobile Data Connection), la LAN/Local Area Network interna e le sottosezioni opzionali della LAN separate da Active Network Components.
Per ottenere le migliori prestazioni è necessario garantire che entrambe le sezioni siano conformi agli standard minimi raccomandati.
Cosa significa &quot;buone prestazioni&quot; nell&#39;ambiente AEM Screens?
I AEM Screens offrono un grande vantaggio agli utenti del digital signage. È in corso il download e il salvataggio locale di tutti i file multimediali necessari, ad esempio immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio, avendo definito una playlist che non viene modificata molto spesso durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.
Le tabelle che seguono offrono una buona panoramica dei dati chiave di connettività di rete per le prestazioni che si possono prevedere e i potenziali tempi di attesa.
Tutte le informazioni devono essere viste come il consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ognuna di queste richieste comporta l&#39;aggiunta e l&#39;estensione del tempo di download.


### WAN / Connessione Internet {#wan-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete già descritta, devono fornire una larghezza di banda sufficiente per utilizzare AEM Screens in modo ordinato e ordinato. In dettaglio, &quot;sufficiente&quot; dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi per gli ospiti.
Tenere presente che tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce in modo lineare, aggiungendo alla rete più utenti/computer.
Oltre alla specifica connessione teorica di rete, è necessario garantire che la copertura del router mobile sia almeno &quot;buona&quot; (fare riferimento al manuale del router mobile). Inoltre, il piano mensile sottostante deve coprire una capacità dati sufficiente e una larghezza di banda sufficiente per servire tutti i client connessi all&#39;interno della LAN collegata.
Le reti dati forniscono una larghezza di banda standard con circa fino a:
・ 3 Go 42 Mbit/sec ・ 4 Go 150 Mbit/sec ・ 5Go 1000 Mbit/sec-10000 Mbit/secMentre si considera quale rete dati debba essere utilizzata, si consiglia di rispondere alle seguenti domande:
・ Quanti clienti sono collegati al Router?
・ Quante modifiche apportate ai contenuti si possono attendere e quali sono le dimensioni medie dei file?
Come follow-up il pacchetto dati necessario deve essere almeno:
Capacità pacchetto dati = # dei client * (# di file di contenuto * dimensione file media) Assicurarsi che il buffer sia sufficiente.
Attenzione: Per il caricamento iniziale dei file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una maggiore quantità di dati e un maggiore tempo di scaricamento, che si rifletta nelle ipotesi di cui sopra.
Come regola di pollice, una rete 4G con una copertura &quot;buona&quot; e dati illimitati dovrebbe corrispondere alle installazioni più comuni in questa configurazione di rete


### Connessione LAN {#lan-connection}

Le prestazioni della LAN, oltre alla raggiungibilità della rete già descritta, garantiscono una larghezza di banda sufficiente per il funzionamento dei AEM Screens in modo ordinato e ordinato. In questi giorni la rete LAN corrisponde almeno a una rete da 100 MBit/sec, in modo che ci dovrebbe essere larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Se si utilizza un altro componente di rete attivo, è necessario che tutti questi componenti soddisfino i requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbit/s e alla larghezza di banda fornita dalla specifica Internet Access/Router.
Nel caso in cui sia prevista una soluzione WiFI per il collegamento dello schermo a Internet Link, si consiglia di utilizzare come minimo standard WIFI moderni come IEEE 802.11g. Questo standard supporta connessioni fino a 54 Mbit. Tutti gli standard più recenti, come 802.11h-n, sono di qualità migliore. Se è richiesto un Ripetitore Wifi consigliamo vivamente Mesh Wifi tecnologie punto di accesso come Google Nest Mesh Wifi o simili.
Altre tecnologie ripetute WiFi finiscono con una massiccia perdita di larghezza di banda nella rete.
