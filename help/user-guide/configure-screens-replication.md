---
title: Configurare gli agenti di replica Screens
description: Segui questa pagina per ottenere informazioni su come configurare gli agenti di replica Screens.
role: Developer
level: Intermediate
source-git-commit: ede0eb02c97c99732c64a92c603e51bedecdbac8
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---


# Configurazione degli agenti di replica Screens {#configuring-screens-replication-agent}

Questa pagina descrive come configurare gli agenti di replica Screens.

## Obiettivo {#objective}

L&#39;agente di replica Screens è responsabile dell&#39;inserimento di dati di comandi quali: *user*, *password*, *RestartSchedule*, *maxNumberOfLogFilesToKeep*, e molti altri valori simili da pubblicare a creare. È essenziale configurarlo in modo che l’autore possa mostrare il ping del dispositivo.

>[!NOTE]
>Per ulteriori informazioni sugli agenti di replica Screens, consulta [Agenti e comandi di replica Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Devi completare entrambe le sezioni per completare la configurazione di Screens Replication Agent:

1. [Abilitazione degli utenti e aggiornamento della password](#enable-users)
1. [Aggiornamento delle impostazioni per l&#39;agente di replica Screens](#replicate-agent)

## Abilitazione degli utenti e aggiornamento della password {#enable-users}

Segui i passaggi seguenti per abilitare gli utenti e aggiornare la password per screens-ricevitore-user:

>[!NOTE]
>Per motivi di sicurezza, si consiglia di evitare di utilizzare la password dell&#39;amministratore per screens-ricevitore-user.

1. Passa all’istanza di AEM Author.

1. Fai clic su strumenti —> **Sicurezza** —> **Utenti**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Cerca **screen-ricevitore-user**.

1. Seleziona la **screen-ricevitore-user** e fai clic su **Abilita** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Fai clic su **OK** per confermare.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Dopo aver abilitato l’utente, visualizzerai l’ **screen-ricevitore-user** come **Abilitato** in **Stato** campo .

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Seleziona la **screen-ricevitore-user** e fai clic su **Proprietà** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Fai clic su **Modifica password** sotto **Impostazioni account** dal **Dettagli** , come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Immetti una nuova password nel **Modifica password** e fai clic su **Salva**.

   >[!NOTE]
   >Immetti la password utente amministratore esistente in **Password** campo .

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Fai clic su **Salva e chiudi**.

1. Seleziona la **screen-ricevitore-user** e fai clic su **Attiva** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Fai clic su **OK** per confermare.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Seleziona la **screen-ricevitore-user** e fai clic su **Disattiva** dalla barra delle azioni.

   >[!IMPORTANT]
   > Disabilitazione **screen-ricevitore-user** disabilita solo questo utente dall’istanza di authoring e tutti gli utenti nell’istanza di pubblicazione rimangono ancora attivi. Non fare clic su **Disattiva** dalla barra delle azioni, poiché la disattivazione rimuoverà l’utente anche dalle istanze di pubblicazione.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Fai clic su **OK** per confermare.

## Aggiornamento delle impostazioni per l&#39;agente di replica Screens {#replicate-agent}

Segui la sezione seguente per aggiornare le impostazioni nell’agente di replica Screens:

>[!IMPORTANT]
>È necessario completare i seguenti passaggi su TUTTI gli agenti di replica delle schermate esistenti.

1. Passa all’istanza AEM.

1. Fai clic su strumenti —> **Distribuzione** —> **Replica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Fai clic su **Agenti sull&#39;autore**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Cerca tutti gli agenti di replica Screens sull’autore e fai clic sul collegamento, come illustrato nella figura seguente.

   >[!NOTE]
   >Cerca tutti gli agenti di replica Screens. Il nome dell’agente di replica Screens includerà una lettera **S** nel titolo.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Fai clic su **Modifica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Controlla **Abilitato** dal **Impostazioni** scheda .

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Passa a **Trasporti** dalla scheda **Impostazioni agente** e aggiorna la **Utente** a **screen-ricevitore-user** e immetti la stessa password impostata in precedenza al passaggio (8) di [Abilitazione degli utenti e aggiornamento della password](#enable-users).

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Fai clic su **OK**.

1. Una volta completati i passaggi precedenti, puoi fare clic su **Prova connessione** per verificare la connessione.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Se la verifica della connessione ha esito positivo, hai completato la configurazione dell’agente di replica Screens.