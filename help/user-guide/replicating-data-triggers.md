---
title: Replica dei trigger di dati sui server di pubblicazione
description: Scopri come replicare i trigger di dati sul server di pubblicazione per AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---

# Replica di Data Triggers su server di pubblicazione {#replicating-data-triggers}

Quando si utilizzano ContextHub e il motore di targeting dell’AEM per personalizzare il contenuto in base ai trigger di dati in una configurazione di authoring/pubblicazione, tutte le configurazioni relative a ContextHub e Personalizzazione non vengono replicate automaticamente con i canali quando vengono pubblicate.

Questa pagina ti aiuta a scoprire i passaggi manuali necessari per pubblicare separatamente queste configurazioni.

Questo si riduce fondamentalmente alla pubblicazione manuale:

1. Configurazioni dei moduli Store e UI di ContextHub
1. Tipi di pubblico per personalizzazione
1. Attività di personalizzazione

## Passaggi per replicare Data Triggers su Publish Server {#replicating-data-triggers-publish}

Segui i passaggi seguenti per replicare i trigger di dati sul server di pubblicazione.

### Passaggio 1: replica delle configurazioni ContextHub {#replicating-contexthub-configurations}

1. Accedi a **Strumenti** > **Distribuzione** > **Distribuzione** > **Agente di pubblicazione** e fai clic sull’agente di pubblicazione per configurare le impostazioni.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >In alternativa, è possibile utilizzare `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` per passare direttamente alla schermata e configurare e verificare la connessione.

1. Clic **Verifica connessione** dalla barra delle azioni, in modo da poter convalidare la comunicazione dell’Autore con l’istanza Publishing, come illustrato di seguito:

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Se il test non riesce, correggi la configurazione dell’agente di replica tra l’istanza Author e Publishing. Consulta [Risoluzione dei problemi di prova della connessione](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) per ulteriori dettagli.

1. Clic **Aggiungi** dal **Agente di distribuzione** struttura dello schermo e fai clic sul percorso di configurazione per il progetto, ad esempio, `/conf/screens/settings/cloudsettings/configuration`.

1. Fai clic su **Invia**.

### Replica dei tipi di pubblico {#replicating-audiences}

1. Passa all’istanza AEM > **Personalizzazione** > **Tipi di pubblico** o utilizzare `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` per navigare direttamente.

1. Approfondisci la cartella del progetto, ad esempio `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Fai clic su tutti i tipi di pubblico e i segmenti dall’interfaccia utente di.

1. Clic **Gestisci pubblicazione** dalla barra delle azioni.

1. Clic **Successivo** e **Pubblica**.

### Replica delle attività  {#replicating-activities}

1. Passa all’istanza AEM > **Personalizzazione** > **Attività** o utilizzare `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` per navigare direttamente.

1. Approfondisci la cartella del progetto, ovvero `/content/campaigns/screens/…`.

1. Dall’interfaccia utente, fai clic su tutte le attività.

1. Clic **Gestisci pubblicazione** dalla barra delle azioni.

1. Clic **Successivo** e **Pubblica**.

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

1. Passa a Strumenti > **Distribuzione** > **Distribuzione** > **Agente di pubblicazione**.

1. Clic **Modifica** dalla barra delle azioni e assicurati che l’URL dell’endpoint in **Endpoint importazione** Il campo punta anche all’URL del server di pubblicazione nell’agente di distribuzione.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Se non utilizzi le credenziali amministratore predefinite, devi configurare l’agente di distribuzione con un nome utente e una password diversi.

   Effettua le seguenti operazioni:

   1. Passa a Strumenti > **Operazioni** > **Console web** `http://localhost:4502/system/console/configMgr`in modo da poter aprire **Schermata Console Web Adobe Experience Manager**.
   1. Cerca **Credenziali trasporto distribuzione Apache Sling - Credenziali utente basate su DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Creare una configurazione, compilando **Nome**, **Nome utente**, e **password** ad esempio: *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Clic **Salva**
   1. Utilizzare `Cmd +F` per cercare **Agente di distribuzione Apache Sling - Factory agenti di inoltro** per aprire le configurazioni e cercare **Provider segreto di trasporto**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Aggiornare il `(name=default)` con `(name=slingTransportSecretProvider)`.
   1. Clic **Salva** ed esegui nuovamente la connessione di prova da **Agente di distribuzione** dall’istanza AEM.
