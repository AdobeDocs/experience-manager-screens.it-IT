---
title: Rete aziendale chiusa
description: Rete aziendale chiusa
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Rete aziendale chiusa (cablata/wireless) {#enclosed-corporate-networks}

La configurazione della rete aziendale è applicabile alle aziende più piccole, grandi e piccole. Può essere teoricamente più complesso, e la configurazione logica è mostrata nella figura seguente.

![](/help/using/assets/enclosed-network-1.png)


## Connessione  AEM Screens Player a Direct Internet Access {#connecting-aem-screens-players}

Seguire i passaggi indicati di seguito per garantire la corretta connessione dei lettori AEM dello schermo in questa configurazione:

1. Assicurarsi che ciascuno dei lettori AEM dello schermo sia collegato alla rete Routers.
1. Verificate la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Nel caso in cui si riceva un errore, controllare le impostazioni di rete. Esistono sostanzialmente due opzioni per una connessione di rete adeguata:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurarsi che l&#39;impostazione della scheda di rete corrisponda alle impostazioni del router e verificare che la quantità massima di indirizzi IP disponibili nella rete non sia raggiunta.

1. Verificare che il router sia connesso correttamente alla rete Internet Wide Area Network (Internet Link). Questo può essere identificato anche utilizzando un LED di segnale su router standard.
1. Se la chiamata URL ha esito positivo, potete continuare a installare l’AEM Screens  e registrarvi. Avviate  AEM Screens.

   >[!NOTE]
   >**Suggerimenti per la risoluzione dei problemi**
   >Se  AEM Screens non si collega correttamente e il contenuto previsto non viene visualizzato:
   >
   >1. Se sono presenti restrizioni relative a `TCP/IP Port 80/443`, controllate il firewall di Internet Router.
   >1. Accertatevi che tutte le porte necessarie siano consentite.


## Impostazione di reti aziendali chiuse {#requirements-enclosed-networks}

La configurazione della rete aziendale chiusa può essere logicamente separata in due blocchi:

* Wide Area Network (WAN)
* LAN (Local Area Network).

### Rete {#wan-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete, devono fornire una larghezza di banda sufficiente per funzionare  gli aggiornamenti dei contenuti AEM Screens senza problemi.
*Una larghezza di* banda sufficiente dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi guest.

>[!NOTE]
>
>Tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce in modo lineare quando si aggiungono più utenti o computer alla rete.

### Rete locale {#lan-connection}

Le prestazioni della LAN (Local Area Network), oltre alla raggiungibilità della rete, devono fornire una larghezza di banda sufficiente per operare  gli aggiornamenti dei contenuti AEM Screens senza problemi.

La rete LAN all&#39;interno delle organizzazioni aziendali è generalmente di almeno 1000 MBit/sec di rete, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema. L&#39;utilizzo di altri componenti di rete attivi richiede che tutti questi componenti soddisfino i requisiti di larghezza di banda della rete.

Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalla specifica di accesso a Internet/router.

### Altre specifiche di rete aziendale {#other-networks}

Le reti aziendali dispongono di una serie di dispositivi collegati, sono separati in varie sottorete reti e dispongono di connessioni Internet ridondanti o multiplex per fornire prestazioni sufficienti per molte migliaia di accessi simultanei.
Questo schema è semplificato e si adatta alla maggior parte dei casi agli ambienti disponibili per il client.

Nel caso in cui sia prevista una soluzione Wi-Fi per collegare le schermate a Internet Link, si consiglia di utilizzare come minimo standard Wi-Fi moderni come `IEEE 802.11g`. Questo Standard supporta connessioni fino a 54 Mbps. Tutti gli standard *più recenti* come `802.11h-n` sono di qualità migliore. Se è necessario un ripetitore Wi-Fi, consigliamo vivamente le tecnologie Mesh Wi-Fi punto di accesso come Google Nest Mesh Wi-Fi o simili.
Altre tecnologie ripetute Wi-Fi finiscono con una massiccia perdita di larghezza di banda nella rete.

## Download di file multimediali e risorse {#download}

 AEM Screens offre un grande vantaggio agli utenti del digital signage. Consente di scaricare e salvare localmente tutti i file multimediali necessari, come immagini e video. Il traffico di rete principale si verifica in presenza di nuovo contenuto da visualizzare su un display specifico.

Per le normali operazioni, ad esempio, una playlist definita che si aggiorna frequentemente durante il giorno, offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore.

Per gli scenari in cui ci sono più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza del cliente.

La tabella seguente fornisce una panoramica sui dati chiave della connettività di rete.

>[!NOTE]
>Le informazioni consentono di visualizzare l&#39;uso di ciascun dispositivo nella rete che richiede e scarica un&#39;origine Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/enclosed-network-download.png)
