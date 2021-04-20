---
title: Registrazione automatica dei giocatori
seo-title: Registrazione automatica dei giocatori
description: Segui questa pagina per scoprire la registrazione automatica dei giocatori con AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Registrazione automatica dei giocatori {#auto-registration}

La registrazione collettiva di migliaia di giocatori manualmente può diventare molto ingombrante e aggiunge tempo e costi. Per semplificare questo processo, la funzione di registrazione in blocco ti consente di specificare una chiave pre-condivisa in AEM che può essere fornita in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

## Implementazione della registrazione automatica dei giocatori {#bulk-registering-implementation}

Segui i passaggi seguenti per implementare la registrazione automatica dei giocatori:

1. Accedi all&#39;istanza AEM e seleziona il progetto schermate AEM e fai clic su **Proprietà** nella barra delle azioni.
1. Seleziona la scheda **Avanzate** per visualizzare la sezione **Registrazione dispositivo** .

1. Specifica un codice di registrazione automatica nel campo **Codice di registrazione bulk** e una visualizzazione predefinita facoltativa in **Assegnazione visualizzazione predefinita** per assegnare al lettore che viene registrato automaticamente.
   >[!NOTE]
   >Immetti un codice a tua scelta e seleziona una visualizzazione predefinita, se necessario.

   ![immagine](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Effettua il provisioning dei tuoi lettori con l’URL del server e il codice di registrazione appropriati utilizzando un file MDM o JSON di configurazione.

   >[!NOTE]
   >Per ulteriori informazioni, consulta la pagina di implementazione per il lettore specifico del sistema operativo in uso. Puoi anche utilizzare l’interfaccia utente amministratore per inserire il codice di registrazione.

1. Se l’attributo `registrationKey` corrisponde a quello configurato in AEM, il lettore si registra automaticamente e, se è configurata una visualizzazione predefinita, il contenuto viene scaricato e riprodotto.

   ![immagine](/help/user-guide/assets/auto-registration/auto-register2.png)

## Tecniche consigliate per la sicurezza {#security-best-practices}

Segui la sezione seguente per prendere in considerazione alcune delle best practice per la sicurezza:

* Per garantire che il codice di registrazione non sia compromesso, configura il codice in AEM immediatamente prima di avviare la registrazione collettiva e, al termine, cancella quel campo e salva in AEM.

* Puoi configurare il percorso `/bin/screens/registration` in modo che sia accessibile solo da intervalli IP noti, se possibile.

* Prendi in considerazione l’utilizzo di un MDM per il provisioning del lettore con la configurazione.

* Utilizza sempre `HTTPS` e non `HTTP` per la comunicazione del lettore con AEM.

   >[!NOTE]
   >L&#39;assegnazione predefinita della visualizzazione attualmente funziona solo per la registrazione in serie e non per la registrazione manuale senza un codice di registrazione.