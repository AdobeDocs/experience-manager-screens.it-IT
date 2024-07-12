---
title: Implementazione di Chrome OS Player
description: Scopri l’implementazione di Chrome OS Player tramite Chrome Management Console.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# Implementazione di Chrome OS Player {#implementing-chrome-os-player}

Questa sezione descrive come implementare Chrome OS Player utilizzando Chrome Management Console.

## Utilizzo di Chrome Management Console {#using-chrome-management-console}

Segui i passaggi seguenti per configurare la console di gestione Chrome:

1. Registrarsi a Chrome Management Console. È necessario ottenere una licenza per Chrome Management Console. Per ulteriori informazioni, contattare il [supporto Google](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) per gestire le impostazioni dei dispositivi Chrome.
1. Registra il dispositivo del sistema operativo Chrome nel dominio e attendi 15 minuti per la sincronizzazione del dispositivo con Chrome Management Console. Per ulteriori informazioni sulla registrazione del dispositivo Chrome, fare clic [qui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome Player è disponibile nel Chrome Web Store.

>[!NOTE]
>
>Per l&#39;installazione e la gestione dei dispositivi del sistema operativo Chrome è consigliata una soluzione di gestione dei dispositivi come Chrome Management Console. Anche se questo documento fornisce l&#39;implementazione per Chrome Management Console, esistono altri fornitori che affermano di fornire funzionalità simili. Contattare il fornitore del software di gestione dei dispositivi.

## Denominazione del lettore del sistema operativo Chrome {#name-chrome}

Puoi assegnare un nome descrittivo al tuo lettore Chrome, inviando in tal modo il nome del dispositivo assegnato a Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Chrome, ma anche di assegnare facilmente il contenuto appropriato.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Dopo la registrazione del lettore, il nome del lettore non può più essere modificato.

Per configurare il nome in Chrome Player, attenersi alla procedura descritta di seguito:

1. Facoltativamente, puoi consentire agli integratori Audio-Video o agli amministratori IT di impostare l’ID risorsa e la posizione come parte della registrazione aziendale.

   ![immagine](/help/user-guide/assets/chrome-device/chrome1.png)

1. Quando è possibile registrare il dispositivo, vengono visualizzate le opzioni disponibili.

   ![immagine](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. È possibile impostare l&#39;ID risorsa come parte dell&#39;iscrizione Enterprise e in Chrome Management Console.

   ![immagine](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome Player deve essere iscritto all’iscrizione Enterprise e Chrome Player deve essere distribuito tramite Chrome Management Console; in caso contrario, l’ID risorsa restituisce un valore vuoto (ad esempio, Chrome come estensione). Il nome del dispositivo viene registrato solo al momento della registrazione. Le modifiche future non vengono prese in considerazione da Adobe Experience Manager (AEM).

### Abilitazione della modalità Kiosk (chiosco) {#enabling-kiosk-mode}

Per attivare la modalità Kiosk (Chiosco), procedere come segue:

1. Accedi a Chrome Developer Console.

   ![schermata_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Passa a **Gestione dispositivi** > **Gestione Chrome** > **Impostazioni dispositivi**.
1. Scorri verso il basso fino a **Impostazioni chiosco** e fai clic su **Gestisci applicazioni chiosco**.

   ![chiosco](assets/kiosk.png)

1. Fare clic su AEM Screens Player dal Chrome Web Store.

   >[!NOTE]
   >
   >La pubblicazione di un&#39;app in questo elenco potrebbe richiedere circa 15 minuti.

1. Fai clic su **AEM Screens Player** dal menu a discesa **Auto Launch Kiosk App**.

   L&#39;applicazione delle modifiche potrebbe richiedere alcuni minuti a seconda della rete. Si consiglia di riavviare il sistema.

#### Verifica dello stato del dispositivo remoto {#checking-remote-device-status}

1. Accedi a Chrome Developer Console.
1. Passare a **Gestione dispositivi** > **Dispositivi Chrome** e fare clic sul dispositivo che si desidera controllare.
1. Fare clic su **Attività di sistema e risoluzione dei problemi**.
1. Controllare le proprietà **Riavvia dispositivo** e **Cattura schermo** del dispositivo. È inoltre possibile controllare lo stato e le informazioni sullo stato del dispositivo.

>[!NOTE]
>
>Queste impostazioni possono essere attivate diversi minuti dopo la registrazione del dispositivo. Ogni opzione può diventare abilitata nel tempo.

### Configurazione della configurazione remota dei lettori del sistema operativo Chrome {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player è un&#39;applicazione abilitata per i chioschi che consente anche la configurazione remota dei criteri per i lettori del sistema operativo Chrome.

Segui i passaggi seguenti per configurare le varie opzioni del lettore:

1. Accedere a Chrome Management Console.
1. Fai clic su **Gestione dispositivi** > **Gestione Chrome** > **Gestione app**. AEM Screens Player viene visualizzato nell’elenco.
1. Fare clic sull&#39;applicazione **AEM Screens Player**.
1. Fai clic su **Impostazioni chiosco** e fai clic sull&#39;organizzazione (*se utilizzi un ambiente di test*).
1. Fai clic su **carica file di configurazione** e carica i criteri di configurazione (*file JSon*).
1. Fai clic su **Salva**. Riavviare il dispositivo per sincronizzare i criteri.

>[!NOTE]
>
>Riavviare il dispositivo per sincronizzare le modifiche ai criteri.

#### Esempio di file JSON per i criteri {#example-policy-json-file}

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

Nella tabella seguente vengono riepilogati i criteri e le relative funzioni.

| **Nome criterio** | **Scopo** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| registrationKey | Utilizzato per la registrazione in blocco di dispositivi utilizzando una chiave già condivisa. |
| risoluzione | Risoluzione del dispositivo. |
| rebootSchedule | Pianificazione per il riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente di amministrazione per configurare il dispositivo sul sito. Impostato su false una volta che è completamente configurato e in produzione. |
| enableOSD | Abilita l’interfaccia utente per cambiare canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false, una volta che è completamente configurato e in produzione. |
| enableActivityUI | Abilita questa opzione affinché tu possa visualizzare l’avanzamento di attività quali download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| cloudMode | Impostare su true se si desidera che Chrome Player si connetta a Screens as a Cloud Service. Impostare su false per connettersi a AMS o a un AEM locale. |
| cloudToken | Token di registrazione per la registrazione a Screens as a Cloud Service. |

>[!NOTE]
>
>Le configurazioni dei criteri vengono rigorosamente applicate e l’interfaccia utente di amministrazione del lettore non viene bypassata manualmente. Per consentire la configurazione manuale del lettore per un determinato criterio, non specificare il criterio nella ***configurazione del criterio***. Se ad esempio si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave ***rebootSchedule*** nella configurazione dei criteri.

### Uso del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzionalità: [Controllo remoto Screens](implementing-remote-control.md)
