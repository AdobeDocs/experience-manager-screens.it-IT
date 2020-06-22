---
title: Rete aziendale chiusa
description: Rete aziendale chiusa
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# Reti aziendali collegate {#enclosed-corporate-networks}

La configurazione della rete aziendale chiusa è applicabile alle aziende più piccole, grandi e piccole. Può essere teoricamente più complesso, ma l’impostazione logica è sempre come illustrato di seguito in un esempio semplificato.

## Requisiti per l&#39;impostazione di reti aziendali chiuse {#requirements-enclosed-networks}

La configurazione della rete aziendale chiusa può essere logicamente separata in due blocchi. La rete WAN (Wide Area Network) e la rete LAN (Local Area Network) interna.

![](/help/using/assets/enclosed-network-1.png)

### Ampia rete di reti {#wan-connection}

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete già descritta, devono fornire una larghezza di banda sufficiente per utilizzare AEM Screens in modo ordinato e ordinato.
In dettaglio, &quot;sufficiente&quot; dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti WiFi per gli ospiti.
Tenere presente che tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda è generalmente in diminuzione lineare, mentre l&#39;aggiunta di più consumatori/computer alla rete.

### Rete locale {#lan-connection}

Le prestazioni della LAN, oltre alla raggiungibilità della rete già descritta, garantiscono una larghezza di banda sufficiente per il funzionamento dei AEM Screens in modo ordinato e ordinato. In questi giorni la rete LAN all&#39;interno delle organizzazioni aziendali corrisponde almeno a una rete da 1000 MBit/sec, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Se si utilizza un altro componente di rete attivo, è necessario che tutti questi componenti soddisfino i requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 1000 Mbit/s e alla larghezza di banda fornita dalla specifica Internet Access/Router.

### Altre reti aziendali specifiche {#other-networks}

Solitamente le reti aziendali dispongono di un carico di dispositivi collegati, potrebbero essere separati in varie sottorete reti e potrebbero disporre di connessioni Internet ridondanti o multiplex per fornire prestazioni sufficienti per molte migliaia di accessi simultanei.
Lo schema di cui sopra è semplificato e si adatta nella maggior parte dei casi all&#39;ambiente disponibile per il client.
Nel caso in cui sia prevista una soluzione WiFI per il collegamento dello schermo a Internet Link, si consiglia di utilizzare come minimo standard WIFI moderni come IEEE 802.11g. Questo standard supporta connessioni fino a 54 Mbit. Tutti gli standard più recenti, come 802.11h-n, sono di qualità migliore. Se è richiesto un Ripetitore WIFI, consigliamo vivamente le tecnologie Mesh WIFI Access-point come Google Nest Mesh WIFI o simili.
Altre tecnologie ripetute WiFi finiscono con una massiccia perdita di larghezza di banda nella rete.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. È in corso il download e il salvataggio locale di tutti i file multimediali necessari, ad esempio immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio, avendo definito una playlist che non viene modificata molto spesso durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore. Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.

Le tabelle che seguono offrono una buona panoramica dei dati chiave di connettività di rete per le prestazioni che si possono prevedere e i potenziali tempi di attesa.

Tutte le informazioni devono essere viste come il consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ognuna di queste richieste comporta l&#39;aggiunta e l&#39;estensione del tempo di download.