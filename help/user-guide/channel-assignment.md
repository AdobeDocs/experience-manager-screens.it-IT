---
title: Assegnazione canale
description: Scopri Assegnazione canale e ripartizione giornaliera.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 2%

---

# Assegnazione canale {#channel-assignment}

>[!IMPORTANT]
>Questa sezione evidenzia l’assegnazione dei canali e la pianificazione dei canali per Feature Pack precedenti alla versione di Screens di AEM 6.5.5.

Dopo aver configurato una visualizzazione, devi assegnare un canale a una visualizzazione per visualizzarne il contenuto.

Questa pagina mostra come assegnare un canale alla visualizzazione.

>[!NOTE]
>È possibile assegnare più canali a una visualizzazione.

## Assegnazione di un canale {#assign-a-channel}

Per assegnare un canale a una visualizzazione, segui i passaggi seguenti:

1. Passa alla visualizzazione desiderata, ad esempio: **DemoProject** > **Posizioni** > **SanJose** > **StoreDisplay**.

   ![immagine](assets/screen_shot_2018-08-23at25359pm.png)

1. Seleziona **Assegna canale** nella barra delle azioni.

   oppure

   Seleziona **Dashboard** e seleziona **+Assegna canale** dal **CANALI ASSEGNATI** per aprire il **Assegnazione canale** .

   ![immagine](/help/user-guide/assets/channel-assign1.png)

   Puoi configurare le proprietà da **Assegnazione canale** dalla sezione seguente. Fai riferimento a [Proprietà canale](#channel-properties) per ulteriori informazioni sulle proprietà del canale.

## Informazioni sulle proprietà del canale da Assegnazione canale {#channel-properties}

### Canale di riferimento {#ref-channel}

Canale di riferimento consente di fornire un riferimento al canale desiderato, in base al nome del canale o al percorso del canale.

* **per percorso** : fornisci un riferimento esplicito utilizzando il percorso assoluto del canale.

* **per nome** - Immetti il nome del canale che viene risolto in un canale effettivo per contesto. Questa funzione consente di creare una versione locale di un canale per risolvere in modo dinamico il contenuto specifico della posizione. Ad esempio, un canale con nome *offerte del giorno*, in cui il contenuto effettivo sarebbe diverso in due città, ma si dispone comunque del ruolo di canale sano su tutti gli schermi.

### Ruolo canale {#role-channel}

Il ruolo del canale definisce il contesto della visualizzazione. Il ruolo è oggetto di varie azioni ed è indipendente dal canale effettivo che lo svolge.

### Priorità {#priority-channel}

La priorità viene utilizzata per ordinare le assegnazioni nel caso in cui più corrispondano ai criteri di riproduzione. Quello con il valore più alto ha sempre la precedenza sui valori più bassi. Ad esempio, se sono presenti due canali A e B. A ha una priorità di 1 e B ha una priorità di 2, quindi viene visualizzato il canale B, in quanto ha una priorità più alta di A.

>[!NOTE]
>La priorità per un canale è impostata come numero (1 per il minimo) nel **Assegnazione canale** come indicato in precedenza. Inoltre, i canali assegnati vengono ordinati in base alla priorità decrescente.

### Eventi supportati {#supported-events-channel}

* **Caricamento iniziale** - Carica il canale all&#39;avvio del lettore. Può essere assegnato a più canali con una pianificazione.
* **Schermata di inattività** : viene caricato quando lo schermo è inattivo. Può essere assegnato a più canali con una pianificazione.
* **Timer** - Deve essere impostato quando viene fornita una pianificazione.
* **Interazione utente** - Il lettore passa al canale specificato in caso di interazione dell&#39;utente sullo schermo (contatto) in un canale inattivo e si carica quando lo schermo viene toccato.

### Metodo di interruzione {#interruption-method-channel}

>[!IMPORTANT]
>
> Questa opzione è disponibile solo con <!--AEM 6.4 Feature Pack 8 or -->Feature Pack 4 per AEM 6.5.

In qualità di autore di contenuti, specifica quando un canale viene interrotto in modo da poter scegliere di tagliare i contenuti non critici, ma facoltativamente lascia che vengano riprodotti contenuti importanti prima di interromperne la riproduzione a causa della pianificazione.

Selezionare una delle seguenti opzioni disponibili per impostare il metodo di interruzione dal menu **Assegnazione canale** finestra di dialogo:

* **Immediatamente** - Ogni volta che si attiva la programmazione o si riceve un aggiornamento, è possibile interrompere la riproduzione e aggiornare immediatamente o riprodurre il nuovo contenuto.
* **Alla fine dell&#39;elemento corrente** - Quando si attiva una nuova programmazione o si riceve un aggiornamento, è possibile attendere che l&#39;elemento corrente della sequenza finisca la riproduzione. Solo in seguito è possibile aggiornare o riprodurre il nuovo contenuto.

  >[!NOTE]
  >Questa opzione è selezionata per impostazione predefinita.
* **Alla fine della sequenza** - Quando si attiva una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere che l’intera sequenza raggiunga la fine. Quindi, immediatamente prima della sequenza desiderata, puoi tornare al primo elemento, aggiornare o riprodurre il nuovo contenuto.

  >[!NOTE]
  >Se si utilizza la seconda o la terza opzione, gli orari di programmazione definiti nell&#39;assegnazione potrebbero subire un leggero differimento. Il motivo è che il lettore attende la fine dell’elemento o della sequenza (dopo l’ora specificata) prima di eseguire l’aggiornamento. Il ritardo dipende dalla durata di riproduzione dell’elemento.

### Pianificazione {#schedule-channel}

Pianifica consente di fornire una descrizione testuale di quando deve apparire il canale. Consente inoltre di definire una data di inizio (**attivo da**) e una data di fine (**attivo fino a**) per il canale da visualizzare.

**Mostra descrizione attrazione**

Mostra descrizione comando attrazione definisce se la descrizione comando attrazione (&quot;*Toccare ovunque per iniziare*&quot;) deve essere visualizzato o meno mentre il canale è in esecuzione.

### DayParting {#dayparting}

Schedules quando combinati con **DayParting**, consente di impostare una pianificazione globale con più canali in esecuzione in orari specifici del giorno e di riutilizzare tale configurazione per tutti gli schermi contemporaneamente.

DayParting si riferisce alla suddivisione di un giorno in intervalli di tempo e alla specifica del contenuto riprodotto all’ora desiderata. AEM Screens consente di pianificare i canali in termini di DayPparting entro un giorno, una settimana o un mese in base al requisito.

Gli esempi seguenti illustrano la suddivisione giornaliera nei canali in tre diversi scenari:

#### Riproduzione di contenuti in un singolo giorno suddiviso in più slot temporali {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio mostra come un ristorante utilizza DayParting per mostrare il menu per la colazione, il pranzo e la cena.

In questo caso, puoi dividere ogni giorno in tre diversi intervalli di tempo in modo che il contenuto del canale venga riprodotto nell’ora specificata del giorno:

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| Menu_A | Colazione |  | Dopo le 6:00 e prima delle 11:00 |
| Menu_B | Pranzo |  | Dopo le 11:00 e prima delle 15:00 |
| Menu_C | Cena |  | Dopo le 15:00 e prima delle 20:00 |

#### Riproduzione di contenuti in un giorno specifico della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra il dayParting ottenuto in un casinò in cui si verifica un evento live ogni fine settimana dalle 20:00 alle 22:00 e i menu per la cena sono disponibili dopo le 22:00 fino all’1:00.

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
   <td>Programmi specialiCena</td>
   <td>Fine settimana</td>
   <td> </td>
   <td>21 ottobre 2017 - 22 ottobre 2017 <br /> dopo le 22:00 prima dell’1:00</td>
  </tr>
 </tbody>
</table>

#### Riproduzione di contenuti per un mese/mesi particolare {#playing-content-for-a-particular-month-months}

Questo esempio mostra DayParting per un negozio che visualizza la raccolta estiva dai mesi di giugno ad agosto e la raccolta autunnale da settembre a fine ottobre.

In questo caso, puoi creare DayParting al mese, in modo che il contenuto del canale venga riprodotto in base ai mesi specificati dell’anno.

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| CollezioneEstate | Estate |  | 1 giugno 2017 - 31 agosto 2017 |
| FallCollection | Autunno |  | 1 settembre 2017 - 30 ottobre 2017 |

>[!NOTE]
>
>Inoltre, puoi definire ***Priorità*** per ciascuno dei canali. Ad esempio, se due canali sono impostati per lo stesso giorno e ora o per lo stesso mese, viene riprodotto prima il canale con priorità più elevata. Il valore minimo di priorità può essere impostato su 0.

#### Riproduzione di contenuti per canali con la stessa priorità {#playing-content-for-channels-with-same-priority}

Questo esempio mostra il DayParting per un negozio che visualizza la raccolta invernale con la stessa pianificazione nel mese di dicembre. Ma poiché il canale B ha priorità impostata su 2, durante quella settimana; il canale B riproduce il suo contenuto invece del canale A.

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| A | Inverno | 1 | 1 dicembre 2017 - 31 dicembre 2017 |
| B | Natale | 2 | 24 dicembre 2017 - 31 dicembre 2017 |


>[!NOTE]
>
> Per ulteriori informazioni su DayParting, fare riferimento alle sezioni seguenti:
>
>* [Gestione della ricorrenza nelle risorse](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [Gestione della ricorrenza per le risorse in un canale](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
