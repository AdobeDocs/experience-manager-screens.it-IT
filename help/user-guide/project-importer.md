---
title: Nuova importazione progetti da file
description: Questa funzionalità consente di importare in blocco un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 1%

---

# Nuova importazione progetti da file {#new-project-importer-from-file}

Questa sezione descrive una funzionalità per importare in blocco un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.

## Introduzione {#introduction}

Quando imposti un progetto AEM Screens per la prima volta nell’organizzazione, crea anche tutte le posizioni. Se il progetto coinvolge molte posizioni, si ottiene una noiosa attività che comporta molti clic e attese nell’interfaccia utente.

L’obiettivo di questa funzione è ridurre il tempo necessario per configurare il progetto e risolvere quindi i problemi di budget.

Consentendo all&#39;autore di fornire un foglio di calcolo come file di input e consentendo al sistema di creare automaticamente la struttura di posizioni nel back-end, questa funzione:

* *migliora le prestazioni rispetto al clic manuale nell’interfaccia utente*
* *consente al cliente di esportare i siti di cui dispone dal proprio sistema e di importarli facilmente direttamente nell&#39;AEM*

Questo consente di risparmiare tempo e denaro durante la configurazione iniziale del progetto o quando si estende l’AEM Screens esistente a nuove posizioni.

## Panoramica dell’architettura {#architectural-overview}

Il diagramma seguente mostra la panoramica dell’architettura per la funzione Importazione progetti:

![screen_shot_2019-05-14alle20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modello dati {#data-model}

Il modello dati per Importazione progetti è descritto di seguito:

>[!NOTE]
>
>La versione corrente supporta solo l’importazione di posizioni.

| **Proprietà** | **Descrizione** |
|---|---|
| ***`path {string*}`*** | Percorso della risorsa per la posizione |
| ***`[./jcr:title] {string*}`*** | Nome del modello da utilizzare, ovvero posizione *screens/core/templates/location*) |
| ***`template {string}`*** | Titolo facoltativo da utilizzare per la pagina |
| ***`[./jcr:description] {string}`*** | Descrizione facoltativa da utilizzare per la pagina |

Il file del foglio di calcolo (CSV/XLS) richiede quindi le seguenti colonne:

* **percorso {string}** : percorso del percorso da importare, in cui la directory principale del percorso è la cartella dei percorsi del progetto (ovvero *`/foo`* viene importato in *`/content/screens/<project>/locations/foo`*)
* **modello {string}** - Modello da utilizzare per la nuova posizione; per ora l’unico valore consentito è &quot;posizione&quot;, ma questo verrà esteso in futuro a tutti i modelli Screens (`display`, `sequencechannel`e così via)
* **[./*] {string}** - Qualsiasi proprietà facoltativa da impostare sulla posizione (ovvero `./jcr:title`, `./jcr:description`, `./foo, ./bar`). La versione corrente non consente alcun filtro.

>[!NOTE]
>
>Qualsiasi colonna che non soddisfa le condizioni di cui sopra viene ignorata. Ad esempio, se nel foglio (CSV/XLS) è definita un’altra colonna diversa da **percorso**, **modello**, **titolo**, e **descrizione** nel file, tali campi vengono ignorati. E, **Importazione progetti** non convalida tali campi aggiuntivi per l’importazione del progetto nel progetto AEM Screens.

## Utilizzo di Importazione progetti {#using-project-importer}

La sezione seguente descrive come viene utilizzata l’Importazione progetti in un progetto AEM Screens.

>[!CAUTION]
>
>Limiti:
>
>* I file diversi dalle estensioni CSV/XLS/XLSX non sono supportati nella versione corrente.
>* Non esiste alcun filtro delle proprietà per i file importati e nulla che inizi con &quot;./&quot; viene importato.
>

### Prerequisiti {#prerequisites}

* Crea un progetto con titolo **ImportazioneProgettoDemo**

* Utilizza un file CSV o Excel di esempio da importare.

A scopo dimostrativo, puoi scaricare un file excel dalla sezione seguente.

[Ottieni file](assets/minimal-file.xls)

### Importazione del file con i campi obbligatori minimi {#importing-the-file-with-minimum-required-fields}

Per importare un file in una cartella di percorso contenente campi obbligatori minimi, attenersi alla procedura descritta di seguito.

>[!NOTE]
>
>L’esempio seguente mostra i quattro campi minimi necessari per importare il progetto:

![screen_shot_2019-05-14alle21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Passa al progetto AEM Screens (**ImportazioneProgettoDemo**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Selezionare il progetto,** DemoProjectImporter **>** Crea **>** Importa posizioni** dalla barra laterale.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. Il **Importa** viene visualizzata la procedura guidata. Selezionare il file per il progetto con le posizioni o selezionare il file (***minimal-file.xls***) scaricato da *Prerequisiti* sezione.

   Dopo aver selezionato il file, fai clic su **Successivo**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Verifica il contenuto del file (percorsi) dall’Importazione guidata e fai clic su **Importa**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Di conseguenza, ora puoi visualizzare tutte le posizioni importate nel progetto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
