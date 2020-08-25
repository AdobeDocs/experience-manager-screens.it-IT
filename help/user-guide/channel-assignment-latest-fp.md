---
title: Assegnazione canale - Ultimo FP
seo-title: Assegnazione canale - Ultimo FP
description: Segui questa pagina per saperne di più sull’assegnazione del canale e la suddivisione del giorno.
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 29%

---


# Assegnazione dei canali {#channel-assignment}

>[!IMPORTANT]
>In questa sezione vengono evidenziati l’assegnazione dei canali e la programmazione dei canali per AEM Feature Pack 6.5.5 Screens e versioni successive.

Una volta configurato uno schermo, è necessario assegnare un canale a uno schermo per visualizzare il contenuto.

Questa pagina mostra l’assegnazione di un canale al display.

>[!NOTE]
>Potete assegnare più canali a uno schermo.


## Assigning a Channel {#assign-a-channel-new-release}

Seguite le sezioni riportate di seguito per creare un progetto AEM Screens  e assegnare un canale a uno schermo.

### Creazione di un progetto e di canali AEM Screens  {#creating-project}

Per impostare un progetto e un canale, effettuate le seguenti operazioni:

1. Create un progetto AEM Screens  denominato **DemoScreens**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Per informazioni su come creare un progetto AEM Screens , consultate [Creazione e gestione di progetti](creating-a-screens-project.md) .

1. Create un canale di sequenza denominato **Cafeteria** nella cartella **Canali** .

1. Seleziona il canale e fai clic su **Modifica** dalla barra delle azioni per aggiungere dei contenuti al canale.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Ad esempio, il canale **Cafeteria** ora mostra le immagini seguenti:

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Create una posizione denominata **SanJose** e una visualizzazione come **Sala d’attesa**.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Assegnazione di un canale a uno schermo {#assigning-channel-to-display}

Una volta completata la configurazione del progetto, dovete assegnare il canale a uno schermo per visualizzare il contenuto.

1. Passare alla visualizzazione desiderata, ad esempio **DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**.

1. Tap/click **Assign Channel** from the action bar.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Oppure,

   Toccate/fate clic su **Dashboard** e fate clic su **+Assegna canale** dal pannello CANALI **ASSEGNATI e PIANIFICAZIONI** .

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Dall’opzione **Impostazioni** , potete scegliere il canale per percorso o per nome, immettere il ruolo del canale, la priorità, gli eventi supportati e i metodi di interruzione. Inoltre, è possibile attivare l&#39;opzione relativa alla descrizione comando di attrazione da questa finestra di dialogo.

   ![immagine](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Per ulteriori informazioni sulle proprietà del canale, consulta la sezione Proprietà [](#channel-properties) canale.

1. Dall&#39;opzione **Pianificazioni** , selezionate il **Fuso orario** di riferimento, la finestra **** Attivazione e la Pianificazione **** ricorrenza.

1. Dopo aver configurato le preferenze, fate clic su **Salva** .

### Visualizzazione del contenuto in Chrome Player {#viewing-content-output}

### Informazioni sulle proprietà del canale dall&#39;assegnazione del canale {#channel-properties}

### Riferimento a canale {#ref-channel}

il riferimento a canale consente di fornire un riferimento al canale desiderato, per nome o in base al percorso del canale.

* **In base al percorso**: fornisci un riferimento esplicito usando il percorso assoluto del canale.

* **per nome**: Immettere il nome del canale che verrà risolto in un canale effettivo per contesto. Questa funzione consente di creare la versione locale di un canale, per determinare dinamicamente i contenuti in base alla posizione. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

### Ruolo canale {#role-channel}

Il ruolo canale definisce il contesto della visualizzazione. Il ruolo è mirato da diverse azioni ed è indipendente dal canale effettivo che svolge il ruolo.

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
> Questa opzione è disponibile solo con il Feature Pack 8 AEM 6.4 o con il Feature Pack 4 AEM 6.5.

In qualità di autore dei contenuti, dovreste essere in grado di specificare quando un canale viene interrotto, in modo da poter scegliere di interrompere i contenuti non critici, ma avere la possibilità di consentire la riproduzione completa dei contenuti importanti prima di interrompere la riproduzione a causa della programmazione.

Selezionate una delle seguenti opzioni disponibili per impostare il metodo di interruzione dalla finestra di dialogo Assegnazione **** canale:

* **Immediatamente**: ogni volta che la pianificazione viene attivata o viene ricevuto un aggiornamento, potete interrompere la riproduzione e aggiornare o riprodurre immediatamente il nuovo contenuto
* **Alla fine della voce** corrente: quando viene attivata una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere il termine della riproduzione dell’elemento corrente nella sequenza e solo dopo aver aggiornato o riprodotto il nuovo contenuto
   >[!NOTE]
   >Per impostazione predefinita, questa opzione è selezionata.
* **Alla fine della sequenza**: quando viene attivata una nuova pianificazione o viene ricevuto un aggiornamento, potete aspettare che l&#39;intera sequenza raggiunga la fine, e subito prima della sequenza desiderata, tornate al primo elemento, aggiornate o riproducete il nuovo contenuto

   >[!NOTE]
   >Utilizzando la seconda o la terza opzione è possibile che i tempi di programmazione definiti per l&#39;assegnazione vengano leggermente posticipati, in quanto il lettore aspetterà la fine dell&#39;elemento o della sequenza (dopo il tempo specificato) prima di effettuare l&#39;aggiornamento. Il ritardo dipenderà dalla durata di riproduzione dell’elemento.