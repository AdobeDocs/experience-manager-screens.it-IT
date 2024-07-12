---
title: Assegnazione canale - FP più recente
description: Scopri assegnazione canale e ripartizione giornaliera.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 2%

---

# Assegnazione canale {#channel-assignment}

>[!IMPORTANT]
>
>In questa sezione vengono illustrate l’assegnazione dei canali e la pianificazione dei canali per Screens Feature Pack di AEM 6.5.5 e versioni successive.

Dopo aver impostato una visualizzazione, assegna un canale a una visualizzazione per visualizzarne il contenuto.

Questa pagina mostra come assegnare un canale alla visualizzazione, comprendere le proprietà del canale e DayParting.

>[!NOTE]
>
>È possibile assegnare più canali a una visualizzazione.


## Assegnazione di un canale {#assign-a-channel-new-release}

Segui le sezioni seguenti per creare un progetto AEM Screens e assegnare un canale a una visualizzazione.

### Creazione di un progetto e di canali AEM Screens {#creating-project}

Segui i passaggi seguenti per configurare un progetto e un canale:

1. Crea un progetto AEM Screens denominato **DemoScreens**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Per informazioni sulla creazione di un progetto AEM Screens, vedere [Creazione e gestione di progetti](creating-a-screens-project.md).

1. Crea un canale di sequenza denominato **Cafeteria** nella cartella **Channels**.

1. Fai clic sul canale, quindi fai clic su **Modifica** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Ad esempio, il canale **Cafeteria** visualizza ora le seguenti immagini:

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Crea una posizione con titolo **SanJose** e una visualizzazione come **Lobby**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Assegnazione di un canale a una visualizzazione {#assigning-channel-to-display}

Al termine della configurazione del progetto, assegna il canale a una visualizzazione per visualizzare il contenuto.

1. Passa alla visualizzazione desiderata, ad esempio **DemoScreens** > **Percorsi** > **SanJose** > **Lobby**.

1. Fare clic su **Assegna canale** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Oppure

   Fai clic su **Dashboard** nella barra delle azioni, quindi fai clic su **+Assegna canale** nel pannello **CANALI E PIANIFICAZIONI ASSEGNATI**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Viene visualizzata la finestra di dialogo **Assegnazione canale**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Dall&#39;opzione **Impostazioni**, è possibile scegliere il canale **in base al percorso** o **in base al nome**, immettere **Ruolo canale**, **Priorità**, **Eventi supportati** e **Metodi di interruzione**. Inoltre, è possibile attivare la descrizione comando attrazione da questa finestra di dialogo.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle proprietà di assegnazione canale, consulta la sezione [Proprietà canale](#channel-properties).

1. Dall&#39;opzione **Pianificazione**, fare clic su **Finestra di attivazione** e **Pianificazione ricorrenza**.
   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle proprietà di assegnazione canale, consulta la sezione [Proprietà canale](#channel-properties).

1. Dopo aver configurato le preferenze, fai clic su **Salva**.

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

Questo esempio mostra l&#39;output in un lettore Chrome. Dopo aver assegnato il canale al display, registrare il dispositivo su un lettore.

Per informazioni su come registrare un dispositivo in un lettore AEM Screens, vedere [Registrazione dispositivo](device-registration.md).

Puoi visualizzare il seguente output nella scelta del lettore:

![nuovo1](assets/channel-assignment/channel-assign-output.gif)

## Vista Timeline {#timeline-view}

Quando hai assegnato un canale a una visualizzazione e hai impostato una pianificazione di ricorrenza, puoi visualizzare la timeline dal pannello **CANALI E PIANIFICAZIONI ASSEGNATI**.

Per passare alla vista timeline, segui la procedura riportata di seguito:

1. Passa alla visualizzazione desiderata, ad esempio **DemoScreens** > **Percorsi** > **SanJose** > **Lobby**.

1. Fare clic su **Assegna canale** nella barra delle azioni.

   Oppure

   Fai clic su **Dashboard** e poi su **Timeline** dal pannello **SCHEDULES E CANALI ASSEGNATI**.

   ![immagine](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Informazioni sulle proprietà del canale dalla finestra di dialogo Assegnazione canale {#channel-properties}

Le seguenti proprietà sono impostate dall&#39;opzione **Impostazioni** nella finestra di dialogo **Assegnazione canale**.

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleziona un canale {#select-channel}

La selezione di un canale consente di fornire un riferimento al canale desiderato, in base al nome o al percorso del canale.

* **Per percorso** - Fornisci un riferimento esplicito utilizzando il percorso assoluto del canale.
* **Per nome** - Immettere il nome del canale che viene risolto in un canale effettivo in base al contesto. Questa funzione ti consente di creare una versione locale di un canale in modo da poter risolvere dinamicamente il contenuto specifico della posizione. Ad esempio, un canale con il nome *offerte del giorno*, in cui il contenuto effettivo sarebbe diverso in due città, ma si dispone ancora del ruolo canale sano su tutte le visualizzazioni.

### Ruolo canale {#role-channel}

Il ruolo del canale definisce il contesto della visualizzazione. Il ruolo è assegnato a diverse azioni. È indipendente dal canale effettivo che svolge il ruolo.

### Priorità {#priority-channel}

La priorità viene utilizzata per ordinare le assegnazioni nel caso in cui più corrispondano ai criteri di riproduzione. Quello con il valore più alto ha sempre la precedenza sui valori più bassi. Ad esempio, se sono presenti due canali A e B. A ha una priorità di 1 e B ha una priorità di 2, quindi viene visualizzato il canale B, in quanto ha una priorità più alta di A.

>[!NOTE]
>
>La priorità per un canale è impostata come numero (minimo 1) nella finestra di dialogo **Assegnazione canale**, come indicato in precedenza. Inoltre, i canali assegnati vengono ordinati in base alla priorità decrescente.

### Eventi supportati {#supported-events-channel}

* **Caricamento iniziale** - Carica il canale all&#39;avvio del lettore. Può essere assegnato a più canali con una pianificazione.
* **Schermata di inattività** - Carica quando lo schermo è inattivo. Può essere assegnato a più canali con una pianificazione.
* **Timer** - Deve essere impostato quando viene fornita una pianificazione.
* **Interazione utente** - Il lettore passa al canale specificato se sullo schermo è presente un&#39;interazione dell&#39;utente (touch) in un canale inattivo e viene caricato quando lo schermo viene toccato.

### Metodo di interruzione {#interruption-method-channel}

>[!IMPORTANT]
> Questa opzione è disponibile solo con <!--AEM 6.4 Feature Pack 8 or-->AEM 6.5 Feature Pack 4.

In qualità di autore di contenuti, puoi specificare quando un canale viene interrotto. In questo modo è possibile scegliere di eliminare i contenuti non critici. ma offre anche la possibilità di riprodurre completamente i contenuti importanti prima di interromperli a causa della programmazione.

Selezionare una delle opzioni seguenti disponibili per impostare il metodo di interruzione dalla finestra di dialogo **Assegnazione canale**:

* **Immediatamente** - Quando la pianificazione si attiva o viene ricevuto un aggiornamento, puoi interrompere la riproduzione e aggiornare immediatamente o riprodurre il nuovo contenuto
* **Fine dell&#39;elemento corrente** - Quando si attiva una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere il termine della riproduzione dell&#39;elemento corrente nella sequenza. Successivamente, sarà possibile aggiornare o riprodurre il nuovo contenuto.

  >[!NOTE]
  >Questa opzione è selezionata per impostazione predefinita.

* **Alla fine della sequenza** - Quando si attiva una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere che l&#39;intera sequenza raggiunga la fine. Quindi, immediatamente prima della sequenza desiderata, puoi tornare al primo elemento, aggiornare o riprodurre il nuovo contenuto.

  >[!NOTE]
  >Se si utilizza la seconda o la terza opzione, gli orari di programmazione definiti nell&#39;assegnazione potrebbero subire un leggero differimento. Il motivo è che il lettore attende la fine dell’elemento o della sequenza (dopo l’ora specificata) prima di eseguire l’aggiornamento. Il ritardo dipende dalla durata di riproduzione dell’elemento.

Le seguenti proprietà sono impostate dall&#39;opzione **Pianifica** nella finestra di dialogo **Assegnazione canale**.

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Finestra di attivazione {#activation-window}

La finestra di attivazione consente di selezionare una **data di inizio** e una **data di fine** per visualizzare il contenuto.

### Pianificazione ricorrenza {#recurrence-schedule}

La pianificazione di ricorrenza consente di impostare una pianificazione ricorrente per il contenuto. Fai clic su **+ Aggiungi pianificazione** per aggiungere una pianificazione di ricorrenza al tuo canale.

>[!NOTE]
>Puoi aggiungere più pianificazioni ricorrenti al tuo canale.
>Gli Schedules ricorrenti introducono *DayParting*. Puoi impostare una pianificazione globale con più canali in esecuzione in orari specifici della giornata e riutilizzare quella impostata per tutte le visualizzazioni contemporaneamente.

È possibile impostare le seguenti opzioni:

* **Nome** - Titolo della pianificazione di ricorrenza.
* **Ripeti** - Scegliere se la pianificazione esegue **Giornaliero**, **Settimanale**, **Mensile** o **Annuale**.
* **Inizio** - Ora di inizio della pianificazione.
* **Fine** - Ora di fine della pianificazione. Puoi impostarla in base all’ora o alla durata.
   * **Ora** - La pianificazione termina all&#39;ora specificata.
   * **Durata** - La pianificazione viene eseguita per un periodo di tempo specifico in ore o minuti.

### DayParting {#dayparting}

Per ripartizione giornaliera si intende la suddivisione di un giorno in più fessure temporali e la specifica del contenuto da riprodurre all’ora desiderata. AEM Screens consente di pianificare i canali in termini di DayParting entro un giorno, una settimana o un mese in base al requisito.

Gli esempi seguenti illustrano DayParting nei canali in tre diversi scenari:

#### Riproduzione di contenuti in un singolo giorno suddiviso in più slot temporali {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio mostra come un ristorante utilizza DayParting per mostrare ogni giorno il menu per la colazione, il pranzo e la cena.

In questo caso, ogni giorno è diviso in diversi intervalli di tempo, in modo che il contenuto del canale venga riprodotto in base all’ora del giorno specificata. Imposta le seguenti proprietà della pianificazione della ricorrenza per il canale per riprodurre il contenuto in base a questo caso d’uso.

| **Nome** | **Ripetizioni** | **Avvia** | **Fine** |
|---|---|---|---|
| Colazione | Giornaliero | 06:00 | 11:00 |
| Pranzo | Giornaliero | 11:00 | 15:00 |
| Cena | Giornaliero | 15:00 | 20:00 |

#### Riproduzione di contenuti in un giorno specifico della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra il DayParting implementato in un casinò in cui si verifica un evento in diretta ogni fine settimana dalle 20:00 alle 22:00 e sono disponibili speciali per il menu di cena dopo le 22:00 fino all’1:00.

| **Nome** | **Ripetizioni** | **Avvia** | **Fine** |
|---|---|---|---|
| Fine settimana | Settimanale: sabato e domenica | 20:00 | 22:00 |
| Programmi speciali | Giornaliero: dal lunedì al venerdì | 22:00 | 01:00 |

>[!NOTE]
>
>Inoltre, puoi definire ***Priorità*** per ciascuno dei canali. Ad esempio, se due canali sono impostati per lo stesso giorno e ora o per lo stesso mese, viene riprodotto prima il canale con priorità più elevata. Il valore minimo di priorità può essere impostato su 0.
