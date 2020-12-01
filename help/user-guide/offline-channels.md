---
title: Canali offline
seo-title: Canali offline
description: 'Il lettore AEM Screens  fornisce supporto offline per i canali sfruttando la tecnologia ContentSync. Segui questa pagina per saperne di più sui gestori di aggiornamenti e sull''abilitazione della configurazione offline per un canale.  '
seo-description: 'Il lettore AEM Screens  fornisce supporto offline per i canali sfruttando la tecnologia ContentSync. Segui questa pagina per saperne di più sui gestori di aggiornamenti e sull''abilitazione della configurazione offline per un canale.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 2%

---


# Canali offline {#offline-channels}

Il lettore Screens fornisce supporto offline per i canali sfruttando la tecnologia ***ContentSync***.

I lettori utilizzano un server http locale per distribuire il contenuto decompresso.

Quando un canale è configurato per eseguire *online*, il lettore gestisce le risorse del canale accedendo al server AEM, ma quando il canale è configurato per eseguire *offline*, il lettore fornisce le risorse del canale da un server http locale.

Il flusso di lavoro per il processo è il seguente:

1. Analizzare le pagine desiderate
1. Raccolta di tutte le risorse correlate
1. Creare pacchetti di tutti gli elementi in un file zip
1. Scaricate il file ZIP ed estraetelo localmente
1. Visualizza copia locale del contenuto

## Gestori di aggiornamento {#update-handlers}

***ContentSync*** utilizza gestori di aggiornamento per analizzare e raccogliere tutte le pagine e le risorse necessarie per un progetto specifico.  AEM Screens utilizza i seguenti handler di aggiornamento:

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
   <td>estensione: estensione della risorsa da raccogliere<br /> [pathSuffix='']: suffisso da aggiungere al percorso del canale<br /> </td> 
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
1. Aprite la pagina iniziale e verificate il vostro stato dell&#39;app

## Abilitazione della configurazione offline per un canale {#enabling-offline-config-for-a-channel}

Per attivare la configurazione offline per un canale, effettuate le seguenti operazioni:

1.  Inspect il contenuto del canale e verificate se è richiesto da un&#39;istanza AEM (online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Andate al dashboard del canale e fate clic su **...** nel pannello **INFORMAZIONI CANALI** per modificare le proprietà.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Andate alle proprietà del canale e accertatevi che la casella di controllo sia disabilitata nella scheda **Canale**. Fai clic su **Salva e chiudi**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Prima che il contenuto venga distribuito correttamente nel dispositivo, fare clic su **Aggiorna contenuto offline**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Anche lo stato **Offline** in **PROPERTIES** si aggiorna di conseguenza.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1.  Inspect il contenuto del canale e controlla se è richiesto dalla cache locale del lettore.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Per ulteriori informazioni sul modello per i gestori di risorse offline personalizzati e sui requisiti minimi in `pom.xml` per quel progetto specifico, fare riferimento a [Template for Custom Handlers](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) in **Developing a Custom Component for  AEM Screens** (Modello per i gestori personalizzati&lt;a2/> in &lt;a3/>Sviluppo di un componente personalizzato per&lt;a4/>).