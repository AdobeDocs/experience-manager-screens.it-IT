---
title: Elenco di controllo della sicurezza
description: Scopri le aree di sicurezza chiave di AEM Screens con un elenco di domande e considerazioni.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: ad8509deaff9f90df5f6b50947f587a74e420661
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Elenco di controllo della sicurezza di AEM Screens {#security-checklist}

La pagina Elenco di controllo della sicurezza di AEM Screens descrive le aree di sicurezza chiave con un elenco di controllo contenente domande e considerazioni.

## Tabella elenco di controllo {#checklist-table}

| **Area di protezione** | **Elenco di controllo** | **Sì/No/NA** |
|---|---|---|
| **Aggiornamenti software per AEM e Screens** | **a.** *È stato applicato il service pack Adobe Experience Manager (AEM) più recente?* <br>**b.** *È stato applicato il Feature Pack di AEM Screens più recente?* <br>**c.** *Stai utilizzando il software AEM Screens Player più recente disponibile da [Download di AEM Screens Player](https://download.macromedia.com/screens/)?* | |
| **Sicurezza fisica** | **a.** *Hai disabilitato tutte le porte non necessarie?* <br>**b.** *Cablaggio e hardware protetti?* <br>**c.** *Se applicabile, si utilizzano contenitori?* | |
| **Sicurezza di rete** | **a.** *Si sta utilizzando una subnet isolata per i dispositivi di segnaletica?* <br>**b.** *La subnet isolata consente l&#39;accesso agli endpoint richiesti, inclusi AEM, Adobe Analytics o altri servizi richiesti?* <br>**c.** *Hai protetto il tuo Wi-Fi utilizzando le best practice aziendali?* <br>**d.** *Se si utilizza la riproduzione sincronizzata, è stato consentito il 24503 TCP per WebSocket solo sui dispositivi primari?* <br>**e.** *È stato sbloccato l&#39;intervallo di indirizzi IP dei dispositivi di riproduzione in modo che solo i dispositivi autorizzati possano accedere al servizio di registrazione nell&#39;istanza di authoring?* | |
| **Sicurezza del sistema operativo** | **a.** *Hai effettuato l&#39;aggiornamento alla versione più recente del sistema operativo e hai applicato tutte le patch di sicurezza necessarie?* <br>**b.** *Hai disabilitato tutti i servizi non necessari e rimosso le applicazioni non necessarie?* <br>**c.** *Hai iscritto il dispositivo alla gestione dei dispositivi per applicare i criteri aziendali?* <br>**d.** *Hai bloccato il dispositivo su un singolo chiosco di applicazioni (lettore)?* <br>**e.** *Sono attive procedure operative standard per l&#39;installazione degli aggiornamenti di sicurezza del sistema operativo nel tempo?*<br>**f.***Hai seguito le best practice di sicurezza per il sistema operativo in uso, ad esempio software antimalware, utente non amministrativo?* | |
| **Sicurezza applicazioni** | **a.** *Hai disabilitato l&#39;interfaccia utente amministratore, il selettore canale e l&#39;interfaccia utente attività per la produzione?* <br>**b.** *Il livello di registro per la produzione è stato ridotto a icona?* <br>**c.** *Si utilizza https per la connessione ad AEM?* <br>**d.** *Si utilizza un certificato firmato da una CA o una PKI dell&#39;organizzazione? (certificati non autofirmati)*<br>**e.***Stai utilizzando TLS e non SSL v3?*<br>**f.** *Convalidare il token di registrazione nel dispositivo e in AEM durante la registrazione?*<br> **g.** *I dati in uso sono stati classificati e sul dispositivo non esistono PII o PHI?*<br> **h.** *I dati in uso sono stati classificati e nel dispositivo non sono presenti informazioni personali (PII) o informazioni sanitarie protette (PHI)?*<br> **i.** *Hai configurato il monitoraggio delle e-mail? È attivo un SOP per rispondere alle e-mail di monitoraggio e gestire i dispositivi non ping?* | |
| **Controllo dell&#39;accesso** | **a.** *Si dispone di un controllo degli accessi basato sul ruolo (RBAC) identificato e gestito internamente?* <br>**b.** *Hai seguito il principio del privilegio minimo nel fornire accesso ad autori, amministratori e lettori utilizzando le best practice di Adobe?* | |

### Scarica elenco di controllo della sicurezza {#download-checklist}

Per scaricare l&#39;elenco di controllo della sicurezza di AEM Screens, fai clic [qui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
