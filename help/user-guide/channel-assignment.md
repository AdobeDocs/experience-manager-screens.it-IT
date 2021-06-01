---
title: Assegnazione dei canali
seo-title: Assegnazione dei canali
description: Segui questa pagina per informazioni sull'assegnazione dei canali e la suddivisione dei giorni.
feature: Screens di authoring, Assegnazione canale
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1219'
ht-degree: 41%

---


# Assegnazione dei canali {#channel-assignment}

>[!IMPORTANT]
>Questa sezione evidenzia l’assegnazione e la pianificazione dei canali per i Feature Pack precedenti alla versione 6.5.5 Screens AEM.

Una volta impostata una visualizzazione, è necessario assegnare un canale a una visualizzazione per visualizzare il contenuto.

Questa pagina mostra l’assegnazione di un canale alla visualizzazione.

>[!NOTE]
>È possibile assegnare più canali a una visualizzazione.

## Assegnazione di un canale {#assign-a-channel}

Segui la procedura seguente per assegnare un canale a una visualizzazione:

1. Passa alla visualizzazione richiesta, ad esempio **DemoProject** —> **Posizioni** —> **SanJose** —> **StoreDisplay**.

   ![immagine](assets/screen_shot_2018-08-23at25359pm.png)

1. Tocca o fai clic su **Assegna canale** nella barra delle azioni

   Oppure,

   Tocca/fai clic su **Dashboard** e fai clic su **+Assegna canale** dal pannello **CANALI ASSEGNATI** per aprire la finestra di dialogo **Assegnazione canale** .

   ![immagine](/help/user-guide/assets/channel-assign1.png)

   Puoi configurare le proprietà dalla finestra di dialogo **Assegnazione canale** nella sezione seguente. Per ulteriori informazioni sulle proprietà del canale, consulta la sezione [Proprietà canale](#channel-properties) .


## Informazioni sulle proprietà del canale dall&#39;assegnazione del canale {#channel-properties}

### Riferimento a canale {#ref-channel}

il riferimento a canale consente di fornire un riferimento al canale desiderato, per nome o in base al percorso del canale.

* **In base al percorso**: fornisci un riferimento esplicito usando il percorso assoluto del canale.

* **per nome**: Immetti il nome del canale che verrà risolto in un canale effettivo per contesto. Questa funzione consente di creare la versione locale di un canale, per determinare dinamicamente i contenuti in base alla posizione. Ad esempio, un canale con nome *offerte del giorno*, in cui il contenuto effettivo sarebbe diverso in due città, ma si dispone comunque dello stesso ruolo di canale su tutte le visualizzazioni.

### Ruolo canale {#role-channel}

Il ruolo canale definisce il contesto della visualizzazione. Il ruolo è mirato da varie azioni ed è indipendente dal canale effettivo che svolge il ruolo.

### Priorità {#priority-channel}

La priorità viene usata per ordinare le assegnazioni nel caso in cui più utenti corrispondano ai criteri di riproduzione. Quella con il valore più alto avrà sempre la precedenza su quella con i valori più bassi. Ad esempio, se ci sono due canali A e B, A ha una priorità di 1 e B ha una priorità di 2, viene quindi visualizzato il canale B, che ha una priorità maggiore di A.

>[!NOTE]
>La priorità per un canale è impostata come numero (1 corrisponde alla priorità minima) nella finestra di dialogo **Assegnazione canale**, come detto sopra. Inoltre, i canali assegnati vengono ordinati in base a una priorità decrescente.

### Eventi supportati {#supported-events-channel}

* **Caricamento iniziale**: carica il canale quando il lettore viene avviato. Può essere assegnato a più canali in combinazione con la pianificazione
* **Schermata di inattività**: il canale viene caricato quando la schermata è inattiva. Può essere assegnato a più canali in combinazione con la pianificazione
* **Timer:** deve essere impostato quando viene fornita una pianificazione
* **Interazione utente**: il lettore passa al canale specificato, se c&#39;è un&#39;interazione utente sullo schermo (un tocco) in un canale inattivo; il canale viene caricato quando lo schermo viene toccato.

### Metodo di interruzione {#interruption-method-channel}

>[!IMPORTANT]
>
> Questa opzione è disponibile solo con AEM 6.4 Feature Pack 8 o AEM 6.5 Feature Pack 4.

In qualità di autore dei contenuti, è necessario essere in grado di specificare quando un canale viene interrotto in modo da poter scegliere di interrompere i contenuti non critici, ma avere la possibilità di consentire la riproduzione completa di contenuti importanti prima di interrompere la riproduzione a causa della programmazione.

Selezionare una delle seguenti opzioni disponibili per impostare il metodo di interruzione dalla finestra di dialogo **Assegnazione canale**:

* **Immediatamente**: ogni volta che la pianificazione si attiva o viene ricevuto un aggiornamento, è possibile interrompere la riproduzione e aggiornare immediatamente o riprodurre il nuovo contenuto
* **Alla fine dell&#39;elemento** corrente: quando viene attivata una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere che l&#39;elemento corrente nella sequenza finisca la riproduzione e solo dopo aver aggiornato o riprodotto il nuovo contenuto
   >[!NOTE]
   >Per impostazione predefinita, questa opzione è selezionata.
* **Alla fine della sequenza**: quando viene attivata una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere che l&#39;intera sequenza raggiunga la fine e, poco prima della sequenza desiderata, tornare al primo elemento, aggiornare o riprodurre il nuovo contenuto

   >[!NOTE]
   >L&#39;utilizzo della seconda o della terza opzione può comportare un lieve differimento dei tempi di programmazione definiti sull&#39;assegnazione, in quanto il lettore attenderà la fine dell&#39;elemento o della sequenza (dopo il tempo specificato) prima dell&#39;aggiornamento. Il ritardo dipende dalla durata di riproduzione dell’elemento.

### Pianificazione {#schedule-channel}

la pianificazione consente di inserire una descrizione testuale circa quando il canale deve essere visualizzato. Inoltre, permette di definire una data iniziale (**attivo da**) e una data finale (**attivo fino al**) per il canale da visualizzare.

**Mostra descrizione luogo di interesse**:

Mostra descrizione luogo di interesse definisce se la descrizione del luogo di interesse (&quot;*Tocca un punto qualsiasi per iniziare*&quot;) deve essere visualizzato o meno mentre il canale è in esecuzione.

### DayParting {#dayparting}

Le pianificazioni, se combinate con **DayParting**, consentono di impostare una pianificazione globale con più canali in esecuzione in momenti specifici della giornata e di riutilizzare tale impostazione per tutti i display contemporaneamente.

DayParting si riferisce alla suddivisione di un giorno in fasce orarie e alla specificazione del contenuto riprodotto all&#39;ora desiderata. AEM Screens ti consente di pianificare i canali in termini di ripartizione giornaliera entro un giorno, una settimana o un mese, in base alle esigenze.

Gli esempi seguenti spiegano la suddivisione giornaliera dei canali in tre scenari diversi:

#### Riproduzione di contenuto su un singolo giorno suddiviso in più fasce orarie {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio mostra come un Ristorante utilizza la ripartizione giornaliera per mostrare il suo menu di colazione, pranzo e cena.

Qui, divideremo ogni giorno in tre fasce orarie diverse, in modo che il contenuto del canale venga riprodotto secondo l&#39;ora specificata del giorno:

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| Menu_A | Colazione |  | dopo le 6:00 e prima delle 11:00 |
| Menu_B | Pranzo |  | dopo le 11:00 e prima delle 15:00 |
| Menu_C | Cena |  | dopo le 15:00 e prima delle 20:00 |

#### Riproduzione di contenuto in un particolare giorno della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra il dayParting realizzato in un casinò dove l&#39;evento live si verifica ogni fine settimana dalle 8:00 alle 10:00 pm e le specialità sono disponibili per il menu di cena dopo le 10:00 pm fino all&#39;1:00.

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
   <td>21 ottobre 2017 - 22 ottobre 2017 <br /> dopo le 20.00 prima delle 22.00</td>
  </tr>
  <tr>
   <td>CenaSpecials</td>
   <td>Fine settimana</td>
   <td> </td>
   <td>21 ottobre 2017 - 22 ottobre 2017 <br /> dopo le 22.00 prima delle 1.00</td>
  </tr>
 </tbody>
</table>

#### Riproduzione di contenuto per un mese/mesi particolare/i {#playing-content-for-a-particular-month-months}

Questo esempio mostra DayParting per un negozio che visualizza la raccolta estiva dai mesi di giugno ad agosto e la raccolta autunnale da settembre a fine ottobre.

In questo caso, creerai la suddivisione del giorno in base ai mesi, in modo che il contenuto del canale venga riprodotto in base ai mesi specificati dell’anno.

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| RaccoltaEstiva | Estate |  | 01 giugno 2017 - 31 agosto 2017 |
| FallCollection | Autunno |  | 01 settembre 2017 - 30 ottobre 2017 |

>[!NOTE]
>
>Inoltre, puoi definire la ***Priorità*** per ciascuno dei canali. Ad esempio, se due canali sono impostati per lo stesso giorno e la stessa ora o per lo stesso mese, il canale con priorità più alta viene riprodotto per primo. Il valore minimo per la priorità può essere impostato su 0.

#### Riproduzione di contenuto per i canali con la stessa priorità {#playing-content-for-channels-with-same-priority}

In questo esempio viene illustrato DayParting per un negozio che visualizza la propria collezione invernale con la stessa pianificazione nel mese di dicembre. Ma poiché il canale B ha la priorità impostata su 2, durante quella settimana il canale B riproduce il suo contenuto piuttosto che il canale A.

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| A | Inverno | 1 | 01 dicembre 2017 - 31 dicembre 2017 |
| B | Natale | 2 | 24 dicembre 2017 - 31 dicembre 2017 |


>[!NOTE]
>
> Per ulteriori informazioni su DayParting, consulta le sezioni seguenti:
>
>* [Gestione della ricorrenza nelle risorse](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [Gestione della ricorrenza per le risorse in un canale](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)


