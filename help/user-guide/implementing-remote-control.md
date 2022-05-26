---
title: Implementazione del telecomando
seo-title: Impementing the Remote Control
description: Segui questa pagina per informazioni sulla funzione Controllo remoto Screens.
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: ff59c3748ea69a37ca68e81e5bf753881e8464b0
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Utilizzo del telecomando Screens  {#implementing-remote-control}

La funzione di controllo remoto facilita l&#39;accesso all&#39;interfaccia utente amministratore, al commutatore di canale o a funzioni come Cancella cache e ricarica. Inoltre, fornisce un metodo per visualizzare la versione del firmware locale e le informazioni di sistema sul lettore. Questo è particolarmente utile perché può essere difficile collegare un mouse e operare su dispositivi di produzione che sono fuori portata e ancora di più se il lettore ha perso la connessione con AEM. Questo è utile anche quando si utilizza Samsung RMS perché la differenza di risoluzione può rendere molto difficile individuare e aprire l&#39;interfaccia utente amministratore utilizzando un mouse.

## Combinazioni di tasti comuni per il controllo remoto {#using-common-remote-control}

Su tutti i lettori è possibile utilizzare le seguenti combinazioni di tasti nel telecomando Screens:

1. Attiva/disattiva interfaccia utente amministratore - CTRL + 1
1. Attiva/disattiva il commutatore del canale - CTRL + 2
1. Cancella cache - CTRL + ALT + 3
1. Ricarica lettore - CTRL + 4

## Combinazioni specifiche di tasti di controllo remoto {#using-tizen-remote-control}

Specifico per il lettore Tizen, è possibile utilizzare il telecomando hardware o il telecomando software disponibile in Samsung RMS per accedere a queste funzionalità:

1. A - Attiva/Disattiva interfaccia utente amministratore
1. B - Commutatore del canale
1. C - Cancella cache
1. D - Ricarica lettore

## Note sull&#39;utilizzo aggiuntive {#using-additional-remote-control}

1. Con l’interfaccia utente amministratore aperta, puoi utilizzare le frecce verso l’alto o il basso per navigare nelle schede e visualizzare le informazioni nelle schede.
1. Con il commutatore del canale aperto, è possibile utilizzare i tasti freccia su e giù per navigare sui canali e premere il tasto Invio (o il pulsante al centro delle frecce sul telecomando) per cambiare i canali.

Il diagramma seguente illustra l&#39;utilizzo chiave di un remoto Samsung:
![immagine](assets/tizen/remote.png)

>[!NOTE]
>Se imposti i valori di configurazione del dispositivo di enableAdminUI e/o enableOSD su false, il telecomando non attiva l’interfaccia utente amministratore e il commutatore del canale. Inoltre, non potrai utilizzare i tasti freccia per navigare nell’interfaccia utente o nei canali di amministrazione. Tuttavia è ancora possibile cancellare la cache e ricaricare il lettore. È possibile disattivare la funzione di controllo remoto se una delle combinazioni di tastiera è in conflitto con il contenuto interattivo utilizzando questo codice:

```javascript require(/['util/ScreensDisplay'/], function() /{window.ScreensDisplay.ignoreRemoteControl = true;/}); ```
