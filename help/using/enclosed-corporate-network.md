---
title: Rete aziendale chiusa
description: Rete aziendale chiusa
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---

# Rete aziendale chiusa (cablata/wireless) {#enclosed-corporate-networks}

L&#39;Enclosed Corporate Network SetUp è applicabile alle aziende di piccole, grandi e grandi dimensioni. Può essere teoricamente più complesso, e l&#39;impostazione logica è mostrata nella figura seguente.

![](/help/using/assets/enclosed-network-1.png)


## Connessione di AEM Screens Player all&#39;accesso diretto a Internet

Segui i passaggi seguenti per garantire la corretta connessione dei lettori AEM Screen in questa configurazione:

1. Assicurarsi che ogni lettore AEM Screen sia collegato alla rete dei router.
1. Verificare la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >In caso di errore, controllare le impostazioni di rete. Esistono fondamentalmente due opzioni per una connessione di rete corretta:
   >* DHCP
   >* Configurazione IP manuale

1. Verificare che l&#39;impostazione della scheda di rete corrisponda alle impostazioni del router e verificare che non sia stato raggiunto il numero massimo di indirizzi IP disponibili nella rete.

1. Verificare che il router sia connesso correttamente all&#39;ISP Wide Area Network (collegamento Internet). Questa connessione può anche essere identificata utilizzando un LED di segnale sui router standard.
1. Se la chiamata URL ha esito positivo, puoi continuare a installare AEM Screens e registrarti. Avvia AEM Screens.

   >[!NOTE]
   >**Suggerimento per la risoluzione dei problemi**
   >Se AEM Screens non si connette correttamente e il contenuto previsto non viene visualizzato:
   >
   >1. Se sono presenti restrizioni relative a, controlla nel firewall del router Internet `TCP/IP Port 80/443`.
   >1. Verificare che tutte le porte richieste siano consentite.

## Configurazione di reti aziendali chiuse {#requirements-enclosed-networks}

L&#39;installazione di Enclosed Corporate Network può essere separata logicamente in due blocchi:

* WAN (Wide Area Network)
* LAN interna.

### Wide Area Network {#wan-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete, devono fornire una larghezza di banda sufficiente per consentire un agevole aggiornamento dei contenuti AEM Screens.
*Larghezza di banda sufficiente* dipende dal numero di AEM Screens connesse. Dipende anche dall&#39;uso di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi guest.

>[!NOTE]
>
>Tutti i dispositivi hanno accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce linearmente quando si aggiungono più utenti o computer alla rete.

### Local Area Network {#lan-connection}

Le prestazioni della rete LAN (Local Area Network), oltre alla raggiungibilità della rete, devono fornire una larghezza di banda sufficiente per gestire senza problemi gli aggiornamenti dei contenuti AEM Screens.

La rete LAN all&#39;interno delle organizzazioni aziendali è in genere di almeno 1000 MBit/sec, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Quando si utilizzano altri componenti di rete attivi, è obbligatorio che tutti i componenti corrispondano ai requisiti di larghezza di banda della rete.

Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalle specifiche di accesso a Internet e router.

### Altre reti aziendali specifiche {#other-networks}

Le reti aziendali hanno diversi dispositivi connessi, sono separate in varie sottoreti e dispongono di connessioni Internet ridondanti o multiplexate per fornire prestazioni sufficienti per molte migliaia di accessi simultanei.
Questo schema è semplificato e si adatta nella maggior parte dei casi agli ambienti disponibili per il client.

Nel caso in cui sia prevista una soluzione Wi-Fi per collegare AEM Screens al collegamento Internet, si consiglia di utilizzare standard Wi-Fi moderni come `IEEE 802.11g` come minimo. Questo standard supporta connessioni fino a 54 Mbps. Qualsiasi *più recente* Standard come `802.11h-n` sono di migliore qualità. Se è necessario un ripetitore Wi-Fi, Adobe consiglia tecnologie per punti di accesso Wi-Fi Mesh come Google Nest Mesh Wi-Fi o simili.
Altre tecnologie di ripetizione Wi-Fi finiscono in una massiccia perdita di larghezza di banda nella rete globale.

## Download di contenuti multimediali e risorse {#download}

AEM Screens offre un vantaggio significativo agli utenti di digital signage. Scarica e salva localmente tutti i file multimediali necessari, ad esempio immagini e video. Il traffico di rete principale si verifica quando è presente un nuovo contenuto da visualizzare su una visualizzazione specifica.

Per le normali operazioni, ad esempio una playlist definita che si aggiorna frequentemente durante il giorno - offre un funzionamento simile a quello della rete, dopo che tutti i file sono stati salvati sul lettore.

Negli scenari in cui sono presenti più interazioni con sensori o attivatori e contenuti dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata allo schermo al fine di garantire la migliore esperienza possibile per il cliente.

Nella tabella seguente viene fornita una panoramica sui dati chiave della connettività di rete.

>[!NOTE]
>Le informazioni consentono di visualizzare il consumo di ogni dispositivo nella rete richiedendo e scaricando un&#39;origine Internet. Ognuna di queste richieste aggiunge ed estende il Tempo di download.

![](/help/using/assets/enclosed-network-download.png)
