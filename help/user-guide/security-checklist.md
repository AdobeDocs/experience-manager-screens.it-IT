---
title: Lista di controllo sicurezza
seo-title: Lista di controllo sicurezza
description: La pagina descrive le aree di protezione principali con un elenco di domande e considerazioni.
seo-description: La pagina descrive la Lista di controllo protezione
feature: Amministrazione di schermi
role: Administrator
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---


# Lista di controllo AEM Screens {#security-checklist}

La pagina Lista di controllo sicurezza di AEM Screens descrive le aree di protezione chiave con una lista di controllo contenente domande e considerazioni.

## Tabella elenco di controllo {#checklist-table}

| **Area di sicurezza** | **Elenco di controllo** | **Sì/No/NA** |
|---|---|---|
| **Aggiornamenti software AEM e Screens** | ***a.*** *È stato applicato il service pack Adobe Experience Manager (AEM) più recente?* <br>***b.***  *È stato applicato l&#39;ultimo Feature Pack di AEM Screens?* <br>***c.*** *Utilizzi il software AEM Screens Player più recente disponibile dai download di  [AEM Screens Player](https://download.macromedia.com/screens/)?* |
| **Sicurezza fisica** | ***a.*** *Hai disabilitato tutte le porte superflue?* <br>***b.***  *Hai protetto cavi e hardware?* <br>***c.*** *Utilizzi eventuali contenitori?* |
| **Sicurezza della rete** | ***a.*** *Utilizzi una subnet isolata per i dispositivi di segnaletica?* <br>***b.***  *La subnet isolata consente l&#39;accesso agli endpoint richiesti, compresi AEM, Adobe Analytics o altri servizi richiesti?* <br>***c.*** *Hai protetto il tuo Wi-Fi utilizzando le best practice aziendali?* <br>***d.*** *Se si utilizza la riproduzione sincronizzata, è consentito TCP 24503 solo per WebSocket sui dispositivi master?* <br>***e.*** *Hai sbloccato l&#39;intervallo di indirizzi IP dei dispositivi di riproduzione in modo che solo i dispositivi autorizzati possano accedere al servizio di registrazione sull&#39;autore?* |
| **Sicurezza del sistema operativo** | ***a.*** *Hai effettuato l&#39;aggiornamento alla versione più recente del sistema operativo e applicato tutte le patch di sicurezza necessarie?* <br>***b.*** *Hai disabilitato tutti i servizi superflui e rimosso le applicazioni superflue?* <br>***c.*** *Hai registrato il dispositivo nella gestione dei dispositivi per applicare i criteri aziendali?* <br>***d.*** *Hai bloccato il dispositivo al chiosco per applicazione singola (player)?* <br>***e.*** *Disponi di procedure operative standard (SOP) per installare gli aggiornamenti di sicurezza del sistema operativo nel tempo?*<br>***f.*** *Hai seguito le best practice di sicurezza per il sistema operativo in uso, come software anti-malware, utente non amministrativo?* |
| **Sicurezza dell&#39;applicazione** | ***a.*** *Hai disabilitato Interfaccia utente amministratore, Controllo canali e Interfaccia utente attività per la produzione?* <br>***b.*** *Hai ridotto al minimo il livello di log per la produzione?* <br>***c.*** *Utilizzi https per la connessione a AEM?* <br>***d.*** *Utilizzi un certificato firmato CA o un PKI Enterprise? (non certificati autofirmati)*<br>***e.*** *Utilizzi TLS e non SSL v3?*<br>***f.*** *Stai convalidando il token di registrazione sul dispositivo e AEM durante la registrazione?*<br> ***g.*** *Hai classificato i dati in uso e che sul dispositivo non esiste alcun PII o PHI?*<br> ***h.*** *Hai classificato i dati in uso e che sul dispositivo non esistono informazioni personali identificabili (PII) o informazioni sanitarie protette (PHI)?*<br> ***i.*** *Hai configurato il monitoraggio delle e-mail e disponi di un SOP per rispondere al monitoraggio delle e-mail e alla gestione dei dispositivi non ping?* |
| **Controllo accesso** | ***a.*** *Hai un controllo dell&#39;accesso basato sul ruolo (RBAC) identificato e gestito internamente?* <br>***b.*** *Hai seguito il principio del minimo privilegio nel fornire l&#39;accesso ad autori, amministratori e giocatori utilizzando le best practice di Adobe?* |

### Download della checklist di sicurezza {#download-checklist}

Per scaricare la Lista di controllo sicurezza AEM Screens, fai clic [qui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).