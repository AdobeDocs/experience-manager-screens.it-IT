---
title: Assegnazione del canale - Ultima FP
seo-title: Assegnazione del canale - Ultima FP
description: Segui questa pagina per informazioni sull'assegnazione dei canali e la ripartizione dei giorni.
feature: Screens di authoring, Assegnazione canale
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 22%

---

# Assegnazione dei canali {#channel-assignment}

>[!IMPORTANT]
>
>Questa sezione evidenzia l&#39;assegnazione e la pianificazione dei canali per AEM Feature Pack 6.5.5 Screens e versioni successive.

Una volta impostata una visualizzazione, è necessario assegnare un canale a una visualizzazione per visualizzare il contenuto.

Questa pagina mostra l’assegnazione di un canale alla visualizzazione, le proprietà del canale e DayParting.

>[!NOTE]
>
>È possibile assegnare più canali a una visualizzazione.


## Assegnazione di un canale {#assign-a-channel-new-release}

Segui le sezioni seguenti per creare un progetto AEM Screens e assegnare un canale a una visualizzazione.

### Creazione di un progetto e di canali AEM Screens {#creating-project}

Per impostare un progetto e un canale, effettua le seguenti operazioni:

1. Crea un progetto AEM Screens denominato **DemoScreens**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Per informazioni su come creare un progetto AEM Screens, consulta [Creazione e gestione di progetti](creating-a-screens-project.md) .

1. Crea un canale per sequenza intitolato **Cafeteria** nella cartella **Canali** .

1. Seleziona il canale e fai clic su **Modifica** nella barra delle azioni per aggiungere contenuto al canale.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Ad esempio, il canale **Cafeteria** ora visualizza le immagini seguenti:

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Crea una posizione denominata **SanJose** e una visualizzazione come **Lobby**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Assegnazione di un canale a una visualizzazione {#assigning-channel-to-display}

Una volta completata la configurazione del progetto, devi assegnare il canale a una visualizzazione per visualizzare il contenuto.

1. Passa alla visualizzazione richiesta, ad esempio **DemoScreens** —> **Posizioni** —> **SanJose** —> **Lobby**.

1. Tocca o fai clic su **Assegna canale** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Oppure,

   Tocca/fai clic su **Dashboard** dalla barra delle azioni e fai clic su **+Assegna canale** dal pannello **CANALI ASSEGNATI e PIANIFICAZIONI** .

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Viene visualizzata la finestra di dialogo **Assegnazione canale**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Dall&#39;opzione **Impostazioni**, puoi scegliere il canale **per percorso** o **per nome**, immetti **Ruolo canale**, **Priorità**, **Eventi supportati** e **Metodi di interruzione**. Inoltre, è possibile abilitare la descrizione comando di attrazione da questa finestra di dialogo.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle proprietà di assegnazione dei canali, consulta la sezione [Proprietà canale](#channel-properties) .

1. Dall&#39;opzione **Pianificazione** selezionare la **Finestra di attivazione** e la **Pianificazione di ricorrenza**.
   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle proprietà di assegnazione dei canali, consulta la sezione [Proprietà canale](#channel-properties) .

1. Una volta configurate le preferenze, fai clic su **Salva**.

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

Questo esempio mostra l&#39;output su un lettore Chrome. Dopo aver assegnato il canale al display, è necessario registrare il dispositivo su un lettore.

Per informazioni su come registrare un dispositivo su un lettore AEM Screens, consulta [Registrazione dispositivo](device-registration.md) .

Verrà visualizzato il seguente output a scelta del lettore:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Vista Timeline {#timeline-view}

Dopo aver assegnato un canale a una visualizzazione e aver impostato una pianificazione della ricorrenza, è possibile visualizzare la timeline dal pannello **CANALI ASSEGNATI &amp; PIANIFICAZIONI**.

Per passare alla visualizzazione timeline, effettua le seguenti operazioni:

1. Passa alla visualizzazione richiesta, ad esempio **DemoScreens** —> **Posizioni** —> **SanJose** —> **Lobby**.

1. Tocca o fai clic su **Assegna canale** dalla barra delle azioni.

   Oppure,

   Tocca o fai clic su **Dashboard** e fai clic su **Timeline** nel pannello **CANALI ASSEGNATI e PIANIFICAZIONI**.

   ![immagine](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Informazioni sulle proprietà del canale dalla finestra di dialogo Assegnazione canale {#channel-properties}

Le seguenti proprietà sono impostate dall&#39;opzione **Impostazioni** nella finestra di dialogo **Assegnazione canale**.

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleziona un canale {#select-channel}

La selezione di un canale consente di fornire un riferimento al canale desiderato, per nome del canale o per percorso del canale.

* **In base al percorso**: fornisci un riferimento esplicito usando il percorso assoluto del canale.

* **per nome**: Immetti il nome del canale che verrà risolto in un canale effettivo per contesto. Questa funzione consente di creare la versione locale di un canale, per determinare dinamicamente i contenuti in base alla posizione. Ad esempio, un canale con nome *offerte del giorno*, in cui il contenuto effettivo sarebbe diverso in due città, ma si dispone comunque dello stesso ruolo di canale su tutte le visualizzazioni.

### Ruolo canale {#role-channel}

Il ruolo canale definisce il contesto della visualizzazione. Il ruolo è mirato da varie azioni ed è indipendente dal canale effettivo che svolge il ruolo.

### Priorità {#priority-channel}

La priorità viene usata per ordinare le assegnazioni nel caso in cui più utenti corrispondano ai criteri di riproduzione. Quella con il valore più alto avrà sempre la precedenza su quella con i valori più bassi. Ad esempio, se ci sono due canali A e B, A ha una priorità di 1 e B ha una priorità di 2, viene quindi visualizzato il canale B, che ha una priorità maggiore di A.

>[!NOTE]
>
>La priorità per un canale è impostata come numero (1 corrisponde alla priorità minima) nella finestra di dialogo **Assegnazione canale**, come detto sopra. Inoltre, i canali assegnati vengono ordinati in base a una priorità decrescente.

### Eventi supportati {#supported-events-channel}

* **Caricamento iniziale**: carica il canale quando il lettore viene avviato. Può essere assegnato a più canali in combinazione con la pianificazione
* **Schermata di inattività**: il canale viene caricato quando la schermata è inattiva. Può essere assegnato a più canali in combinazione con la pianificazione
* **Timer:** deve essere impostato quando viene fornita una pianificazione
* **Interazione utente**: il lettore passa al canale specificato, se c&#39;è un&#39;interazione utente sullo schermo (un tocco) in un canale inattivo; il canale viene caricato quando lo schermo viene toccato.

### Metodo di interruzione {#interruption-method-channel}

>[!IMPORTANT]
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

Le seguenti proprietà sono impostate dall&#39;opzione **Schedule** nella finestra di dialogo **Channel Assignment**.

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Finestra di attivazione {#activation-window}

La finestra Attivazione consente di selezionare una **data di inizio** e una **data di fine** per visualizzare il contenuto.

### Pianificazione ricorrenza {#recurrence-schedule}

La pianificazione della ricorrenza consente di impostare una pianificazione periodica per il contenuto. Fai clic su **+ Aggiungi pianificazione** per aggiungere una pianificazione della ricorrenza al tuo canale.

>[!NOTE]
>Puoi aggiungere più pianificazioni ricorrenti al tuo canale.
>La pianificazione ricorrenza introduce *DayParting*, che consente di impostare una pianificazione globale con più canali in esecuzione in momenti specifici della giornata e di riutilizzare tale impostazione per tutti i display contemporaneamente.

Puoi impostare le seguenti opzioni:

* **Nome**: Titolo della pianificazione della ricorrenza.
* **Ripeti**: Scegli se la pianificazione viene eseguita  **Giornaliero**,  **Settimanale**,  **Mensile** o  **Annuale**.
* **Avvia**: Ora di inizio della pianificazione.
* **Fine**: L&#39;orario finale della tua pianificazione. Puoi impostarlo per ora o durata.
   * **Ora**: La pianificazione termina a un&#39;ora specificata.
   * **Durata**: La pianificazione viene eseguita per una particolare durata in ore o minuti.

### DayParting {#dayparting}

DayParting si riferisce alla suddivisione di un giorno in fasce orarie e alla specificazione del contenuto riprodotto al momento desiderato. AEM Screens ti consente di pianificare i canali in termini di DayParting entro un giorno, una settimana o un mese, in base alle esigenze.

Gli esempi seguenti spiegano DayParting nei canali in tre scenari diversi:

#### Riproduzione di contenuto su un singolo giorno suddiviso in più fasce orarie {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio mostra come un ristorante utilizza DayParting per mostrare quotidianamente il menu di colazione, pranzo e cena.

In questo caso, divideremo ogni giorno in diversi intervalli di tempo, in modo che il contenuto del canale venga riprodotto in base all&#39;ora specificata del giorno. Imposta le seguenti proprietà della pianificazione della ricorrenza per il canale per riprodurre il contenuto in base a questo caso d’uso.

| **Nome** | **Ripetizioni** | **Avvia** | **Fine** |
|---|---|---|---|
| Colazione | Giornaliero | 6:00 | 11:00 |
| Pranzo | Giornaliero | 11:00 | 15:00 |
| Cena | Giornaliero | 15:00 | 8:00 PM |

#### Riproduzione di contenuto in un particolare giorno della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra il DayParting implementato in un casinò in cui l&#39;evento live si verifica ogni fine settimana dalle 8:00 alle 10:00 pm e le specialità sono disponibili per il menu di cena dopo le 10:00 fino all&#39;1:00.

| **Nome** | **Ripetizioni** | **Avvia** | **Fine** |
|---|---|---|---|
| Fine settimana | Settimanale: sabato,domenica | 8:00 PM | 10:00 |
| Specialità | Giornaliero: Lunedì-Venerdì | 10:00 | 1:00 |

>[!NOTE]
>
>Inoltre, puoi definire la ***Priorità*** per ciascuno dei canali. Ad esempio, se due canali sono impostati per lo stesso giorno e la stessa ora o per lo stesso mese, il canale con priorità più alta viene riprodotto per primo. Il valore minimo per la priorità può essere impostato su 0.
