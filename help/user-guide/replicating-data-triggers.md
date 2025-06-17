---
title: Replica dei trigger di dati sui server di pubblicazione
description: Scopri come replicare i trigger di dati sul server di pubblicazione per AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# Replica di Data Triggers su server di pubblicazione {#replicating-data-triggers}

Quando si utilizzano ContextHub e il motore di targeting AEM per personalizzare il contenuto in base ai trigger di dati in una configurazione di authoring/pubblicazione, tutte le configurazioni relative a ContextHub e Personalization non vengono replicate automaticamente con i canali quando vengono pubblicate.

Questa pagina ti aiuta a scoprire i passaggi manuali necessari per pubblicare separatamente queste configurazioni.

Questo processo si riduce essenzialmente alla pubblicazione manuale dei seguenti elementi:

1. Configurazioni dei moduli Store e UI di ContextHub
1. Pubblico Personalization
1. Attività Personalization

## Passaggi per replicare Data Triggers su Publish Server {#replicating-data-triggers-publish}

Segui i passaggi seguenti per replicare i trigger di dati sul server di pubblicazione.

### Passaggio 1: replica delle configurazioni ContextHub {#replicating-contexthub-configurations}

1. Passa a **Strumenti** > **Distribuzione** > **Distribuzione** > **Agente di pubblicazione** e fai clic sull&#39;agente di pubblicazione per configurare le impostazioni.

   ![immagine1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >In alternativa, è possibile utilizzare `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` per passare direttamente alla schermata per configurare e verificare la connessione.

1. Fare clic su **Verifica connessione** dalla barra delle azioni per convalidare la comunicazione dell&#39;autore con l&#39;istanza Publishing, come illustrato di seguito:

   ![immagine1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Se il test non riesce, correggi la configurazione dell’agente di replica tra l’istanza Author e Publishing. Per ulteriori dettagli, vedere [Risoluzione dei problemi relativi alla connessione di prova](/help/user-guide/replicating-data-triggers.md#troubleshoot-test).

1. Fare clic su **Aggiungi** dalla struttura ad albero dell&#39;**Agente di distribuzione** e quindi sul percorso di configurazione del progetto, ad esempio `/conf/screens/settings/cloudsettings/configuration`.

1. Fai clic su **Invia**.

### Replica dei tipi di pubblico {#replicating-audiences}

1. Passa alla tua istanza di AEM > **Personalization** > **Tipi di pubblico** oppure utilizza `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` per navigare direttamente.

1. Espandere la cartella del progetto, ad esempio `/conf/screens/`.

   ![immagine1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Fai clic su tutti i tipi di pubblico e i segmenti dall’interfaccia utente di.

1. Fai clic su **Gestisci pubblicazione** nella barra delle azioni.

1. Fai clic su **Avanti** e **Pubblica**.

### Replica delle attività {#replicating-activities}

1. Passa alla tua istanza di AEM > **Personalization** > **Attività** oppure utilizza `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` per navigare direttamente.

1. Espandere la cartella del progetto, ovvero `/content/campaigns/screens/…`.

1. Dall’interfaccia utente, fai clic su tutte le attività.

1. Fai clic su **Gestisci pubblicazione** nella barra delle azioni.

1. Fai clic su **Avanti** e **Pubblica**.

>[!IMPORTANT]
>
>La replica di configurazioni e tipi di pubblico ContextHub viene eseguita durante la configurazione del progetto durante la replica delle attività e è necessaria ogni volta che il targeting viene modificato all’interno di un canale.

#### Risultato {#result}

Se la replica ha esito positivo, è necessario visualizzare la seguente struttura sull’istanza Publish (o simile per il progetto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Risoluzione dei problemi di prova della connessione {#troubleshoot-test}

Se la connessione di prova non riesce durante la replica delle configurazioni ContextHub, segui la sezione seguente per la risoluzione del problema:

1. Passa a **Strumenti** > **Distribuzione** > **Distribuzione** > **Agente di pubblicazione**.

1. Fare clic su **Modifica** nella barra delle azioni e verificare che anche l&#39;URL dell&#39;endpoint nel campo **Endpoint importazione** punti punti punti rimandi all&#39;URL del server di pubblicazione nell&#39;agente di distribuzione.
   ![immagine1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Se non utilizzi le credenziali amministratore predefinite, devi configurare l’agente di distribuzione con un nome utente e una password diversi.

   Effettua le seguenti operazioni:

   1. Passa a Strumenti > **Operazioni** > **Console Web** `http://localhost:4502/system/console/configMgr`per aprire la **schermata Console Web Adobe Experience Manager**.
   1. Cerca **`Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider`**

      ![immagine1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Creare una configurazione compilando **Name**, **User name** e **password**, ad esempio *slingTransportSecretProvider*.

      ![immagine1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Fai clic su **Salva**
   1. Utilizzare `Cmd +F` per cercare **Agente di distribuzione Apache Sling - Forward Agents Factory** per aprire le configurazioni e cercare **Provider segreto di trasporto**.

      ![immagine1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Aggiorna `(name=default)` con `(name=slingTransportSecretProvider)`.
   1. Fai clic su **Salva** ed esegui nuovamente la connessione di prova dalla schermata **Agente di distribuzione** dall&#39;istanza AEM.
