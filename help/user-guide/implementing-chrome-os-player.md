---
title: Implementazione di Chrome OS Player
seo-title: Implementazione di Chrome OS Player
description: Segui questa pagina per scoprire l'implementazione di Chrome OS Player utilizzando la console di gestione Chrome.
seo-description: Segui questa pagina per scoprire l'implementazione di Chrome OS Player utilizzando la console di gestione Chrome.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Amministrazione di schermi
role: Administrator
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---


# Implementazione di Chrome OS Player {#implementing-chrome-os-player}

Questa sezione descrive come implementare Chrome OS Player utilizzando la console di gestione Chrome.

## Utilizzo della console di gestione Chrome {#using-chrome-management-console}

Per configurare la console di gestione chrome, effettua le seguenti operazioni:

1. Registrati alla console di gestione Chrome. È necessario ottenere una licenza per Chrome Management Console. Contatta [Supporto Google](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) per gestire le impostazioni dei dispositivi Chrome per ulteriori informazioni.
1. Registra il tuo dispositivo Chrome OS nel dominio in attesa di 15 minuti perché il dispositivo si sincronizzi con la console di gestione Chrome. Per ulteriori informazioni sulla registrazione del dispositivo chrome, fai clic [qui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Il lettore Chrome sarà disponibile nello store Web Chrome.

>[!NOTE]
>
>Una soluzione di gestione dei dispositivi come Chrome Management Console è consigliata per la distribuzione e la gestione dei dispositivi OS Chrome. Anche se, questo documento fornisce l&#39;implementazione per Chrome Management Console, ci sono altri fornitori che pretendono di fornire funzionalità simili. Contattare il fornitore del software di gestione dei dispositivi.

### Abilitazione della modalità Kiosk {#enabling-kiosk-mode}

Per attivare la modalità Kiosk, effettua le seguenti operazioni:

1. Accedi a Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Passa a **Gestione dispositivi** > **Gestione Chrome** > **Impostazioni dispositivo**.
1. Scorri verso il basso fino a **Impostazioni chiosco** e fai clic su **Gestisci applicazioni chiosco**.

   ![chiosco](assets/kiosk.png)

1. Seleziona AEM Screens Player dal Web Store Chrome.

   >[!NOTE]
   >
   >L&#39;elenco di un&#39;app pubblicata di recente potrebbe richiedere circa 15 minuti.

1. Seleziona **AEM Screens Player** dal menu a discesa **Avvio automatico app chiosco** .

   Potrebbero essere necessari alcuni minuti a seconda della rete per rendere effettive le modifiche. Si consiglia di riavviare il sistema.

#### Controllo dello stato del dispositivo remoto {#checking-remote-device-status}

1. Accedi a Chrome Developer Console.
1. Vai a **Gestione dispositivi** > **Dispositivi Chrome** e seleziona il dispositivo che desideri controllare.
1. Fai clic su **Attività di sistema e risoluzione dei problemi**.
1. Controllare le proprietà **Reboot Device** e **Screen Capture** del dispositivo. È inoltre possibile controllare lo stato del dispositivo e le informazioni di integrità.

>[!NOTE]
>
>Tieni presente che queste impostazioni possono essere attivate diversi minuti dopo la registrazione del dispositivo. Ogni opzione può diventare attivata nel tempo.

### Configurazione della configurazione remota dei lettori del sistema operativo Chrome {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player è un&#39;applicazione abilitata per i chioschi che abilita anche la configurazione dei criteri remoti per i lettori di sistema operativo Chrome.

Segui i passaggi seguenti per configurare varie opzioni del lettore:

1. Accedi alla console di gestione Chrome.
1. Fai clic su **Gestione dispositivi** > **Gestione Chrome** > **Gestione app**. Nell&#39;elenco viene visualizzato AEM Screens Player.
1. Fai clic sull&#39;applicazione **AEM Screens Player**.
1. Fai clic su **Impostazioni chiosco** e seleziona la tua organizzazione (*se utilizzi un ambiente di test*).
1. Fai clic su **carica il file di configurazione** e carica il criterio di configurazione (*file Json*).
1. Fai clic su **Salva**. Per sincronizzare il criterio, è necessario riavviare il dispositivo.

>[!NOTE]
>
>Riavvia il dispositivo per sincronizzare le modifiche ai criteri.

#### Esempio di file JSON dei criteri {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### Attributi e finalità dei criteri {#policy-attributes-and-purpose}

Nella tabella seguente sono riepilogati i criteri con le relative funzioni.

| **Nome criterio** | **Scopo** |
|---|---|
| *server* | URL del server Adobe Experience Manager |
| *risoluzione* | Risoluzione del dispositivo operativo Chrome |
| *RestartSchedule* | Pianificazione del riavvio del lettore Chrome |
| *enableAdminUI* | Abilita l’interfaccia utente amministratore ai tecnici per configurare il dispositivo sul sito. Imposta su false una volta configurato completamente e in produzione. |
| *enableOSD* | Abilita l’interfaccia utente del commutatore del canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false una volta configurata completamente e in produzione. |
| *enableActivityUI* | Attiva per mostrare l&#39;avanzamento delle attività come il download e la sincronizzazione. Attiva per la risoluzione dei problemi e disattiva una volta configurato completamente e in produzione. |

>[!NOTE]
>
>Le configurazioni dei criteri vengono applicate in modo rigoroso e non vengono sostituite manualmente nell’interfaccia utente amministratore del lettore. Per consentire la configurazione manuale del lettore per un criterio specifico, non specificare il criterio nella ***configurazione del criterio,*** ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave ***RestartSchedule*** nella configurazione del criterio.
