---
title: Nozioni di base sul digital signage per [!UICONTROL AEM Screens]
description: Scopri le basi di un progetto di digital signage.
exl-id: e3913be2-9028-4773-a034-e16924a71e04
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Nozioni di base di un progetto di digital signage {#basics-digital-signage}

Prima di immergerti nelle best practice per l’implementazione di AEM Screens, è importante considerare il progetto come un progetto di digital signage, invece di uno sviluppo software tradizionale.

Questa sezione fornisce consigli sui principali elementi chiave fondamentali per l’implementazione di un progetto AEM Screens.

## Elementi chiave nel digital signage {#key-elements}

Gli elementi chiave *1&rbrace; in un progetto di digital signage sono:*

![](/help/assets/Elements-Revised.png)

Definire gli elementi chiave è essenziale prima di implementare un progetto di digital signage:

1. **Hardware**

   L’hardware definisce i componenti hardware ideali per l’implementazione del progetto di digital signage:
   * Il dispositivo dispone di spazio di archiviazione sufficiente per eseguire tutte le varianti delle esperienze offline?
   * Sono consentiti il tipo e la lunghezza del cavo video? Il dispositivo supporta sia le risoluzioni desiderate (HD, Full HD, `4K` e così via) che i codec video che intendo distribuire (h.264, h.265 e così via)
   * Uso del filo di rame fisico
   * Dimensioni degli schermi
   * Numero di schermate
      * orientation
      * proporzioni
      * preferenza di risoluzione

1. **Connettività**

   Connectivity pone l’accento sulle seguenti domande:
   * Rete (cellulare o wi-fi) o standalone?
      * È necessario consentire gli aggiornamenti dei contenuti USB?
      * Devi consentire l’utilizzo della raccolta dati?

1. **Installazione**

   L&#39;installazione include:
   * Display: orizzontale o verticale
   * Come viene montato lo schermo?
      * Orientamento verticale e orientamento orizzontale
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

1. **Interattivo**

   Il servizio interattivo include:
   * Tipo di touchscreen preferito? (resistivo, capacitivo, multi-touch)?
      * Pressione pulsante
      * Gesto
   * Attivazione dati (I/O)?
      * Invio/ricezione di comandi seriali (chiusura contatto, PLC e così via)
      * I dati in arrivo vengono visualizzati sullo schermo (RSS) o attivano il contenuto
      * RFID/NFC/Bluetooth/iBeacon
      * Servizi esterni (meteo, traffico)

1. **Ambiente**

   L&#39;ambiente pone l&#39;accento su:
   * Mostrare la posizione?
      * Interno ed esterno
      * Fuori dalla portata o direttamente esposto
   * Requisito particolare di temperatura?
   * Prova di atti vandalici?
   * Luce ambiente elevata? Contrasti forti?

1. **Manutenzione**

   La manutenzione è incentrata su:

   * Sono necessari manuali di installazione e guide utente?
   * Si sta configurando (programmando) il dispositivo prima della spedizione?
   * È necessario acquisire ogni numero di serie a scopo di tracciamento?
   * Sono previsti requisiti di alimentazione di riserva (alimentazione senza interruzioni)?
   * Come vengono distribuiti gli aggiornamenti di sistema? E come vengono monitorati i dispositivi in remoto? È necessaria una soluzione MDM?
