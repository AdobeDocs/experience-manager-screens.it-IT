---
title: Assegnazione dei canali
seo-title: Assegnazione dei canali
description: Segui questa pagina per maggiori informazioni sull'assegnazione dei canali e il dayparting.
seo-description: Segui questa pagina per maggiori informazioni sull'assegnazione dei canali e il dayparting.
uuid: fe429485-dcc9-4507-864c-b04393cedeee
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 212adcd1-835b-453d-9d3e-775366abf181
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Assegnazione dei canali {#channel-assignment}

Questa sezione illustra i seguenti argomenti:

* **Assegnazione di un canale**
* **Informazioni sulle proprietà dell'assegnazione del canale, finestra di dialogo**
* **Dayparting**

Una volta definita una visualizzazione, è necessario assegnarle un canale.

Questa pagina mostra come assegnare i canali alle visualizzazioni.

**Prerequisiti**:

* [Configurazione e distribuzione di Screens](configuring-screens-introduction.md)
* [Creare e gestire il progetto Screens](creating-a-screens-project.md)
* [Creare e gestire canali](managing-channels.md)
* [Creare e gestire le posizioni](managing-locations.md)
* [Creare e gestire le visualizzazioni](managing-displays.md)

## Assegnazione di un canale {#assign-a-channel}

Segui la procedura seguente per assegnare un canale a una visualizzazione:

1. Passare alla visualizzazione desiderata, ad esempio **DemoProject*** *—&gt; **Locations** —&gt; **SanJose** —&gt; **StoreDisplay**.

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. Toccate/fate clic **Assegna canale **nella barra delle azioni

   Oppure,

   Tap/click **Dashboard **and** **click** +Assign Channel **from the** ASSIGNED CHANNNELS **panel to open the **Channel Assignment** dialog box.

   ![screen_shot_2018-08-23at25938pm](assets/screen_shot_2018-08-23at25938pm.png)

   È possibile configurare le seguenti proprietà dalla finestra di dialogo **Assegnazione canale **s:

   **Ruolo canale**:

   Il ruolo canale definisce il contesto della visualizzazione. Il ruolo è mirato da diverse azioni ed è indipendente dal canale effettivo che svolge il ruolo.

   **Riferimento a canale**:

   il riferimento a canale consente di fornire un riferimento al canale desiderato, per nome o in base al percorso del canale.

   * **In base al percorso**: fornisci un riferimento esplicito usando il percorso assoluto del canale.
   * **per nome**: Immettere il nome del canale che verrà risolto in un canale effettivo per contesto. Questa funzione consente di creare la versione locale di un canale, per determinare dinamicamente i contenuti in base alla posizione. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.
   **Priorità:**

   La priorità viene usata per ordinare le assegnazioni nel caso in cui più utenti corrispondano ai criteri di riproduzione. Quella con il valore più alto avrà sempre la precedenza su quella con i valori più bassi. Ad esempio, se ci sono due canali A e B, A ha una priorità di 1 e B ha una priorità di 2, viene quindi visualizzato il canale B, che ha una priorità maggiore di A.

   La priorità per un canale è impostata come numero (1 per un valore minimo) nella finestra di dialogo **Channel Assignment **come indicato sopra. Inoltre, i canali assegnati vengono ordinati in base a una priorità decrescente.

   **Eventi supportati**:

   * **Caricamento iniziale**: carica il canale quando il lettore viene avviato. Può essere assegnato a più canali in combinazione con la pianificazione
   * **Schermata di inattività**: il canale viene caricato quando la schermata è inattiva. Può essere assegnato a più canali in combinazione con la pianificazione
   * **Timer:** deve essere impostato quando viene fornita una pianificazione
   * **Interazione utente**: il lettore passa al canale specificato, se c'è un'interazione utente sullo schermo (un tocco) in un canale inattivo; il canale viene caricato quando lo schermo viene toccato.
   **Pianificazione**:

   la pianificazione consente di inserire una descrizione testuale circa quando il canale deve essere visualizzato. Inoltre, permette di definire una data iniziale (**attivo da**) e una data finale (**attivo fino al**) per il canale da visualizzare. La sintassi per l'espressione di pianificazione si basa sulle sintassi dei testo e cron di later.js:

   * [https://bunkat.github.io/later/parsers.html#text](https://bunkat.github.io/later/parsers.html#text) 
   * [https://bunkat.github.io/later/parsers.html#cron](https://bunkat.github.io/later/parsers.html#cron) 
   **Mostra descrizione luogo di interesse**:

   Mostra descrizione luogo di interesse definisce se la descrizione del luogo di interesse ("*Tocca un punto qualsiasi per iniziare*") deve essere visualizzato o meno mentre il canale è in esecuzione.

1. Fai clic su **Salva** per assegnare il canale creato a una visualizzazione.

### Dayparting {#dayparting}

Schedules when when combined with **Dayparting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

DayParting si riferisce alla suddivisione di un giorno in fasce orarie e alla specificazione del contenuto riprodotto all'ora desiderata. AEM Screens consente di pianificare i canali in termini di dayparting entro un giorno, una settimana o un mese, a seconda delle esigenze.

Gli esempi che seguono spiegano il dayparting dei canali in tre diversi scenari:

#### Riproduzione di contenuto su un singolo giorno suddiviso in più fasce orarie {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio indica come un ristorante usa il dayparting per mostrare il suo menù per colazione, pranzo e cena.

Qui, divideremo ogni giorno in tre fasce orarie diverse, in modo che il contenuto del canale venga riprodotto secondo l'ora specificata del giorno:

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| Menu_A | Colazione |  | dopo le 6:00 e prima delle 11:00 |
| Menu_B | Pranzo |  | dopo le 11:00 e prima delle 15:00 |
| Menu_C | Cena |  | dopo le 15:00 e prima delle 20:00 |

#### Riproduzione di contenuto in un particolare giorno della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra il dayparting in un casinò in cui l'evento live ha luogo ogni fine settimana dalle 20:00 alle 22:00 e le offerte speciali sono disponibili per il menù serale dalle 22:00 fino all'1:00.

<table>
 <tbody>
  <tr>
   <td><strong>Canale</strong></td>
   <td><strong>Ruolo</strong></td>
   <td><strong>Priorità</strong></td>
   <td><strong>Pianificazione</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>Fine settimana</td>
   <td> </td>
   <td>21 ottobre 2017 - 22 ottobre 2017 <br /> dopo le 20:00 prima delle 22:00</td>
  </tr>
  <tr>
   <td>SpecialsDinner</td>
   <td>Fine settimana</td>
   <td> </td>
   <td>21 ottobre 2017 - 22 ottobre 2017 <br /> dopo le 22:00 prima dell'1:00</td>
  </tr>
 </tbody>
</table>

#### Riproduzione di contenuto per un mese/mesi particolare/i {#playing-content-for-a-particular-month-months}

Questo esempio mostra il dayparting per un negozio che espone la propria collezione estate da giugno ad agosto e la collezione autunnale da settembre a fine ottobre.

Qui puoi creare il dayparting secondo i mesi, in modo che il contenuto del canale venga riprodotto secondo i mesi dell'anno specificati.

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| SummerCollection | Estate |  | 01 giugno 2017 - 31 agosto 2017 |
| FallCollection | Autunno |  | 01 settembre 2017 - 30 ottobre 2017 |

>[!NOTE]
>
>Inoltre, puoi definire la ***Priorità**per ciascuno dei canali.* Ad esempio, se due canali sono impostati per lo stesso giorno e la stessa ora o per lo stesso mese, il canale con priorità più alta viene riprodotto per primo. Il valore minimo per la priorità può essere impostato su 0.

#### Riproduzione di contenuto per i canali con la stessa priorità {#playing-content-for-channels-with-same-priority}

Questo esempio mostra il dayparting per un negozio che espone la propria collezione inverno con la stessa pianificazione nel mese di dicembre. Ma poiché il canale B ha la priorità impostata su 2, durante quella settimana il canale B riproduce il suo contenuto piuttosto che il canale A.

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| A | Inverno | 1 | 01 dicembre 2017 - 31 dicembre 2017 |
| B | Natale | 2 | 24 dicembre 2017 - 31 dicembre 2017 |

