---
title: Sequenze incorporate
seo-title: Sequenze incorporate
description: Consulta questa pagina per conoscere le sequenze incorporate per i canali che consentono all'utente di aggiungere i componenti nel canale padre e di riutilizzare il contenuto proveniente da un canale diverso e incorporarlo nel canale padre.
seo-description: Consulta questa pagina per conoscere le sequenze incorporate per i canali che consentono all'utente di aggiungere i componenti nel canale padre e di riutilizzare il contenuto proveniente da un canale diverso e incorporarlo nel canale padre.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 41%

---


# Sequenze incorporate {#embedded-sequences}

L&#39;utilizzo di ***Sequenze incorporate*** per i canali consente all&#39;utente di aggiungere componenti nel canale principale e di riutilizzare il contenuto da un canale diverso e di incorporarlo nel canale principale.

## Aggiunta di sequenze incorporate {#adding-embedded-sequences}

È possibile aggiungere i seguenti componenti al canale della sequenza:

* Sequenza incorporata
* Sequenza incorporata dinamica

>[!NOTE]
>
>Per informazioni sull&#39;uso di altri componenti nel progetto Screens, consulta [Aggiunta di componenti a un canale](adding-components-to-a-channel.md).

### Aggiunta di una sequenza incorporata {#adding-an-embedded-sequence}

È possibile aggiungere una sequenza incorporata al canale. Una sequenza incorporata è un altro canale che include risorse come immagini o video. L&#39;aggiunta di una sequenza incorporata consente all&#39;utente di aggiungere la sequenza a un canale in base al ***Percorso del canale***.

>[!NOTE]
>***Percorso canale*** definisce un riferimento esplicito al canale.
>Per ulteriori informazioni sul *Percorso del canale*, consulta [Assegnazione canale](channel-assignment.md) in Screens di authoring.

Segui i passaggi sottostanti per aggiungere una sequenza incorporata al canale:

1. Seleziona il canale in cui incorporare una pagina. Ad esempio, **We.Retail In-Store** —> **Channels** —> **Idle Channel**.

1. Fare clic su **Modifica** nella barra delle azioni per aprire il canale in modalità editor.
1. Fai clic sull&#39;icona dei componenti nella barra laterale sinistra per aggiungere la pagina incorporata. Trascinare nell&#39;editor **Sequenza incorporata**.
1. Fate doppio clic sul componente **Sequenza incorporata** per aggiungere il canale al canale della sequenza originale.
1. Selezionare il **Percorso canale** del canale.
1. Selezionare la **Durata (ms)** per il canale incorporato nella scheda **Sequenza**. Per impostazione predefinita, la durata è impostata su **-1**, il che significa che il canale incorporato è completamente in esecuzione. Se l&#39;utente specifica una durata, la sottosequenza verrà interrotta all&#39;ora specificata.

1. Impostare la **Strategia di riproduzione controllata** su **normal**.

Per impostazione predefinita, è impostata su **normal**. Impostando il valore su **normal** (Riproduci tutti gli elementi) la sequenza padre verrà eseguita completamente su ogni ciclo della sequenza padre. L&#39;altro valore possibile è **Riproduci un elemento singolo** (Riproduci un elemento singolo) e visualizzi solo un elemento della sequenza successiva su ogni esecuzione (ad esempio, il primo elemento sul primo loop, il secondo elemento sul secondo ciclo e così via).

>[!IMPORTANT]
>
>È necessario assegnare il canale (utilizzato in sequenza incorporata) allo stesso display.
>
>Seguite i passaggi indicati di seguito dopo aver aggiunto una sequenza incorporata al canale dai passaggi precedenti:
>
>1. Individuare la visualizzazione e selezionarla dalla cartella **Locations**.
>1. Fate clic su **Dashboard** dalla barra delle azioni per passare al dashboard di visualizzazione.
>1. Selezionare **+ Assegna canali** da **CANALI ASSEGNATI &amp; PANNELLI PIANIFICATI** per aprire la finestra di dialogo **Assegnazione canale**.

   >
   >
1. Selezionare il percorso del canale che si trova (utilizzato nella sequenza incorporata) in **Percorso canale**.
>1. Assicurarsi che la **Priorità** sia inferiore al canale principale.

   >
   >
1. Non è necessario selezionare **Eventi supportati**.
>1. Fare clic su **Save** una volta completata.

>



L&#39;esempio seguente mostra l&#39;aggiunta di una sequenza incorporata (**Canale inattivo - notte**) a un canale già esistente (**Canale inattivo**).

![new2](assets/new2.gif)

### Aggiunta di una sequenza incorporata dinamica {#adding-a-dynamic-embedded-sequence}

È possibile aggiungere una sequenza incorporata dinamica al canale. Una sequenza incorporata dinamica è simile ad una sequenza incorporata, ma permette all&#39;utente di seguire una gerarchia in cui le modifiche o aggiornamenti apportati ad un canale vengono propagati ad un altro ad esso relazionato. Segue la gerarchia padre-figlio e include anche risorse come immagini o video. L&#39;aggiunta di una sequenza dinamica consente all&#39;utente di aggiungere un canale per ruolo.

>[!NOTE]
>
>Il ***Ruolo canale*** definisce il ruolo dei canali nel contesto della visualizzazione.
>
>Per ulteriori informazioni sul *Ruolo canale*, consulta [Assegnazione canale](channel-assignment.md) in Screens di authoring.

Segui i passaggi sottostanti per aggiungere una sequenza incorporata al canale:

1. Seleziona il canale in cui incorporare una sequenza dinamica. Ad esempio, **We.Retail In-Store** —> **Channels** —> **Idle Channel**.

1. Fare clic su **Modifica** nella barra delle azioni per aprire il canale in modalità editor.
1. Fai clic sull&#39;icona dei componenti nella barra laterale sinistra per aggiungere la sequenza incorporata dinamica. Trascinare nell&#39;editor **Dynamic** **Embedded Sequence**.

1. Fare doppio clic sul componente **Dynamic** **Sequenza incorporata** per aggiungere la pagina al canale della sequenza.

1. Inserire il ruolo di assegnazione del canale **Ruolo**.
1. Impostare la **Strategia di riproduzione controllata** su **normal**. Per impostazione predefinita, è impostata su **normal**. Impostando il valore su **normal** (Riproduci tutti gli elementi) la sequenza padre verrà eseguita completamente su ogni ciclo della sequenza padre. L&#39;altro valore possibile è **Riproduci un elemento singolo** (Riproduci un elemento singolo) e visualizzi solo un elemento della sequenza successiva su ogni esecuzione (ad esempio, il primo elemento sul primo loop, il secondo elemento sul secondo ciclo e così via).

1. Selezionare la **Durata (ms)** nella scheda **Sequenza** per il canale incorporato nella sequenza.

![last](assets/latest.gif)

