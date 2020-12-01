---
title: Elenco di controllo protezione
seo-title: Elenco di controllo protezione
description: La pagina descrive l'elenco di controllo della protezione
seo-description: La pagina descrive l'elenco di controllo della protezione
translation-type: tm+mt
source-git-commit: ccc1baa0b57cb1311855065433aabf627814d16a
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


#  elenco di controllo della sicurezza AEM Screens {#security-checklist}

Nella  pagina AEM Screens Security Checklist vengono elencate le aree di protezione chiave con un elenco di domande e considerazioni.

## Tabella elenco di controllo {#checklist-table}

| **Area di sicurezza** | **Elenco di controllo** | **Sì/No/NA** |
|---|---|---|
| **Aggiornamenti software AEM e Screens** | ***a.*** *È stato applicato il service pack Adobe Experience Manager (AEM) più recente?* <br>***b.***  *È stato applicato  più recente AEM Screens Feature Pack?* <br>***c.*** *Utilizzate il software AEM Screens Player più recente disponibile   [ download](https://download.macromedia.com/screens/) di AEM Screens Player?* |
| **Sicurezza fisica** | ***a.*** *Avete disattivato tutte le porte superflue?* <br>***b.***  *Hai protetto cavi e hardware?* <br>***c.*** *Utilizzate dei contenitori, se applicabile?* |
| **Protezione della rete** | ***a.*** *Utilizzate una subnet isolata per i dispositivi di segnaletica?* <br>***b.***  *La subnet isolata consente l&#39;accesso agli endpoint richiesti, compresi AEM,  Adobe Analytics o altri servizi richiesti?* <br>***c.*** *Hai protetto il Wi-Fi utilizzando le best practice aziendali?* <br>***d.*** *Se si utilizza la riproduzione sincronizzata è stato consentito TCP 24503 per WebSocket solo sui dispositivi master?* <br>***e.*** *Hai sbloccato l&#39;intervallo di indirizzi IP dei dispositivi del lettore in modo che solo i dispositivi autorizzati possano accedere al servizio di registrazione sull&#39;autore?* |
| **Sicurezza del sistema operativo** | ***a.*** *Hai effettuato l&#39;aggiornamento alla versione più recente del sistema operativo e applicato tutte le patch di sicurezza necessarie?* <br>***b.*** *Hai disattivato tutti i servizi superflui e rimosso le applicazioni superflue?* <br>***c.*** *Hai registrato il dispositivo nella gestione dei dispositivi per applicare i criteri aziendali?* <br>***d.*** *Hai bloccato il dispositivo su un chiosco di applicazione singola (lettore)?* <br>***e.*** *Disponete di un SOP (Standard Operating Procedure) per l&#39;installazione degli aggiornamenti di sicurezza del sistema operativo nel tempo?*<br>***f.*** *Hai seguito le best practice di sicurezza per il sistema operativo in uso, come software anti-malware, utente non amministrativo?* |
| **Application Security** | ***a.*** *Hai disabilitato l&#39;interfaccia utente Amministratore, il Channel Switcher e l&#39;interfaccia utente dell&#39;attività per la produzione?* <br>***b.*** *Avete ridotto il livello di registro per la produzione?* <br>***c.*** *Utilizzate https per la connessione a AEM?* <br>***d.*** *Utilizzate un certificato CA firmato o un PKI Enterprise? (non certificati autofirmati)*<br>***e.*** *Utilizzate TLS e non SSL v3?*<br>***f.*** *State convalidando il token di registrazione sul dispositivo e AEM durante la registrazione?*<br> ***g.*** *Hai classificato i dati in uso e che nessun PII o PHI esiste sul dispositivo?*<br> ***h.*** *Hai classificato i dati utilizzati e che sul dispositivo non esistono informazioni personali (PII) o informazioni sulla salute protetta (PHI)?*<br> ***i.*** *Hai configurato e-mail di monitoraggio e disponi di un SOP per rispondere al monitoraggio delle e-mail e alla gestione di dispositivi non di ping?* |
| **Controllo accesso** | ***a.*** *È presente un controllo dell&#39;accesso basato su ruolo (RBAC) identificato e gestito internamente?* <br>***b.*** *Hai seguito il principio di minor privilegio nel fornire l&#39;accesso ad autori, amministratori e giocatori utilizzando le best practice  Adobe?* |

### Download dell&#39;elenco di controllo della sicurezza {#download-checklist}

Per scaricare l&#39;elenco di controllo  sicurezza AEM Screens, fare clic su [qui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).