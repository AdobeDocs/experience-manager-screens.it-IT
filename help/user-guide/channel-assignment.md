---
title: Assegnazione canale
description: Scopri Assegnazione canale e ripartizione giornaliera.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
TQID: https://experienceleague.adobe.com/3KiJEdVpZNlcvEo9PBzkyYJqIsQfBgXQY7-HlZZVxVE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: ba4275ba-c29a-4197-90dc-5a633402ca3c
  - id: d4878390-3838-4e80-8cb3-33bc1a01ea16
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 1285
ht-degree: 2%

---

# Assegnazione canale {#channel-assignment}

>[!IMPORTANT]
>Questa sezione illustra l’assegnazione dei canali e la pianificazione dei canali per Feature Pack precedenti alla versione Screens di AEM 6.5.5.

Dopo aver impostato una visualizzazione, assegna un canale a una visualizzazione per visualizzarne il contenuto.

Questa pagina mostra come assegnare un canale alla visualizzazione.

Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>È possibile assegnare più canali a una visualizzazione.

## Assegnazione di un canale {#assign-a-channel}

Per assegnare un canale a una visualizzazione, segui i passaggi seguenti:

1. Passa alla visualizzazione richiesta, ad esempio **Progetto demo** > **Posizioni** > **SanJose** > **Visualizzazione store**.

   ![immagine](assets/screen_shot_2018-08-23at25359pm.png)

1. Fare clic su **Assegna canale** nella barra delle azioni.

   oppure

   Fai clic su **Dashboard** e su **+Assegna canale** dal pannello **CANALI ASSEGNATI** per aprire la finestra di dialogo **Assegnazione canale**.

   ![immagine](/help/user-guide/assets/channel-assign1.png)

   Puoi configurare le proprietà dalla finestra di dialogo **Assegnazione canale** dalla sezione seguente. Consulta la sezione [Proprietà canale](#channel-properties) per ulteriori informazioni sulle proprietà del canale.

## Informazioni sulle proprietà del canale da Assegnazione canale {#channel-properties}

### Canale di riferimento {#ref-channel}

Un canale di riferimento consente di fornire un riferimento al canale desiderato, in base al nome del canale o al percorso del canale.

* **per percorso** - Fornisci un riferimento esplicito utilizzando il percorso assoluto del canale.

* **per nome** - Immetti il nome del canale che viene risolto in un canale effettivo in base al contesto. Questa funzione ti consente di creare una versione locale di un canale in modo da poter risolvere dinamicamente il contenuto specifico della posizione. Ad esempio, un canale con il nome *offerte del giorno*, in cui il contenuto effettivo sarebbe diverso in due città, ma si dispone ancora del ruolo canale sano su tutte le visualizzazioni.

### Ruolo canale {#role-channel}

Il ruolo del canale definisce il contesto della visualizzazione. Il ruolo esegue il targeting di varie azioni ed è indipendente dal canale effettivo che svolge il ruolo.

### Priorità {#priority-channel}

La priorità viene utilizzata per ordinare le assegnazioni nel caso in cui più corrispondano ai criteri di riproduzione. Quello con il valore più alto ha sempre la precedenza sui valori più bassi. Ad esempio, se sono presenti due canali A e B. A ha una priorità di 1 e B ha una priorità di 2, quindi viene visualizzato il canale B, in quanto ha una priorità più alta di A.

>[!NOTE]
>La priorità per un canale è impostata come numero (minimo 1) nella finestra di dialogo **Assegnazione canale**, come indicato in precedenza. Inoltre, i canali assegnati vengono ordinati in base alla priorità decrescente.

### Eventi supportati {#supported-events-channel}

* **Caricamento iniziale** - Carica il canale all&#39;avvio del lettore. Può essere assegnato a più canali con una pianificazione.
* **Schermata di inattività** - Carica quando lo schermo è inattivo. Può essere assegnato a più canali con una pianificazione.
* **Timer** - Deve essere impostato quando viene fornita una pianificazione.
* **Interazione utente** - Il lettore passa al canale specificato se sullo schermo è presente un&#39;interazione dell&#39;utente (touch) in un canale inattivo e viene caricato quando lo schermo viene toccato.

### Metodo di interruzione {#interruption-method-channel}

>[!IMPORTANT]
>
> Questa opzione è disponibile solo con <!--AEM 6.4 Feature Pack 8 or -->AEM 6.5 Feature Pack 4.

In qualità di autore di contenuti, specifica quando un canale viene interrotto. In questo modo è possibile tagliare i contenuti non critici, se necessario, ma facoltativamente consentire la riproduzione di contenuti importanti prima di interromperne la riproduzione a causa della programmazione.

Fare clic su una delle opzioni seguenti disponibili per impostare il metodo di interruzione nella finestra di dialogo **Assegnazione canale**:

* **Immediatamente** - Quando la pianificazione si attiva o viene ricevuto un aggiornamento, puoi interrompere la riproduzione e aggiornare immediatamente o riprodurre il nuovo contenuto.
* **Alla fine dell&#39;elemento corrente** - Quando si attiva una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere che l&#39;elemento corrente della sequenza finisca la riproduzione. Solo in seguito è possibile aggiornare o riprodurre il nuovo contenuto.

  >[!NOTE]
  >Questa opzione è selezionata per impostazione predefinita.
* **Alla fine della sequenza** - Quando si attiva una nuova pianificazione o viene ricevuto un aggiornamento, è possibile attendere che l&#39;intera sequenza raggiunga la fine. Quindi, immediatamente prima della sequenza desiderata, puoi tornare al primo elemento, aggiornare o riprodurre il nuovo contenuto.

  >[!NOTE]
  >Se si utilizza la seconda o la terza opzione, gli orari di programmazione definiti nell&#39;assegnazione potrebbero subire un leggero differimento. Il motivo è che il lettore attende la fine dell’elemento o della sequenza (dopo l’ora specificata) prima di eseguire l’aggiornamento. Il ritardo dipende dalla durata di riproduzione dell’elemento.

### Pianificazione {#schedule-channel}

Pianifica consente di fornire una descrizione testuale di quando deve apparire il canale. Ti consente inoltre di definire una data di inizio (**attiva da**) e una data di fine (**attiva fino a**) per il canale da visualizzare.

**Descrizione comando attrazione**

Mostra descrizione comando attrazione definisce se la descrizione comando attrazione (&quot;*Toccare un punto qualsiasi per iniziare*&quot;) deve essere visualizzata o meno mentre il canale è in esecuzione.

### DayParting {#dayparting}

Le pianificazioni, se combinate con **DayParting**, ti consentono di impostare una pianificazione globale con più canali in esecuzione in orari specifici del giorno e di riutilizzare tale configurazione per tutte le visualizzazioni contemporaneamente.

DayParting viene definito come suddivisione di un giorno in intervalli di tempo e specifica quale contenuto viene riprodotto all’ora desiderata. AEM Screens consente di pianificare i canali in termini di DayPparting entro un giorno, una settimana o un mese in base al requisito.

Gli esempi seguenti illustrano la suddivisione giornaliera nei canali in tre diversi scenari:

#### Riproduzione di contenuti in un singolo giorno suddiviso in più slot temporali {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Questo esempio mostra come un ristorante utilizza DayParting per mostrare il menu per la colazione, il pranzo e la cena.

In questo caso, puoi dividere ogni giorno in tre diversi intervalli di tempo in modo che il contenuto del canale venga riprodotto nell’ora specificata del giorno:

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| Menu_A | Colazione |  | Dopo 6:00 e prima di 11:00 |
| Menu_B | Pranzo |  | Dopo 11:00 e prima di 15:00 |
| Menu_C | Cena |  | Dopo 15:00 e prima di 20:00 |

#### Riproduzione di contenuti in un giorno specifico della settimana {#playing-content-on-a-particular-day-of-the-week}

Questo esempio mostra il dayParting ottenuto in un casinò in cui si verifica un evento live ogni fine settimana dalle 20:00 alle 22:10:00 e i piatti speciali sono disponibili per il menu di cena dopo le 22:00 alle 13:00.:00:00:00:00

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
   <td>21 ottobre 2017 - 22 ottobre 2017 <br /> dopo le 22:00 prima dell'1:00</td>
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

Questo esempio mostra il DayParting per un negozio che visualizza la raccolta invernale con la stessa pianificazione nel mese di dicembre. Ma poiché il canale B ha la priorità impostata su 2, durante quella settimana; il canale B riproduce il suo contenuto invece del canale A.

| **Canale** | **Ruolo** | **Priorità** | **Pianificazione** |
|---|---|---|---|
| A | Inverno | 1 | 1 dicembre 2017 - 31 dicembre 2017 |
| B | Natale | 2 | 24 dicembre 2017 - 31 dicembre 2017 |


>[!NOTE]
>
> Per ulteriori informazioni su DayParting, vedere le sezioni seguenti:
>
>* [Gestione della ricorrenza in Assets](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [Gestione della ricorrenza per Assets in un canale](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
