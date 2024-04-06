---
title: Assegnazione canale - FP più recente
seo-title: Channel Assignment - Latest FP
description: Segui questa pagina per scoprire di più su Assegnazione canali e DayParting.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 2%

---

# Assegnazione canale {#channel-assignment}

>[!IMPORTANT]
>
>Questa sezione descrive come assegnare i canali e programmarne di nuovi per AEM 6.5.5 Screens Feature Pack e versioni successive.

Dopo aver configurato una visualizzazione, devi assegnare un canale a una visualizzazione per visualizzarne il contenuto.

Questa pagina mostra come assegnare un canale alla visualizzazione, comprendere le proprietà del canale e DayParting.

>[!NOTE]
>
>È possibile assegnare più canali a una visualizzazione.


## Assegnazione di un canale {#assign-a-channel-new-release}

Segui le sezioni seguenti per creare un progetto AEM Screens e assegnare un canale a una visualizzazione.

### Creazione di un progetto e di canali AEM Screens {#creating-project}

Segui i passaggi seguenti per configurare un progetto e un canale:

1. Creare un progetto AEM Screens con titolo **DemoScreens**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Fai riferimento a [Creazione e gestione di progetti](creating-a-screens-project.md) per scoprire come creare un progetto AEM Screens.

1. Crea un canale di sequenza denominato **Caffetteria** nel **Canali** cartella.

1. Seleziona il canale e fai clic su **Modifica** dalla barra delle azioni per aggiungere contenuto al canale.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Ad esempio, il **Caffetteria** channel visualizza ora le seguenti immagini:

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Crea una posizione con titolo **SanJose** e un display come **Lobby**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Assegnazione di un canale a una visualizzazione {#assigning-channel-to-display}

Una volta completata la configurazione del progetto, devi assegnare il canale a una visualizzazione per visualizzare il contenuto.

1. Passa alla visualizzazione desiderata, ad esempio: **DemoScreens** > **Posizioni** > **SanJose** > **Lobby**.

1. Tocca o fai clic **Assegna canale** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Oppure

   Tocca o fai clic **Dashboard** dalla barra delle azioni e fai clic su **+Assegna canale** dal **CANALI E PIANIFICAZIONI ASSEGNATI** pannello.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Il **Assegnazione canale** viene visualizzata.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Dalla sezione **Impostazioni** , è possibile scegliere il canale **per percorso** o **per nome**, immetti il **Ruolo canale**, **Priorità**, **Eventi supportati**, e **Metodi di interruzione**. In questa finestra di dialogo è inoltre possibile attivare la descrizione comando per l&#39;attrazione.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Fai riferimento a [Proprietà canale](#channel-properties) per ulteriori informazioni sulle proprietà di assegnazione dei canali.

1. Dalla sezione **Pianificazione** opzione seleziona la **Finestra di attivazione** e **Pianificazione ricorrenza**.
   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Fai riferimento a [Proprietà canale](#channel-properties) per ulteriori informazioni sulle proprietà di assegnazione dei canali.

1. Clic **Salva** dopo aver configurato le preferenze.

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

Questo esempio mostra l’output in un Chrome Player. Dopo aver assegnato il canale al display, è necessario registrare il dispositivo su un lettore.

Fai riferimento a [Registrazione dispositivo](device-registration.md) per scoprire come registrare un dispositivo su un lettore AEM Screens.

Viene visualizzato il seguente output sulla scelta del lettore:

![nuovo1](assets/channel-assignment/channel-assign-output.gif)

## Vista Timeline {#timeline-view}

Dopo aver assegnato un canale a una visualizzazione e aver impostato una pianificazione di ricorrenza, puoi visualizzare la timeline dalla sezione **CANALI E PIANIFICAZIONI ASSEGNATI** pannello.

Per passare alla vista timeline, segui la procedura riportata di seguito:

1. Passa alla visualizzazione desiderata, ad esempio: **DemoScreens** > **Posizioni** > **SanJose** > **Lobby**.

1. Tocca o fai clic **Assegna canale** dalla barra delle azioni.

   Oppure

   Tocca o fai clic **Dashboard** e fai clic su **Timeline** dal **CANALI E PIANIFICAZIONI ASSEGNATI** pannello.

   ![immagine](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Informazioni sulle proprietà del canale dalla finestra di dialogo Assegnazione canale {#channel-properties}

Le seguenti proprietà sono impostate dal **Impostazioni** opzione in **Assegnazione canale** .

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleziona un canale {#select-channel}

La selezione di un canale consente di fornire un riferimento al canale desiderato, in base al nome o al percorso del canale.

* **per percorso**: fornisci un riferimento esplicito utilizzando il percorso assoluto del canale.

* **per nome**: immetti il nome del canale che verrà risolto in un canale effettivo in base al contesto. Questa funzione consente di creare una versione locale di un canale per risolvere in modo dinamico il contenuto specifico della posizione. Ad esempio, un canale con nome *offerte del giorno*, in cui il contenuto effettivo sarebbe diverso in due città, ma si dispone comunque del ruolo di canale sano su tutti gli schermi.

### Ruolo canale {#role-channel}

Il ruolo del canale definisce il contesto della visualizzazione. Il ruolo è oggetto di varie azioni ed è indipendente dal canale effettivo che lo svolge.

### Priorità {#priority-channel}

La priorità viene utilizzata per ordinare le assegnazioni nel caso in cui più corrispondano ai criteri di riproduzione. Quello con il valore più alto avrà sempre la precedenza sui valori più bassi. Ad esempio, se sono presenti due canali A e B. A ha una priorità di 1 e B ha una priorità di 2, quindi viene visualizzato il canale B, in quanto ha una priorità più alta di A.

>[!NOTE]
>
>La priorità per un canale è impostata come numero (1 per il minimo) nel **Assegnazione canale** come indicato in precedenza. Inoltre, i canali assegnati vengono ordinati in base alla priorità decrescente.

### Eventi supportati {#supported-events-channel}

* **Caricamento iniziale**: carica il canale all’avvio del lettore. Può essere assegnato a più canali in combinazione con la pianificazione
* **Schermata di inattività**: viene caricato quando lo schermo è inattivo. Può essere assegnato a più canali in combinazione con la pianificazione
* **Timer**: deve essere impostato quando viene fornita una pianificazione
* **Interazione utente**: il lettore passa al canale specificato, se sullo schermo (touch) è presente un’interazione dell’utente in un canale inattivo e si carica quando lo schermo viene toccato

### Metodo di interruzione {#interruption-method-channel}

>[!IMPORTANT]
> Questa opzione è disponibile solo con il Feature Pack 8 di AEM 6.4 o il Feature Pack 4 di AEM 6.5.

In qualità di autore di contenuti, dovresti essere in grado di specificare quando un canale viene interrotto, in modo da poter scegliere di tagliare i contenuti non critici, ma avere la possibilità di consentire la riproduzione completa di contenuti importanti prima di interrompere la riproduzione a causa della pianificazione.

Selezionare una delle seguenti opzioni disponibili per impostare il metodo di interruzione dal menu **Assegnazione canale** finestra di dialogo:

* **Immediatamente**: quando la pianificazione si attiva o viene ricevuto un aggiornamento, puoi interrompere la riproduzione e aggiornare immediatamente o riprodurre il nuovo contenuto
* **Alla fine dell&#39;elemento corrente**: quando si attiva una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere il termine della riproduzione dell’elemento corrente nella sequenza e solo dopo aver aggiornato o riprodotto il nuovo contenuto

  >[!NOTE]
  >Questa opzione è selezionata per impostazione predefinita.

* **Alla fine della sequenza**: quando si attiva una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere che l’intera sequenza raggiunga la fine e, immediatamente prima della sequenza desiderata, si torna al primo elemento, si aggiorna o si riproduce il nuovo contenuto

  >[!NOTE]
  >Se si utilizza la seconda o la terza opzione, gli orari di programmazione definiti nell’assegnazione potrebbero essere leggermente differiti, in quanto il lettore attenderà la fine dell’elemento o della sequenza (dopo l’ora specificata) prima di aggiornarli. Il ritardo dipenderà dalla durata di riproduzione dell’elemento.

Le seguenti proprietà sono impostate dal **Pianificazione** opzione in **Assegnazione canale** .

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Finestra di attivazione {#activation-window}

La finestra di attivazione consente di selezionare un **Data di inizio** e un **Data di fine** per visualizzare il contenuto.

### Pianificazione ricorrenza {#recurrence-schedule}

La pianificazione di ricorrenza consente di impostare una pianificazione ricorrente per il contenuto. Fai clic su **+ Aggiungi pianificazione** per aggiungere una pianificazione di ricorrenza al canale.

>[!NOTE]
>Puoi aggiungere più pianificazioni ricorrenti al tuo canale.
>Gli Schedules per la Ricorrenza introducono *DayParting*, che consente di impostare una pianificazione globale con più canali in esecuzione in momenti specifici della giornata e di riutilizzare tale configurazione per tutti i display contemporaneamente.

È possibile impostare le seguenti opzioni:

* **Nome**: titolo dello Schedule ricorrente.
* **Ripeti**: scegli se la pianificazione viene eseguita **Giornaliero**, **Ogni settimana**, **Mensile**, o **Annuale**.
* **Inizio**: ora di inizio della pianificazione.
* **Fine**: ora di fine della pianificazione. È possibile impostare l’IT in base all’ora o alla durata.
   * **Ora**: la pianificazione termina a un’ora specificata.
   * **Durata**: la pianificazione viene eseguita per una particolare durata di tempo in ore o minuti.

### DayParting {#dayparting}

DayParting si riferisce alla suddivisione di un giorno in intervalli temporali e alla specifica del contenuto riprodotto all’ora desiderata. AEM Screens consente di pianificare i canali in termini di DayParting entro un giorno, una settimana o un mese in base al requisito.

Gli esempi seguenti illustrano DayParting nei canali in tre diversi scenari:

#### Riproduzione di contenuti in un singolo giorno suddiviso in più slot temporali {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio mostra come un ristorante utilizza DayParting per mostrare ogni giorno il menu per la colazione, il pranzo e la cena.

In questo caso, ogni giorno viene diviso in diversi intervalli di tempo, in modo che il contenuto del canale venga riprodotto in base all’ora del giorno specificata. Imposta le seguenti proprietà della pianificazione della ricorrenza per il canale per riprodurre il contenuto in base a questo caso d’uso.

| **Nome** | **Si ripete** | **Avvia** | **Fine** |
|---|---|---|---|
| Colazione | Giornaliero | 6:00 | 11:00 |
| Pranzo | Giornaliero | 11:00 | 15:00 |
| Cena | Giornaliero | 15:00 | 20:00 |

#### Riproduzione di contenuti in un giorno specifico della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra il DayParting implementato in un casinò in cui si verifica un evento live ogni fine settimana dalle 20:00 alle 22:00 e sono disponibili speciali per il menu di cena dopo le 22:00 fino all’1:00

| **Nome** | **Si ripete** | **Avvia** | **Fine** |
|---|---|---|---|
| Fine settimana | Settimanale: sabato, domenica | 20:00 | 22:00 |
| Programmi speciali | Giornaliero: lunedì-venerdì | 22:00 | 01:00 |

>[!NOTE]
>
>Inoltre, puoi definire ***Priorità*** per ciascuno dei canali. Ad esempio, se due canali sono impostati per lo stesso giorno e ora o per lo stesso mese, viene riprodotto prima il canale con priorità più elevata. Il valore minimo di priorità può essere impostato su 0.
