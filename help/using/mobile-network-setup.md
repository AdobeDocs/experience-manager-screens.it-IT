---
title: Rete mobile diretta
description: La pagina descrive l’impostazione della rete mobile diretta
translation-type: tm+mt
source-git-commit: 0b1106b3cf7f83857f83e43f773a0d19556cfec5
workflow-type: tm+mt
source-wordcount: '951'
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
1. Se tutte le impostazioni precedenti sono configurate correttamente e continua a essere visualizzato un messaggio di errore, verifica se sono presenti restrizioni di porta sui componenti di rete attivi come Switch o router aggiuntivi.
1. Se la chiamata URL ha avuto esito positivo, potete continuare a installare gli AEM Screens e registrarli di conseguenza. AEM Screens iniziali.

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

Le prestazioni della connessione Internet, oltre alla raggiungibilità della rete già descritta, devono fornire una larghezza di banda sufficiente per utilizzare AEM Screens in modo ordinato e ordinato. In dettaglio, &quot;sufficiente&quot; dipende dalla quantità di schermi AEM collegati e dall&#39;utilizzo di altri consumatori all&#39;interno della rete, come smartphone, tablet, cassieri, computer o reti Wi-Fi per gli ospiti.
Tenere presente che tutti i dispositivi dispongono di un accesso simultaneo alla connessione Internet e la larghezza di banda diminuisce in genere in modo lineare, aggiungendo alla rete più utenti/computer.
Oltre alla specifica connessione teorica di rete, è necessario garantire che la copertura del router mobile sia almeno &quot;buona&quot; (fare riferimento al manuale del router mobile). Inoltre, il piano mensile sottostante deve coprire una capacità dati sufficiente e una larghezza di banda sufficiente per servire tutti i client connessi all&#39;interno della LAN collegata.
Le reti dati forniscono una larghezza di banda standard con circa fino a:
・ 3 Go 42 Mbit/sec ・ 4 Go 150 Mbit/sec ・ 5Go 1000 Mbit/sec-10000 Mbit/secMentre si considera quale rete dati debba essere utilizzata, si consiglia di rispondere alle seguenti domande:
・ Quanti clienti sono collegati al Router?
・ Quante modifiche apportate ai contenuti si possono attendere e quali sono le dimensioni medie dei file?
Come follow-up il pacchetto dati necessario deve essere almeno:
Capacità pacchetto dati = # dei client * (# di file di contenuto * dimensione file media) Assicurarsi che il buffer sia sufficiente.
Attenzione: Per il caricamento iniziale dei file multimediali, ad esempio, mentre si integrano nuovi lettori, è necessario prevedere una maggiore quantità di dati e un maggiore tempo di scaricamento, che si rifletta nelle ipotesi di cui sopra.
Come regola di pollice, una rete 4G con una copertura &quot;buona&quot; e dati illimitati dovrebbe corrispondere alle installazioni più comuni in questa configurazione di rete


### Rete locale {#lan-connection}

Le prestazioni della LAN hanno, oltre alla raggiungibilità di rete già descritta, di fornire banda sufficiente per il funzionamento dei AEM Screens in modo ordinato e ordinato. In questi giorni la rete LAN corrisponde almeno a una rete da 100 MBit/sec, in modo che ci dovrebbe essere Bandwith sufficiente per collegare molti dispositivi con buone prestazioni al sistema. Se si utilizza un altro componente di rete attivo, è obbligatorio che tutti gli altri componenti corrispondano ai requisiti della banda di rete. Ad esempio, i componenti di rete devono corrispondere almeno allo standard 100 Mbit/s e al Banda fornito dalla specifica Internet Access/Router.

## Download di file multimediali e risorse {#download}

I AEM Screens offrono un grande vantaggio agli utenti del digital signage. È in corso il download e il salvataggio locale di tutti i file multimediali necessari, ad esempio immagini e video. A causa di questo concetto, il traffico di rete principale si verifica nel caso in cui su uno schermo specifico sia presente nuovo contenuto da visualizzare.
Per il normale funzionamento, ad esempio, avendo definito una playlist che non viene modificata molto spesso durante il giorno, questo offre un funzionamento indipendente dalla rete, una volta salvati tutti i file sul lettore.
Per quei casi d&#39;uso in cui ci sono più interazioni con Sensori o altri Attivatori e i contenuti sono molto dinamici, una connessione di rete veloce e affidabile è essenziale per una reazione immediata dello schermo, al fine di garantire la migliore esperienza cliente.
Le tabelle che seguono offrono una buona panoramica dei dati chiave di connettività di rete per le prestazioni che si possono prevedere e i potenziali tempi di attesa.
Tutte le informazioni devono essere viste come il consumo di ogni dispositivo nella rete che richiede e scarica una fonte Internet. Ognuna di queste richieste comporta l&#39;aggiunta e l&#39;estensione del tempo di download.

![](/help/using/assets/download-times-mobile.png)



