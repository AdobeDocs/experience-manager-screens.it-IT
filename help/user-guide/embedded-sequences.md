---
title: Sequenze incorporate
seo-title: Embedded Sequences
description: Segui questa pagina per scoprire le sequenze incorporate per i canali, le quali consentono all’utente di aggiungere componenti al canale principale e anche di riutilizzare i contenuti di un canale diverso e incorporarli nel canale principale.
seo-description: Follow this page to learn about embedded sequences for channels that allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 2%

---

# Sequenze incorporate {#embedded-sequences}

Utilizzo di ***Sequenze incorporate***, per i canali, consente all’utente di aggiungere componenti nel canale principale e anche di riutilizzare il contenuto da un canale diverso e incorporarlo nel canale principale.

## Aggiunta di sequenze incorporate {#adding-embedded-sequences}

È possibile aggiungere i seguenti componenti al canale della sequenza:

* Sequenza incorporata
* Sequenza incorporata dinamica

>[!NOTE]
>
>Per informazioni sull’utilizzo di altri componenti nel progetto Screens, consulta [Aggiunta di componenti a un canale](adding-components-to-a-channel.md).

### Aggiunta di una sequenza incorporata {#adding-an-embedded-sequence}

Puoi aggiungere una sequenza incorporata al tuo canale. Una sequenza incorporata è un altro canale che include risorse come immagini o video. L’aggiunta di una sequenza incorporata consente all’utente di aggiungere la sequenza a un canale ***Percorso canale***.

>[!NOTE]
>***Percorso canale*** definisce un riferimento esplicito al canale.
>Per ulteriori informazioni su *Percorso canale*, vedi [Assegnazione canale](channel-assignment.md) in Authoring Screens.

Per aggiungere una sequenza incorporata al canale, effettua le seguenti operazioni:

1. Seleziona il canale in cui desideri incorporare una pagina. Ad esempio: **In-store We.Retail** —> **Canali** —> **Canale inattivo**.

1. Clic **Modifica** dalla barra delle azioni per aprire il canale in modalità editor.
1. Fai clic sull’icona dei componenti nella barra laterale sinistra per aggiungere la pagina incorporata. Trascina la **Sequenza incorporata** all’editor.
1. Fai doppio clic su **Sequenza incorporata** per aggiungere il canale al canale della sequenza originale.
1. Seleziona la **Percorso canale** del canale.
1. Seleziona la **Durata (ms)** per il canale incorporato in **Sequenza** scheda. Per impostazione predefinita, la durata è impostata su **-1**, ciò significa che il canale incorporato è completamente in esecuzione. Se l’utente specifica una durata, la sottosequenza viene interrotta (ovvero, cut-off) all’ora specificata.

1. Imposta il **Strategia di riproduzione controllata** a **normale**.

Per impostazione predefinita, è impostato su **normale**. Impostazione del valore su **normale** (Riproduci tutti gli elementi) significa che la sottosequenza verrà eseguita completamente su ogni ciclo della sequenza principale. L’altro valore possibile è **Riproduci un singolo elemento** (Riproduci un singolo elemento) e che mostrasse un solo elemento della sottosequenza a ogni esecuzione (ad esempio, il primo elemento sul primo ciclo, il secondo elemento sul secondo ciclo e così via).

>[!IMPORTANT]
>
>È necessario assegnare il canale (utilizzato nella sequenza incorporata) alla stessa visualizzazione.
>
>Dopo aver aggiunto al canale una sequenza incorporata tra quelle precedenti, effettua le seguenti operazioni:
>
>1. Passa alla visualizzazione e selezionala da **Posizioni** cartella.
>1. Fai clic su **Dashboard** dalla barra delle azioni per passare al dashboard di visualizzazione.
>1. Seleziona **+ Assegna canali** dal **CANALI ASSEGNATI E PANNELLI PIANIFICATI** per aprire **Finestra di dialogo Assegnazione canale**.
>
>1. Seleziona il percorso del canale in cui (utilizzato nella sequenza incorporata) **Percorso canale**.
>1. Assicurati che il **Priorità** è inferiore al canale principale.
>
>1. Non selezionare alcuna **Eventi supportati**.
>1. Clic **Salva** una volta fatto.

>


L&#39;esempio seguente mostra l&#39;aggiunta di una sequenza incorporata (**Canale inattivo - Notte**) a un canale già esistente (**Canale inattivo**).

![new2](assets/new2.gif)

### Aggiunta di una sequenza dinamica incorporata {#adding-a-dynamic-embedded-sequence}

Puoi aggiungere una sequenza dinamica incorporata al canale. Una sequenza incorporata dinamica è simile a una sequenza incorporata, ma consente all’utente di seguire una gerarchia in cui le modifiche o gli aggiornamenti apportati a un canale vengono propagati a un altro in relazione. Segue la gerarchia genitore-figlio, ma include anche risorse come immagini e video. L’aggiunta di una sequenza dinamica consente all’utente di aggiungere un canale in base al ruolo del canale.

>[!NOTE]
>
>***Ruolo canale*** definisce il ruolo Canale definisce il contesto della visualizzazione.
>
>Per ulteriori informazioni su *Ruolo canale*, vedi [Assegnazione canale](channel-assignment.md) in Authoring Screens.

Per aggiungere una sequenza incorporata al canale, effettua le seguenti operazioni:

1. Selezionate il canale in cui desiderate incorporare una sequenza dinamica. Ad esempio: **In-store We.Retail** —> **Canali** —> **Canale inattivo**.

1. Clic **Modifica** dalla barra delle azioni per aprire il canale in modalità editor.
1. Fai clic sull’icona dei componenti nella barra laterale sinistra per aggiungere la sequenza dinamica incorporata. Trascina la **Dinamico** **Sequenza incorporata**  all’editor.

1. Fai doppio clic su **Dinamico** **Sequenza incorporata** per aggiungere la pagina al canale della sequenza.

1. Inserisci il **Ruolo assegnazione canale**.
1. Imposta il **Strategia di riproduzione controllata** a **normale**. Per impostazione predefinita, è impostato su **normale**. Impostazione del valore su **normale** (Riproduci tutti gli elementi) significa che la sottosequenza verrà eseguita completamente su ogni ciclo della sequenza principale. L’altro valore possibile è **Riproduci un singolo elemento** (Riproduci un singolo elemento) e che mostrasse un solo elemento della sottosequenza a ogni esecuzione (ad esempio, il primo elemento sul primo ciclo, il secondo elemento sul secondo ciclo e così via).

1. Seleziona la **Durata (ms)** in **Sequenza** per il canale incorporato nella sequenza.

![più recente](assets/latest.gif)
