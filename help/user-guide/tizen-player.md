---
title: Giocatore Tizen
description: Questa pagina descrive l’installazione e il funzionamento di Tizen Player.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 1%

---

# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Segui i passaggi seguenti per implementare Tizen Player per AEM Screens:

1. Accedi a [Download di AEM Screens Player](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installare il lettore Tizen *(.zip)* dal computer locale.

## Configurazione del server http {#setting-local-server}

>[!NOTE]
> Estrai il file zip e rendi disponibile il lettore Tizen tramite un `http server`. (Il `http server` non deve essere un server locale o Apache).

Effettua le seguenti operazioni:

1. Copiare i due file estratti, ad esempio `AEMScreensPlayer.wgt` e `sssp_config.xml` nella directory principale del server web Apache locale.

   >[!NOTE]
   >Il `AEMScreensPlayer.wgt`è l’effettiva applicazione lettore Tizen e `sssp_config.xml` contiene informazioni su questa mappa che consentono di installarla sul dispositivo Tizen.

1. Ottieni l’IP o l’URL del server HTTP locale (e il percorso della cartella contenente i file estratti al passaggio 2 se estratti in una sottocartella e non nella cartella principale)

1. Il lettore Tizen scarica il programma di installazione dal server locale.

### Denominazione del lettore Tizen {#name-tizen}

Puoi assegnare un nome descrittivo al tuo lettore Tizen, inviando in tal modo il nome del dispositivo assegnato ad Adobe Experience Manager (AEM). Questa funzionalità consente non solo di denominare il lettore Tizen, ma anche di assegnare facilmente i contenuti appropriati.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Una volta registrato, il nome del lettore non può più essere modificato.

Segui i passaggi seguenti per configurare il nome in Tizen player:

1. Fare clic sul pulsante del menu sul telecomando.
1. Accedi a **rete** —> **Nome dispositivo** per assegnare un nome al lettore.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Per completare l’installazione del lettore AEM Screens sul dispositivo Samsung, segui i passaggi indicati di seguito:

1. Passa al dispositivo Samsung e accendi.

1. Fai clic su **MENU** dal telecomando del dispositivo e scorrere verso il basso fino a **Sistema** dalla barra di navigazione a sinistra.

1. Scorri verso il basso e seleziona la **Riproduci tramite** e modificarla in **Utilità di avvio URL** opzione.
   ![immagine](/help/user-guide/assets/tizen/rms-2.png)

1. Una volta impostato l&#39;URL Launcher, premere il tasto **Home** dal telecomando.

1. Accedi a **Impostazioni modulo di avvio URL** e immettere l&#39;indirizzo IP del server localhost e fare clic su **Fine**.
   >[!NOTE]
   >Il lettore Tizen deve essere in grado di connettersi al server http.

1. AEM Screens Player dovrebbe ora essere installato e avviato automaticamente sul tuo dispositivo Samsung.

   >[!NOTE]
   >Sia il dispositivo Tizen che il `http` Il server dovrebbe essere in grado di connettersi tra di loro, ovvero il server dovrebbe essere raggiungibile dal lettore Tizen.


## Esenzione degli agenti utente con il problema relativo ai cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Questa sezione si applica alle versioni da Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Alcuni motori del browser non sono compatibili con *SameSite=Nessuno* attributo utilizzato nel token di accesso rilasciato da AEM 6.5 a AEM 6.7. Di solito, il problema può essere risolto aggiornando il browser all’ultima versione disponibile. In alcuni casi tali aggiornamenti potrebbero non essere possibili, ad esempio con display avanzati, set top box o altri dispositivi con motori di navigazione incorporati.

Segui i passaggi seguenti per esentare questi client incompatibili quando utilizzi *SameSite=Nessuno*:

1. Aggiornamento ad Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Dopo il riavvio dell’AEM vai a `/system/console/configMgr` e cerca **Adobe Gestore autenticazione token Granite**. Imposta il valore per **SameSite** valore per **Nessuno**.

1. Dovresti visualizzare una nuova opzione *Agenti utente da esentare dall’attributo samesite*. Popola questo con un regex corrispondente all’agente utente incompatibile con il *SameSite=Nessuno* attributo.
   >[!NOTE]
   >Consulta [SameSite=None: client incompatibili noti](https://www.chromium.org/updates/same-site/incompatible-clients) per ulteriori dettagli. Per il giocatore Tizen usa il regex: `(.*)Tizen(.*)`.

1. Registra il lettore Tizen rispetto all’istanza AEM 6.5.5 e versioni successive e deve registrarsi e mostrare il contenuto normalmente.

## Provisioning remoto di Tizen Player {#remote-provisioning}

Il provisioning remoto di Tizen Player consente di distribuire centinaia e migliaia di display Samsung Tizen senza troppi sforzi. Evita il tedioso sforzo manuale di configurare ogni lettore con l’URL del server e il codice di registrazione in blocco, o altri parametri e nel caso di Schermi as a Cloud Service a configurare la modalità cloud e il token cloud.

Questa funzione consente di configurare in remoto il lettore Tizen e, se necessario, di aggiornare centralmente le configurazioni. Tutto ciò che serve è il `HTTP` server utilizzato per ospitare l&#39;applicazione Tizen `(wgt and xml file)` e un editor di testo per salvare `config.json` con i parametri appropriati.

Accertati di aver configurato l&#39;indirizzo del modulo di avvio URL sul dispositivo Tizen, ovvero il pulsante Home —> le impostazioni del modulo di avvio URL.
Il giorno `HTTP` che ospita l&#39;applicazione Tizen, inserire il file `config.json` nella stessa posizione del `wgt` file. Il nome file deve essere `config.json`.
Il lettore Tizen verrà installato e al momento del lancio (e di ogni riavvio) verificherà e applicherà le impostazioni in `config.json` file.

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
>Le configurazioni dei criteri vengono rigorosamente applicate e non vengono ignorate manualmente nell’interfaccia utente di amministrazione del lettore. Per consentire la configurazione manuale del lettore per un determinato criterio, non specificare il criterio nella configurazione del criterio. Ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave `rebootSchedule` nella configurazione dei criteri. Le configurazioni dei criteri vengono lette ogni volta che il lettore viene ricaricato.

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


## Iscrizione del dispositivo Tizen a Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Segui i passaggi seguenti per registrare il dispositivo Tizen su Samsung Remote Management Service (RMS) e configurare in remoto l’URL Launcher:

>[!NOTE]
>Verificare le impostazioni di rete e il monitor.

1. Accedi a **Menu** -> **Rete** -> **Impostazioni rete server** e premere **Invio**.

1. Passa all’indirizzo del server e digita nell’URL MagicInfo, quindi premi **Fine**.

1. Imposta TLS, se necessario. Passare alla porta, selezionare il numero di porta dal server e fare clic su **Salva**.

1. Accedi a **Dispositivo** e verificare la periferica appena configurata. Una volta trovato un dispositivo, fai clic sulla casella di controllo e seleziona **Approva**.

   >![immagine](/help/user-guide/assets/tizen/rms-3.png)

1. Inserire le informazioni richieste e selezionare un gruppo di dispositivi. Fai clic su **OK** per completare il processo di approvazione.

   >![immagine](/help/user-guide/assets/tizen/rms-7.png)

1. Una volta approvato, il dispositivo dovrebbe comparire nell&#39;elenco dei dispositivi. Fai clic sul pulsante *Informazioni* sulla scatola del dispositivo, ovvero **i**, come illustrato nella figura seguente.

   >![immagine](/help/user-guide/assets/tizen/rms-6.png)

1. Viene visualizzata la finestra di dialogo Informazioni dispositivo. Seleziona la **Informazioni dispositivo** e fai clic su **Modifica**.

   >![immagine](/help/user-guide/assets/tizen/rms-5.png)

1. Modifica le opzioni del dispositivo e seleziona la **Configurazione** scheda. Accedi a **Utilità di avvio URL** e immetti l’URL che ospita il wgt e `SSSP config file` per installare un `SSSP` come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/tizen/rms-9.png)

1. Fai clic su **Salva** affinché le modifiche vengano visualizzate sullo schermo.

### Utilizzo del telecomando Screens {#using-remote-control}

AEM Screens fornisce funzionalità di controllo remoto. Ulteriori informazioni su questa funzione qui: [Controllo remoto Schermi](implementing-remote-control.md)
