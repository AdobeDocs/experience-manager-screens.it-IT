---
title: Canali offline
seo-title: Canali offline
description: 'Il lettore AEM Screens supporta i canali offline sfruttando la tecnologia ContentSync. Segui questa pagina per saperne di più sui gestori di aggiornamenti e sull''abilitazione della configurazione offline per un canale.  '
seo-description: 'Il lettore AEM Screens supporta i canali offline sfruttando la tecnologia ContentSync. Segui questa pagina per saperne di più sui gestori di aggiornamenti e sull''abilitazione della configurazione offline per un canale.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canali offline {#offline-channels}

Il lettore Screens fornisce supporto offline per i canali sfruttando la tecnologia ***ContentSync*** .

I lettori utilizzano un server http locale per distribuire il contenuto decompresso.

Quando un canale è configurato per l’esecuzione *online*, il lettore gestisce le risorse del canale accedendo al server AEM, ma quando il canale è configurato per l’esecuzione *offline*, il lettore fornisce le risorse del canale da un server HTTP locale.

Il flusso di lavoro per il processo è il seguente:

1. Analizzare le pagine desiderate
1. Raccolta di tutte le risorse correlate
1. Creare pacchetti di tutti gli elementi in un file zip
1. Scaricate il file ZIP ed estraetelo localmente
1. Visualizza copia locale del contenuto

## Aggiorna gestori {#update-handlers}

ContentSync ****** utilizza gestori di aggiornamento per analizzare e raccogliere tutte le pagine e le risorse necessarie per un progetto specifico. AEM Screens utilizza i seguenti handler di aggiornamento:

### Opzioni comuni {#common-options}

* *type*: il tipo di gestore di aggiornamenti da utilizzare
* *percorso*: percorso della risorsa
* *[targetRootDirectory]*: cartella di destinazione nel file zip

<table>
 <tbody>
  <tr>
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrizione</strong></td> 
   <td><strong>Opzioni</strong></td> 
  </tr>
  <tr>
   <td>canali</td> 
   <td>raccoglie un canale</td> 
   <td>estensione: estensione della risorsa per la raccolta<br /> di [pathSuffix='']: suffisso da aggiungere al percorso del canale<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>raccogliere la libreria client specificata</td> 
   <td>[extension='']: può essere css o js, per raccogliere solo il primo, o solo il secondo</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>raccogliere i rendering delle risorse</td> 
   <td>[rappresentazioni=[]]: elenco di rappresentazioni da raccogliere. Impostazione predefinita per la rappresentazione originale</td> 
  </tr>
  <tr>
   <td>copia</td> 
   <td>copiare la struttura specificata dal percorso</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Verifica della configurazione di ContentSync {#testing-contentsync-configuration}

Per verificare la configurazione di ContentSync, effettuate le seguenti operazioni:

1. Apri `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Selezionate la configurazione nell’elenco
1. Fate clic su Cancella cache
1. Fare clic su Aggiorna cache
1. Fai clic su Scarica
1. Estrarre il file zip
1. Avviare un server locale nella cartella estratta
1. Aprite la pagina iniziale e verificate il vostro stato dell'app

## Abilitazione della configurazione offline per un canale {#enabling-offline-config-for-a-channel}

Per attivare la configurazione offline per un canale, effettuate le seguenti operazioni:

1. Controlla il contenuto del canale e verifica se è richiesto da un’istanza AEM (Online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. **Andate al dashboard del canale e fate clic**... nel pannello **INFORMAZIONI** CANALE per modificare le proprietà.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Andate alle proprietà del canale e accertatevi che la casella di controllo sia disabilitata nella scheda **Canale** . Fate clic su **Salva e chiudi**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Prima che il contenuto venga distribuito correttamente sul dispositivo, fate clic su **Aggiorna contenuto** offline.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Anche lo stato **Offline** in **PROPERTIES** viene aggiornato di conseguenza.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Controllate il contenuto del canale e verificate se è richiesto dalla cache locale del lettore.

   ![chlimage_1-26](assets/chlimage_1-26.png)

