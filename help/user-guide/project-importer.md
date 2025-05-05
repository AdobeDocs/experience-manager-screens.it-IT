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
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---

# Nuova importazione progetti da file {#new-project-importer-from-file}

Questa sezione descrive una funzionalità per importare in blocco un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.

## Introduzione {#introduction}

Quando imposti un progetto AEM Screens per la prima volta nell’organizzazione, crea anche tutte le posizioni. Se il progetto coinvolge molte posizioni, si ottiene una noiosa attività che richiede molta selezione e attesa nell’interfaccia utente.

L’obiettivo di questa funzione è ridurre il tempo necessario per configurare il progetto e risolvere quindi i problemi di budget.

Consentendo all&#39;autore di fornire un foglio di calcolo come file di input e consentendo al sistema di creare automaticamente la struttura di posizioni nel back-end, questa funzione:

* *ottiene prestazioni notevolmente migliori rispetto alla selezione manuale tramite l&#39;interfaccia utente*
* *consente al cliente di esportare le posizioni di cui dispone dal proprio sistema e di importarle facilmente direttamente in AEM*

Questo processo consente di risparmiare tempo e denaro durante la configurazione iniziale del progetto o quando si estende l’AEM Screens esistente a nuove posizioni.

## Panoramica dell’architettura {#architectural-overview}

Il diagramma seguente mostra la panoramica dell’architettura per la funzione Importazione progetti:

![schermata_shot_2019-05-14alle20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modello dati {#data-model}

Il modello dati per Importazione progetti è descritto di seguito:

>[!NOTE]
>
>La versione corrente supporta solo l’importazione di posizioni.

| **Proprietà** | **Descrizione** |
|---|---|
| ***`path {string*}`*** | Percorso della risorsa per la posizione |
| ***`[./jcr:title] {string*}`*** | Il nome del modello da utilizzare (ovvero la posizione per *screens/core/templates/location*) |
| ***`template {string}`*** | Titolo facoltativo da utilizzare per la pagina |
| ***`[./jcr:description] {string}`*** | Descrizione facoltativa da utilizzare per la pagina |

Il file del foglio di calcolo (CSV/XLS) richiede quindi le seguenti colonne:

* **percorso {string}** - Percorso per il percorso da importare, dove la radice del percorso è la cartella dei percorsi per il progetto (ovvero *`/foo`* è importato in *`/content/screens/<project>/locations/foo`*)
* **modello {string}** - Modello da utilizzare per la nuova posizione. Per il momento l&#39;unico valore consentito è &quot;posizione&quot;, ma questo valore viene esteso in futuro a tutti i modelli di Screens (`display`, `sequencechannel` e così via)
* **[./*] {string}** - Qualsiasi proprietà facoltativa da impostare nel percorso (ovvero `./jcr:title`, `./jcr:description`, `./foo, ./bar`). La versione corrente non consente alcun filtro.

>[!NOTE]
>
>Qualsiasi colonna che non soddisfa le condizioni di cui sopra viene ignorata. Ad esempio, se nel file del foglio (CSV/XLS) sono definite altre colonne diverse da **percorso**, **modello**, **titolo** e **descrizione**, tali campi verranno ignorati. **Importazione progetti** non convalida i campi aggiuntivi per l&#39;importazione del progetto nel progetto AEM Screens.

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

* Crea un progetto con titolo **DemoProjectImport**

* Utilizza un file CSV o Excel di esempio da importare.

A scopo dimostrativo, puoi scaricare un file excel dalla sezione seguente.

[Ottieni file](assets/minimal-file.xls)

### Importazione del file con i campi obbligatori minimi {#importing-the-file-with-minimum-required-fields}

Per importare un file in una cartella di percorso contenente i campi obbligatori minimi, attenersi alla procedura descritta di seguito.

>[!NOTE]
>
>L’esempio seguente mostra i quattro campi minimi necessari per importare il progetto:

![schermata_shot_2019-05-14alle21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Passa al progetto AEM Screens (**DemoProjectImport**).

   ![schermata_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Fare clic sul progetto,**&#x200B; DemoProjectImporter &#x200B;**>**&#x200B; Crea &#x200B;**>**&#x200B; posizioni di importazione** dalla barra laterale.

   ![schermata_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. Viene visualizzata la procedura guidata **Importa**. Fai clic sul file del progetto con le posizioni o sul file (***minimal-file.xls***) scaricato dalla sezione *Prerequisiti*.

   Dopo aver selezionato il file, fare clic su **Avanti**.

   ![schermata_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Verificare il contenuto del file (percorsi) dall&#39;Importazione guidata e fare clic su **Importa**.

   ![schermata_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Di conseguenza, ora puoi visualizzare tutte le posizioni importate nel progetto.

   ![schermata_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
