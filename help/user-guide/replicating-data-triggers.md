---
title: Replicare gli attivatori di dati sui server di pubblicazione
seo-title: Replica degli attivatori di dati sul server di pubblicazione
description: Replicare gli attivatori di dati sul server di pubblicazione.
seo-description: Replicare gli attivatori di dati sul server di pubblicazione.
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

---


# Replica degli attivatori di dati su Publish Server {#replicating-data-triggers}

Quando utilizzate ContextHub e AEM Targeting Engine per personalizzare il contenuto in base agli attivatori di dati in una configurazione di creazione/pubblicazione, tutte le configurazioni relative a ContextHub e Personalizzazione non vengono replicate automaticamente con i canali al momento della pubblicazione.

Seguite questa pagina per apprendere i passaggi manuali necessari per pubblicare queste configurazioni separatamente.

In pratica, si tratta di pubblicare manualmente:

1. Configurazioni dei moduli ContextHub Store e dell&#39;interfaccia utente
1. Audiences di personalizzazione
1. Attività di personalizzazione

## Passaggi per la replica degli attivatori dati su Publish Server {#replicating-data-triggers-publish}

Per replicare le attivazioni di dati sul server di pubblicazione, effettuate le seguenti operazioni:

### Replica delle configurazioni ContextHub {#replicating-contexthub-configurations}

1. Passa a **Strumenti** > **Distribuzione** > **Distribuzione** > **Pubblica agente** http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish
1. Fate clic sul pulsante Verifica connessione per verificare che l’autore possa comunicare correttamente con l’istanza di pubblicazione
1. Se il test ha esito negativo, è necessario correggere la configurazione dell&#39;agente di replica tra l&#39;autore e la pubblicazione
1. Assicurarsi che l&#39;URL dell&#39;endpoint indichi anche l&#39;URL del server di pubblicazione nell&#39;agente di distribuzione
1. Modifica > Punti finali importazione
1. Fare clic sulla scheda Distribuisci
1. Pulsante di scelta Aggiungi albero
1. Nel browser Percorsi, seleziona il percorso di configurazione del progetto (es. /conf/screens/settings/cloud settings/configuration)
1. Fate clic su Invia

### Replica del pubblico {#replicating-audiences}

1. Passa a Strumenti > Personalizzazione > Pubblicohttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html
1. Approfondisci la cartella del progetto (ad es. /conf/screens/)
1. Seleziona tutte le audience/i segmenti nell&#39;interfaccia utente
1. Fai clic su Gestisci pubblicazione
1. Fai clic su Avanti
1. Fai clic su Pubblica

### Replica delle attività {#replicating-activities}

1. Passa a Strumenti > Personalizzazione > Attivitàhttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html
1. Approfondisci la cartella del progetto (ad es. /content/campaign/screens/...)
1. Seleziona tutte le attività nell’interfaccia utente
1. Fai clic su Gestisci pubblicazione
1. Fai clic su Avanti
1. Fai clic su Pubblica

> [!Note]
>La replica di configurazioni e audience ContextHub viene eseguita durante la configurazione del progetto, mentre le attività di replica e saranno richieste ogni volta che il targeting viene modificato all&#39;interno di un canale.

#### Risultato {#result}

Se la replica ha esito positivo, è necessario visualizzare la struttura seguente nell’istanza di pubblicazione (o simile per il progetto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`