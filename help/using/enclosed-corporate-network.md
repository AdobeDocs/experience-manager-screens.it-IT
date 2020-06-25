---
title: Rete aziendale chiusa
description: Rete aziendale chiusa
translation-type: tm+mt
source-git-commit: ed683a86b7e8c6ec06309577bd0a8690a9cc4684
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# Reti aziendali chiuse (cablate/wireless) {#enclosed-corporate-networks}

La configurazione della rete aziendale chiusa è applicabile alle aziende più piccole, grandi e piccole. Può essere teoricamente più complesso, ma la configurazione logica è illustrata nella figura seguente.

![](/help/using/assets/enclosed-network-1.png)


## Collegamento del lettore AEM Screens a Direct Internet Access {#connecting-aem-screens-players}

Segui i passaggi indicati di seguito per garantire la corretta connessione dei lettori dello schermo AEM in questa configurazione:

1. Accertatevi che ciascuno dei lettori dello schermo AEM sia collegato alla rete Routers.
1. Verificate la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Nel caso in cui si riceva un errore, controllare le impostazioni di rete. Esistono sostanzialmente due opzioni per una connessione di rete adeguata:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurarsi che l&#39;impostazione della scheda di rete corrisponda alle impostazioni del router e verificare che la quantità massima di indirizzi IP disponibili nella rete non sia raggiunta.

1. Verificare che il router sia connesso correttamente alla rete Internet Wide Area Network (Internet Link). Questo può essere identificato anche utilizzando un LED di segnale su router standard.
1. Se la chiamata URL ha esito positivo, potete continuare a installare gli AEM Screens e registrarvi. AEM Screens iniziali.

   >[!NOTE]
   >**Suggerimenti per la risoluzione dei problemi**
   >Se i AEM Screens non si connettono correttamente e il contenuto previsto non viene visualizzato:
   >
   >1. Se sono presenti restrizioni, controllate il firewall Internet Router `TCP/IP Port 80/443`.
   >1. Accertatevi che tutte le porte necessarie siano consentite.


## Requisiti per l&#39;impostazione di reti aziendali chiuse {#requirements-enclosed-networks}

La configurazione della rete aziendale chiusa può essere logicamente separata in due blocchi:

* Wide Area Network (WAN)
* LAN (Local Area Network).

### Ampia rete di reti {#wan-connection}

Le prestazioni della connessione Internet oltre alla raggiungibilità della rete, è di fornire una larghezza di banda sufficiente per operare AEM Screens in modo ordinato e ordinato.
*Una larghezza di banda* sufficiente dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri utenti della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi per gli ospiti.

>[!NOTE]
>Tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda, in genere, diminuisce in modo lineare quando si aggiungono più utenti o computer alla rete.

### Rete locale {#lan-connection}

Le prestazioni della rete LAN (Local Area Network), oltre alla raggiungibilità della rete, consentono di disporre di una larghezza di banda sufficiente a garantire un funzionamento ottimale dei AEM Screens.

In questi giorni la rete LAN all&#39;interno delle organizzazioni aziendali corrisponde almeno a una rete da 1000 MBit/sec, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Durante l&#39;utilizzo di altri componenti di rete attivi, è obbligatorio che tutti questi componenti corrispondano ai requisiti di larghezza di banda della rete.

Ad esempio, i componenti di rete devono corrispondere almeno allo standard 1000 Mbps e alla larghezza di banda fornita dalla specifica Internet Access/Router.

### Altre reti aziendali specifiche {#other-networks}

Solitamente le reti aziendali dispongono di un carico di dispositivi collegati, potrebbero essere separati in varie sottoreti e potrebbero disporre di connessioni Internet ridondanti o multiplex per fornire prestazioni sufficienti per molte migliaia di accessi simultanei.
Questo schema è semplificato e si adatta nella maggior parte dei casi all&#39;ambiente disponibile per il client.

Nel caso in cui sia prevista una soluzione Wi-Fi per collegare lo schermo a Internet Link, si consiglia di utilizzare standard Wi-Fi moderni come `IEEE 802.11g` minimo. Questo standard supporta connessioni fino a 54 Mbps. Tutti gli standard *più recenti* come `802.11h-n` sono di migliore qualità. Se è necessario un ripetitore Wi-Fi, consigliamo vivamente le tecnologie Mesh Wi-Fi Access-Point come Google Nest Mesh Wi-Fi o simili.
Altre tecnologie ripetute Wi-Fi finiscono con una massiccia perdita di larghezza di banda nella rete.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. È in corso il download e il salvataggio locale di tutti i file multimediali necessari, ad esempio immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio, avendo definito una playlist che non viene modificata molto spesso durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore. Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.

Le tabelle che seguono offrono una buona panoramica dei dati chiave di connettività di rete per le prestazioni che si possono prevedere e i potenziali tempi di attesa.

>[!NOTE]
>Tutte le informazioni devono essere viste come il consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/enclosed-network-download.png)