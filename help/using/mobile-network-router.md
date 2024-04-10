---
title: Rete mobile con router dati mobile e componenti di rete attivi
description: La pagina descrive la rete mobile con router dati mobile e componenti di rete attivi
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 0%

---

# Rete mobile con router dati mobile e componenti di rete attivi {#mobile-network-setup}

Adobe I lettori AEM Screens possono anche essere collegati utilizzando reti mobili o cellulari che eseguono almeno una rete 3G.

All’interno di AEM Screens, il contenuto richiesto viene fisicamente scaricato sul controller o sul computer del lettore e memorizzato correttamente all’interno del sistema operativo sottostante. Pertanto, la larghezza di banda specificata influisce solo sui tempi di download iniziali e sugli aggiornamenti dei contenuti, e non influenza le prestazioni della riproduzione regolare dei display.

Il vantaggio di questa configurazione è che il router mobile può essere posizionato in un punto ottimizzato per garantire la migliore copertura di rete disponibile. Questo è di solito in una posizione elevata e aperta, con il minor numero possibile di strutture circostanti in calcestruzzo o metallo.
Questa configurazione offre agli utenti di Schermo AEM flessibilità perché non è richiesta alcuna linea fissa per connettersi ad AEM Screens. Questo è interessante per le configurazioni effimere o mobili.

Il diagramma seguente mostra la configurazione di Mobile Network with Mobile Data Router and Active Network Components (Rete mobile con router dati mobile e componenti di rete attivi). Contiene l’accesso a Internet di qualsiasi controller AEM Screens tramite accesso diretto a Internet tramite un proprio collegamento dati 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Collegamento di AEM Screens Player a una rete mobile con il router dati mobile e i componenti di rete attivi {#connecting-aem-screens-players}

Segui i passaggi seguenti per garantire la corretta connessione dei lettori AEM Screen in questa configurazione:

La configurazione alloca un accesso a Internet per ogni controller AEM Screens mediante un accesso diretto a Internet mediante un collegamento dati dedicato 3/4/5G.

1. Accertarsi che il router dati mobile sia collegato correttamente alla rete dati cellulare come indicato nel sistema operativo e che ciascuno dei lettori AEM Screen sia collegato alla rete dei router.
1. Verificare la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >In caso di errore, controllare le impostazioni di rete. Esistono fondamentalmente due opzioni per una connessione di rete corretta:
   >* DHCP
   >* Configurazione IP manuale

1. Verificare che l&#39;impostazione della scheda di rete corrisponda all&#39;impostazione del router.

1. Verificare che il router sia connesso correttamente alla rete WAN (Internet Link) del provider di servizi Internet. Questo può anche essere identificato utilizzando un LED di segnale sui router standard.
1. Se la chiamata URL ha esito positivo, puoi continuare a installare AEM Screens e registrarti. Avvia AEM Screens.

   >[!NOTE]
   >**Suggerimento per la risoluzione dei problemi**
   >Se AEM Screens non si connette correttamente e il contenuto previsto non viene visualizzato, controlla nel firewall del router Internet se sono presenti restrizioni relative a `TCP/IP Port 80/443`.


## Configurazione di una rete mobile con router dati mobile e componenti di rete attivi {#requirements-direct}

L&#39;installazione di rete può essere separata logicamente in due blocchi:

* Connessione Internet mobile

* Local Area Network

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet, oltre alla già descritta raggiungibilità di rete, devono fornire una larghezza di banda sufficiente per eseguire i download dei contenuti AEM Screens in modo fluido.

*Sufficiente* dipende dal numero di dispositivi AEM Screens connessi e dall&#39;utilizzo di altri utenti all&#39;interno della rete, come Smartphone, Tablet, Cassiere, Computer o reti Wi-Fi guest.
Tenere presente che tutti i dispositivi hanno un accesso simultaneo alla connessione Internet e che la larghezza di banda diminuisce in modo lineare, aggiungendo più consumatori/computer alla rete.
Oltre alla specifica connessione di rete teorica, è necessario garantire che la copertura del router mobile sia almeno &quot;buona&quot;. Inoltre, il piano mensile sottostante deve coprire una capacità di dati sufficiente e una larghezza di banda sufficiente per tutti i client connessi all&#39;interno della LAN connessa.

Nella tabella seguente vengono evidenziate le reti di dati con la larghezza di banda standard:

| Rete dati | Larghezza di banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Quando consideri quale rete dati utilizzare, l’Adobe consiglia di rispondere alle seguenti domande:

* Quanti client sono connessi al router?
* Quante modifiche al contenuto sono previste e quali sono le dimensioni medie dei file?

>[!NOTE]
>
>Il pacchetto dati necessario deve essere almeno:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Per il caricamento iniziale dei file multimediali, ad esempio, durante l’integrazione di nuovi lettori, è necessario prevedere una maggiore quantità di dati e un tempo di download maggiore, ipotesi che si riflettono in precedenza. Una rete 4G con *buono* copertura e dati illimitati devono corrispondere alle installazioni più comuni di questa configurazione di rete.


### Local Area Network {#lan-connection}

Le prestazioni della LAN, oltre alla già descritta raggiungibilità di rete, devono fornire una larghezza di banda sufficiente per consentire il corretto download dei contenuti AEM Screens. In questi giorni, la rete LAN di solito corrisponde almeno a una rete a 100 Mbps, quindi dovrebbe essere disponibile una larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti i componenti corrispondano ai requisiti di larghezza di banda della rete.

Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalle specifiche di accesso a Internet/router.

Nel caso in cui sia prevista una soluzione Wi-Fi per collegare lo schermo al collegamento Internet, si consiglia di utilizzare standard Wi-Fi moderni come IEEE `802.11g` come minimo. Questo standard supporta connessioni fino a 54 Mbps. Qualsiasi *più recente* Standard come `802.11h-n` sono di migliore qualità. Se è necessario un ripetitore Wi-Fi, l&#39;Adobe consiglia tecnologie per punti di accesso Wi-Fi Mesh come Google Nest Mesh Wi-Fi o simili.

## Download di contenuti multimediali e risorse {#download}

AEM Screens offre un vantaggio significativo agli utenti di digital signage. Scarica e salva localmente tutti i file multimediali necessari, ad esempio immagini e video. In base a questo concetto, il traffico di rete principale si verifica nel caso in cui vi siano nuovi contenuti da visualizzare su uno schermo specifico.
Per il normale funzionamento, ad esempio, avendo definito una playlist che non viene aggiornata frequentemente durante il giorno, questo offre un funzionamento quasi indipendente dalla rete quando tutti i file vengono salvati sul lettore.
Per i casi d’uso in cui sono presenti più interazioni con Sensor o altri Triggers e il contenuto è dinamico, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo al fine di garantire la migliore esperienza del cliente possibile.
Le tabelle seguenti offrono una panoramica completa del significato dei dati chiave della connettività di rete per le prestazioni previste e i potenziali tempi di attesa.

>[!NOTE]
>
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una sorgente Internet. Ognuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/using/assets/mobile-router-download.png)
