---
title: Elenco di controllo della sicurezza per AEM Screens
seo-title: Security Checklist for AEM Screens
description: La pagina descrive l’elenco di controllo della sicurezza per AEM Screens
seo-description: The page describes Security Checklist for AEM Screens
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---


# Considerazioni sulla sicurezza del sistema per AEM Screens {#security-checklist}

>[!IMPORTANT]
>Questa è una risorsa Git interna.

Questa pagina illustra le considerazioni sulla sicurezza del sistema per AEM Screens.


## White paper per la sicurezza di AEM Screens {#white-paper}

Questa sezione descrive il white paper. (allegato White Paper in sospeso)


## Domande frequenti sulla sicurezza di AEM Screens {#faqs-screens}

Le seguenti domande frequenti presuppongono un’architettura del lettore autenticata e registrata che utilizza HTTPS come protocollo di comunicazione tra il lettore e il server AEM.

### Domande frequenti 1 {#faq1}

Il traffico del lettore può essere reindirizzato a un server dannoso e istruito a scaricare e riprodurre contenuti multimediali dannosi?

**Risposta**

Non è possibile perché la connessione HTTP identifica entrambe le estremità della connessione e la crittografa. Se tenti di trovarti nel mezzo e di intercettarlo, vedrai solo contenuti crittografati, e se tenti di impersonare il server, il lettore ti rifiuterà perché il tuo certificato è diverso.


### Domande frequenti 2 {#faq2}

Devo utilizzare HTTP o HTTP?

**Risposta**

Utilizza HTTP. Questo è un must se sei preoccupato della sicurezza. Con gli HTTP la comunicazione è crittografata tra il lettore e il server e intercettare il contenuto o modificarlo sarà praticamente impossibile.


### Domande frequenti 3 {#faq3}

In un download di contenuti, esiste una sorta di firma del contenuto o dell’hash?

**Risposta**

Ogni risorsa è firmata (SHA) dal server e quindi convalidata dal lettore per lo stesso hash, in modo da garantire l’integrità.
Se l’hash non corrisponde, tenteremo di riconvalidarlo 3 volte. Dopo 3 tentativi, il comando di download non è valido.


### Domande frequenti 4 {#faq4}

Il server AEM è sicuro?

**Risposta**

Ans 4. Supponendo che tu sia in AMS, ci occupiamo di tutta la sicurezza del server utilizzando le stesse funzioni di Sites o Assets.


### Domande frequenti 5 {#faq5}

Il dispositivo è sicuro?

**Risposta**

Un giocatore fisicamente compromesso può teoricamente essere manipolato per riprodurre qualsiasi contenuto. È anche possibile collegare il lettore all&#39;esterno e collegare un dispositivo USB/HDMI.

Si consiglia quindi di mettere i dispositivi fuori dalla portata, preferibilmente in un contenitore protetto, con il cablaggio fissato. Disattivare inoltre le porte remote a infrarossi.

Se il sistema operativo del dispositivo non viene aggiornato regolarmente, il sistema operativo potrebbe rimanere esposto a fori di sicurezza e consentire attacchi remoti attraverso la rete.

>[!NOTE]
>
>Si consiglia di dotare i dispositivi di funzionalità di aggiornamento e controllo remoto (desktop remoto, soluzione MDM, ecc.). Si consiglia inoltre di utilizzare una rete privata, non esposta ad esempio al WIFI pubblico.


### Domande frequenti 6 {#faq6}

Come potrebbe un hacker tentare di compromettere un giocatore?

**Risposta**

L’unico modo per compromettere un dispositivo di riproduzione è:

1. compromettere il DNS in modo che rappresenti il server sul suo nome host e
1. compromesso
   1. il lato server del certificato per rappresentare il server
   1. e rappresenta il certificato lato client

>[!IMPORTANT]
>Anche se un dispositivo è compromesso, è comunque possibile revocarne facilmente le credenziali in modo che non possa più connettersi all&#39;AEM.





