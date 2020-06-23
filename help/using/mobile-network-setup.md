---
title: Rete mobile diretta
description: La pagina descrive l’impostazione della rete mobile diretta
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---


# Rete mobile diretta {#mobile-network-setup}

I giocatori di AEM Screens possono anche essere collegati tramite reti mobili o cellulari che eseguono almeno una rete 3G.

All&#39;interno dei AEM Screens, il contenuto richiesto viene scaricato fisicamente nel controller del lettore o nel computer e memorizzato correttamente all&#39;interno del sistema operativo sottostante. La larghezza di banda specificata influisce solo sui tempi di download iniziali e non influisce sulle prestazioni dei display.

Connessione dei lettori AEM Screens con Cellulare 3/4/5G ai provider di dati di Mobile Service. Il vantaggio di questa configurazione è che il router per dispositivi mobili può essere collocato in una posizione ottimizzata per garantire la migliore copertura di rete disponibile. Questo è solitamente in posizione elevata e aperta con il meno possibile costruzione di cemento o metallo circostante.

Questa configurazione consente agli utenti dello schermo AEM una grande flessibilità, in quanto non è necessaria alcuna connessione fissa per connettere AEM Screens.

![](/help/using/assets/direct-mobile-1.png)

## Collegamento del lettore AEM Screens alla rete mobile diretta {#connecting-aem-screens-players}

Segui i passaggi indicati di seguito per collegare i lettori di schermo AEM in questa configurazione:

1. Accertatevi che ciascuno dei lettori dello schermo AEM sia collegato alla rete Routers.

1. Verificate la connessione Internet chiamando un URL nel browser del sistema.

   >[!NOTE]
   >Nel caso in cui venga visualizzato un messaggio di errore, controllare le impostazioni di rete. Esistono sostanzialmente due opzioni per una connessione di rete adeguata:
   >* DHCP
   >* Configurazione IP manuale


1. Assicurarsi che l&#39;impostazione della scheda di rete corrisponda all&#39;impostazione del router.
1. Verificare che il router sia collegato correttamente alla rete Internet Wide Area Network (Internet Link). In genere può essere identificato anche utilizzando un LED di segnale su router standard.

1. Se la chiamata URL ha esito positivo, potete continuare a installare gli AEM Screens e registrarli di conseguenza. AEM Screens iniziali.

   >[!NOTE]
   >**Suggerimenti per la risoluzione dei problemi**
   >Se i AEM Screens non si connettono correttamente e non mostrano il contenuto previsto:
   >
   >1. Se sono presenti restrizioni, controllate il firewall Internet Router `TCP/IP Port 80/443`.
   >1. Accertatevi che tutte le porte necessarie siano consentite.



## Requisiti per la configurazione della rete mobile {#requirements-direct}

La configurazione della rete può essere logicamente separata in due blocchi:

* Connessione Internet mobile

* Rete locale

### Connessione Internet mobile {#mobile-internet-connection}

Le prestazioni della connessione Internet oltre alla raggiungibilità della rete forniscono una larghezza di banda sufficiente per utilizzare AEM Screens in modo ordinato e ordinato.

*Sufficiente* dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti WiFi per gli ospiti.
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
>Accertatevi che sia presente un buffer sufficiente.
>Per il caricamento iniziale di file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una quantità maggiore di dati e un tempo di download maggiore, che si riflette nelle ipotesi sopra riportate.Una rete 4G con una *buona* copertura e dati *illimitati* dovrebbe corrispondere alle installazioni più comuni di questa configurazione di rete.


### Rete locale {#lan-connection}

Le prestazioni della LAN, oltre alla raggiungibilità della rete già descritta, garantiscono una larghezza di banda sufficiente per il funzionamento dei AEM Screens in modo ordinato e ordinato. In questi giorni la rete LAN corrisponde almeno a una rete a 100 Mbps, in modo che la larghezza di banda sia sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Se si utilizza un altro componente di rete attivo, è necessario che tutti questi componenti soddisfino i requisiti di larghezza di banda della rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbps e alla larghezza di banda fornita dalla specifica Internet Access/Router.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. Consente di scaricare e salvare localmente tutti i file multimediali necessari, ad esempio immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico siano presenti nuovi contenuti da visualizzare.
Per il normale funzionamento, ad esempio, una playlist definita che non viene modificata molto spesso durante il giorno, offre un funzionamento indipendente dalla rete, una volta che tutti i file sono stati salvati sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.

La tabella seguente fornisce una panoramica dei dati chiave per la connettività di rete relativi alle prestazioni che possono essere previste e ai potenziali tempi di attesa.
>[!NOTE]
>Tutte le informazioni si riferiscono al consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ciascuna di queste richieste aggiunge ed estende il tempo di download.

![](/help/using/assets/download-times-mobile.png)



