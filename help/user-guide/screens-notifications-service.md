---
title: Servizio notifiche AEM Screens
description: Scopri come monitorare l’attività dei dispositivi per AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Servizio notifiche AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Il servizio AEM Screens Notifications*** descrive l&#39;attività del dispositivo di monitoraggio.

Questa sezione tratta i seguenti argomenti:

* **Panoramica**
* **Configurazione delle impostazioni e-mail**
* **Notifica e-mail**
* **Caso d&#39;uso di esempio**

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. -->

## Panoramica {#overview}

***AEM Screens Notifications Service*** consente agli amministratori di ricevere un&#39;e-mail se un lettore AEM Screens non esegue il ping per un periodo di tempo configurabile.

Questo servizio può essere configurato nella console web OSGi.

## Configurazione delle impostazioni e-mail {#configuring-email-settings}

Segui i passaggi seguenti per configurare le impostazioni delle notifiche e-mail:

1. Apri **Configurazione console Web Adobe Experience Manager**.
1. Aprire **Servizio Monitoraggio e-mail dispositivo Screens**.

   ![schermata_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Definisci i campi seguenti per configurare le impostazioni per l’e-mail:

   **Percorso dispositivi** Immettere il percorso dei progetti Screens che si desidera monitorare. Il percorso è in genere `/home/users/screens/<Name of your project>`.

   Ad esempio, se il progetto è **`We.Retail`**, utilizza il percorso del progetto come ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Specifica il percorso del progetto, dove si trovano gli utenti del dispositivo.

   **Frequenza pianificazione** - Specificare un orario (ad esempio, 17:00 o 17:00) o una frequenza in ore (ad esempio, 1) in cui il monitoraggio deve inviare le e-mail.

   **Timeout ping** - Questo campo specifica l&#39;intervallo in minuti dopo il quale un dispositivo deve essere considerato non raggiungibile.

   **Server SMTP** - Specifica il server SMTP utilizzato per l&#39;invio di e-mail.

   **Porta SMTP** - Immettere la porta SMTP.

   **Usa TLS** - TLS (Transport Layer Security) consente di utilizzare una comunicazione protetta con il server SMTP.

   L&#39;Adobe consiglia di utilizzare TLS per la connessione sicura ai server di posta aziendali. Rivolgersi all&#39;amministratore della posta per ottenere i valori appropriati.

   **nomeutente** - Specificare il nome utente per l&#39;invio di e-mail.

   **password** - Specifica la password per l&#39;invio di e-mail.

   **Destinatario** - Specifica l&#39;indirizzo e-mail del destinatario.

   >[!NOTE]
   >
   >Puoi inserire un solo indirizzo e-mail. Per inviare un’e-mail in blocco, crea un gruppo o una lista di distribuzione con gli utenti interessati.

1. Fai clic su **Salva** per configurare l&#39;attività di monitoraggio tramite un&#39;e-mail per il dispositivo AEM Screens.

## Notifica e-mail {#email-notification}

Dopo aver impostato la configurazione per le notifiche e-mail, riceverai una notifica e-mail contenente il collegamento al dispositivo effettivo di cui viene segnalata l’inattività.

L’accesso a tale collegamento ti porta direttamente al dashboard del dispositivo.

Le e-mail vengono inviate solo se:

* esiste almeno un dispositivo che non ha eseguito il ping per il timeout di ping specificato e
* non effettua ancora il ping al momento della generazione dell’e-mail.

### Casi d’uso di esempio {#example-use-cases}

Nell&#39;esempio seguente vengono descritti alcuni scenari di riferimento per configurare le proprietà da Screens Device Email Monitoring Service.

**Scenario 1**

Puoi impostare la frequenza di pianificazione su 1:00 e il timeout del ping su 60. Quindi, se il dispositivo AEM Screens non esegue il ping tra le 12:00 e le 13:00, ricevi una notifica e-mail che conferma l’inattività del dispositivo.

**Scenario 2**

Puoi impostare la frequenza di pianificazione su 1 e il timeout del ping su 60. Quindi, se il dispositivo AEM Screens non esegue il ping immediatamente in un determinato momento della giornata, ricevi una notifica e-mail che conferma l’inattività del dispositivo.
