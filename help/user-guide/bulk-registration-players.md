---
title: Registrazione in serie dei giocatori
seo-title: Registrazione in serie dei giocatori
description: Segui questa pagina per informazioni sulla registrazione in serie dei giocatori con AMS/On-Prem Screens.
translation-type: tm+mt
source-git-commit: a00c761297b80239b741e68ef6f2ac611d3559f2
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Registrazione in serie dei giocatori {#bulk-registration}

La registrazione collettiva di migliaia di giocatori manualmente può diventare molto ingombrante e aggiunge tempo e costi. Per semplificare questo processo, la funzione di registrazione in blocco ti consente di specificare una chiave pre-condivisa in AEM che può essere fornita in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

## Implementazione della registrazione in serie dei lettori {#bulk-registering-implementation}

Segui i passaggi seguenti per implementare la registrazione in serie dei giocatori:

1. Accedi alla tua istanza AEM e seleziona il tuo progetto AEM screens, fai clic su proprietà e sulla scheda Avanzate .
1. Dovresti visualizzare una sezione di registrazione in serie in cui puoi specificare un codice di registrazione in serie e una visualizzazione predefinita opzionale da assegnare al lettore registrato in massa
1. Immetti un codice a tua scelta e seleziona una visualizzazione predefinita se necessario
1. Effettua il provisioning dei tuoi lettori con l’URL del server e il codice di registrazione appropriati utilizzando un file MDM o JSON di configurazione. Per informazioni dettagliate, fai riferimento alla pagina di implementazione per il lettore specifico del tuo sistema operativo. Puoi anche utilizzare l’interfaccia utente amministratore per inserire il codice di registrazione.
1. Se l’attributo `registrationKey` corrisponde a quello configurato in AEM, il lettore si registra automaticamente e, se è configurata una visualizzazione predefinita, il contenuto viene scaricato e riprodotto.

## Tecniche consigliate per la sicurezza {#security-best-practices}

Segui la sezione seguente per prendere in considerazione alcune delle best practice per la sicurezza:

* Per garantire che il codice di registrazione non sia compromesso, configura il codice in AEM subito prima di avviare la registrazione in blocco e, al termine, cancella quel campo e salva in AEM.

* Puoi configurare che il percorso `/bin/screens/`registrazione sia accessibile solo da intervalli IP noti, se possibile.

* Prendi in considerazione l’utilizzo di un MDM per il provisioning del lettore con la configurazione.

* Utilizza sempre `HTTPS` e non `HTTP` per la comunicazione del lettore con AEM.

   >[!NOTE]
   >L&#39;assegnazione predefinita della visualizzazione attualmente funziona solo per la registrazione in serie e non per la registrazione manuale senza un codice di registrazione.