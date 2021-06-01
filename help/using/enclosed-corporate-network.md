---
title: Rete aziendale chiusa
description: Rete aziendale chiusa
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Rete aziendale chiusa (cablata/wireless) {#enclosed-corporate-networks}

La configurazione Enclosed Corporate Network è applicabile alle aziende più piccole, di grandi dimensioni e di grandi dimensioni. Può essere teoricamente più complesso, e la configurazione logica è mostrata nella figura seguente.

![](/help/using/assets/enclosed-network-1.png)


## Connessione di AEM Screens Player all&#39;accesso diretto a Internet {#connecting-aem-screens-players}

Segui i passaggi riportati di seguito per garantire la connessione corretta dei lettori AEM dello schermo in questa configurazione:

1. Assicurati che ciascuno dei lettori AEM schermo sia collegato alla rete router.
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


## Configurazione delle reti aziendali chiuse {#requirements-enclosed-networks}

La configurazione della rete aziendale chiusa può essere logicamente separata in due blocchi:

* Wide Area Network (WAN)
* LAN (Local Area Network) interna.

### Rete ampia {#wan-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete, devono fornire una larghezza di banda sufficiente per gestire gli aggiornamenti dei contenuti AEM Screens senza problemi.
*Una larghezza di* banda sufficiente dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi guest.

>[!NOTE]
>
>Tutti i dispositivi hanno un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce linearmente quando si aggiungono più consumatori o computer alla rete.

### Rete locale {#lan-connection}

Le prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, devono fornire una larghezza di banda sufficiente per gestire gli aggiornamenti dei contenuti AEM Screens senza problemi.

La rete LAN all&#39;interno delle organizzazioni aziendali è solitamente di almeno 1000 MBit/sec di rete, in modo che vi sia una larghezza di banda sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti corrispondano ai requisiti di larghezza di banda della rete.

Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalle specifiche di accesso a Internet/router.

### Altre reti aziendali specifiche {#other-networks}

Le reti aziendali dispongono di una serie di dispositivi collegati, sono separate in varie sottorete e dispongono di connessioni Internet ridondanti o multiplex per fornire prestazioni sufficienti per molte migliaia di accessi simultanei.
Questo schema è semplificato e si adatta alla maggior parte dei casi agli ambienti disponibili per il client.

Nel caso in cui sia prevista una soluzione Wi-Fi per collegare Screens a Internet Link, si consiglia di utilizzare almeno standard Wi-Fi moderni come `IEEE 802.11g`. Questo Standard supporta connessioni fino a 54 Mbps. Tutti gli standard *più recenti* come `802.11h-n` sono di migliore qualità. Se è richiesto un ripetitore Wi-Fi, consigliamo vivamente le tecnologie Mesh Wi-Fi per punti di accesso come la rete Wi-Fi di Google Nest o simili.
Altre tecnologie ripetute Wi-Fi finiscono in una perdita massiccia di larghezza di banda nella rete complessiva.

## Download di file multimediali e risorse {#download}

AEM Screens offre un grande vantaggio agli utenti del digital signage. Scarica e salva localmente tutti i file multimediali necessari, come immagini e video. Il traffico di rete principale si verifica quando su una visualizzazione specifica è presente un nuovo contenuto da visualizzare.

Per le operazioni normali, ad esempio, una playlist definita che si aggiorna frequentemente durante il giorno, offre un funzionamento simile a quello della rete, una volta salvati tutti i file sul lettore.

Per gli scenari in cui vi sono più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza del cliente possibile.

La tabella seguente fornisce una panoramica dei dati chiave della connettività di rete.

>[!NOTE]
>Le informazioni consentono di visualizzare il consumo di ogni dispositivo della rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/using/assets/enclosed-network-download.png)
