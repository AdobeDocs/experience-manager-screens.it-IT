---
title: Canali offline
seo-title: Canali offline
description: 'Il lettore AEM Screens fornisce supporto offline per i canali sfruttando la tecnologia ContentSync. Segui questa pagina per ulteriori informazioni sull’aggiornamento dei gestori e sull’abilitazione della configurazione offline per un canale.  '
seo-description: 'Il lettore AEM Screens fornisce supporto offline per i canali sfruttando la tecnologia ContentSync. Segui questa pagina per ulteriori informazioni sull’aggiornamento dei gestori e sull’abilitazione della configurazione offline per un canale.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: Sviluppo di schermi
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 2%

---


# Canali offline {#offline-channels}

Il lettore Screens fornisce supporto offline per i canali sfruttando la tecnologia ***ContentSync*** .

I lettori utilizzano un server http locale per distribuire il contenuto decompresso.

Quando un canale è configurato per l&#39;esecuzione di *online*, il lettore serve le risorse del canale accedendo al server AEM, ma quando il canale è configurato per l&#39;esecuzione di *offline*, il lettore trasmette le risorse del canale da un server http locale.

Il flusso di lavoro del processo è il seguente:

1. Analizzare le pagine desiderate
1. Raccogliere tutte le risorse correlate
1. Crea un pacchetto in un file zip
1. Scarica il file ZIP ed estrarlo localmente
1. Visualizza la copia locale del contenuto

## Aggiorna gestori {#update-handlers}

Il ***ContentSync*** utilizza gestori di aggiornamenti per analizzare e raccogliere tutte le pagine e le risorse necessarie per un progetto specifico. AEM Screens utilizza i seguenti gestori di aggiornamenti:

### Opzioni comuni {#common-options}

* *tipo*: il tipo di gestore dell&#39;aggiornamento da utilizzare
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
   <td>raccoglie la libreria client specificata</td> 
   <td>[extension='']: può essere css o js, per raccogliere solo il primo, o solo il secondo</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>raccogliere i rendering delle risorse</td> 
   <td>[renditions=[]]: elenco delle rappresentazioni da raccogliere. Impostazioni predefinite del rendering originale</td> 
  </tr>
  <tr>
   <td>copia</td> 
   <td>copia la struttura specificata dal percorso</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Verifica della configurazione di ContentSync {#testing-contentsync-configuration}

Segui i passaggi riportati di seguito per verificare la configurazione di ContentSync:

1. Apri `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Seleziona la configurazione nell’elenco
1. Fai clic su Cancella cache
1. Fai clic su Aggiorna cache
1. Fai clic su Scarica completo
1. Estrai il file zip
1. Avvia un server locale nella cartella estratta
1. Apri la pagina iniziale e verifica lo stato dell’app

## Abilitazione della configurazione offline per un canale {#enabling-offline-config-for-a-channel}

Segui i passaggi seguenti per abilitare la configurazione offline per un canale:

1. Inspect il contenuto del canale e verifica se è richiesto da un&#39;istanza AEM (online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Passa al dashboard del canale e fai clic su **...** nel pannello **INFORMAZIONI CANALE** per modificare le proprietà.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Passa alle proprietà del canale e accertati che la casella di controllo sia disabilitata nella scheda **Canale** . Fai clic su **Salva e chiudi**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Prima che il contenuto venga distribuito correttamente sul dispositivo, fai clic su **Aggiorna contenuto offline**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Anche lo stato **Offline** in **PROPERTIES** viene aggiornato di conseguenza.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect il contenuto del canale e controlla se è richiesto dal locale Player-Cache.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Per ulteriori informazioni sul modello per gestori di risorse offline personalizzati e sui requisiti minimi in `pom.xml` per quel progetto specifico, consulta [Modello per gestori personalizzati](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) in **Sviluppo di un componente personalizzato per AEM Screens**.