---
title: Assegnazione canale - Ultimo FP
seo-title: Assegnazione canale - Ultimo FP
description: Segui questa pagina per saperne di più sull'assegnazione dei canali e la suddivisione dei giorni.
translation-type: tm+mt
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 22%

---


# Assegnazione dei canali {#channel-assignment}

>[!IMPORTANT]
>
>In questa sezione vengono evidenziati l’assegnazione dei canali e la programmazione dei canali per AEM Feature Pack 6.5.5 Screens e versioni successive.

Una volta configurato uno schermo, è necessario assegnare un canale a uno schermo per visualizzare il contenuto.

Questa pagina mostra l’assegnazione di un canale al display, le proprietà del canale e DayParting.

>[!NOTE]
>
>Potete assegnare più canali a uno schermo.


## Assegnazione di un canale {#assign-a-channel-new-release}

Seguite le sezioni riportate di seguito per creare un progetto AEM Screens  e assegnare un canale a uno schermo.

### Creazione di un progetto e di canali AEM Screens  {#creating-project}

Per impostare un progetto e un canale, effettuate le seguenti operazioni:

1. Create un progetto AEM Screens  denominato **DemoScreens**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Per informazioni su come creare un progetto AEM Screens , fare riferimento a [Creazione e gestione di progetti](creating-a-screens-project.md).

1. Create un canale di sequenza denominato **Cafeteria** nella cartella **Channels**.

1. Selezionate il canale e fate clic su **Modifica** dalla barra delle azioni per aggiungere contenuto al canale.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Ad esempio, il canale **Cafeteria** ora visualizza le immagini seguenti:

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Create una posizione con titolo **SanJose** e uno schermo con nome **Lobby**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Assegnazione del canale a un display {#assigning-channel-to-display}

Una volta completata la configurazione del progetto, dovete assegnare il canale a uno schermo per visualizzare il contenuto.

1. Passare alla visualizzazione desiderata, ad esempio **DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**.

1. Toccate/fate clic su **Assegna canale** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Oppure,

   Toccate/fate clic su **Dashboard** nella barra delle azioni e fate clic su **+Assegna canale** nel pannello **CANALI ASSEGNATI &amp; PROGRAMMI**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Viene visualizzata la finestra di dialogo **Assegnazione canale**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Dall&#39;opzione **Impostazioni**, è possibile scegliere il canale **per percorso** o **per nome**, inserire il **Channel Role**, **Priority**, **Eventi supportati** e **Metodi di interruzione**. Inoltre, è possibile abilitare la descrizione comando di attrazione da questa finestra di dialogo.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Fare riferimento alla sezione [Proprietà canale](#channel-properties) per ulteriori informazioni sulle proprietà di assegnazione dei canali.

1. Dall&#39;opzione **Pianificazione**, selezionare la **Finestra di attivazione** e **Programma di ricorrenza**.
   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Fare riferimento alla sezione [Proprietà canale](#channel-properties) per ulteriori informazioni sulle proprietà di assegnazione dei canali.

1. Fare clic su **Salva** dopo aver configurato le preferenze.

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

Questo esempio mostra l&#39;output su un lettore Chrome. Dopo aver assegnato il canale al display, è necessario registrare il dispositivo su un lettore.

Per informazioni su come registrare un dispositivo su un lettore AEM Screens , fare riferimento a [Registrazione dispositivo](device-registration.md).

Verrà visualizzato il seguente output a scelta del lettore:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Visualizzazione timeline {#timeline-view}

Dopo aver assegnato un canale a un display e aver impostato un programma di ricorrenza, potete visualizzare la timeline dal pannello **ASSIGNED CHANNELS &amp; SCHEDULES**.

Per passare alla visualizzazione timeline, effettuate le seguenti operazioni:

1. Passare alla visualizzazione desiderata, ad esempio **DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**.

1. Toccate/fate clic su **Assegna canale** dalla barra delle azioni.

   Oppure,

   Toccate/fate clic su **Dashboard** e fate clic su **Timeline** nel pannello **CANALI ASSEGNATI e PROGRAMMI**.

   ![immagine](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Informazioni sulle proprietà del canale dalla finestra di dialogo Assegnazione canale {#channel-properties}

Le seguenti proprietà sono impostate dall&#39;opzione **Impostazioni** nella finestra di dialogo **Assegnazione canale**.

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Seleziona un canale {#select-channel}

La selezione di un canale consente di fornire un riferimento al canale desiderato, sia per nome del canale che per percorso del canale.

* **In base al percorso**: fornisci un riferimento esplicito usando il percorso assoluto del canale.

* **per nome**: Immettere il nome del canale che verrà risolto in un canale effettivo per contesto. Questa funzione consente di creare la versione locale di un canale, per determinare dinamicamente i contenuti in base alla posizione. Ad esempio, un canale con il nome *offre tutte le offerte del giorno*, dove il contenuto effettivo sarebbe diverso in due città, ma l&#39;utente ha comunque lo stesso ruolo di canale su tutti i display.

### Ruolo canale {#role-channel}

Il ruolo canale definisce il contesto della visualizzazione. Il ruolo è mirato da diverse azioni ed è indipendente dal canale effettivo che svolge il ruolo.

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
> Questa opzione è disponibile solo con il Feature Pack 8 AEM 6.4 o con il Feature Pack 4 AEM 6.5.

In qualità di autore dei contenuti, dovreste essere in grado di specificare quando un canale viene interrotto, in modo da poter scegliere di interrompere i contenuti non critici, ma avere la possibilità di consentire la riproduzione completa dei contenuti importanti prima di interrompere la riproduzione a causa della programmazione.

Selezionare una delle seguenti opzioni disponibili per impostare il metodo di interruzione dalla finestra di dialogo **Assegnazione canale**:

* **Immediatamente**: ogni volta che la pianificazione viene attivata o viene ricevuto un aggiornamento, potete interrompere la riproduzione e aggiornare o riprodurre immediatamente il nuovo contenuto
* **Alla fine della voce** corrente: quando viene attivata una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere il termine della riproduzione dell’elemento corrente nella sequenza e solo dopo aver aggiornato o riprodotto il nuovo contenuto

   >[!NOTE]
   >Per impostazione predefinita, questa opzione è selezionata.

* **Alla fine della sequenza**: quando viene attivata una nuova pianificazione o viene ricevuto un aggiornamento, potete aspettare che l&#39;intera sequenza raggiunga la fine, e subito prima della sequenza desiderata, tornate al primo elemento, aggiornate o riproducete il nuovo contenuto

   >[!NOTE]
   >Utilizzando la seconda o la terza opzione è possibile che i tempi di programmazione definiti per l&#39;assegnazione vengano leggermente posticipati, in quanto il lettore aspetterà la fine dell&#39;elemento o della sequenza (dopo il tempo specificato) prima di effettuare l&#39;aggiornamento. Il ritardo dipenderà dalla durata di riproduzione dell’elemento.

Le seguenti proprietà sono impostate dall&#39;opzione **Schedule** nella finestra di dialogo **Channel Assignment**.

![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Finestra di attivazione {#activation-window}

La finestra Attivazione consente di selezionare una **data di inizio** e una **data di fine** per visualizzare il contenuto.

### Pianificazione ricorrenza {#recurrence-schedule}

La pianificazione ricorrenza consente di impostare una pianificazione periodica per il contenuto. Fare clic su **+ Aggiungi pianificazione** per aggiungere una pianificazione della ricorrenza al canale.

>[!NOTE]
>Puoi aggiungere più pianificazioni ricorrenti al tuo canale.
>Nei programmi di ricorrenza viene introdotto *DayParting*, che consente di impostare una pianificazione globale con più canali in esecuzione in orari specifici del giorno e di riutilizzare la configurazione per tutti i display contemporaneamente.

Potete impostare le seguenti opzioni:

* **Nome**: Titolo della pianificazione della ricorrenza.
* **Ripeti**: Scegliete se la pianificazione viene eseguita  **Quotidianamente**,  **Settimanalmente**,  **Mensilmente** o  **Annualmente**.
* **Inizio**: Ora di inizio per la pianificazione.
* **Fine**: L&#39;ora di fine del programma. Potete impostare l&#39;impostazione per ora o durata.
   * **Ora**: La pianificazione termina a un&#39;ora specificata.
   * **Durata**: La pianificazione viene eseguita per una particolare durata in ore o minuti.

### DayParting {#dayparting}

DayParting fa riferimento alla suddivisione di un giorno in orari fissi e alla specifica del contenuto riprodotto al momento desiderato.  AEM Screens consente di pianificare i canali in termini di DayParting entro un giorno, una settimana o un mese, a seconda dei requisiti.

Gli esempi seguenti spiegano DayParting nei canali in tre scenari diversi:

#### Riproduzione di contenuto su un singolo giorno suddiviso in più fasce orarie {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio mostra come un ristorante utilizza DayParting per mostrare la sua colazione, pranzo e cena menu ogni giorno.

In questo caso, ogni giorno verrà suddiviso in diversi orari, in modo che il contenuto dei canali venga riprodotto in base all&#39;ora specificata del giorno. Impostate le seguenti proprietà della Pianificazione ricorrenza per il canale per riprodurre il contenuto come da questo caso d’uso.

| **Nome** | **Ripetizioni** | **Avvia** | **Fine** |
|---|---|---|---|
| Colazione | Giornaliero | 6:00 AM | 11:00 |
| Pranzo | Giornaliero | 11:00 | 3:00 PM |
| Cena | Giornaliero | 3:00 PM | 8:00 PM |

#### Riproduzione di contenuto in un particolare giorno della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra la DayParting implementata in un casinò dove l&#39;evento live si verifica ogni weekend dalle 8:00 pm alle 10:00 pm e i piatti speciali sono disponibili per il menu di cena dopo le 10:00 pm fino alle 1:00 am.

| **Nome** | **Ripetizioni** | **Avvia** | **Fine** |
|---|---|---|---|
| Fine settimana | Settimanale: Sabato,Domenica | 8:00 PM | 10:00 PM |
| Specials | Giornaliero: Lunedì-Venerdì | 10:00 PM | 1:00 |

>[!NOTE]
>
>Inoltre, puoi definire la ***Priorità*** per ciascuno dei canali. Ad esempio, se due canali sono impostati per lo stesso giorno e la stessa ora o per lo stesso mese, il canale con priorità più alta viene riprodotto per primo. Il valore minimo per la priorità può essere impostato su 0.
