---
title: Elenco di controllo della sicurezza per AEM Screens
seo-title: Elenco di controllo della sicurezza per AEM Screens
description: La pagina descrive l'elenco di controllo di sicurezza per AEM Screens
seo-description: La pagina descrive l'elenco di controllo di sicurezza per AEM Screens
translation-type: tm+mt
source-git-commit: dd1198dbfb502287ae72c3ccef297606aef069a2
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 1%

---


# Considerazioni sulla sicurezza del sistema per AEM Screens {#security-checklist}

>[!IMPORTANT]
>Si tratta di una risorsa Git interna.

In questa pagina vengono evidenziate le considerazioni sulla sicurezza del sistema per AEM Screens.


## White paper per la sicurezza di AEM Screens {#white-paper}

Questa sezione descrive il Libro bianco. (allegato del Libro bianco in sospeso)


## Domande frequenti per la sicurezza di AEM Screens {#faqs-screens}

Le seguenti domande frequenti si basano su un&#39;architettura del lettore autenticata e registrata che utilizza HTTPS come protocollo di comunicazione tra il lettore e AEM Server.

### Domande frequenti 1 {#faq1}

Il traffico del lettore può essere reinstradato a un server dannoso e istruito a scaricare e riprodurre contenuti multimediali dannosi?

**Risposta**

Non è possibile perché la connessione HTTP identifica entrambe le estremità della connessione e la codifica. Se provate a essere al centro e ad intercettare, viene visualizzato solo il contenuto crittografato e, se tentate di rappresentare il server, il lettore vi rifiuterà perché il vostro certificato è diverso.


### Domande frequenti 2 {#faq2}

È necessario utilizzare HTTP o HTTP?

**Risposta**

Utilizzate HTTP. Questo è un must se sei preoccupato per la sicurezza. Con HTTP la comunicazione è criptata tra lettore e server, e intercettare il contenuto o modificarlo sarà praticamente impossibile.


### Domande frequenti 3 {#faq3}

In un download di contenuto, esiste una sorta di firma del contenuto o dell&#39;hash?

**Risposta**

Ogni risorsa viene firmata (SHA) dal server e quindi convalidata dal lettore per lo stesso hash per garantire l’integrità.
Se l&#39;hash non corrisponde, si tenta di riconvalidare 3 volte. Dopo 3 tentativi, il comando di download viene considerato non valido.


### Domande frequenti 4 {#faq4}

AEM Server è sicuro?

**Risposta**

Ans 4. Se utilizzi AMS, Sony si occupa di tutta la sicurezza del server utilizzando le stesse funzionalità di Sites o Assets.


### Domande frequenti 5 {#faq5}

Il dispositivo è sicuro?

**Risposta**

Un giocatore fisicamente compromesso può teoricamente essere manipolato per riprodurre qualsiasi contenuto. È inoltre possibile collegare il lettore e collegare un&#39;unità USB/HDMI.

Si consiglia quindi di mettere i dispositivi fuori portata, preferibilmente in un contenitore sicuro, con cablaggio anche fissato. Disattivate anche le porte remote IR.

Se il sistema operativo del dispositivo non viene aggiornato regolarmente, il sistema operativo potrebbe essere lasciato esposto a fori di sicurezza e consentire attacchi remoti attraverso la rete.
>[!NOTE]
>Si consiglia di utilizzare i dispositivi con funzionalità di aggiornamento e controllo remoto affidabili (desktop remoto, soluzione MDM, ecc.). Si consiglia inoltre di utilizzare una rete privata, non esposta ad esempio al WIFI pubblico.


### Domande frequenti 6 {#faq6}

Come potrebbe un hacker tentare di compromettere un giocatore?

**Risposta**

L&#39;unico modo per compromettere un dispositivo di riproduzione è:

1. compromettere il DNS per rappresentare il server sul suo nome host, e
1. compromesso
   1. lato server certificati per rappresentare il server
   1. e rappresentare il certificato sul lato client

>[!IMPORTANT]
>Anche se un dispositivo è compromesso, puoi comunque revocare facilmente le sue credenziali in modo che non possa più connettersi ad AEM.





