---
title: Elenco di controllo della sicurezza per AEM Screens
description: Ulteriori informazioni sull’elenco di controllo per la sicurezza di AEM Screens.
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Considerazioni sulla sicurezza del sistema per AEM Screens {#security-checklist}

>[!IMPORTANT]
>Una risorsa Git interna.

Questa pagina illustra le considerazioni sulla sicurezza del sistema per AEM Screens.


## White paper per la sicurezza di AEM Screens {#white-paper}

Questa sezione descrive il white paper. (allegato White Paper in sospeso)


## Domande frequenti sulla sicurezza di AEM Screens {#faqs-screens}

Le seguenti domande frequenti presuppongono un’architettura del lettore autenticata e registrata. Utilizza HTTPS come protocollo di comunicazione tra il lettore e il server AEM.

### Domande frequenti 1 {#faq1}

Il traffico del lettore può essere reindirizzato a un server dannoso e istruito a scaricare e riprodurre contenuti multimediali dannosi?

**Risposta**

Non è possibile perché la connessione HTTP identifica entrambe le estremità della connessione e la crittografa. Se provi a trovarti al centro e ad intercettarlo, vedi solo contenuto crittografato. Se tenti di impersonare il server, il lettore ti rifiuta perché il certificato è diverso.


### Domande frequenti 2 {#faq2}

Devo utilizzare HTTP o HTTP?

**Risposta**

Utilizza HTTP. Questo protocollo è un must se sei preoccupato per la sicurezza. Con gli HTTP, la comunicazione è crittografata tra il lettore e il server e intercettare il contenuto o modificarlo è impossibile.


### Domande frequenti 3 {#faq3}

In un download di contenuti, esiste una sorta di firma del contenuto o dell’hash?

**Risposta**

Ogni risorsa è firmata (SHA) dal server. Il lettore lo convalida quindi per lo stesso hash per garantire l’integrità.
Se l&#39;hash non corrisponde, il software tenta di riconvalidare tre volte. Dopo tre tentativi, il comando di download viene considerato non valido.


### Domande frequenti 4 {#faq4}

Il server AEM è sicuro?

**Risposta**

Se utilizzi AMS, il software si occupa di tutta la sicurezza del server utilizzando le stesse funzioni di Sites o Assets.


### Domande frequenti 5 {#faq5}

Il dispositivo è sicuro?

**Risposta**

Un giocatore fisicamente compromesso può teoricamente essere manipolato per riprodurre qualsiasi contenuto. È inoltre possibile scollegare il lettore e collegare una chiavetta USB/HDMI.

Mettere i dispositivi fuori dalla portata, preferibilmente in un contenitore protetto, con il cablaggio fissato. Disattivare inoltre le porte remote a infrarossi.

Se il sistema operativo del dispositivo non viene aggiornato regolarmente, il sistema operativo potrebbe rimanere esposto a fori di sicurezza e consentire attacchi remoti attraverso la rete.

>[!NOTE]
>
>Si consiglia di dotare i dispositivi di funzionalità di aggiornamento e controllo remoto (desktop remoto, soluzione MDM e così via). Si consiglia inoltre di utilizzare una rete privata, non esposta ad esempio al WIFI pubblico.


### Domande frequenti 6 {#faq6}

Come potrebbe un hacker tentare di compromettere un giocatore?

**Risposta**

L’unico modo per compromettere un dispositivo di riproduzione è:

1. compromettere il DNS per rappresentare il server su questo nome host e
1. compromesso
   1. il lato server del certificato per rappresentare il server
   1. e rappresenta il certificato lato client

>[!IMPORTANT]
>Anche se un dispositivo è compromesso, è comunque possibile revocarne facilmente le credenziali in modo che non possa più connettersi all&#39;AEM.





