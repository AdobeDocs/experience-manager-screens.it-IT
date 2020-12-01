---
title: Aggiunta di componenti a un canale
seo-title: Aggiunta di componenti a un canale
description: Segui questa pagina per ulteriori informazioni sull'aggiunta di componenti ai canali in un progetto di AEM Screens.
seo-description: Segui questa pagina per ulteriori informazioni sull'aggiunta di componenti ai canali in un progetto di AEM Screens.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 60%

---


# Aggiunta di componenti a un canale{#adding-components-to-a-channel}

I componenti sono gli elementi fondamentali dell&#39;esperienza di AEM (Adobe Experience Manager). Puoi utilizzare una serie di componenti e aggiungerla al canale in un progetto di AEM Screens.

## Componenti in AEM Screens {#components-in-aem-screens}

AEM Screens fornisce i vari componenti di AEM che possono essere utilizzati in un progetto Screens.

### Visualizzare i componenti AEM Screens  {#viewing-aem-screens-components}

Ogni volta che crei un progetto AEM Screens, viene visualizzato un elenco dei componenti standard che possono essere aggiunti al progetto.

Per visualizzare i componenti standard al progetto Screens, segui i seguenti passaggi:

1. Seleziona il canale. Ad esempio,**We.Retail in Store** --> **Canali** --> **Canale inattivo**.

1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor AEM.
1. Fai clic sull&#39;icona **+** nella barra laterale per aprire i componenti.
1. Vengono visualizzati tutti i componenti che sono inclusi per impostazione predefinita in un progetto AEM Screens, come mostrato nella figura qui sotto.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Aggiunta di un nuovo componente {#adding-a-new-component}

AEM offre una serie di altri componenti. È sempre possibile aggiungere altri componenti (non inclusi per impostazione predefinita) al progetto, purché compatibili con AEM Screens.

L&#39;esempio seguente mostra l&#39;aggiunta di un componente Livefyre a un progetto AEM Screens:

1. Seleziona il canale a cui desideri aggiungere un nuovo componente. Ad esempio,**We.Retail in Store** --> **Canali** --> **Canale inattivo**.

1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor.
1. Selezionare la modalità **Progettazione**.
1. Seleziona l&#39;intero editor di progettazione a destra e fai clic sul simbolo delle impostazioni per aprire la finestra di dialogo **Progettazione ParSys**.
1. Puoi selezionare i componenti che desideri importare nel tuo progetto AEM Screens. L&#39;esempio seguente mostra l&#39;aggiunta del componente **Livefyre** a un progetto AEM Screens .

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>Allo stesso modo, puoi aggiungere un numero qualunque di altri nuovi componenti compatibili con il progetto AEM Screens.

## Nozioni fondamentali sui componenti AEM Screens  {#understanding-aem-screen-components}

Nella sezione seguente sono illustrati i componenti AEM Screens  che è possibile utilizzare nel progetto.

>[!NOTE]
>
>Per visualizzare le proprietà di qualsiasi componente, seleziona il componente e fai clic sull&#39;icona a martello per aprire/visualizzare le proprietà.

### Applicazione  {#application}

Il componente **Applicazione** consente di aggiungere un&#39;applicazione al tuo canale.

Il componente Applicazione ha le seguenti proprietà:

| **Proprietà** | **Descrizione** |
|---|---|
| ***Percorso dell&#39;applicazione*** | Seleziona il percorso assoluto in cui si trova l&#39;applicazione. |
| ***Durata (ms)*** | Seleziona la durata dell&#39;applicazione. Per impostazione predefinita, la durata è impostata su -1, ossia l’elemento viene eseguito per sempre (applicazione a pagina singola). Con il valore durata impostato a >0, si mostra l&#39;elemento per la durata specificata e quindi si passa a quello successiva. |

L’esempio seguente mostra come incorporare un componente applicazione con l’anteprima delle relative proprietà:

![adding_components_application](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Fai riferimento all&#39;esempio precedente per visualizzare le proprietà di ogni componente qui sotto.

### Canale  {#channel}

Il componente **Canale** consente di aggiungere un intero canale al progetto.

Il componente Canale ha le seguenti proprietà:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong><em>Percorso del canale</em></strong></td>
   <td>Seleziona questo percorso assoluto in cui si trova l'applicazione.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durata (ms)</em></strong></td>
   <td>Seleziona l’intera durata del canale. Impostando la durata su -1, il canale incorporato viene eseguito per tutta la lunghezza in un particolare canale.</td>
  </tr>
 </tbody>
</table>

### Pagina incorporata {#embedded-page}

Una **Pagina incorporata** consente di aggiungere una pagina incorporata al progetto. Ad esempio, è possibile che si tratti di un&#39;applicazione web o un catalogo di prodotti.

La pagina incorporata ha le seguenti proprietà:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong><em>Pagina Percorso<br /> </em></strong></td>
   <td>Questo percorso assoluto in cui si trova il canale.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durata (ms)</em></strong></td>
   <td>Seleziona l’intera durata del canale. Impostando la durata su -1, il canale incorporato viene eseguito per tutta la lunghezza in un particolare canale.</td>
  </tr>
 </tbody>
</table>

### Sequenza incorporata {#embedded-sequence}

>[!NOTE]
>
>Per informazioni dettagliate sulle sequenze incorporate, consultare [Sequenze incorporate](embedded-sequences.md) nella sezione Creazione di schermate.

Una sequenza incorporata consente di aggiungere un canale per sequenza incorporato all&#39;interno di un canale esistente (con altre risorse).

La Sequenza incorporata ha le seguenti proprietà di pagina:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td>Percorso del canale</td>
   <td>Il percorso assoluto della sequenza che vuoi includere nel tuo canale.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durata (ms)</em></strong></td>
   <td>Seleziona l’intera durata del canale. Impostando la durata su -1, il canale incorporato viene eseguito per tutta la lunghezza in un particolare canale.</td>
  </tr>
  <tr>
   <td><strong><em>Strategia</em></strong></td>
   <td>Impostarla su <strong>originale</strong> o <strong>singolo</strong>. Se si imposta il valore su <strong>originale</strong>, la successiva verrà eseguita completamente su ogni ciclo della sequenza padre. L'altro valore possibile è <strong>single</strong> che mostrerebbe solo un elemento della sequenza successiva su ogni esecuzione (ad esempio, il primo elemento sul primo loop, il secondo elemento sul secondo ciclo e così via).</td>
  </tr>
 </tbody>
</table>

### Sequenza incorporata dinamica {#dynamic-embedded-sequence}

Una sequenza incorporata dinamica consente di aggiungere una sequenza simile a quella indicata più sopra, ad eccezione del ruolo di canale.

Per informazioni dettagliate sulle sequenze incorporate, consultare [Sequenze incorporate](embedded-sequences.md) nella sezione Creazione di schermate.

La sequenza dinamica incorporata ha le seguenti proprietà:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong><em>Ruolo assegnazione canale</em></strong><br /> </td>
   <td>Immetti il ruolo del canale.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durata (ms)</em></strong></td>
   <td>Seleziona l’intera durata del canale. Impostando la durata su -1, il canale incorporato viene eseguito per tutta la lunghezza in un particolare canale.</td>
  </tr>
  <tr>
   <td><strong><em>Strategia</em></strong></td>
   <td>Impostarla su <strong>originale</strong> o <strong>singolo</strong>. Se si imposta il valore su <strong>originale</strong>, la successiva verrà eseguita completamente su ogni ciclo della sequenza padre. L'altro valore possibile è <strong>single</strong> che mostrerebbe solo un elemento della sequenza successiva su ogni esecuzione (ad esempio, il primo elemento sul primo loop, il secondo elemento sul secondo ciclo e così via).</td>
  </tr>
 </tbody>
</table>

### Frammento esperienza {#experience-fragment}

Un frammento esperienza consente di aggiungere un frammento esperienza (gruppo di uno o più componenti, inclusi contenuti e layout a cui è possibile fare riferimento all&#39;interno delle pagine) al canale AEM Screens . Trascinate e rilasciate il componente per AEM editor e selezionate il frammento esperienza.

Per ulteriori informazioni su come creare un frammento esperienza e sfruttarlo in un progetto AEM Screens , consultare [Utilizzo di frammenti esperienza](experience-fragments-in-screens.md).

![exp](assets/exp.gif)

| **Proprietà** | **Descrizione** |
|---|---|
| **Frammento esperienza** |
| ***Frammento esperienza*** | Selezionare il frammento esperienza. |
| ***Durata*** | Selezionate l&#39;intera durata del frammento esperienza che viene riprodotto nel canale. |
| **Configurazione offline** |
| ***Librerie lato client*** | File JavaScript e CSS. |
| ***File statici*** | File statici che è possibile aggiungere come configurazioni offline al frammento esperienza. |

>[!NOTE]
>
>Le **librerie lato client** e i **file statici** aggiunti da questo componente saranno in aggiunta alle **librerie lato client** già configurate e ai file statici aggiunti dal frammento esperienza **Properties**.

### Immagine {#image}

Un&#39;immagine consente di aggiungere un&#39;immagine al tuo canale.

La risorsa immagine ha tre schede, ovvero **Immagine**, **Accessibilità** e **Sequenza**:

| **Proprietà** | **Descrizione** |
|---|---|
| **Immagine** |
| ***Risorsa immagine*** | Seleziona la risorsa immagine. |
| ***Titolo*** | Titolo dell&#39;immagine. |
| ***Collega a*** | Aggiungi un collegamento all&#39;immagine. |
| ***Descrizione*** | Breve descrizione dell&#39;immagine. |
| ***Dimensione*** | Dimensioni dell&#39;immagine. |
| **Accessibilità** |
| ***Testo alternativo*** | Testo alternativo all&#39;immagine. |
| **Sequenza** |
| ***Durata*** | Per impostazione predefinita, la durata è impostata su *8000 ms*. Per modificare la durata di riproduzione dell&#39;immagine, aggiornare il campo **Durata**. |

### Transizione {#transition}

Il componente Transizione consente di aggiungere una transizione al tuo progetto Screens.

L’immagine seguente mostra il componente di transizione (aggiunto mediante trascinamento) nell’editor.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Selezionate l&#39;icona della transizione e fate clic su **Configura** (icona chiave inglese) per aprire la finestra di dialogo **Transizione**. Questa finestra di dialogo include tre schede:

* **Transizione**
* **Sequenza**
* **Attivazione**

>[!NOTE]
>
>Per impostazione predefinita, la sequenza è impostata su 600 ms. È possibile aggiornare la sequenza di transizione ad altro valore utilizzando la scheda **Sequence**.

![transizione](assets/transition.gif)

Il componente Transizione ha le seguenti proprietà:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><strong>Transizione</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Tipo</em></strong></td>
   <td><p>Il tipo di transizione tra l'elemento prima e dopo. La transizione <strong>Type</strong> include le seguenti opzioni:</p>
    <ul>
     <li><strong>Normale</strong></li>
     <li><strong>Dissolvenza</strong></li>
     <li><strong>Scorri da destra</strong></li>
     <li><strong>Scorri da sinistra</strong></li>
     <li><strong>Scorri dall'alto</strong></li>
     <li><strong>Scorri dal basso</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Sequenza</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Durata</em></strong></td>
   <td>Seleziona l'intera durata della transizione. Per impostazione predefinita, è impostata su 600 ms.</td>
  </tr>
  <tr>
   <td><strong>Attivazione</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Attivo da</em></strong></td>
   <td>Timestamp che descrive da quando la transizione può essere attiva.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Attivo fino a</em></strong></td>
   <td>Timestamp che descrive fino a quando la transizione può essere attiva.</td>
  </tr>
  <tr>
   <td><strong><em>Pianificazione</em></strong></td>
   <td>Aggiungere una pianificazione predefinita.</td>
  </tr>
 </tbody>
</table>

### Video {#video}

Il componente Video consente di aggiungere un video al tuo progetto Screens.

Il componente Video ha le seguenti proprietà:

<table>
 <tbody>
  <tr>
   <td><strong>Proprietà</strong></td>
   <td><strong>Descrizione</strong></td>
  </tr>
  <tr>
   <td><em><strong>Risorsa video</strong></em></td>
   <td>Seleziona il collegamento al video.</td>
  </tr>
  <tr>
   <td><em><strong>Durata</strong></em></td>
   <td>Seleziona la durata del video. Per impostazione predefinita, la durata è impostata su -1, ossia l’elemento viene eseguito per sempre. Con il valore durata impostato a &gt;0, si mostra l'elemento per la durata specificata e quindi si passa a quello successiva.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>Rendering</strong></em></td>
   <td><p>Se la proporzione del video non è adatta allo schermo, puoi regolare il rendering su <strong>Contain</strong> (Contiene) o <strong>Cover</strong> (Copri).</p> <p><em>Contain</em> (Contieni) significa che viene visualizzato il video completo e che le aree mancanti vengono riempite con un bordo nero.</p> <p><em>Cover</em> (Copri) significa che il video copre l'intero campo, ma alcune parti che si estendono ai lati sono nascoste.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Dimensione</strong></em></td>
   <td>Dimensioni del video.</td>
  </tr>
 </tbody>
</table>

