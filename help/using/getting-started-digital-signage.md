---
title: Nozioni di base del digital signage per [!UICONTROL AEM Screens]
seo-title: Basics Of Digital  Signage for [!UICONTROL AEM Screens]
description: La guida descrive i fondamenti di un progetto di digital signage
seo-description: The guide describes the basics of a digital signage project
exl-id: e3913be2-9028-4773-a034-e16924a71e04
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 2%

---

# Nozioni di base di un progetto di digital signage {#basics-digital-signage}

Prima di immergerti nelle best practice per l’implementazione di AEM Screens, è importante considerare il progetto come un progetto di digital signage, invece di uno sviluppo software tradizionale.

Questa sezione fornisce consigli sui principali elementi chiave critici prima dell’implementazione di un progetto AEM Screens.

## Elementi chiave nel digital signage {#key-elements}

Il *Elementi chiave* in un progetto di digital signage:

![](/help/assets/Elements-Revised.png)

Definire gli elementi chiave è essenziale prima di implementare un progetto di digital signage:

1. **Hardware**

   L’hardware definisce i componenti hardware ideali per l’implementazione del progetto di digital signage:
   * Il dispositivo dispone di spazio di archiviazione sufficiente per eseguire tutte le varianti delle esperienze offline?
   * Sono consentiti il tipo e la lunghezza del cavo video? Il dispositivo supporta entrambe le risoluzioni desiderate (HD, Full HD, 4K, ecc.) e codec video che intendo distribuire (h.264, h.265, ecc.)
   * Uso del filo di rame fisico
   * Dimensioni degli schermi
   * Numero di schermate
      * orientation
      * proporzioni
      * preferenza di risoluzione

1. **Connettività**

   Connectivity pone l’accento sulle seguenti domande:
   * Rete (cellulare o wi-fi) o standalone?
      * è necessario consentire gli aggiornamenti dei contenuti USB?
      * è necessario consentire la raccolta dei dati di utilizzo?

1. **Installazione**

   L&#39;installazione include:
   * Display: orizzontale o verticale
   * Come verrà montato lo schermo?
      * Verticale e orizzontale
      * Alloggiamento completo
      * Piastra di copertura
   * Supporto di dispositivi fissi
   * Personale: responsabile dell&#39;installazione dell&#39;apparecchiatura e del suo collegamento alla rete
   * Quanto dista la fonte di alimentazione dall&#39;impianto?
   * Quanto dista il pannello fisico dal dispositivo effettivo?

1. **Contenuto**

   Il contenuto include:
   * Zona singola o zona multipla?
      * Quante risorse multimediali sono visualizzate sullo schermo contemporaneamente?
      * Quante pagine per le applicazioni interattive?
      * Definire il ciclo dell’interfaccia utente
      * Contenuto basato su dati?
   * Controllo della versione

1. **Interattiva**

   Il servizio interattivo include:
   * Tipo di touchscreen preferito? (resistivo, capacitivo, multi-touch)?
      * Pressione pulsante
      * Gesto
   * Attivazione dati (I/O)?
      * Comandi seriali di invio/ricezione (chiusura contatto, PLC, ecc.)
      * I dati in arrivo vengono visualizzati sullo schermo (RSS) o attivano il contenuto
      * RFID/NFC/Bluetooth/iBeacon
      * Servizi esterni (meteo, traffico)

1. **Ambiente**

   L&#39;ambiente sottolinea:
   * Posizione di visualizzazione?
      * Interno ed esterno
      * Fuori dalla portata o direttamente esposto
   * Requisito particolare di temperatura?
   * Prova di atti vandalici?
   * Luce ambiente elevata? Contrasti forti?

1. **Manutenzione**

   La manutenzione è incentrata su:

   * Sono necessari manuali di installazione/guide utente dettagliate?
   * Stiamo configurando (programmando) il dispositivo prima della spedizione?
   * È necessario acquisire ogni numero di serie a scopo di tracciamento?
   * Sono previsti requisiti di alimentazione di riserva (alimentazione senza interruzioni)?
   * Come vengono distribuiti gli aggiornamenti di sistema? E come vengono monitorati i dispositivi in remoto? È necessaria una soluzione MDM?
