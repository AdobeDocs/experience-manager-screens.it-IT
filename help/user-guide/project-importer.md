---
title: Nuova importazione progetti da file
seo-title: New Project Importer from File
description: Questa funzionalità consente di importare in blocco un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.
seo-description: This functionality allows you to bulk-import a set of locations from a CSV/XLS spreadsheet to your AEM Screens project.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 2%

---

# Nuova importazione progetti da file {#new-project-importer-from-file}

Questa sezione descrive una funzionalità per importare in blocco un set di posizioni da un foglio di calcolo CSV/XLS al progetto AEM Screens.

## Introduzione {#introduction}

Quando imposti un progetto AEM Screens, per la prima volta nella tua organizzazione devi creare anche tutte le posizioni. Se il progetto coinvolge un numero elevato di posizioni, si traduce in un’attività noiosa che comporta molti clic e attese nell’interfaccia utente.

L’obiettivo di questa funzione è ridurre il tempo necessario per configurare il progetto e risolvere quindi i problemi di budget.

Consentendo all&#39;autore di fornire un foglio di calcolo come file di input e consentendo al sistema di creare automaticamente la struttura di posizioni nel back-end, questa funzione:

* *offre prestazioni migliori rispetto al clic manuale nell’interfaccia utente*
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
| ***percorso {string*}** | Percorso della risorsa per la posizione |
| ***[./jcr:titolo] {string*}** | Nome del modello da utilizzare, ovvero posizione *screens/core/templates/location*) |
| ***modello {string}*** | Titolo facoltativo da utilizzare per la pagina |
| ***[./jcr:descrizione] {string}*** | Descrizione facoltativa da utilizzare per la pagina |

Il file del foglio di calcolo (CSV/XLS) richiede pertanto le seguenti colonne:

* **percorso {string}** Percorso del percorso da importare, dove la directory principale del percorso è la cartella dei percorsi del progetto (ovvero */foo* verrà importato in */content/screens/&lt;project>/locations/foo*)

* **modello {string}** Modello da utilizzare per la nuova posizione; per ora l’unico valore consentito è &quot;posizione&quot;, ma questo verrà esteso in futuro a tutti i modelli Screens (&quot;visualizzazione&quot;, &quot;sequencechannel&quot; e così via)
* **[./*] {string}** Qualsiasi proprietà facoltativa da impostare sulla posizione (ovvero, ./jcr:title, ./jcr:descrizione, ./foo, ./barra). Al momento la versione corrente non consente alcun filtro

>[!NOTE]
>
>Qualsiasi colonna che non corrisponde alle condizioni precedenti verrà semplicemente ignorata. Ad esempio, se nel foglio (CSV/XLS) è definita un’altra colonna diversa da **percorso**,**modello**,**titolo**, e **descrizione** nel file, tali campi verranno ignorati e **Importazione progetti** non convalida i campi aggiuntivi per importare il progetto nel progetto AEM Screens.

## Utilizzo di Importazione progetti {#using-project-importer}

La sezione seguente descrive come viene utilizzata l’Importazione progetti in un progetto AEM Screens.

>[!CAUTION]
>
>Limiti:
>
>* I file diversi dalle estensioni CSV/XLS/XLSX non sono supportati nella versione corrente.
>* Non esiste alcun filtro delle proprietà per i file importati e nulla che inizi con &quot;./&quot; verrà importato.
>


### Prerequisiti {#prerequisites}

* Crea un nuovo progetto denominato **ImportazioneProgettoDemo**

* Utilizza un file CSV o excel di esempio da importare.

A scopo dimostrativo, puoi scaricare un file excel dalla sezione seguente.

[Ottieni file](assets/minimal-file.xls)

### Importazione del file con i campi obbligatori minimi {#importing-the-file-with-minimum-required-fields}

Per importare un file nella cartella dei percorsi contenente i campi obbligatori minimi, effettua le seguenti operazioni:

>[!NOTE]
>
>L’esempio seguente mostra i quattro campi minimi necessari per importare il progetto:

![screen_shot_2019-05-14alle21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Passa al progetto AEM Screens (**ImportazioneProgettoDemo**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Selezionare il progetto,** DemoProjectImporter **—>** Crea **—>** Importa posizioni** dalla barra laterale.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. Il **Importa** apertura guidata. Selezionare il file disponibile per il progetto con le posizioni oppure selezionare il file (***minimal-file.xls***) scaricato da *Prerequisiti* sezione.

   Dopo aver selezionato il file, fai clic su **Successivo**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Verifica il contenuto del file (percorsi) dall’Importazione guidata e fai clic su **Importa**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Di conseguenza, ora potrai visualizzare tutte le posizioni importate nel progetto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
