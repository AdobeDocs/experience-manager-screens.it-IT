---
title: Giocatore Tizen
description: Questa pagina descrive l'installazione e il funzionamento di Tizen Player.
feature: Amministrazione di schermi, lettori
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 1%

---

# Implementazione di Tizen Player {#tizen-player}

## Installazione di Tizen Player {#installing-tizen-player}

Per implementare Tizen Player per AEM Screens, effettua le seguenti operazioni:

1. Passa alla pagina [Download di AEM Screens Player](https://download.macromedia.com/screens/) per scaricare Tizen Player.

1. Installa il file Tizen player *(.zip)* dal computer locale.

## Configurazione del server locale ed estrazione dei file ZIP {#setting-local-server}

>[!NOTE]
> Estrai il file zip e rendi disponibile il Tizen player tramite un `http server`. (Il `http server` non deve essere un server locale o Apache).

Effettua le seguenti operazioni:

1. Copia i due file estratti, ad esempio `AEMScreensPlayer.wgt` e `sssp_config.xml` nella directory principale del server Web Apache locale.

   >[!NOTE]
   >L&#39; `AEMScreensPlayer.wgt`è l&#39;applicazione Tizen Player effettiva e `sssp_config.xml` contiene informazioni su questa mappa che ti aiutano a installarla sul dispositivo Tizen.

1. Ottieni l’IP o l’URL del server HTTP locale (e il percorso della cartella contenente i file estratti nel passaggio 2 se estratti in una sottocartella e non in una cartella principale)

1. Il Tizen Player scarica il programma di installazione dal server locale.

### Assegnazione di un nome a Tizen Player {#name-tizen}

È possibile assegnare un nome di dispositivo semplice da usare al lettore Tizen, inviando in tal modo il nome assegnato ad Adobe Experience Manager (AEM). Questa funzionalità consente non solo di assegnare un nome al lettore personalizzato, ma anche di assegnare facilmente il contenuto appropriato.

Per configurare il nome in Tizen Player, effettua le seguenti operazioni:

1. Fare clic sul pulsante del menu sul telecomando.
1. Passa a **rete** —> **Nome dispositivo** per assegnare un nome al lettore.

### Configurazione degli aggiornamenti sul dispositivo Samsung {#config-updates}

Segui i passaggi seguenti sul dispositivo Samsung per completare l&#39;installazione del lettore AEM Screens sul dispositivo:

1. Passa al tuo dispositivo Samsung e accendi.

1. Fai clic sul pulsante **MENU** dal telecomando del dispositivo e scorri verso il basso fino a **Sistema** dalla barra di navigazione a sinistra.

1. Scorri verso il basso e seleziona l&#39;opzione **Riproduci tramite** e modificala in **URL Launcher** .
   ![immagine](/help/user-guide/assets/tizen/rms-2.png)

1. Una volta impostato l&#39;URL Launcher, premere il pulsante **Home** dal telecomando.

1. Passa a **Impostazioni di avvio URL** e immetti l&#39;indirizzo IP del server localhost e fai clic su **Fine**.
   >[!NOTE]
   >Il lettore Tizen deve essere in grado di connettersi al server http.

1. AEM Screens Player dovrebbe ora installare e avviare automaticamente sul tuo dispositivo Samsung.

   >[!NOTE]
   >Sia il dispositivo Tizen che il server `http` devono essere in grado di connettersi tra loro, ovvero il server deve essere raggiungibile con il lettore Tizen.


## Esenzione degli agenti utente con il problema del cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Questa sezione si applica ad Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Alcuni motori del browser sono incompatibili con l&#39;attributo *SameSite=None* utilizzato nel token di accesso rilasciato da AEM 6.5 a AEM 6.7. Di solito, il problema può essere risolto aggiornando il browser all&#39;ultima versione disponibile. In alcuni casi tali aggiornamenti potrebbero non essere possibili, ad esempio con display intelligenti, decoder o altri dispositivi con motori di navigazione incorporati.

Segui i passaggi seguenti per esentare questi client incompatibili quando utilizzi *SameSite=None*:

1. Aggiornamento a Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Dopo AEM riavvio, vai a `/system/console/configMgr` e cerca **Gestore di autenticazione dei token di Adobe**. Imposta il valore per il valore **SameSite** su **None**.

1. Dovresti vedere una nuova opzione *Agenti utente da esentare dall&#39;attributo samesite*. Compila questo con un regex corrispondente all’agente utente che è(i) incompatibile con l’attributo *SameSite=None* .
   >[!NOTE]
   >Vedere [SameSite=None: Client noti incompatibili](https://www.chromium.org/updates/same-site/incompatible-clients) per ulteriori dettagli. Per il giocatore Tizen usare il regex: `(.*)Tizen(.*)`.

1. Registra il Tizen player rispetto alla tua istanza AEM 6.5.5 e successive e dovrebbe registrare e mostrare il contenuto normalmente.

## Provisioning remoto di Tizen Player {#remote-provisioning}

Il provisioning remoto del Tizen Player consente di distribuire centinaia e migliaia di display Samsung Tizen senza molto sforzo. Evita il noioso sforzo manuale di configurare ogni lettore con l&#39;URL del server e il codice di registrazione in massa, o altri parametri e nel caso di Screens come Cloud Service per configurare la modalità cloud e il token cloud.

Questa funzione consente di configurare Tizen Player in remoto e di aggiornare anche centralmente le configurazioni, se necessario. È sufficiente il server `HTTP` utilizzato per ospitare l&#39;applicazione Tizen `(wgt and xml file)` e un editor di testo per salvare l&#39; `config.json` con i parametri appropriati.

Assicurati di aver configurato l’indirizzo del modulo di avvio URL sul dispositivo personalizzato, ovvero Pulsante Home > Impostazioni del modulo di avvio URL.
Sul server `HTTP` che ospita l&#39;applicazione Tizen, posizionare il file `config.json` nella stessa posizione del file `wgt`. Il nome del file deve essere `config.json`.
Il Tizen Player verrà installato e al momento del riavvio (e ogni riavvio) controllerà e applicherà le impostazioni nel file `config.json`.

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
>Le configurazioni dei criteri vengono applicate in modo rigoroso e non vengono sostituite manualmente nell’interfaccia utente amministratore del lettore. Per consentire la configurazione manuale del lettore per un criterio specifico, non specificare il criterio nella configurazione del criterio, ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave `rebootSchedule` nella configurazione del criterio. Le configurazioni dei criteri vengono lette ogni volta che il lettore si ricarica.

| **Nome criterio** | **Scopo** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| registrationKey | Utilizzato per la registrazione in massa di dispositivi utilizzando una chiave pre-condivisa. |
| risoluzione | La risoluzione del dispositivo. |
| RestartSchedule | Pianificazione del riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente amministratore per configurare il dispositivo sul sito. Imposta su false una volta configurato completamente e in produzione. |
| enableOSD | Abilita l’interfaccia utente del commutatore del canale affinché gli utenti possano cambiare canale sul dispositivo. Considera l’impostazione su false una volta configurata completamente e in produzione. |
| enableActivityUI | Attiva per mostrare l&#39;avanzamento delle attività come il download e la sincronizzazione. Attiva per la risoluzione dei problemi e disattiva una volta configurato completamente e in produzione. |
| cloudMode | Imposta su true se desideri che il lettore Tizen si connetta a Screens come Cloud Service. Imposta su false per connettersi ad AMS o a AEM on-Prem. |
| cloudToken | Token di registrazione per registrarsi su Screens come Cloud Service. |


## Registrazione del dispositivo Tizen al servizio di gestione remota Samsung (RMS) {#enroll-tizen-device-rms}

Segui i passaggi seguenti per registrare il dispositivo Tizen al servizio di gestione remota Samsung (RMS) e configurare in remoto l&#39;URL Launcher:

>[!NOTE]
>Verificare le impostazioni di rete e il monitor.

1. Passa a **Menu** -> **Rete** -> **Impostazioni di rete del server** e premi **Invio**.

1. Accedi all&#39;indirizzo Server e digita l&#39;accesso all&#39;URL MagicInfo e premi **Fine**.

1. Imposta TLS, se necessario. Passa alla porta e seleziona il numero di porta dal server e fai clic su **Salva**.

1. Passa alla scheda **Dispositivo** e controlla il dispositivo appena configurato. Una volta trovato un dispositivo, fai clic sulla casella di controllo e seleziona **Approva**.

   >![immagine](/help/user-guide/assets/tizen/rms-3.png)

1. Compila le informazioni richieste e seleziona un gruppo di dispositivi. Fai clic su **OK** per completare il processo di approvazione.

   >![immagine](/help/user-guide/assets/tizen/rms-7.png)

1. Una volta approvato, il dispositivo dovrebbe essere visualizzato nell&#39;elenco dei dispositivi. Fai clic sul pulsante *Informazioni* situato nella casella del dispositivo, ovvero **i**, come illustrato nella figura riportata di seguito.

   >![immagine](/help/user-guide/assets/tizen/rms-6.png)

1. Viene visualizzata la finestra di dialogo delle informazioni sul dispositivo. Seleziona la scheda **Informazioni sul dispositivo** e fai clic su **Modifica**.

   >![immagine](/help/user-guide/assets/tizen/rms-5.png)

1. Modifica le opzioni del dispositivo e seleziona la scheda **Configurazione** . Passa alla sezione **URL Launcher** e immetti l’URL che ospita il wgt e `SSSP config file` per installare un’applicazione `SSSP`, come illustrato nella figura riportata di seguito.

   ![immagine](/help/user-guide/assets/tizen/rms-9.png)

1. Fai clic su **Salva** per visualizzare le modifiche nella schermata di visualizzazione.
