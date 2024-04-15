---
title: Registrazione dispositivo
description: Scopri il processo di registrazione del dispositivo in un progetto AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Registrazione dispositivo {#device-registration}

La pagina seguente descrive il processo di registrazione del dispositivo in un progetto AEM Screens.

## Registrazione di un dispositivo {#registering-a-device}

Il processo di registrazione del dispositivo viene eseguito su due computer distinti:

* Il dispositivo effettivo da registrare, ad esempio il display per la segnaletica
* Server AEM utilizzato per registrare il dispositivo

>[!NOTE]
>
>Dopo aver scaricato l&#39;ultimo Windows Player (*.exe*), da [Download del lettore AEM 6.4](https://download.macromedia.com/screens/) , seguire i passaggi del lettore per completare l&#39;installazione ad hoc:
>
>1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
>1. Accedi a **Configurazione** dal menu Azioni sinistro e immettere l&#39;indirizzo di localizzazione dell&#39;istanza AEM in **Server** e fai clic su **Salva**.
>1. Seleziona la **Registrazione** dal menu di azione sinistro e i passaggi seguenti per completare il processo di registrazione del dispositivo.
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Sul dispositivo, avvia AEM Screens Player. Viene visualizzata l’interfaccia utente di registrazione.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. In AEM, passare al **Dispositivi** del progetto.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un progetto per Screens nel dashboard AEM, consulta [Creare e gestire un progetto Screens](creating-a-screens-project.md).

1. Tocca o fai clic sul pulsante **Gestione dispositivi** nella barra delle azioni.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Tocca o fai clic sul pulsante **Registrazione dispositivo** in alto a destra.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Seleziona il dispositivo richiesto (come al punto 1) e tocca o fai clic su **Registra dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. In AEM, attendi che il dispositivo invii il suo codice di registrazione.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Nel dispositivo, seleziona **Codice di registrazione**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Se il **Codice di registrazione** è lo stesso in entrambi i computer, tocca o fai clic su **Convalida** nell’AEM, come indicato al punto (6).
1. Impostare il nome desiderato per il dispositivo e fare clic su **Registrati**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Tocca o fai clic **Fine** per completare il processo di registrazione.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >Il **Registra nuovo** consente di registrare un nuovo dispositivo.
   >
   >Il **Assegna visualizzazione** consente di aggiungere direttamente il dispositivo a uno schermo.

   Se si fa clic su **Fine**, assegna il dispositivo a uno schermo.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e la gestione di una visualizzazione per il progetto Screens, consulta [Creazione e gestione delle visualizzazioni](managing-displays.md).

### Assegnazione del dispositivo a una visualizzazione {#assigning-device-to-a-display}

Se non hai assegnato il dispositivo a una visualizzazione, segui i passaggi seguenti per assegnare il dispositivo a una visualizzazione nel progetto AEM Screens:

1. Seleziona il dispositivo e fai clic su **Assegna dispositivo** dalla barra delle azioni.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Seleziona il percorso della visualizzazione in **Percorso configurazione dispositivo/display**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Clic **Assegna** quando si seleziona il percorso.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Clic **Fine** una volta che il dispositivo è stato assegnato correttamente, come illustrato nella figura seguente.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   È inoltre possibile visualizzare il dashboard di visualizzazione facendo clic su **Fine**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Ricerca di un dispositivo da Gestione dispositivi {#search-device}

Dopo aver registrato i dispositivi sul lettore, puoi visualizzarli tutti dall’interfaccia utente di Gestione dispositivi.

1. Dal progetto AEM Screens, accedi all’interfaccia utente di Gestione dispositivi, ad esempio, **DemoScreens** > **Dispositivi**.

1. Seleziona la **Dispositivi** cartella e fai clic su **Gestione dispositivi** dalla barra delle azioni.

   ![immagine](/help/user-guide/assets/device-manager/device-manager-1.png)

1. Viene visualizzato l’elenco delle periferiche registrate.

1. Se si dispone di un lungo elenco di dispositivi registrati, è ora possibile eseguire ricerche utilizzando l&#39;icona di ricerca nella barra delle azioni

   ![immagine](/help/user-guide/assets/device-manager/device-manager-2.png)

   Oppure

   Clic `/` (barra) per richiamare la funzionalità di ricerca.

   ![immagine](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limitazioni alla funzionalità di ricerca {#limitations}

* L’utente è in grado di cercare qualsiasi parola esistente nel *ID dispositivo* o *Nome dispositivo*.

  >[!NOTE]
  >Si consiglia di creare i nomi dei dispositivi in più parole, ad esempio *Lobby del negozio di Boston* anziché un singolo *LobbyStoreBoston*.

* Se si creano nomi di dispositivi quali *Lobby del negozio di Boston*, cerca qualsiasi parola *boston*, *archiviare*, o *atrio*. Tuttavia, se il nome del dispositivo è *LobbyStoreBoston*, quindi ricerca *boston* non mostra alcun risultato.

* wild card, `*` è supportato per la ricerca. Nel caso in cui si desideri trovare tutti i dispositivi con nomi che iniziano con *boston*, è possibile utilizzare *boston**.

* Se il nome del dispositivo è *LobbyStoreBoston* e ricerca *boston* non restituisce il risultato, quindi utilizza *boston** nei criteri di ricerca restituisce il risultato.

## Limitazioni alla registrazione del dispositivo {#limitations-on-device-registration}

Le restrizioni della password utente a livello di sistema potrebbero causare errori nella registrazione del dispositivo. La registrazione del dispositivo utilizza una password generata in modo casuale per creare l&#39;utente del dispositivo.

Se la password è limitata da *AuthorizableActionProvider* configurazione, la creazione dell&#39;utente del dispositivo potrebbe non riuscire.

>[!NOTE]
>
>La password casuale attualmente generata è composta da 36 caratteri ASCII, da 33 a 122 (include quasi tutti i caratteri speciali).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Altre risorse {#additional-resources}

Per informazioni su AEM Screens Player, consulta [Lettore AEM Screens](working-with-screens-player.md).
