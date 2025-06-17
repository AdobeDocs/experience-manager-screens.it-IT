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
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '721'
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
>Dopo aver scaricato la versione più recente di Windows Player (*.exe*) dalla pagina [Download di AEM 6.4 Player](https://download.macromedia.com/screens/), seguire la procedura del lettore per completare l&#39;installazione ad hoc:
>
>1. Premi a lungo nell’angolo in alto a sinistra per aprire il pannello di amministrazione.
>1. Passa a **Configurazione** dal menu Azioni a sinistra e immetti l&#39;indirizzo del percorso dell&#39;istanza di AEM in **Server**, quindi fai clic su **Salva**.
>1. Fai clic sul collegamento **Registrazione** dal menu Azioni a sinistra e sui passaggi seguenti per completare il processo di registrazione del dispositivo.
>

![schermata_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Sul dispositivo, avvia AEM Screens Player. Viene visualizzata l’interfaccia utente di registrazione.

   ![schermata_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. In AEM, passa alla cartella **Dispositivi** del progetto.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un progetto per Screens nel dashboard di AEM, vedere [Crea e gestisci progetto Screens](creating-a-screens-project.md).

1. Fare clic sul pulsante **Gestione periferiche** nella barra delle azioni.

   ![schermata_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Fai clic sul pulsante **Registrazione dispositivo** in alto a destra.

   ![schermata_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Fare clic sul dispositivo richiesto (come nel passaggio 1) e fare clic su **Registra dispositivo**.

   ![schermata_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. In AEM, attendi che il dispositivo invii il suo codice di registrazione.

   ![schermata_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Nel tuo dispositivo, controlla il **codice di registrazione**.

   ![schermata_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Se il **Codice di registrazione** è lo stesso in entrambi i computer, fare clic sul pulsante **Convalida** in AEM, come illustrato nel passaggio 6.
1. Impostare il nome desiderato per il dispositivo e fare clic su **Registra**.

   ![schermata_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Fai clic su **Fine** per completare il processo di registrazione.

   ![schermata_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >**Registra nuovo** consente di registrare un nuovo dispositivo.
   >
   >**Assegna visualizzazione** consente di aggiungere direttamente il dispositivo a una visualizzazione.

   Se si fa clic su **Fine**, assegnare il dispositivo a una visualizzazione.

   ![schermata_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e la gestione di una visualizzazione per il progetto Screens, vedere [Creazione e gestione di visualizzazioni](managing-displays.md).

### Assegnazione del dispositivo a una visualizzazione {#assigning-device-to-a-display}

Se non hai assegnato il dispositivo a una visualizzazione, segui i passaggi seguenti per assegnare il dispositivo a una visualizzazione nel progetto AEM Screens:

1. Fare clic sul dispositivo e fare clic su **Assegna dispositivo** nella barra delle azioni.

   ![schermata_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Fare clic sul percorso della visualizzazione nel **Percorso di configurazione schermo/dispositivo**.

   ![schermata_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Fare clic su **Assegna** quando si fa clic sul percorso.

   ![schermata_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Fare clic su **Fine** dopo aver assegnato correttamente il dispositivo, come illustrato nella figura seguente.

   ![schermata_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   È inoltre possibile visualizzare il dashboard di visualizzazione selezionando **Fine**.

   ![schermata_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Ricerca di un dispositivo da Gestione dispositivi {#search-device}

Dopo aver registrato i dispositivi sul lettore, puoi visualizzarli tutti dall’interfaccia utente di Gestione dispositivi.

1. Passa all&#39;interfaccia utente di Gestione dispositivi dal progetto AEM Screens, ad esempio **Schermi dimostrativi** > **Dispositivi**.

1. Fare clic sulla cartella **Dispositivi** e fare clic su **Gestione dispositivi** nella barra delle azioni.

   ![immagine](/help/user-guide/assets/device-manager/device-manager-1.png)

1. Viene visualizzato l’elenco delle periferiche registrate.

1. Se si dispone di un lungo elenco di dispositivi registrati, è ora possibile eseguire ricerche utilizzando l&#39;icona di ricerca nella barra delle azioni

   ![immagine](/help/user-guide/assets/device-manager/device-manager-2.png)

   Oppure

   Selezionare `/` (barra) per richiamare la funzionalità di ricerca.

   ![immagine](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limitazioni alla funzionalità di ricerca {#limitations}

* L&#39;utente è in grado di cercare qualsiasi parola esistente nel *ID dispositivo* o nel *Nome dispositivo*.

  >[!NOTE]
  >È consigliabile creare i nomi dei dispositivi in più parole, ad esempio *`Boston Store Lobby`*, anziché in un singolo *`BostonStoreLobby`*.

* Se sono stati creati nomi di dispositivo come *`Boston Store Lobby`*, verrà eseguita la ricerca di qualsiasi parola *`boston`*, *`store`* o *`lobby`*. Tuttavia, se il nome del dispositivo è *`BostonStoreLobby`*, la ricerca di *`boston`* non mostrerà alcun risultato.

* Il carattere jolly `*` è supportato per la ricerca. Se si desidera trovare tutti i dispositivi con nomi che iniziano con *`boston`*, utilizzare *`boston`**.

* Se il nome del dispositivo è *`BostonStoreLobby`* e la ricerca di *`boston`* non restituisce il risultato, l&#39;utilizzo di *`boston`** nei criteri di ricerca restituisce il risultato.

## Limitazioni alla registrazione del dispositivo {#limitations-on-device-registration}

Le restrizioni della password utente a livello di sistema potrebbero causare errori nella registrazione del dispositivo. La registrazione del dispositivo utilizza una password generata in modo casuale per creare l&#39;utente del dispositivo.

Se la configurazione di *AuthorizableActionProvider* limita la password, la creazione dell&#39;utente del dispositivo potrebbe non riuscire.

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

Per ulteriori informazioni su AEM Screens Player, vedere [AEM Screens Player](working-with-screens-player.md).
