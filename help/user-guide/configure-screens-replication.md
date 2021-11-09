---
title: Configura l'agente di replica Screens
description: Segui questa pagina per ottenere informazioni su come configurare l'agente di replica Screens.
role: Developer
level: Intermediate
source-git-commit: 75250cf11254499dbb30b3a5b04b1849753ea266
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 6%

---


# Configurazione dell’agente di replica Screens {#configuring-screens-replication-agent}

Questa sezione descrive come configurare l’agente di replica Screens.

## Abilitazione degli utenti e aggiornamento della password {#enable-users}

Effettua le seguenti operazioni:

1. Passa all’istanza AEM.

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
   >È necessario immettere **admin** in **Password** campo .

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

## Aggiornamento dell’agente di replica Screens {#replicate-agent}

Segui la sezione seguente per aggiornare le impostazioni nell’agente di replica Screens:

1. Passa all’istanza AEM.

1. Fai clic su strumenti —> **Distribuzione** —> **Replica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Fai clic su **Agenti sull&#39;autore**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Fai clic sul collegamento, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Fai clic su **Modifica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Controlla **Abilitato** dal **Impostazioni** scheda .

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Passa a **Trasporti** dalla scheda **Impostazioni agente** e immetti la stessa password impostata in precedenza nel passaggio (8) di [Abilitazione degli utenti e aggiornamento della password](#enable-users). Fai clic su **OK**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. Una volta completati i passaggi precedenti, puoi fare clic su **Prova connessione** per verificare la connessione.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Se la verifica della connessione ha esito positivo, hai completato la configurazione dell’agente di replica Screens.