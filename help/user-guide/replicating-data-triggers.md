---
title: Replicare gli attivatori di dati sui server di pubblicazione
seo-title: Replica degli attivatori di dati sul server di pubblicazione
description: Replicare gli attivatori di dati sul server di pubblicazione.
seo-description: Replicare gli attivatori di dati sul server di pubblicazione.
translation-type: tm+mt
source-git-commit: 47e0204ea734a1348385ddd3c7108038c88d1933

---


# Replica degli attivatori di dati su Publish Server {#replicating-data-triggers}

Quando utilizzate ContextHub e AEM Targeting Engine per personalizzare il contenuto in base agli attivatori di dati in una configurazione di creazione/pubblicazione, tutte le configurazioni relative a ContextHub e Personalizzazione non vengono replicate automaticamente con i canali al momento della pubblicazione.

Seguite questa pagina per apprendere i passaggi manuali necessari per pubblicare queste configurazioni separatamente.

In pratica, si tratta di pubblicare manualmente:

1. Configurazioni dei moduli ContextHub Store e dell&#39;interfaccia utente
1. Audiences di personalizzazione
1. Attività di personalizzazione

## Passaggi per la replica degli attivatori dati su Publish Server {#replicating-data-triggers-publish}

Seguite i passaggi riportati di seguito per replicare le attivazioni dei dati sul server di pubblicazione.

### Passaggio 1:Replica delle configurazioni ContextHub {#replicating-contexthub-configurations}

1. Accedete a **Strumenti** > **Distribuzione** > **Distribuzione** > **Pubblica agente** e fate clic sull’agente di pubblicazione per configurare le impostazioni.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Note]
   >In alternativa, è possibile utilizzare il [collegamento](http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish) per navigare direttamente sullo schermo per configurare e verificare la connessione.

1. Fate clic su **Test connessione** dalla barra delle azioni per convalidare la comunicazione dell’autore con l’istanza di pubblicazione, come illustrato nella figura riportata di seguito.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Note]
   >Se il test ha esito negativo, è necessario correggere la configurazione dell&#39;agente di replica tra l&#39;istanza di creazione e di pubblicazione. Per ulteriori informazioni, consulta [Risoluzione dei problemi relativi alla connessione](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) di prova.

1. Fate clic su **Modifica** nella schermata qui sopra e accertatevi che l’URL dell’endpoint nel campo Endpoint **** importazione indichi anche l’URL del server di pubblicazione nell’agente di distribuzione.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers3.png)

1. Selezionate **Aggiungi** nella struttura ad albero della schermata **Agente** di distribuzione e selezionate il percorso di configurazione del progetto, ovvero `/conf/screens/settings/cloudsettings/configuration)`.

1. Fate clic su **Invia**

### Replica del pubblico {#replicating-audiences}

1. Passa a **Strumenti** > **Personalizzazione** > **Pubblico** o usa il [collegamento](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html) per navigare direttamente.

1. Approfondisci la cartella del tuo progetto, ovvero `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers5.png)

1. Seleziona tutte le audience e i segmenti dall&#39;interfaccia utente.

1. Fai clic su **Gestisci pubblicazione** dalla barra delle azioni.

1. Fate clic su **Avanti** e **Pubblica**.

### Replica delle attività {#replicating-activities}

1. Passa a **Strumenti** > **Personalizzazione** > **Attività** oppure usa il [collegamento](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html) per spostarsi direttamente.

1. Approfondisci la cartella del tuo progetto, ovvero `/content/campaigns/screens/…`.

1. Seleziona tutte le attività dall&#39;interfaccia utente.

1. Fai clic su **Gestisci pubblicazione** dalla barra delle azioni.

1. Fate clic su **Avanti** e **Pubblica**.

   > [!Note]
   >La replica di configurazioni e audience ContextHub viene eseguita durante la configurazione del progetto, mentre le attività di replica e saranno richieste ogni volta che il targeting viene modificato all&#39;interno di un canale.

#### Risultato {#result}

Se la replica ha esito positivo, è necessario visualizzare la struttura seguente nell’istanza di pubblicazione (o simile per il progetto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Risoluzione dei problemi di connessione di prova {#troubleshoot-test}

Se la connessione di prova non riesce durante la replica delle configurazioni ContextHub, seguite la sezione seguente per risolvere il problema:

1. Andate al campo **Importer Endpoints** e accertatevi che l&#39;URL dell&#39;endpoint indichi l&#39;URL del server di pubblicazione nell&#39;agente di distribuzione.

1. Se non utilizzate le credenziali predefinite, dovete configurare l&#39;agente di distribuzione con una password amministratore diversa.
Effettuate le seguenti operazioni:

   1. Passa a Strumenti > **Operazioni** > Console Web** `http://localhost:4502/system/console/configMgr`per aprire la schermata **Console Web** Adobe Experience Manager.

   1. Cerca credenziali di trasporto distribuzione **Apache Sling - Credenziali utente basate su DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Create una configurazione compilando **Nome**, Nome **** utente e **password**, ad esempio *slingTransportSecretProvider*. .
   1. Fai clic su **Salva**

   1. Cerca il nome dell&#39;agente di distribuzione tramite `Cmd +F`.

   1. Fare clic per aprire la configurazione osgi agente di distribuzione.

   1. Cercate Transport Secret Provider nella configurazione osgi e aggiornatelo con `"(name=slingTransportSecretProvider)"`.

   1. Fate clic su **Salva** ed eseguite la connessione di prova.
