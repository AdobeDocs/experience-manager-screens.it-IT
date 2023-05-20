---
title: Elenco di controllo della sicurezza
seo-title: Security Checklist
description: La pagina descrive le aree di sicurezza principali con un elenco di controllo contenente domande e considerazioni.
seo-description: The page describes Security Checklist
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Elenco di controllo della sicurezza di AEM Screens  {#security-checklist}

La pagina Elenco di controllo della sicurezza di AEM Screens descrive le aree di sicurezza chiave con un elenco di controllo contenente domande e considerazioni.

## Tabella elenco di controllo {#checklist-table}

| **Area di sicurezza** | **Elenco di controllo** | **Sì/No/NA** |
|---|---|---|
| **Aggiornamenti software per AEM e Screens** | ***a.*** *È stato applicato il service pack Adobe Experience Manager (AEM) più recente?* <br>***b.***  *È stato applicato il Feature Pack di AEM Screens più recente?* <br>***c.*** *Stai utilizzando il più recente software AEM Screens Player disponibile da [Download di AEM Screens Player](https://download.macromedia.com/screens/)?* |
| **Sicurezza fisica** | ***a.*** *Sono state disattivate tutte le porte non necessarie?* <br>***b.***  *Sono stati protetti i cavi e l&#39;hardware?* <br>***c.*** *Se applicabile, stai utilizzando dei contenitori?* |
| **Sicurezza di rete** | ***a.*** *Si sta utilizzando una subnet isolata per i dispositivi di segnaletica?* <br>***b.***  *La subnet isolata consente l&#39;accesso agli endpoint richiesti, inclusi AEM, Adobe Analytics o altri servizi richiesti?* <br>***c.*** *Hai protetto la tua rete Wi-Fi utilizzando le best practice aziendali?* <br>***d.*** *Se si utilizza la riproduzione sincronizzata è stato consentito il 24503 TCP per WebSocket solo sui dispositivi master?* <br>***e.*** *Hai sbloccato l’intervallo di indirizzi IP dei dispositivi di riproduzione in modo che solo i dispositivi autorizzati possano accedere al servizio di registrazione su Author?* |
| **Sicurezza del sistema operativo** | ***a.*** *È stato eseguito l&#39;aggiornamento alla versione più recente del sistema operativo e sono state applicate tutte le patch di sicurezza necessarie?* <br>***b.*** *Sono stati disattivati tutti i servizi non necessari e sono state rimosse le applicazioni non necessarie?* <br>***c.*** *Hai iscritto il dispositivo alla gestione dei dispositivi per applicare i criteri aziendali?* <br>***d.*** *Hai bloccato il dispositivo su un singolo chiosco di applicazione (lettore)?* <br>***e.*** *Sono disponibili procedure operative standard (SOP) per l&#39;installazione degli aggiornamenti di sicurezza del sistema operativo nel tempo?*<br>***f.*** *Hai seguito le best practice di sicurezza per il sistema operativo in uso, ad esempio software antimalware, utente non amministrativo?* |
| **Sicurezza dell&#39;applicazione** | ***a.*** *Hai disabilitato l’interfaccia utente amministratore, il selettore canale e l’interfaccia utente attività per la produzione?* <br>***b.*** *Il livello di registro per la produzione è stato ridotto a icona?* <br>***c.*** *Utilizzi https per la connessione a AEM?* <br>***d.*** *Si utilizza un certificato firmato da una CA o una PKI dell&#39;organizzazione? (certificati non autofirmati)*<br>***e.*** *Stai utilizzando TLS e non SSL v3?*<br>***f.*** *Convalida il token di registrazione sul dispositivo e AEM durante la registrazione?*<br> ***g.*** *Hai classificato i dati in uso e che non esistono dati PII o PHI sul dispositivo?*<br> ***h.*** *Hai classificato i dati in uso e non sono presenti informazioni personali (PII, Personally Identifiable Information) né informazioni protette sulla salute (PHI, Protected Health Information) sul dispositivo?*<br> ***i.*** *Hai configurato il monitoraggio delle e-mail e hai impostato un SOP per rispondere al monitoraggio delle e-mail e gestire i dispositivi non ping?* |
| **Controllo accesso** | ***a.*** *Hai un Role Based Access Control (RBAC) identificato e gestito internamente?* <br>***b.*** *Hai seguito il principio del privilegio minimo nel fornire accesso ad autori, amministratori e lettori utilizzando le best practice di Adobe?* |

### Download elenco di controllo protezione {#download-checklist}

Per scaricare l’elenco di controllo della sicurezza di AEM Screens, fai clic su [qui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
