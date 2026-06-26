---
title: Configurare gli agenti di replica di Screens
description: Scopri come configurare gli agenti di replica di Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
TQID: https://experienceleague.adobe.com/ms01oXXn6BqzkscgjG0o0g1pq-wEawpMy1eel6Uz1uM
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 531
ht-degree: 4%

---

# Configurazione degli agenti di replica di Screens {#configuring-screens-replication-agent}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Questa pagina descrive come configurare gli agenti di replica di Screens.

## Obiettivo {#objective}

L&#39;agente di replica di Screens è responsabile della trasmissione dei dati dei comandi, ad esempio *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* e molti altri valori di questo tipo da Publish a Author. È essenziale configurare questo agente in modo che l’autore possa mostrare il ping del dispositivo.

>[!NOTE]
>Per ulteriori informazioni sugli agenti di replica di Screens, vedere [Agenti e comandi di replica di Screens](https://experienceleague.adobe.com/it/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Completare entrambe le sezioni se si desidera completare la configurazione dell&#39;agente di replica di Screens:

1. [Abilitazione degli utenti e aggiornamento della password](#enable-users)
1. [Aggiornamento delle impostazioni per l&#39;agente di replica di Screens](#replicate-agent)

## Abilitazione degli utenti e aggiornamento della password {#enable-users}

Per abilitare gli utenti e aggiornare la password per `screens-receiver-user`, eseguire la procedura seguente:

>[!NOTE]
>Per motivi di sicurezza, si consiglia di evitare di utilizzare la password amministratore per `screens-receiver-user`.

1. Passa all’istanza di AEM Author.

1. Fai clic su Strumenti > **Sicurezza** > **Utenti**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Cerca **`screens-receiver-user`**.

1. Fai clic su **`screens-receiver-user`** e fai clic su **Abilita** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Fai clic su **OK** per confermare.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Dopo aver abilitato l&#39;utente, **`screens-receiver-user`** verrà visualizzato come **Abilitato** nel campo **Stato**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Fare clic su **`screens-receiver-user`** e su **Proprietà** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Fare clic su **Cambia password** in **Impostazioni account** nella scheda **Dettagli**, come illustrato nella figura seguente.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Immettere una nuova password nella finestra di dialogo **Cambia password** e fare clic su **Salva**.

   >[!NOTE]
   >Immetti la password utente amministratore esistente nel campo **Password**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Fai clic su **Salva e chiudi**.

1. Fai clic su **`screens-receiver-user`** e fai clic su **Attiva** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Fai clic su **OK** per confermare.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Fai clic su **`screens-receiver-user`** e fai clic su **Disattiva** nella barra delle azioni.

   >[!IMPORTANT]
   > La disabilitazione di **`screens-receiver-user`** comporta solo la disabilitazione dell&#39;utente dall&#39;istanza di authoring e l&#39;attivazione di tutti gli utenti nell&#39;istanza di pubblicazione. Non fare clic su **Disattiva** dalla barra delle azioni, poiché la disattivazione rimuove l&#39;utente anche dalle istanze di pubblicazione.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Fai clic su **OK** per confermare.

## Aggiornamento delle impostazioni per l&#39;agente di replica di Screens {#replicate-agent}

Segui la sezione seguente per aggiornare le impostazioni nell’agente di replica di AEM Screens:

>[!IMPORTANT]
>Completa i seguenti passaggi per TUTTI gli agenti di replica di AEM Screens esistenti.

1. Passa all’istanza di AEM.
1. Fare clic su Strumenti > **Distribuzione** > **Replica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Fare clic su **Agenti sull&#39;autore**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Cerca tutti gli agenti di replica di AEM Screens sull’autore e fai clic sul collegamento, come illustrato nella figura riportata di seguito.

   >[!NOTE]
   >Cerca tutti gli agenti di replica di AEM Screens. Il nome dell&#39;agente di replica di Screens include la lettera **S** nel titolo.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Fai clic su **Modifica**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Seleziona **Abilitato** dalla scheda **Impostazioni**.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Passa alla scheda **Trasporto** dalla finestra di dialogo **Impostazioni agente**, aggiorna **Utente** in **`screens-receiver-user`** e immetti la stessa password impostata in precedenza nel passaggio (8) di [Abilitazione degli utenti e aggiornamento della password](#enable-users).

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Fai clic su **OK**.

1. Dopo aver completato i passaggi precedenti, fare clic su **Verifica connessione** per verificare la connessione.

   ![immagine](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Se la verifica della connessione ha esito positivo, è stata completata la configurazione dell&#39;agente di replica di Screens.

