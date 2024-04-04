---
title: Configurare gli agenti di replica Screens
description: Segui questa pagina per ottenere informazioni su come configurare gli agenti di replica di Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 3%

---

# Configurazione degli agenti di replica di Screens {#configuring-screens-replication-agent}

Questa pagina descrive come configurare gli agenti di replica di Screens.

## Obiettivo {#objective}

L’agente di replica di Screens è responsabile della trasmissione dei dati dei comandi come, *utente*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* e molti altri valori di questo tipo, da pubblicazione a authoring. È essenziale configurarlo in modo che l’autore possa mostrare il ping del dispositivo.

>[!NOTE]
>Per ulteriori informazioni sugli agenti di replica Screens, consulta [Agenti e comandi di replica Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Devi completare entrambe le sezioni per completare la configurazione dell’agente di replica di Screens:

1. [Abilitazione degli utenti e aggiornamento della password](#enable-users)
1. [Aggiornamento delle impostazioni per l’agente di replica Screens](#replicate-agent)

## Abilitazione degli utenti e aggiornamento della password {#enable-users}

Per abilitare gli utenti e aggiornare la password per screens-receiver-user, segui la procedura riportata di seguito:

>[!NOTE]
>Per motivi di sicurezza, si consiglia di evitare di utilizzare la password amministratore per screens-receiver-user.

1. Passa all’istanza di authoring dell’AEM.

1. Fai clic sugli strumenti > **Sicurezza** > **Utenti**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Cerca **screens-receiver-user**.

1. Seleziona la **screens-receiver-user** e fai clic su **Abilita** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Fai clic su **OK** per confermare.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Dopo aver abilitato l’utente, visualizzerai **screens-receiver-user** as **Abilitato** sotto **Stato** campo.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Seleziona la **screens-receiver-user** e fai clic su **Proprietà** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Fai clic su **Cambia password** in **Impostazioni account** dal **Dettagli** come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Immettere una nuova password in **Cambia password** e fare clic su **Salva**.

   >[!NOTE]
   >Immetti la password utente amministratore esistente in **Password** campo.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Fai clic su **Salva e chiudi**.

1. Seleziona la **screens-receiver-user** e fai clic su **Attiva** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Fai clic su **OK** per confermare.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Seleziona la **screens-receiver-user** e fai clic su **Disattiva** dalla barra delle azioni.

   >[!IMPORTANT]
   > Disattivazione **screens-receiver-user** disabilita questo utente solo dall’istanza di authoring e tutti gli utenti nell’istanza di pubblicazione rimangono attivi. Non fare clic su **Disattiva** dalla barra delle azioni, poiché la disattivazione rimuoverà l’utente anche dalle istanze di pubblicazione.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Fai clic su **OK** per confermare.

## Aggiornamento delle impostazioni per l’agente di replica Screens {#replicate-agent}

Segui la sezione seguente per aggiornare le impostazioni nell’agente di replica di Screens:

>[!IMPORTANT]
>Devi completare i seguenti passaggi su TUTTI gli agenti di replica Screens esistenti.

1. Passa all’istanza AEM.

1. Fai clic sugli strumenti > **Distribuzione** > **Replica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Fai clic su **Agenti per creazione**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Cerca tutti gli agenti di Replica Screens nell’istanza di authoring e fai clic sul collegamento, come illustrato nella figura riportata di seguito.

   >[!NOTE]
   >Cerca tutti gli agenti di Replica Screens. Il nome dell’agente di replica Screens includerà una lettera **S** nel titolo.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Fai clic su **Modifica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Verifica **Abilitato** dal **Impostazioni** scheda.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Accedi a **Trasporto** scheda da **Impostazioni agente** e aggiorna il **Utente** a **screens-receiver-user** e immettere la stessa password impostata in precedenza al punto (8) di [Abilitazione degli utenti e aggiornamento della password](#enable-users).

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Fai clic su **OK**.

1. Dopo aver completato i passaggi precedenti, puoi fare clic su **Verifica connessione** per verificare la connessione.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Se la verifica della connessione ha esito positivo, è stata completata la configurazione dell’agente di replica di Screens.
