---
title: Giocatore Tizen
description: Scopri l’installazione e il funzionamento del lettore Tizen.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 1%

---

# Implementazione di Tizen player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Segui i passaggi seguenti per implementare Tizen player per AEM Screens:

1. Accedi a [Download di AEM Screens Player](https://download.macromedia.com/screens/) per scaricare il lettore Tizen.

1. Installare il lettore Tizen *(.zip)* dal computer locale.

## Configurazione del server http {#setting-local-server}

>[!NOTE]
> Estrai il file zip e rendi disponibile il lettore Tizen tramite un `http server`. (Il `http server` non deve essere un server locale o Apache).

Effettua le seguenti operazioni:

1. Copiare i due file estratti, ad esempio `AEMScreensPlayer.wgt` e `sssp_config.xml` nella directory principale del server web Apache locale.

   >[!NOTE]
   >Il `AEMScreensPlayer.wgt`è l’effettiva applicazione lettore Tizen e `sssp_config.xml` contiene informazioni su questa mappa che consentono di installarla sul dispositivo Tizen.

1. Ottieni l’IP o l’URL del server HTTP locale (e il percorso della cartella contenente i file estratti al passaggio 2, se estratti in una sottocartella e non in una cartella principale).

1. Il lettore Tizen scarica il programma di installazione dal server locale.

### Denominazione del lettore Tizen {#name-tizen}

Puoi assegnare un nome descrittivo al tuo lettore Tizen, inviando in tal modo il nome del dispositivo assegnato a Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Tizen, ma anche di assegnare facilmente il contenuto appropriato.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Dopo la registrazione del lettore, il nome del lettore non può più essere modificato.

Segui i passaggi seguenti per configurare il nome nel lettore Tizen:

1. Fare clic sul pulsante del menu sul telecomando.
1. Accedi a **Rete** > **Nome dispositivo** in modo da poter assegnare un nome al lettore.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Segui i passaggi seguenti sul dispositivo Samsung in modo da poter completare l’installazione di AEM Screens Player sul dispositivo:

1. Passa al dispositivo Samsung e accendi.
1. Fai clic su **MENU** dal telecomando del dispositivo e scorrere verso il basso fino a **Sistema** dalla barra di navigazione a sinistra.
1. Scorri verso il basso e fai clic su **Gioca tramite** e modificarla in **Utilità di avvio URL** opzione.
   ![immagine](/help/user-guide/assets/tizen/rms-2.png)
1. Quando l&#39;utilità di avvio URL è impostata, premere il tasto **Home** dal telecomando.
1. Accedi a **Impostazioni modulo di avvio URL** e immettere l&#39;indirizzo IP del server localhost e fare clic su **Fine**.

   >[!NOTE]
   >Il lettore Tizen deve essere in grado di connettersi al server HTTP.

1. AEM Screens Player si installa e si avvia automaticamente sul tuo dispositivo Samsung.

   >[!NOTE]
   >Sia il dispositivo Tizen che il `http` Il server dovrebbe essere in grado di connettersi tra di loro, ovvero il server dovrebbe essere raggiungibile dal lettore Tizen.


## Esenzione degli agenti utente con il problema relativo ai cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Questo paragrafo si applica alla Adobe Experience Manager (AEM) da 6.5.5 a AEM 6.5.7**
>
>Alcuni motori del browser non sono compatibili con *`SameSite=None`* attributo utilizzato nel token di accesso rilasciato dall’AEM 6.5.5 all’AEM 6.5.7. Di solito, il problema può essere risolto aggiornando il browser all’ultima versione disponibile. Talvolta tali aggiornamenti potrebbero non essere possibili, ad esempio con display avanzati, set-top box o altri dispositivi con motori di navigazione incorporati.

Segui i passaggi seguenti per esentare questi client incompatibili quando utilizzi *SameSite=Nessuno*:

1. Aggiornamento a Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Dopo il riavvio dell’AEM, vai a `/system/console/configMgr` e cerca **Adobe Gestore autenticazione token Granite**. Imposta il valore per **SameSite** valore per **Nessuno**.

1. Dovresti visualizzare una nuova opzione *`User agents to be exempted from samesite attribute`*. Popola questa opzione con un regex corrispondente all’agente utente incompatibile con il *SameSite=Nessuno* attributo.

   >[!NOTE]
   >
   >Consulta [SameSite=None: client incompatibili noti](https://www.chromium.org/updates/same-site/incompatible-clients) per ulteriori dettagli. Per il lettore Tizen, utilizza il codice regex: `(.*)Tizen(.*)`.

1. Registra il lettore Tizen rispetto all’istanza AEM 6.5.5 e versioni successive e deve registrarsi e mostrare il contenuto normalmente.

## Provisioning remoto del lettore Tizen {#remote-provisioning}

Provisioning remoto del lettore Tizen consente di distribuire centinaia e migliaia di display Samsung Tizen senza troppi sforzi. Evita di configurare manualmente ogni lettore con l’URL del server e il codice di registrazione in blocco o altri parametri. E, se è presente AEM Screens as a Cloud Service, per configurare la modalità cloud e il token cloud.

Questa funzione consente di configurare in remoto il lettore Tizen e, se necessario, di aggiornare centralmente le configurazioni. Tutto ciò che serve è il `HTTP` server utilizzato per ospitare l&#39;applicazione Tizen `(wgt and xml file)` e un editor di testo per salvare `config.json` con i parametri appropriati.

Verifica di aver configurato l’indirizzo URL Launcher sul dispositivo Tizen. Fai clic sul pulsante Home > Impostazioni modulo di avvio URL.
Il giorno `HTTP` che ospita l&#39;applicazione Tizen, inserire il file `config.json` nella stessa posizione del `wgt` file. Il nome file deve essere `config.json`.
Il lettore Tizen installa e, al momento del lancio (e di ogni riavvio), controlla e applica le impostazioni in `config.json` file.

### Esempio di criterio JSON {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### Attributi e finalità dei criteri {#policy-attributes}

Nella tabella seguente vengono riepilogati i criteri e le relative funzioni.

>[!NOTE]
>Le configurazioni dei criteri dell’interfaccia utente di amministrazione del lettore vengono rigorosamente applicate e non vengono ignorate manualmente. Per consentire la configurazione manuale del lettore per un determinato criterio, non specificare il criterio nella configurazione del criterio.
>Ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave `rebootSchedule` nella configurazione dei criteri. Le configurazioni dei criteri vengono lette ogni volta che il lettore viene ricaricato.

| **Nome criterio** | **Finalità** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| registrationKey | Utilizzato per la registrazione in blocco di dispositivi utilizzando una chiave già condivisa. |
| risoluzione | Risoluzione del dispositivo. |
| rebootSchedule | Pianificazione per il riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente di amministrazione per configurare il dispositivo sul sito. Impostato su false una volta che è completamente configurato e in produzione. |
| enableOSD | Abilita l’interfaccia utente per cambiare canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false, una volta che è completamente configurato e in produzione. |
| enableActivityUI | Abilita questa opzione affinché tu possa visualizzare l’avanzamento di attività quali download e sincronizzazione. Abilita per la risoluzione dei problemi e disabilita una volta che è completamente configurato e in produzione. |
| cloudMode | Imposta su true se desideri che il lettore Tizen si connetta a Screens as a Cloud Service. Impostare su false per connettersi a AMS o a un AEM locale. |
| cloudToken | Token di registrazione da registrare su Screens as a Cloud Service. |


## Iscrizione del dispositivo Tizen a Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Segui i passaggi seguenti per registrare il dispositivo Tizen su Samsung Remote Management Service (RMS) e configurare in remoto l’URL Launcher:

>[!NOTE]
>Verificare le impostazioni di rete e il monitor.

1. Accedi a **Menu** -> **Rete** -> **Impostazioni rete server** e premere **Invio**.

1. Passa all’indirizzo del server e digita nell’URL MagicInfo, quindi premi **Fine**.

1. Imposta TLS, se necessario. Passare alla porta, fare clic sul numero di porta dal server e quindi su **Salva**.

1. Accedi a **Dispositivo** e controllare il dispositivo configurato. Quando viene trovato un dispositivo, fare clic sulla casella di controllo e quindi su **Approva**.

   >![immagine](/help/user-guide/assets/tizen/rms-3.png)

1. Immettere le informazioni richieste e fare clic su un gruppo di dispositivi. Fai clic su **OK**.

   >![immagine](/help/user-guide/assets/tizen/rms-7.png)

1. Quando il dispositivo viene approvato, viene visualizzato nell&#39;elenco dei dispositivi. Clic *Informazioni* nella casella del dispositivo, come illustrato di seguito.

   >![immagine](/help/user-guide/assets/tizen/rms-6.png)

1. Viene visualizzata la finestra di dialogo Informazioni dispositivo. Fai clic su **Informazioni dispositivo** e fai clic su **Modifica**.

   >![immagine](/help/user-guide/assets/tizen/rms-5.png)

1. Modifica le opzioni del dispositivo e fai clic su **Configurazione** scheda. Accedi a **Utilità di avvio URL** e immetti l’URL che ospita il wgt e `SSSP config file` in modo da poter installare un `SSSP` come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/tizen/rms-9.png)

1. Fai clic su **Salva**.

### Utilizzo del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzione qui: [Controllo remoto Schermi](implementing-remote-control.md)
