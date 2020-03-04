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
source-git-commit: 23ecaf3533c2298d98c37f2bbcb6cbe50aed17fc

---


# Sequenze incorporate {#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

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
>
>***Percorso*** canale definisce un riferimento esplicito al canale.
>
>Per ulteriori informazioni sul *Percorso del canale*, consulta [Assegnazione canale](channel-assignment.md) in Screens di authoring.

Segui i passaggi sottostanti per aggiungere una sequenza incorporata al canale:

1. Seleziona il canale in cui incorporare una pagina. For example, **We.Retail In-Store** --> **Channels** --> **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Fai clic sull&#39;icona dei componenti nella barra laterale sinistra per aggiungere la pagina incorporata. Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. Select the **Channel Path** of the channel.
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. Se l&#39;utente specifica una durata, la sottosequenza verrà interrotta all&#39;ora specificata.

1. Impostate la strategia **di riproduzione** controllata su **normale**.

By default, it is set to **normal**. Setting the value to **normal** (Play all items) means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item** (Play a single item) and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

>[!Iimportante]
>È necessario assegnare il canale (utilizzato in sequenza incorporata) allo stesso display.
>
>Seguite i passaggi indicati di seguito dopo aver aggiunto una sequenza incorporata al canale dai passaggi precedenti:
>
>1. Passate alla visualizzazione e selezionatela dalla cartella **Posizioni** .
>1. Fate clic su **Dashboard** dalla barra delle azioni per passare alla dashboard di visualizzazione.
>1. Selezionate **+ Assegna canali** dai **CANALI ASSEGNATI e PANNELLI** PIANIFICATI per aprire la finestra di dialogo **Assegnazione** canale.
   >
   >
1. Selezionate il percorso del canale che avete (utilizzato nella sequenza incorporata) in Percorso **** canale.
>1. Assicurarsi che la **Priorità** sia inferiore al canale principale.
   >
   >
1. Non è possibile selezionare eventi **** supportati.
>1. Al termine, fate clic su **Salva** .
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

1. Seleziona il canale in cui incorporare una sequenza dinamica. For example, **We.Retail In-Store** --> **Channels** --> **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Fai clic sull&#39;icona dei componenti nella barra laterale sinistra per aggiungere la sequenza incorporata dinamica. Trascinare e **rilasciare nell&#39;editor la sequenza dinamica** **Embedded Sequenza **incorporata.

1. Double-click the **Dynamic** **Embedded Sequence** component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. Impostate la strategia **di riproduzione** controllata su **normale**. By default, it is set to **normal**. Setting the value to **normal** (Play all items) means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item** (Play a single item) and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![last](assets/latest.gif)

