---
title: Registrazione dispositivo
seo-title: Registrazione dispositivo
description: Questa pagina descrive il processo di registrazione del dispositivo in un progetto AEM Screens .
seo-description: Questa pagina descrive il processo di registrazione del dispositivo in un progetto AEM Screens .
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
translation-type: tm+mt
source-git-commit: 6731c984122083ff340eda690452729c0b846fb5
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 1%

---


# Registrazione dispositivo {#device-registration}

La pagina seguente descrive il processo di registrazione del dispositivo in un progetto AEM Screens .

## Registrazione di un dispositivo {#registering-a-device}

Il processo di registrazione del dispositivo viene eseguito su due computer separati:

* Il dispositivo da registrare, ad esempio il display del segnale
* Server AEM utilizzato per registrare il dispositivo

>[!NOTE]
>
>Una volta scaricata la versione più recente di Windows Player (*.exe*), dalla pagina [AEM 6.4 Player Downloads](https://download.macromedia.com/screens/), seguire i passaggi sul lettore per completare l&#39;installazione ad hoc:
>
>1. Tenete premuto sull’angolo in alto a sinistra per aprire il pannello di amministrazione.
>1. Andate a **Configuration** dal menu delle azioni a sinistra e immettete l&#39;indirizzo della posizione dell&#39;istanza AEM in **Server**, quindi fate clic su **Save**.
>1. Fare clic sul collegamento **Registrazione** dal menu delle azioni a sinistra e seguire i passaggi per completare il processo di registrazione del dispositivo.

>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Sul dispositivo, avviate  AEM Screens Player. Viene visualizzata l’interfaccia utente di registrazione.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. In AEM, andate alla cartella **Devices** del progetto.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un nuovo progetto per schermi nel dashboard di AEM, vedere [Crea e gestisci progetto schermi](creating-a-screens-project.md).

1. Toccate/fate clic sul pulsante **Gestione dispositivi** nella barra delle azioni.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Toccate/fate clic sul pulsante **Registrazione dispositivo** in alto a destra.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Selezionate il dispositivo richiesto (come al punto 1) e toccate o fate clic su **Registra dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. In AEM, attendete che il dispositivo invii il codice di registrazione.

   ![screen_shot_2018-11-26at105150 am](assets/screen_shot_2018-11-26at105150am.png)

1. Nel dispositivo, controllare il **Codice di registrazione**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Se il **Codice di registrazione** è lo stesso su entrambi i computer, toccate/fate clic sul pulsante **Convalida** in AEM, come illustrato nel passaggio (6).
1. Impostate il nome desiderato per il dispositivo e fate clic su **Register**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Toccate/fate clic su **Fine** per completare il processo di registrazione.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >La **Registra nuovo** consente di registrare un nuovo dispositivo.
   >
   >La **Assegna display** consente di aggiungere direttamente il dispositivo a un display.

   Se si fa clic su **Fine**, sarà necessario assegnare il dispositivo a un display.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e gestione di una visualizzazione per il progetto Screens, fare riferimento a [Creazione e gestione di display](managing-displays.md).

### Assegnazione del dispositivo a un display {#assigning-device-to-a-display}

Se il dispositivo non è stato assegnato a uno schermo, attenetevi alla procedura seguente per assegnare il dispositivo a uno schermo nel progetto AEM Screens :

1. Selezionate il dispositivo e fate clic su **Assegna dispositivo** dalla barra delle azioni.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Selezionare il percorso della visualizzazione in **Percorso di configurazione del dispositivo/visualizzazione**.

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. Fare clic su **Assign** quando si seleziona il percorso.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Fare clic su **Fine** una volta che il dispositivo è stato assegnato correttamente, come illustrato nella figura seguente.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Inoltre, è possibile visualizzare il dashboard di visualizzazione facendo clic su **Fine**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

### Ricerca di un dispositivo da Gestione periferiche {#search-device}

Dopo aver registrato i dispositivi sul lettore, puoi visualizzare tutti i dispositivi dall&#39;interfaccia utente di Gestione dispositivi.

1. Andate all&#39;interfaccia utente di Gestione dispositivi dal progetto AEM Screens , ad esempio **DemoScreens** —> **Devices**.

1. Selezionate la cartella **Devices** e fate clic su **Device Manager** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/device-manager/device-manager-1.png)

1. Viene visualizzato l’elenco dei dispositivi registrati.

1. Se si dispone di un lungo elenco di dispositivi registrati, è ora possibile effettuare ricerche utilizzando l&#39;icona di ricerca dalla barra delle azioni

   ![immagine](/help/user-guide/assets/device-manager/device-manager-2.png)

   Oppure,

   Fare clic su `/` (barra) per richiamare la funzionalità di ricerca.

   ![immagine](/help/user-guide/assets/device-manager/device-manager-3.png)


#### Limiti della funzionalità di ricerca {#limitations}

* L&#39;utente sarà in grado di cercare qualsiasi parola esistente in *ID dispositivo* o *Nome dispositivo*.

   >[!NOTE]
   >Si consiglia di creare i nomi dei dispositivi in più parole, ad esempio *Boston Store Lobby* anziché in un&#39;unica *BostonStoreLobby*.

* Se si creano nomi di dispositivi come *Boston Store Lobby*, è possibile cercare qualsiasi parola *boston*, *store* o *lobby* ma se il nome del dispositivo è indicato come *BostonStoreLobby* ricerca *boston* non mostrerà i risultati.

* Caratteri jolly, `*` è supportato per la ricerca. Se si desidera trovare tutti i dispositivi con nomi che iniziano con *boston*, è possibile utilizzare *boston**.

* Se il nome del dispositivo è *BostonStoreLobby* e la ricerca di *boston* non restituirà il risultato, invece di utilizzare *boston** nei criteri di ricerca restituirà il risultato.

## Limitazioni per la registrazione del dispositivo {#limitations-on-device-registration}

Limitazioni della password utente a livello di sistema potrebbero causare un errore nella registrazione del dispositivo. La registrazione del dispositivo utilizza una password generata in modo casuale per creare l&#39;utente del dispositivo.

Se la password è limitata dalla configurazione *AuthorizableActionProvider*, la creazione dell&#39;utente del dispositivo potrebbe non riuscire.

>[!NOTE]
>
>La password casuale generata corrente è composta da 36 caratteri ASCII, compresi tra 33 e 122 (include quasi tutti i caratteri speciali).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Risorse aggiuntive {#additional-resources}

Per informazioni su  AEM Screens Player, vedere [ AEM Screens Player](working-with-screens-player.md).
