---
title: Registrazione automatica dei lettori
description: Segui questa pagina per scoprire di più sulla registrazione automatica dei lettori con AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
TQID: https://experienceleague.adobe.com/uvCRS49L6CQbah4AKFwRdhGN-pvKnTWtNMN8CnFojIQ
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 388
ht-degree: 0%

---

# Registrazione automatica dei lettori {#auto-registration}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

La registrazione manuale in blocco di migliaia di giocatori può diventare complicata e aggiunge tempo e costi. Per semplificare questo processo, la funzione di registrazione in blocco consente di specificare una chiave già condivisa in AEM che può essere fornita in un lettore tramite un file di configurazione o una soluzione MDM (Mobile Device Management).

## Implementazione della registrazione automatica dei lettori {#bulk-registering-implementation}

Segui i passaggi seguenti per implementare la registrazione automatica dei lettori:

1. Accedi all&#39;istanza di AEM e fai clic sul progetto AEM Screens, quindi fai clic su **Proprietà** nella barra delle azioni.
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

* Assicurati che il codice di registrazione non sia compromesso: configura il codice in AEM subito prima di avviare la registrazione in blocco, al termine cancella tale campo e salva in AEM.

* È possibile configurare il percorso `/bin/screens/registration` in modo che sia accessibile solo da intervalli IP noti, se possibile.

* Prendi in considerazione l’utilizzo di un MDM per eseguire il provisioning del lettore con la configurazione.

* Utilizza sempre `HTTPS` e non `HTTP` per la comunicazione del lettore con AEM.

  >[!NOTE]
  >L&#39;assegnazione di visualizzazione predefinita funziona attualmente solo per la registrazione in blocco. Non funziona per la registrazione manuale quando un codice di registrazione non è disponibile.
