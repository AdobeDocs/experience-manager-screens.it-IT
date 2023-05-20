---
title: Servizio notifiche AEM Screens
seo-title: AEM Screens Notifications Service
description: Segui questa pagina per ulteriori informazioni su come monitorare l’attività del dispositivo.
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Servizio notifiche AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Servizio notifiche AEM Screens***, descrive la funzione in cui è possibile monitorare l&#39;attività del dispositivo.

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Configurazione delle impostazioni e-mail**
* **Notifica e-mail**
* **Caso d’uso di esempio**

>[!CAUTION]
>
>Questa funzionalità di AEM Screens è disponibile solo se è stato installato AEM 6.3.2 Feature Pack 3 o AEM 6.4.1 Screens Feature Pack 1.
>
>Per accedere a questo Feature Pack, contatta il supporto Adobe e richiedi l’accesso. Una volta ricevute le autorizzazioni, puoi scaricarle da Condivisione pacchetti.

## Panoramica {#overview}

***Servizio notifiche AEM Screens***, consente agli amministratori di ricevere un’e-mail se un lettore AEM screens non esegue il ping per un periodo di tempo configurabile.

Questo servizio può essere configurato nella console web OSGi.

## Configurazione delle impostazioni e-mail {#configuring-email-settings}

Per configurare le impostazioni delle notifiche e-mail, effettua le seguenti operazioni:

1. Apri **Configurazione della console web Adobe Experience Manager**.
1. Apri **Servizio di monitoraggio e-mail del dispositivo Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Definisci i campi seguenti per configurare le impostazioni per l’e-mail:

   **Percorso dispositivi** Immetti il percorso dei progetti Screens che desideri monitorare. Il percorso è in genere `/home/users/screens/<Name of your project>`.

   Ad esempio, se il progetto è **We.Retail**, utilizzerai il percorso del progetto come ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Specifica il percorso del progetto, dove si trovano gli utenti del dispositivo.

   **Frequenza Schedule** Specifica un orario (ad esempio, 17:00 o 17:00) o una frequenza in ore (ad esempio 1) in cui il monitoraggio deve inviare le e-mail.

   **Timeout ping** Specifica l&#39;intervallo in minuti dopo il quale un dispositivo deve essere considerato non raggiungibile.

   **Server SMTP** Specifica il server SMTP utilizzato per l&#39;invio di e-mail.

   **Porta SMTP** Immettere la porta SMTP.

   **Usa TLS** Transport Layer Security (TLS) consente di utilizzare una comunicazione protetta con il server SMTP.

   Si consiglia di utilizzare TLS per la connessione sicura ai server di posta aziendali. Rivolgersi all&#39;amministratore della posta per verificare i valori appropriati.

   **nome utente** Specifica il nome utente per l’invio di e-mail.

   **password** Specifica la password per l’invio delle e-mail.

   **Destinatario** Specifica l’indirizzo e-mail del destinatario.

   >[!NOTE]
   >
   >Puoi inserire un solo indirizzo e-mail. Per inviare un’e-mail in blocco, crea un gruppo o una lista di distribuzione con gli utenti pertinenti.

1. Clic **Salva** per configurare l’attività di monitoraggio tramite un’e-mail per il dispositivo AEM Screens.

## Notifica e-mail {#email-notification}

Una volta impostata la configurazione per le notifiche e-mail, riceverai una notifica e-mail che conterrà il collegamento al dispositivo effettivo segnalato come inattivo.

L’accesso a tale collegamento ti porterà direttamente al dashboard del dispositivo.

Le e-mail verranno inviate solo se esiste almeno un dispositivo che non ha eseguito il ping per il timeout di ping specificato e non esegue ancora il ping al momento della generazione dell’e-mail.

### Casi d’uso di esempio {#example-use-cases}

L’esempio seguente descrive alcuni scenari di riferimento per configurare le proprietà da Screens Device Email Monitoring Service.

**Scenario 1**:

Se imposti la frequenza di pianificazione su 1:00 e il timeout del ping su 60, se il dispositivo Screens non esegue il ping tra le 12:00 e le 13:00, riceverai una notifica e-mail che conferma l’inattività del dispositivo.

**Scenario 2**:

Se imposti la frequenza di pianificazione su 1 e il timeout del ping su 60, se il dispositivo Screens non esegue il ping tra una volta e un’ora particolare della giornata, riceverai una notifica e-mail di conferma dell’inattività del dispositivo.
