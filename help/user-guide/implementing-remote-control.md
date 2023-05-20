---
title: Implementazione del telecomando
seo-title: Impementing the Remote Control
description: Seguire questa pagina per ulteriori informazioni sulla funzione Screens Remote Control.
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
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: 6cd68194bf3128464ec368f3e7fd69d20925c3d6
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Utilizzo del telecomando Screens  {#implementing-remote-control}

La funzione di controllo remoto semplifica l’accesso all’interfaccia utente di amministrazione, allo switcher di canale o a funzioni quali Cancella cache e ricarica. Inoltre, fornisce un metodo per visualizzare la versione locale del firmware e le informazioni di sistema sul lettore. Questo è particolarmente utile perché può essere difficile collegare un mouse e operare su dispositivi di produzione che sono fuori portata e ancora di più se il lettore ha perso la connessione con l&#39;AEM. Questo è utile anche quando si utilizza Samsung RMS perché la differenza di risoluzione può rendere molto difficile individuare e aprire l’interfaccia utente di amministrazione utilizzando un mouse.

## Combinazioni di tasti comuni del telecomando {#using-common-remote-control}

Su tutti i lettori è possibile utilizzare le seguenti combinazioni di tasti nel telecomando Screens:

1. Attiva/disattiva interfaccia utente amministratore - CTRL + 1
1. Attiva/disattiva cambio canale - CTRL + 2
1. Cancella cache - CTRL + ALT + 3
1. Ricarica lettore - CTRL + 4

## Combinazioni di tasti telecomando specifiche per il cittadino {#using-tizen-remote-control}

Specificamente per il lettore Tizen, è possibile utilizzare il telecomando hardware o il telecomando software disponibile in Samsung RMS per accedere a queste funzioni:

1. A - Attiva/Disattiva interfaccia utente amministratore
1. B - Attiva/disattiva switcher di canale
1. C - Cancella cache
1. D - Ricarica lettore

## Note di utilizzo aggiuntive {#using-additional-remote-control}

1. Con l’interfaccia utente di amministrazione aperta, puoi utilizzare le frecce su e giù per navigare tra le schede e visualizzare le informazioni nelle schede.
1. Con il commutatore di canale aperto, è possibile utilizzare i tasti freccia su e giù per navigare tra i canali e premere il tasto Invio (o il pulsante al centro delle frecce sul telecomando) per cambiare canale.

Il diagramma seguente illustra l’utilizzo chiave su un telecomando Samsung:
![immagine](assets/tizen/remote.png)

>[!NOTE]
>Se si impostano su false i valori di configurazione del dispositivo enableAdminUI e/o enableOSD, il telecomando non attiva l&#39;interfaccia utente amministratore e il commutatore di canale. Inoltre, non potrai utilizzare i tasti freccia per navigare nell’interfaccia utente o nei canali di amministrazione. Tuttavia, è ancora possibile cancellare la cache e ricaricare il lettore. È possibile disattivare la funzione di controllo remoto se una qualsiasi delle combinazioni di tastiera è in conflitto con il contenuto interattivo utilizzando questo codice:

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
