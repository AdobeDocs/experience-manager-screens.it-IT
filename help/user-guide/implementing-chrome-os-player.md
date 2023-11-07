---
title: Implementazione di Chrome OS Player
seo-title: Implementing Chrome OS Player
description: Segui questa pagina per scoprire l’implementazione di Chrome OS Player tramite Chrome Management Console.
seo-description: Follow  this page to learn about the implementation of the Chrome OS Player using the Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 970762bb08f19ab07917dd5a21f67a007ec1143f
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 0%

---

# Implementazione di Chrome OS Player  {#implementing-chrome-os-player}

Questa sezione descrive come implementare Chrome OS Player utilizzando Chrome Management Console.

## Utilizzo di Chrome Management Console {#using-chrome-management-console}

Segui i passaggi seguenti per configurare la console di gestione Chrome:

1. Registrati alla Chrome Management Console. È necessario ottenere una licenza per Chrome Management Console. Contatto [Supporto Google](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) per ulteriori informazioni, consulta Gestire le impostazioni del dispositivo Chrome.
1. Iscrivi il dispositivo Chrome OS nel dominio attendi 15 minuti per la sincronizzazione del dispositivo con Chrome Management Console. Per ulteriori informazioni sulla registrazione del dispositivo Chrome, fare clic su [qui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome Player sarà disponibile nel Chrome Web Store.

>[!NOTE]
>
>Per la distribuzione e la gestione dei dispositivi Chrome OS, si consiglia una soluzione di gestione dei dispositivi come Chrome Management Console. Anche se, questo documento fornisce l’implementazione per Chrome Management Console, ci sono altri fornitori che affermano di fornire funzionalità simili. Contattare il fornitore del software di gestione dei dispositivi.

## Denominazione del lettore Chrome OS {#name-chrome}

Puoi assegnare un nome descrittivo del dispositivo al lettore Chrome, inviando in tal modo il nome del dispositivo assegnato a Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Chrome, ma anche di assegnare facilmente i contenuti appropriati.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Una volta registrato, il nome del lettore non può più essere modificato.

Segui i passaggi seguenti per configurare il nome nel lettore Chrome:

1. Facoltativamente, è possibile consentire agli integratori AV o agli amministratori IT di impostare l&#39;ID risorsa e la posizione come parte della registrazione aziendale.

   ![immagine](/help/user-guide/assets/chrome-device/chrome1.png)

1. Quando sarà possibile registrare il dispositivo, verranno visualizzate le opzioni disponibili.

   ![immagine](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Puoi impostare l’ID risorsa come parte dell’iscrizione Enterprise e nella console di gestione Chrome.

   ![immagine](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >I lettori Chrome devono essere iscritti all’iscrizione Enterprise e il lettore Chrome deve essere distribuito tramite Chrome Management Console; in caso contrario, l’ID risorsa restituirà vuoto (ad esempio, chrome come estensione). Il nome del dispositivo viene registrato solo al momento della registrazione. Le modifiche future non saranno accettate da Adobe Experience Manager (AEM).

### Abilitazione della modalità Kiosk (chiosco) {#enabling-kiosk-mode}

Per attivare la modalità Kiosk (Chiosco), procedere come segue:

1. Accedi a Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Sfoglia per **Gestione dei dispositivi** > **Gestione Chrome** > **Impostazioni dispositivo**.
1. Scorri verso il basso fino a **Impostazioni chiosco** e fai clic su **Gestione delle applicazioni Kiosk**.

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
1. Clic **Attività di sistema e risoluzione dei problemi**.
1. Controlla la **Riavvia dispositivo** e **Acquisizione schermo** proprietà del dispositivo. È inoltre possibile controllare lo stato e le informazioni sullo stato del dispositivo.

>[!NOTE]
>
>Tieni presente che queste impostazioni potrebbero essere attivate diversi minuti dopo la registrazione del dispositivo. Ogni opzione può diventare abilitata nel tempo.

### Configurazione della configurazione remota dei lettori Chrome OS {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player è un’applicazione abilitata per i chioschi che abilita anche la configurazione dei criteri remoti per i lettori Chrome OS.

Segui i passaggi seguenti per configurare varie opzioni del lettore:

1. Accedi a Chrome Management Console.
1. Clic **Gestione dei dispositivi** > **Gestione Chrome** > **Gestione app**. AEM Screens Player viene visualizzato nell’elenco.
1. Fai clic sull’applicazione **Lettore AEM Screens**.
1. Clic **Impostazioni chiosco** e seleziona la tua organizzazione (*se si utilizza un ambiente di test*).
1. Fai clic su **carica file di configurazione** e carica il criterio di configurazione (*File Json*).
1. Fai clic su **Salva**. Per sincronizzare i criteri è necessario riavviare il dispositivo.

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
| enableActivityUI | Abilita questa opzione per mostrare l’avanzamento di attività come download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| cloudMode | Imposta su true se desideri che il lettore Tizen si connetta a Screens as a Cloud Service. Impostare su false per connettersi a AMS o a un AEM locale. |
| cloudToken | Token di registrazione da registrare su Screens as a Cloud Service. |

>[!NOTE]
>
>Le configurazioni dei criteri vengono rigorosamente applicate e non vengono ignorate manualmente nell’interfaccia utente di amministrazione del lettore. Per consentire la configurazione manuale del lettore per un determinato criterio, non specificare il criterio in ***configurazione dei criteri,*** ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave ***rebootSchedule*** nella configurazione dei criteri.

### Utilizzo del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzione qui: [Controllo remoto Schermi](implementing-remote-control.md)
