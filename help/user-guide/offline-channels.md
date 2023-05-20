---
title: Canali offline
seo-title: Offline Channels
description: Il lettore AEM Screens fornisce supporto offline per i canali sfruttando la tecnologia ContentSync. Segui questa pagina per ulteriori informazioni sui gestori di aggiornamenti e sull’abilitazione della configurazione offline per un canale.
seo-description: The AEM Screens player provides offline support for channels by leveraging the ContentSync technology. Follow this page to learn more about update handlers and enabling offline configuration for a channel.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# Canali offline {#offline-channels}

Il lettore Screens fornisce supporto offline per i canali sfruttando il ***Sincronizzazione contenuti*** tecnologia.

I lettori utilizzano un server http locale per distribuire il contenuto decompresso.

Quando un canale è configurato per l’esecuzione *online*, il lettore distribuisce le risorse del canale accedendo al server AEM, ma quando il canale è configurato per l’esecuzione *offline*, il lettore distribuisce le risorse del canale da un server http locale.

Il flusso di lavoro per il processo è il seguente:

1. Analizza le pagine desiderate
1. Raccogli tutte le risorse correlate
1. Crea un pacchetto di tutto in un file zip
1. Scarica il file ZIP ed estrailo localmente
1. Visualizza copia locale del contenuto

## Gestori aggiornamenti {#update-handlers}

Il ***Sincronizzazione contenuti*** utilizza i gestori di aggiornamenti per analizzare e raccogliere tutte le pagine e le risorse necessarie per un progetto specifico. AEM Screens utilizza i seguenti gestori di aggiornamenti:

### Opzioni comuni {#common-options}

* *tipo*: tipo di gestore di aggiornamento da utilizzare
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
   <td>raccogliere le rappresentazioni della risorsa</td> 
   <td>[renditions=[]]: elenco di rendering da raccogliere. Valore predefinito per la rappresentazione originale</td> 
  </tr>
  <tr>
   <td>copia</td> 
   <td>copia la struttura specificata dal percorso</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Verifica della configurazione ContentSync {#testing-contentsync-configuration}

Per verificare la configurazione di ContentSync, segui i passaggi seguenti:

1. Apri `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Seleziona la configurazione nell’elenco
1. Fai clic su Cancella cache
1. Fai clic su Aggiorna cache
1. Fai clic su Scarica completo
1. Estrai il file zip
1. Avvia un server locale nella cartella estratta
1. Apri la pagina iniziale e controlla lo stato dell’app

## Abilitazione della configurazione offline per un canale {#enabling-offline-config-for-a-channel}

Per abilitare la configurazione offline per un canale, effettua le seguenti operazioni:

1. Inspect il contenuto del canale e verifica se è richiesto da un’istanza AEM (online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Passa al dashboard dei canali e fai clic su **...** nel **INFORMAZIONI SUL CANALE** Pannello per modificare le proprietà.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Passa alle proprietà del canale e assicurati che la casella di controllo sia disabilitata in **Canale** scheda. Fai clic su **Salva e chiudi**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Prima di distribuire correttamente il contenuto nel dispositivo, fai clic sul pulsante **Aggiorna contenuto offline**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Il **Offline** stato in **PROPRIETÀ** viene aggiornato di conseguenza.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect il contenuto del canale e verifica se è richiesto da Player-Cache locale.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Per ulteriori informazioni sul modello per i gestori di risorse offline personalizzati e sui requisiti minimi in `pom.xml` per quel progetto specifico, consulta [Modello per gestori personalizzati](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) in **Sviluppo di un componente personalizzato per AEM Screens**.
