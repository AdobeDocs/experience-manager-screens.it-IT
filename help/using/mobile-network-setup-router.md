---
title: Rete mobile con Mobile Data Router e Componenti di rete attivi
description: La pagina descrive Mobile Network con Mobile Data Router e Active Network Components
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---


# Rete mobile con Mobile Data Router e Componenti di rete attivi {#mobile-network-setup}

I lettori di AEM Screens Adobe possono anche essere connessi utilizzando Mobile/Cellular Networks con almeno una rete 3G.
All&#39;interno dei AEM Screens, il contenuto necessario viene fisicamente scaricato nel controller/computer del lettore e archiviato correttamente all&#39;interno del sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali e non influenza affatto le prestazioni dei sistemi di visualizzazione.
Connessione dei lettori AEM Screens con Cellulare 3/4/5G ai provider di dati di Mobile Service. Il vantaggio di questa configurazione è che il router per dispositivi mobili può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è solitamente in posizione elevata e aperta con il meno possibile costruzione di cemento o metallo circostante.
Questa configurazione consente agli utenti dello schermo AEM una grande flessibilità, in quanto non è necessaria una linea fissa per connettere AEM Screens.

![](/help/using/assets/mobile-network-1.png)

## Collegamento del lettore AEM Screens alla rete mobile con il router dati mobile e i componenti di rete attivi {#connecting-aem-screens-players}

Segui i passaggi indicati di seguito per collegare i lettori di schermo AEM in questa configurazione:

La configurazione contiene l&#39;accesso a Internet di uno qualsiasi dei controller AEM Screens tramite accesso diretto a Internet tramite un proprio collegamento dati 3/4/5G.
La connessione corretta dei lettori dello schermo AEM in questa configurazione è semplice:

1. Assicurarsi che Mobile Data Router sia correttamente collegato alla rete dati cellulare come indicato nel sistema operativo.
1. Verificate che ciascuno dei lettori dello schermo AEM sia collegato alla rete Routers
1. Verificate la connessione Internet chiamando un URL nel browser del sistema.
   >[!NOTE]
   >Nel caso in cui venga visualizzato un messaggio di errore, controllare le impostazioni di rete. Esistono sostanzialmente due opzioni per una connessione di rete adeguata:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurarsi che l&#39;impostazione della scheda di rete corrisponda all&#39;impostazione del router.
1. Verificare che il router sia collegato correttamente alla rete Internet Wide Area Network (Internet Link). In genere può essere identificato anche utilizzando un LED di segnale su router standard. Se non sembra corretto, contattate il servizio ISP per controllare il router da remoto.
IV. Se tutte le impostazioni sopra riportate sono configurate correttamente e viene ancora visualizzato un messaggio di errore, controllate i componenti di rete attivi come Switch o router aggiuntivi, in caso siano presenti restrizioni della porta.
1. Se la chiamata URL ha avuto esito positivo, potete continuare a installare gli AEM Screens e registrarli di conseguenza. AEM Screens iniziali

   >[!NOTE]
   >**Suggerimenti per la risoluzione dei problemi**
   >Se i AEM Screens non si connettono correttamente e non mostrano il contenuto previsto:
   >
   >1. Se sono presenti restrizioni, controllate il firewall Internet Router `TCP/IP Port 80/443`.
   >1. Accertatevi che tutte le porte necessarie siano consentite.



## Requisiti per la configurazione di Mobile Network con Mobile Data Router e componenti di rete attivi {#requirements-direct}

La configurazione della rete può essere logicamente separata in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete già descritta, devono fornire una larghezza di banda sufficiente per utilizzare AEM Screens in modo ordinato e ordinato. In dettaglio, &quot;sufficiente&quot; dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti WiFi per gli ospiti.
Tenere presente che tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda è generalmente in diminuzione lineare, mentre l&#39;aggiunta di più consumatori/computer alla rete.
Oltre alla specifica connessione teorica di rete, è necessario garantire che la copertura del router mobile sia almeno &quot;buona&quot; (fare riferimento al manuale del router mobile). Inoltre, il piano mensile sottostante deve coprire una capacità dati sufficiente e una larghezza di banda sufficiente per servire tutti i client connessi all&#39;interno della LAN collegata.
Le reti dati forniscono una larghezza di banda standard con:

**3G**
* 42 Mbps

**4G**
* 150 Mbps

**5G**
* 1000 Mbps-10000 Mbps

Mentre considera quale rete dati utilizzare, si consiglia di rispondere alle seguenti domande:

* Quanti client sono collegati al router?

* Quante modifiche ai contenuti sono previste e quali sono tali dimensioni medie dei file?

>[!NOTE]
>Il pacchetto dati necessario deve essere almeno:
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Per il caricamento iniziale dei file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una maggiore quantità di dati e un maggiore tempo di scaricamento, che si riflette nelle ipotesi sopra riportate. Una rete 4G con una *buona* copertura e dati illimitati deve corrispondere alle installazioni più comuni di questa configurazione di rete.


### Rete locale {#lan-connection}

Le prestazioni della LAN, oltre alla raggiungibilità della rete già descritta, garantiscono una larghezza di banda sufficiente per il funzionamento dei AEM Screens in modo ordinato e ordinato. In questi giorni la rete LAN corrisponde almeno a una rete a 100 Mbps, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Se si utilizza un altro componente di rete attivo, è necessario che tutti questi componenti soddisfino i requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalla specifica Internet Access/Router.
Nel caso in cui sia prevista una soluzione WiFI per il collegamento dello schermo a Internet Link, si consiglia di utilizzare come minimo standard WIFI moderni come IEEE 802.11g. Questo standard supporta connessioni fino a 54 Mbps. Tutti gli standard più recenti, come 802.11h-n, sono di qualità migliore. Se è richiesto un Ripetitore WIFI, consigliamo vivamente le tecnologie Mesh Wifi Access-point come Google Nest Mesh WIFI o simili.
Altre tecnologie ripetute WiFi finiscono con una massiccia perdita di larghezza di banda nella rete.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. È in corso il download e il salvataggio locale di tutti i file multimediali necessari, ad esempio immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio, avendo definito una playlist che non viene modificata molto spesso durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.
Le tabelle che seguono offrono una buona panoramica dei dati chiave di connettività di rete per le prestazioni che si possono prevedere e i potenziali tempi di attesa.

>[!NOTE]
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/mobile-router-download.png)


