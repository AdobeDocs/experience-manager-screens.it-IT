---
title: Registrazione automatica dei lettori
description: Segui questa pagina per scoprire di più sulla Registrazione automatica dei lettori con AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Registrazione automatica dei lettori {#auto-registration}

La registrazione manuale in blocco di migliaia di giocatori può diventare complicata e aggiunge tempo e costi. Per semplificare questo processo, la funzione di registrazione in blocco consente di specificare una chiave già condivisa in AEM che può essere fornita in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

## Implementazione della registrazione automatica dei lettori {#bulk-registering-implementation}

Segui i passaggi seguenti per implementare la registrazione automatica dei lettori:

1. Accedi all’istanza AEM, seleziona il progetto AEM Screens e fai clic su **Proprietà** dalla barra delle azioni.
1. Seleziona la **Avanzate** in modo da visualizzare **Registrazione dispositivo** sezione.

1. Specificare un codice di registrazione automatica in **Codice di registrazione in blocco** e una visualizzazione predefinita facoltativa in **Assegnazione visualizzazione predefinita** per assegnare al lettore la registrazione automatica.

   >[!NOTE]
   >Immetti un codice a tua scelta e, se necessario, seleziona una visualizzazione predefinita.

   ![immagine](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Fornisci ai lettori l’URL del server e il codice di registrazione appropriati utilizzando un file MDM o JSON di configurazione.

   >[!NOTE]
   >Per ulteriori informazioni, consulta la pagina di implementazione del lettore specifico per il sistema operativo in uso. Puoi anche utilizzare l’interfaccia utente di amministrazione per immettere il codice di registrazione.

1. Se il `registrationKey` corrisponde a quello configurato in AEM, il lettore si registra automaticamente e, se è configurata una visualizzazione predefinita, il contenuto viene scaricato e riprodotto.

   ![immagine](/help/user-guide/assets/auto-registration/auto-register2.png)

## Best practice per la sicurezza {#security-best-practices}

Segui la sezione seguente per prendere in considerazione alcune delle best practice per la sicurezza:

* Assicurati che il codice di registrazione non sia compromesso: configura il codice in AEM immediatamente prima di avviare la registrazione in blocco e, una volta completato, cancella tale campo e salva in AEM.

* Puoi configurare il percorso `/bin/screens/registration` per essere accessibile solo da intervalli IP noti, se possibile.

* Prendi in considerazione l’utilizzo di un MDM per eseguire il provisioning del lettore con la configurazione.

* Usa sempre `HTTPS` e non `HTTP` per la comunicazione tra i giocatori e l’AEM.

  >[!NOTE]
  >L&#39;assegnazione di visualizzazione predefinita funziona attualmente solo per la registrazione in blocco e non per la registrazione manuale senza un codice di registrazione.
