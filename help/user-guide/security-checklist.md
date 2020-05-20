---
title: Elenco di controllo protezione
seo-title: Elenco di controllo protezione
description: La pagina descrive l'elenco di controllo della protezione
seo-description: La pagina descrive l'elenco di controllo della protezione
translation-type: tm+mt
source-git-commit: aade9071cebddf147dfad51d7319fb6f0e1c22bf
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# Elenco di controllo per la sicurezza di AEM Screens  {#security-checklist}

La pagina dell&#39;elenco di controllo di sicurezza di AEM Screens descrive le aree di protezione chiave con un elenco di domande e considerazioni.

## Tabella elenco di controllo {#checklist-table}

| **Area di sicurezza** | **Elenco di controllo** | **Sì/No/NA** |
|---|---|---|
| **Aggiornamenti software AEM e Screens** | ***a.*** *È stato applicato il service pack più recente di Adobe Experience Manager (AEM)?* <br>***b.****È stato applicato il più recente Feature Pack di AEM Screens?*<br>***c.*** *Stai utilizzando il software AEM Screens Player più recente disponibile dai download[di](https://download.macromedia.com/screens/)AEM Screens Player?* |
| **Sicurezza fisica** | ***a.*** *Avete disattivato tutte le porte superflue?* <br>***b.****Hai protetto cavi e hardware?*<br>***c.*** *Utilizzi dei contenitori, se applicabile?* |
| **Protezione della rete** | ***a.*** *Utilizzate una subnet isolata per i dispositivi di segnalamento?* <br>***b.****La subnet isolata consente l&#39;accesso agli endpoint richiesti, inclusi AEM, Adobe Analytics o altri servizi richiesti?*<br>***c.*** *Hai protetto il Wi-Fi utilizzando le best practice aziendali?* <br>***d.****Se si utilizza la riproduzione sincronizzata è stato consentito TCP 24503 per WebSocket solo sui dispositivi master?*<br>***e.*** *Hai inserito in una whitelist gli intervalli IP dei dispositivi del lettore in modo che solo i dispositivi autorizzati possano accedere al servizio di registrazione sull&#39;autore?* |
| **Sicurezza del sistema operativo** | ***a.*** *È stato aggiornato alla versione più recente del sistema operativo e applicato tutte le patch di sicurezza necessarie?* <br>***b.****Avete disattivato tutti i servizi superflui e rimosso le applicazioni superflue?*<br>***c.*** *Il dispositivo è stato registrato nella gestione dei dispositivi per applicare i criteri aziendali?* <br>***d.****Hai bloccato il dispositivo su un chiosco per una singola applicazione (lettore)?*<br>***e.*** *È disponibile un SOP (Standard Operating Procedure) per l&#39;installazione degli aggiornamenti di sicurezza del sistema operativo nel tempo?*<br>***f.****Hai seguito le best practice di sicurezza per il sistema operativo in uso, come software anti-malware, utenti non amministrativi?* |
| **Application Security** | ***a.*** *Hai disabilitato l&#39;interfaccia utente Amministratore, il commutatore di canale e l&#39;interfaccia utente Attività per la produzione?* <br>***b.****Avete ridotto il livello di registro per la produzione?*<br>***c.*** *Utilizzate https per la connessione ad AEM?* <br>***d.****Stai utilizzando un certificato CA firmato o un&#39;infrastruttura PKI Enterprise? (non certificati autofirmati)*<br>***e.**** Utilizzate TLS e non SSL v3?*<br>*** f.****Durante la registrazione, state convalidando il token di registrazione sul dispositivo e su AEM?*<br> ***g.*** *Hai classificato i dati in uso e che nessun PII o PHI esiste sul dispositivo?*<br> ***h.*** *Hai classificato i dati in uso e che sul dispositivo non esistono informazioni personali (PII) o informazioni sulla salute protetta (PHI)?*<br> ***i.*** *Hai configurato le E-mail di monitoraggio e disponi di un SOP per rispondere alle e-mail di monitoraggio e per gestire i dispositivi non di ping?* |
| **Controllo accesso** | ***a.*** *Hai un controllo dell&#39;accesso basato su ruolo (RBAC) identificato e gestito internamente?* <br>***b.****Hai rispettato il principio del privilegio minimo per fornire l&#39;accesso a autori, amministratori e lettori utilizzando le best practice di Adobe?* |

### Download dell&#39;elenco di controllo della sicurezza {#download-checklist}

Per scaricare l&#39;elenco di controllo della sicurezza di AEM Screens, fai clic [qui](/help/user-guide/assets/Screens-Security-Checklist.pdf).



