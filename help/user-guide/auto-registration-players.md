---
title: Registrazione automatica dei lettori
description: Segui questa pagina per scoprire di più sulla registrazione automatica dei lettori con AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Registrazione automatica dei lettori {#auto-registration}

La registrazione manuale in blocco di migliaia di giocatori può diventare complicata e aggiunge tempo e costi. Per semplificare questo processo, la funzione di registrazione in blocco consente di specificare una chiave già condivisa in AEM che può essere fornita in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

## Implementazione della registrazione automatica dei lettori {#bulk-registering-implementation}

Segui i passaggi seguenti per implementare la registrazione automatica dei lettori:

1. Accedi all&#39;istanza AEM e fai clic sul progetto AEM Screens, quindi fai clic su **Proprietà** nella barra delle azioni.
1. Fare clic sulla scheda **Avanzate** per visualizzare la sezione **Registrazione dispositivo**.

1. Specificare un codice di registrazione automatica nel campo **Codice di registrazione in blocco**. Quindi una visualizzazione predefinita facoltativa nell&#39;**Assegnazione visualizzazione predefinita** da assegnare al lettore con registrazione automatica.

   >[!NOTE]
   >Immetti un codice a tua scelta e fai clic su una visualizzazione predefinita, se necessario.

   ![immagine](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Fornisci ai lettori l’URL del server e il codice di registrazione appropriati utilizzando un file MDM o JSON di configurazione.

   >[!NOTE]
   >Per ulteriori dettagli, consulta la pagina di implementazione per il lettore specifico per il sistema operativo in uso. Puoi anche utilizzare l’interfaccia utente di amministrazione per immettere il codice di registrazione.

1. Se l&#39;attributo `registrationKey` corrisponde a quello configurato in AEM, il lettore si registra automaticamente e, se è configurata una visualizzazione predefinita, tale contenuto viene scaricato e riprodotto.

   ![immagine](/help/user-guide/assets/auto-registration/auto-register2.png)

## Best practice per la sicurezza {#security-best-practices}

Segui la sezione seguente per prendere in considerazione alcune delle best practice per la sicurezza:

* Assicurati che il codice di registrazione non sia compromesso: configura il codice in AEM immediatamente prima di avviare la registrazione in blocco e, una volta completato, cancella tale campo e salva in AEM.

* È possibile configurare il percorso `/bin/screens/registration` in modo che sia accessibile solo da intervalli IP noti, se possibile.

* Prendi in considerazione l’utilizzo di un MDM per eseguire il provisioning del lettore con la configurazione.

* Utilizza sempre `HTTPS` e non `HTTP` per la comunicazione del lettore con AEM.

  >[!NOTE]
  >L&#39;assegnazione di visualizzazione predefinita funziona attualmente solo per la registrazione in blocco. Non funziona per la registrazione manuale quando un codice di registrazione non è disponibile.
