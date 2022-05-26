---
title: Giocatore Tizen
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
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

Per implementare Tizen Player per AEM Screens, effettua le seguenti operazioni:

1. Passa a [Download di AEM Screens Player](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installare il lettore Tizen *(.zip)* file dal computer locale.

## Configurazione del server http {#setting-local-server}

>[!NOTE]
> Estrai il file zip e rendi disponibile il lettore Tizen attraverso un `http server`. (2) `http server` non deve essere locale o server Apache).

Effettua le seguenti operazioni:

1. Copia i due file estratti, ad esempio `AEMScreensPlayer.wgt` e `sssp_config.xml` alla directory principale del server Web Apache locale.

   >[!NOTE]
   >La `AEMScreensPlayer.wgt`è l&#39;effettiva applicazione Tizen player e `sssp_config.xml` contiene informazioni su questa mappa che ti aiutano a installarla sul dispositivo Tizen.

1. Ottieni l’IP o l’URL del server HTTP locale (e il percorso della cartella contenente i file estratti nel passaggio 2 se estratti in una sottocartella e non in una cartella principale)

1. Il Tizen Player scarica il programma di installazione dal server locale.

### Assegnazione di un nome a Tizen Player {#name-tizen}

È possibile assegnare un nome di dispositivo semplice da usare al lettore Tizen, inviando in tal modo il nome assegnato ad Adobe Experience Manager (AEM). Questa funzionalità consente non solo di assegnare un nome al lettore personalizzato, ma anche di assegnare facilmente il contenuto appropriato.

>[!NOTE]
>È possibile scegliere il nome del lettore solo prima della registrazione. Una volta registrato il lettore, il nome del lettore non può più essere cambiato.

Per configurare il nome in Tizen Player, effettua le seguenti operazioni:

1. Fare clic sul pulsante del menu sul telecomando.
1. Passa a **rete** —> **Nome del dispositivo** per assegnare un nome al lettore.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Segui i passaggi seguenti sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens sul dispositivo:

1. Passa al tuo dispositivo Samsung e accendi.

1. Fai clic sul pulsante **MENU** dal telecomando del dispositivo e scorri verso il basso fino a **Sistema** dalla barra di navigazione a sinistra.

1. Scorri verso il basso e seleziona la **Riproduci tramite** e cambialo in **URL Launcher** opzione .
   ![immagine](/help/user-guide/assets/tizen/rms-2.png)

1. Una volta impostato l’URL Launcher, premi il pulsante **Pagina principale** dal telecomando.

1. Passa a **Impostazioni URL Launcher** e immetti l&#39;indirizzo IP del server localhost e fai clic su **Fine**.
   >[!NOTE]
   >Il lettore Tizen deve essere in grado di connettersi al server http.

1. AEM Screens Player dovrebbe ora installare e avviare automaticamente sul tuo dispositivo Samsung.

   >[!NOTE]
   >Sia il dispositivo Tizen che il `http` il server dovrebbe essere in grado di connettersi tra di loro, ovvero il server dovrebbe essere raggiungibile con il Tizen player.


## Esenzione degli agenti utente con il problema del cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Questa sezione si applica ad Adobe Experience Manager (AEM) da 6.5.5 a AEM 6.5.7**
>Alcuni motori browser non sono compatibili con *SameSite=None* attributo utilizzato nel token di accesso rilasciato da AEM 6.5 a AEM 6.7. Di solito, il problema può essere risolto aggiornando il browser all&#39;ultima versione disponibile. In alcuni casi tali aggiornamenti potrebbero non essere possibili, ad esempio con smart display, set top box o altri dispositivi con motori di navigazione incorporati.

Segui i passaggi seguenti per esentare questi client incompatibili quando utilizzi *SameSite=None*:

1. Aggiornamento a Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Dopo AEM riavvii, vai a `/system/console/configMgr` e cerca **Gestore autenticazione token di Granite Adobe**. Imposta il valore per **SameSite** valore a **Nessuno**.

1. Dovresti visualizzare una nuova opzione *Agenti utente da esentare dall&#39;attributo samesite*. Popolare questo con un regex corrispondente all&#39;agente utente che è(sono) incompatibile con il *SameSite=None* attributo.
   >[!NOTE]
   >Vedi [SameSite=None: Client noti non compatibili](https://www.chromium.org/updates/same-site/incompatible-clients) per ulteriori dettagli. Per il giocatore Tizen usare il regex: `(.*)Tizen(.*)`.

1. Registra il Tizen player rispetto alla tua istanza AEM 6.5.5 e successive e dovrebbe registrare e mostrare il contenuto normalmente.

## Provisioning remoto di Tizen Player {#remote-provisioning}

Il provisioning remoto del Tizen Player consente di distribuire centinaia e migliaia di display Samsung Tizen senza molto sforzo. Evita il noioso lavoro manuale per configurare ogni lettore con l&#39;URL del server e il codice di registrazione in massa, o altri parametri e nel caso di Screens as a Cloud Service a configurare la modalità cloud e il token cloud.

Questa funzione consente di configurare Tizen Player in remoto e di aggiornare anche centralmente le configurazioni, se necessario. Tutto ciò che richiedi è il `HTTP` server utilizzato per ospitare l&#39;applicazione Tizen `(wgt and xml file)` e un editor di testo per salvare `config.json` con i parametri appropriati.

Assicurati di aver configurato l’indirizzo del modulo di avvio URL sul dispositivo personalizzato, ovvero Pulsante Home > Impostazioni del modulo di avvio URL.
Sulla `HTTP` server che ospita l&#39;applicazione Tizen, inserire il file `config.json` nella stessa posizione del `wgt` file. Il nome del file deve essere `config.json`.
Il Tizen Player verrà installato e al momento del lancio (e ogni riavvio) controllerà e applicherà le impostazioni nel `config.json` file.

### Criteri JSON di esempio {#example-json}

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

Nella tabella seguente sono riepilogati i criteri con le relative funzioni.

>[!NOTE]
>Le configurazioni dei criteri vengono applicate in modo rigoroso e non vengono sostituite manualmente nell’interfaccia utente amministratore del lettore. Per consentire la configurazione manuale del lettore per un criterio specifico, non specificare il criterio nella configurazione del criterio, ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave `rebootSchedule` nella configurazione dei criteri. Le configurazioni dei criteri vengono lette ogni volta che il lettore si ricarica.

| **Nome criterio** | **Scopo** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| registrationKey | Utilizzato per la registrazione in massa di dispositivi utilizzando una chiave pre-condivisa. |
| risoluzione | La risoluzione del dispositivo. |
| RestartSchedule | Pianificazione del riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente amministratore per configurare il dispositivo sul sito. Imposta su false una volta configurato completamente e in produzione. |
| enableOSD | Abilita l’interfaccia utente del commutatore del canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false una volta configurata completamente e in produzione. |
| enableActivityUI | Attiva per mostrare l&#39;avanzamento delle attività come il download e la sincronizzazione. Attiva per la risoluzione dei problemi e disattiva una volta configurato completamente e in produzione. |
| cloudMode | Imposta su true se desideri che il lettore Tizen si connetta a Screens as a Cloud Service. Imposta su false per connettersi ad AMS o a AEM on-Prem. |
| cloudToken | Token di registrazione per registrarsi su Screens as a Cloud Service. |


## Registrazione del dispositivo Tizen al servizio di gestione remota Samsung (RMS) {#enroll-tizen-device-rms}

Segui i passaggi seguenti per registrare il dispositivo Tizen al servizio di gestione remota Samsung (RMS) e configurare in remoto l&#39;URL Launcher:

>[!NOTE]
>Verificare le impostazioni di rete e il monitor.

1. Passa a **Menu** -> **Rete** -> **Impostazioni di rete del server** e premere **Invio**.

1. Passa all&#39;indirizzo del server e digita l&#39;accesso all&#39;URL MagicInfo e premi **Fine**.

1. Imposta TLS, se necessario. Passa alla porta e seleziona il numero di porta dal server e fai clic su **Salva**.

1. Passa a **Dispositivo** e controlla il dispositivo appena configurato. Una volta trovato il dispositivo, fai clic sulla casella di controllo e seleziona **Approva**.

   >![immagine](/help/user-guide/assets/tizen/rms-3.png)

1. Compila le informazioni richieste e seleziona un gruppo di dispositivi. Fai clic su **OK** per completare il processo di approvazione.

   >![immagine](/help/user-guide/assets/tizen/rms-7.png)

1. Una volta approvato, il dispositivo dovrebbe essere visualizzato nell&#39;elenco dei dispositivi. Fai clic sul pulsante *Informazioni* pulsante situato nella casella del dispositivo, ovvero **i**, come illustrato nella figura seguente.

   >![immagine](/help/user-guide/assets/tizen/rms-6.png)

1. Viene visualizzata la finestra di dialogo delle informazioni sul dispositivo. Seleziona la **Informazioni sul dispositivo** e fai clic su **Modifica**.

   >![immagine](/help/user-guide/assets/tizen/rms-5.png)

1. Modifica le opzioni del dispositivo e seleziona la **Configurazione** scheda . Passa a **URL Launcher** e immetti l&#39;URL che ospita il wgt e `SSSP config file` per installare un `SSSP` come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/tizen/rms-9.png)

1. Fai clic su **Salva** per visualizzare le modifiche nella schermata di visualizzazione.

### Utilizzo del telecomando Screens {#using-remote-control}

AEM Screens fornisce la funzionalità Controllo remoto. Ulteriori informazioni su questa funzione sono disponibili qui: [Controllo remoto schermo](implementing-remote-control.md)
