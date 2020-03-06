---
title: Nuovo Importazione progetto da file
seo-title: Nuovo Importazione progetto da file
description: Questa funzionalità consente di importare in massa un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.
seo-description: Questa funzionalità consente di importare in massa un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: 121aee4c8bf08e30898cc25d274ef4fc6bded5aa

---


# Nuovo Importazione progetto da file {#new-project-importer-from-file}

Questa sezione descrive una funzionalità per importare in massa un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.

## Introduzione {#introduction}

Quando imposti un progetto AEM Screens, per la prima volta nella tua organizzazione devi creare anche tutte le posizioni. Se il progetto prevede un numero elevato di posizioni, si ottiene un risultato noioso, che richiede molto clic e attesa nell’interfaccia utente.

L&#39;obiettivo di questa funzione è ridurre il tempo necessario per configurare il progetto e quindi risolvere i problemi di budget.

Consentendo all’autore di fornire un foglio di calcolo come file di input e consentendo al sistema di creare automaticamente la struttura della posizione nel back-end, questa funzione:

* *prestazioni decisamente migliori rispetto al clic manuale nell’interfaccia utente*
* *consente ai clienti di esportare le posizioni del proprio sistema e importarle direttamente in AEM*

Ciò consente di risparmiare tempo e denaro durante la configurazione iniziale del progetto o quando si estendono le schermate AEM esistenti a nuove posizioni.

## Panoramica dell&#39;architettura {#architectural-overview}

Nel diagramma seguente è illustrata la panoramica architettonica della funzione Importazione progetto:

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modello Dati {#data-model}

Il modello dati per Importazione progetti è descritto di seguito:

>[!NOTE]
>
>La versione corrente supporta solo l&#39;importazione di percorsi.

| **Proprietà** | **Descrizione** |
|---|---|
| ***percorso {string *}** | Percorso della risorsa per la posizione |
| ***[./jcr:title]{string *}** | Nome del modello da utilizzare (ovvero posizione per *schermate/core/templates/location*) |
| ***template {string}*** | Titolo facoltativo da utilizzare per la pagina |
| ***[./jcr:description]{string}*** | Descrizione opzionale da utilizzare per la pagina |

Il file del foglio di calcolo (CSV/XLS) richiede pertanto le seguenti colonne:

* **percorso {stringa}** Il percorso della posizione da importare, in cui la radice del percorso è la cartella del percorso per il progetto (ovvero, */foo* verrà importato in */content/screens/&lt;progetto>/locations/foo*)

* **template {string}** Il modello da utilizzare per la nuova posizione, per ora l&#39;unico valore consentito è &quot;location&quot;, ma sarà esteso a tutti i modelli Screens in futuro (&quot;display&quot;, &quot;sequencechannel, e così via)
* **[./*]{string}**Qualsiasi proprietà facoltativa da impostare sulla posizione (ovvero, ./jcr:title, ./jcr:description, ./foo, ./barra). Al momento, la versione corrente non consente alcun filtro

>[!NOTE]
>
>Tutte le colonne che non corrispondono alle condizioni elencate sopra verranno ignorate. Ad esempio, se nel file del foglio (CSV/XLS) sono state definite altre colonne diverse da **percorso**,**modello**,**titolo** e **descrizione** , tali campi verranno ignorati e Importazione **progetti** non convaliderà tali campi aggiuntivi per l&#39;importazione del progetto nel progetto AEM Screens.

## Utilizzo di Importazione progetti {#using-project-importer}

Nella sezione seguente viene descritto l&#39;utilizzo di Importazione progetti in un progetto AEM Screens.

>[!CAUTION]
>
>Limiti:
>
>* I file diversi dalle estensioni CSV/XLS/XLSX non sono supportati nella versione corrente.
>* Per i file importati non esiste alcun filtro delle proprietà e tutto ciò che inizia con &quot;./&quot; verrà importato.
>



### Prerequisiti {#prerequisites}

* Creare un nuovo progetto denominato **DemoProjectImport**

* Usate un file CSV di esempio o Excel da importare.

A scopo dimostrativo, potete scaricare un file excel dalla sezione seguente.

[Ottieni file](assets/minimal-file.xls)

### Importazione del file con campi obbligatori minimi {#importing-the-file-with-minimum-required-fields}

Per importare un file nella cartella dei percorsi con campi obbligatori minimi, effettuate le seguenti operazioni:

>[!NOTE]
>
>L’esempio seguente mostra i quattro campi richiesti per importare il progetto:

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Passa al progetto AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Selezionare il progetto,** DemoProjectImporter **—>** Create **—>** Import Locations** dalla barra laterale.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. Viene aperta la procedura guidata **Importa** . Selezionate il file di cui disponete per il progetto con i percorsi oppure selezionate il file (file ***minimo.xls***) scaricato dalla sezione *Prerequisiti* .

   Dopo aver selezionato il file, fare clic su **Avanti**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Verificare il contenuto del file (percorsi) dalla procedura guidata di importazione e fare clic su **Importa**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Di conseguenza, ora potrete visualizzare tutte le posizioni importate nel progetto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

