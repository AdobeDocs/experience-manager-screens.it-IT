---
title: Replicare gli attivatori dati ai server di pubblicazione
seo-title: Replicare gli attivatori dati al server di pubblicazione
description: Segui questa pagina per scoprire come replicare i trigger di dati sul server di pubblicazione.
seo-description: Replicare gli attivatori dati sul server di pubblicazione.
feature: Amministrazione di Screens, Data Trigger
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# Replica degli attivatori di dati su server di pubblicazione {#replicating-data-triggers}

Quando si utilizzano ContextHub e AEM Targeting Engine per personalizzare il contenuto in base ai trigger di dati in una configurazione di authoring/pubblicazione, tutte le configurazioni relative a ContextHub e Personalizzazione non vengono replicate automaticamente con i canali al momento della pubblicazione.

Segui questa pagina per scoprire i passaggi manuali necessari per pubblicare separatamente queste configurazioni.

In pratica si riduce alla pubblicazione manuale:

1. Configurazioni dei moduli ContextHub Store e UI
1. Pubblico di personalizzazione
1. Attività di personalizzazione

## Passaggi per la replica dei trigger dati su server di pubblicazione {#replicating-data-triggers-publish}

Segui i passaggi riportati di seguito per replicare gli attivatori di dati sul server di pubblicazione.

### Passaggio 1: Replica delle configurazioni ContextHub {#replicating-contexthub-configurations}

1. Passa a **Strumenti** > **Implementazione** > **Distribuzione** > **Pubblica agente** e fai clic sull&#39;agente di pubblicazione per configurare le impostazioni.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >In alternativa, è possibile utilizzare `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` per passare direttamente alla schermata per configurare e verificare la connessione.

1. Fai clic su **Prova connessione** nella barra delle azioni per convalidare la comunicazione dell’autore con l’istanza di pubblicazione, come illustrato nella figura seguente.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Se il test non riesce, devi correggere la configurazione dell’agente di replica tra l’istanza di authoring e quella di pubblicazione. Per ulteriori informazioni, consulta [Risoluzione dei problemi di connessione di prova](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) .

1. Seleziona **Aggiungi** dalla struttura ad albero dello schermo **Agente di distribuzione** e seleziona il percorso di configurazione del progetto, ad esempio `/conf/screens/settings/cloudsettings/configuration`.

1. Fare clic su **Invia**.

### Replica del pubblico {#replicating-audiences}

1. Vai alla tua istanza AEM > **Personalizzazione** > **Audiences** o utilizza `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` per navigare direttamente.

1. Esegui un drill-down nella cartella del progetto, ad esempio `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Seleziona tutti i tipi di pubblico e i segmenti dall’interfaccia utente.

1. Fai clic su **Gestisci pubblicazione** nella barra delle azioni.

1. Fare clic su **Avanti** e su **Pubblica**.

### Replica delle attività {#replicating-activities}

1. Passa all&#39;istanza AEM > **Personalizzazione** > **Attività** o utilizza `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` per navigare direttamente.

1. Esegui il drill-down nella cartella del progetto, ovvero `/content/campaigns/screens/…`.

1. Seleziona tutte le attività dall’interfaccia utente.

1. Fai clic su **Gestisci pubblicazione** nella barra delle azioni.

1. Fare clic su **Avanti** e su **Pubblica**.

>[!IMPORTANT]
>
>La replica delle configurazioni e dei tipi di pubblico ContextHub viene eseguita durante la configurazione del progetto, mentre la replica delle attività viene richiesta ogni volta che il targeting viene modificato all’interno di un canale.

#### Risultato {#result}

Se la replica ha esito positivo, è necessario visualizzare la seguente struttura nell’istanza di pubblicazione (o simile per il progetto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Risoluzione dei problemi di connessione di prova {#troubleshoot-test}

Se la connessione di prova non riesce durante la replica delle configurazioni di ContextHub, segui la sezione sottostante per risolvere il problema:

1. Passa a Strumenti > **Implementazione** > **Distribuzione** > **Pubblica agente**.

1. Fai clic su **Modifica** nella barra delle azioni e assicurati che l&#39;URL dell&#39;endpoint nel campo **Endpoint importazione** indichi anche l&#39;URL del server di pubblicazione nell&#39;agente di distribuzione.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Se non utilizzi le credenziali di amministratore predefinite, devi configurare l’agente di distribuzione con un nome utente e una password diversi.

   Effettua le seguenti operazioni:

   1. Passa a Strumenti > **Operazioni** > **Console web** `http://localhost:4502/system/console/configMgr`per aprire la **schermata Console web Adobe Experience Manager**.
   1. Cerca **Apache Sling Distribution Transport Credentials - User Credentials basato su DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Crea una configurazione popolando **Nome**, **Nome utente** e **password**, ad esempio *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Fai clic su **Salva**
   1. Utilizza `Cmd +F` per cercare **Apache Sling Distribution Agent - Forward Agents Factory** per aprire le configurazioni e cercare **Transport Secret Provider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Aggiorna `(name=default)` con `(name=slingTransportSecretProvider)`.
   1. Fai clic su **Salva** ed esegui di nuovo la connessione di prova dalla schermata **Agente di distribuzione** dalla tua istanza AEM.
