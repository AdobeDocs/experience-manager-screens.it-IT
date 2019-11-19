---
title: Servizio di notifica AEM Screens
seo-title: Servizio di notifica AEM Screens
description: Segui questa pagina per saperne di più su come monitorare l'attività del dispositivo.
seo-description: Segui questa pagina per saperne di più su come monitorare l'attività del dispositivo.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Servizio di notifica AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Il servizio*** di notifica AEM Screens descrive la funzione in cui è possibile monitorare l’attività del dispositivo.

Questa sezione illustra i seguenti argomenti:

* **Panoramica**
* **Configurazione delle impostazioni e-mail**
* **Notifica e-mail**
* **Esempio di caso di utilizzo**

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3.2 Feature Pack 3 o AEM 6.4.1 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l'accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

## Panoramica {#overview}

***Il servizio*** di notifica AEM Screens consente agli amministratori di ricevere un’e-mail se un lettore di schermate AEM non esegue il ping per un periodo di tempo configurabile.

Questo servizio può essere configurato nella console Web OSGi.

## Configurazione delle impostazioni e-mail {#configuring-email-settings}

Per configurare le impostazioni di notifica e-mail, effettuate le operazioni seguenti:

1. Apri la configurazione **della console Web di** Adobe Experience Manager.
1. Aprite **Screens Device Email Monitoring Service**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Definite i seguenti campi per configurare le impostazioni per l’e-mail:

   **Percorso** dispositivi Immettere il percorso dei progetti Screens che si desidera monitorare. Di solito il percorso è `/home/users/screens/<Name of your project>`.

   Ad esempio, se il progetto è **We.Retail**, utilizzerete il percorso del progetto come ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Specificate il percorso del progetto, dove si trovano gli utenti del dispositivo.

   **Frequenza** programmata Specificate un'ora (ad esempio, 5:00 pm o 17:00) o una frequenza in ore (ad esempio, 1) in cui il monitor deve inviare le e-mail.

   **Timeout** ping Indica l'intervallo in minuti dopo il quale un dispositivo deve essere considerato non raggiungibile.

   **Server** SMTP Specifica il server SMTP utilizzato per inviare e-mail.

   **Porta** SMTP Immettere la porta SMTP.

   **Il protocollo TLS** (Transport Layer Security) consente di utilizzare una comunicazione sicura con il server SMTP.

   Si consiglia di utilizzare TLS per la connessione protetta ai server di posta aziendale. Verificate i valori appropriati con il vostro amministratore di posta.

   **nome utente** Specificate il nome utente per l’invio delle e-mail.

   **password** Specificate la password per l'invio delle e-mail.

   **Destinatario** Specificate l'indirizzo e-mail del destinatario.

   >[!NOTE]
   >
   >Potete immettere un solo indirizzo e-mail. Per inviare un messaggio e-mail in blocco, create un gruppo o una lista di distribuzione con gli utenti interessati.

1. Fate clic su **Salva** per configurare l'attività del monitor tramite un messaggio e-mail per il dispositivo AEM Screens.

## Email Notification {#email-notification}

Una volta impostata la configurazione per le notifiche e-mail, riceverete una notifica e-mail che conterrà il collegamento al dispositivo effettivo segnalato di inattività.

L'accesso a tale collegamento consente di accedere direttamente al dashboard del dispositivo.

Le e-mail verranno inviate solo se è presente almeno un dispositivo che non ha eseguito il ping per il timeout di ping specificato e non esegue ancora il ping al momento della generazione dell'e-mail.

###  Esempi di utilizzo {#example-use-cases}

L'esempio seguente descrive alcuni scenari di riferimento, per configurare le proprietà da Screens Device Email Monitoring Service.

**Scenario 1**:

Se imposti la frequenza di programmazione come 1:00 e il timeout di ping come 60, se il dispositivo Screens non esegue il ping tra le 12:00 e le 13:00, riceverai una notifica e-mail di conferma dell'inattività del dispositivo.

**Scenario 2**:

Se imposti la frequenza di programmazione su 1 e il timeout di ping su 60, se il dispositivo Screens non esegue il ping tra una volta in un dato momento della giornata, riceverai una notifica e-mail di conferma dell’inattività del dispositivo.
