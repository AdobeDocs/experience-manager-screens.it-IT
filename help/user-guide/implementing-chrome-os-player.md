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
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Implementazione di Chrome OS Player  {#implementing-chrome-os-player}

Questa sezione descrive come implementare Chrome OS Player utilizzando Chrome Management Console.

## Utilizzo di Chrome Management Console {#using-chrome-management-console}

Segui i passaggi seguenti per configurare la console di gestione Chrome:

1. Registrati alla Chrome Management Console. È necessario ottenere una licenza per Chrome Management Console. Contatto [Supporto Google](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) per ulteriori informazioni, consulta Gestire le impostazioni del dispositivo Chrome.
1. Iscrivi il dispositivo Chrome OS nel dominio attendi 15 minuti per la sincronizzazione del dispositivo con Chrome Management Console. Per ulteriori informazioni sulla registrazione del dispositivo Chrome, seleziona [qui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome Player è disponibile nel Chrome Web Store.

>[!NOTE]
>
>Per la distribuzione e la gestione dei dispositivi Chrome OS, si consiglia una soluzione di gestione dei dispositivi come Chrome Management Console. Anche se questo documento fornisce l’implementazione per Chrome Management Console, ci sono altri fornitori che affermano di fornire funzionalità simili. Contattare il fornitore del software di gestione dei dispositivi.

## Denominazione del lettore Chrome OS {#name-chrome}

Puoi assegnare un nome descrittivo del dispositivo al lettore Chrome, inviando in tal modo il nome del dispositivo assegnato a Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Chrome, ma anche di assegnare facilmente i contenuti appropriati.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Dopo la registrazione del lettore, il nome del lettore non può più essere modificato.

Segui i passaggi seguenti per configurare il nome nel lettore Chrome:

1. Facoltativamente, puoi consentire agli integratori Audio/Video o agli amministratori IT di impostare l’ID risorsa e la posizione come parte della registrazione Enterprise.

   ![immagine](/help/user-guide/assets/chrome-device/chrome1.png)

1. Quando è possibile registrare il dispositivo, vengono visualizzate le opzioni disponibili.

   ![immagine](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Puoi impostare l’ID risorsa come parte della registrazione Enterprise e nella console di gestione Chrome.

   ![immagine](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >I lettori Chrome devono essere iscritti all’iscrizione Enterprise e il lettore Chrome deve essere distribuito tramite Chrome Management Console; in caso contrario, l’ID risorsa restituisce vuoto (ad esempio, chrome come estensione). Il nome del dispositivo viene registrato solo al momento della registrazione. Le modifiche future non vengono prese in considerazione da Adobe Experience Manager (AEM).

### Abilitazione della modalità Kiosk (chiosco) {#enabling-kiosk-mode}

Per attivare la modalità Kiosk (Chiosco), procedere come segue:

1. Accedi a Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Sfoglia per **Gestione dei dispositivi** > **Gestione Chrome** > **Impostazioni dispositivo**.
1. Scorri verso il basso fino a **Impostazioni chiosco** e seleziona **Gestione delle applicazioni Kiosk**.

   ![chiosco](assets/kiosk.png)

1. Seleziona AEM Screens Player dal Chrome Web Store.

   >[!NOTE]
   >
   >La pubblicazione di un&#39;app in questo elenco potrebbe richiedere circa 15 minuti.

1. Seleziona **Lettore AEM Screens** dal **App chiosco per avvio automatico** a discesa.

   L&#39;applicazione delle modifiche potrebbe richiedere alcuni minuti a seconda della rete. Si consiglia di riavviare il sistema.

#### Verifica dello stato del dispositivo remoto {#checking-remote-device-status}

1. Accedi a Chrome Developer Console.
1. Sfoglia per **Gestione dei dispositivi** > **Dispositivi Chrome** e selezionare il dispositivo da controllare.
1. Seleziona **Attività di sistema e risoluzione dei problemi**.
1. Controlla la **Riavvia dispositivo** e **Acquisizione schermo** proprietà del dispositivo. È inoltre possibile controllare lo stato e le informazioni sullo stato del dispositivo.

>[!NOTE]
>
>Queste impostazioni possono essere attivate diversi minuti dopo la registrazione del dispositivo. Ogni opzione può diventare abilitata nel tempo.

### Configurazione della configurazione remota dei lettori Chrome OS {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player è un’applicazione abilitata per i chioschi che abilita anche la configurazione dei criteri remoti per i lettori Chrome OS.

Segui i passaggi seguenti per configurare varie opzioni del lettore:

1. Accedi a Chrome Management Console.
1. Seleziona **Gestione dei dispositivi** > **Gestione Chrome** > **Gestione app**. AEM Screens Player viene visualizzato nell’elenco.
1. Seleziona l’applicazione **Lettore AEM Screens**.
1. Seleziona **Impostazioni chiosco** e seleziona la tua organizzazione (*se si utilizza un ambiente di test*).
1. Seleziona **carica file di configurazione** e carica il criterio di configurazione (*File JSon*).
1. Seleziona **Salva**. Riavviare il dispositivo per sincronizzare i criteri.

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

| **Nome criterio** | **Finalità** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| registrationKey | Utilizzato per la registrazione in blocco di dispositivi utilizzando una chiave già condivisa. |
| risoluzione | Risoluzione del dispositivo. |
| rebootSchedule | Pianificazione per il riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente di amministrazione per configurare il dispositivo sul sito. Impostato su false una volta che è completamente configurato e in produzione. |
| enableOSD | Abilita l’interfaccia utente per cambiare canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false, una volta che è completamente configurato e in produzione. |
| enableActivityUI | Abilita questa opzione affinché tu possa visualizzare l’avanzamento di attività quali download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| cloudMode | Imposta su true se desideri che il lettore Chrome si connetta a Screens as a Cloud Service. Impostare su false per connettersi a AMS o a un AEM locale. |
| cloudToken | Token di registrazione da registrare su Screens as a Cloud Service. |

>[!NOTE]
>
>Le configurazioni dei criteri vengono rigorosamente applicate e non vengono ignorate manualmente nell’interfaccia utente di amministrazione del lettore. Per consentire la configurazione manuale del lettore per un determinato criterio, non specificare il criterio in ***configurazione dei criteri***. Ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave ***rebootSchedule*** nella configurazione dei criteri.

### Utilizzo del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzione qui: [Controllo remoto Schermi](implementing-remote-control.md)
