---
title: Nozioni di base del digital signage per schermi [!UICONTROL AEM]
seo-title: Nozioni di base del digital signage per schermi [!UICONTROL AEM]
description: La guida descrive le basi di un progetto di digital signage
seo-description: La guida descrive le basi di un progetto di digital signage
translation-type: tm+mt
source-git-commit: 30c724ea897fd2da5300bb5cad285d460af5de40

---


# Nozioni di base di un progetto di digital signage {#basics-digital-signage}

Prima di iniziare a utilizzare le procedure ottimali per l'implementazione di AEM Screens, è importante considerare il progetto come un progetto di digital signage, anziché come uno sviluppo software tradizionale.

Questa sezione contiene raccomandazioni sugli elementi chiave principali che sono critici prima dell'implementazione di un progetto AEM Screens.

## Elementi chiave del digital signage {#key-elements}

Gli elementi ** chiave di un progetto di digital signage sono:

![](/help/assets/Elements-Revised.png)

Prima di implementare un progetto di digital signage, è fondamentale definire gli elementi chiave:

1. **Hardware**

   L'hardware definisce i componenti hardware ideali per l'implementazione del progetto di digital signage:
   * Il dispositivo dispone di spazio di archiviazione sufficiente per eseguire tutte le varianti delle esperienze offline?
   * È stato consentito il tipo e la lunghezza del cavo video? Il dispositivo supporta entrambe le risoluzioni desiderate (HD, FullHD, 4K, ecc.) e i codec video che sto pianificando di implementare (h.264, h.265, ecc.)
   * Utilizzo del filo di rame fisico
   * Dimensioni degli schermi
   * Numero di schermate
      * orientation
      * proporzioni
      * preferenza di risoluzione

1. **Connettività**

   La connettività pone l'accento sulle seguenti domande:
   * Rete (cellulare o wi-fi) o standalone?
      * è necessario consentire l'aggiornamento dei contenuti USB?
      * è necessario consentire la raccolta dei dati di utilizzo?

1. **Installazione**

   L'installazione include:
   * Visualizza: orizzontale o verticale
   * Come verrà montato lo schermo?
      * Verticale e orizzontale
      * Struttura completa
      * Piastra di copertura
   * Supporto per la riparazione
   * Personale: responsabile dell'installazione dell'apparecchiatura e della sua connessione alla rete
   * Quanto distante è la fonte di energia dal dispositivo?
   * Quanto è distante il pannello fisico dal dispositivo?

1. **Contenuto**

   Il contenuto include:
   * Zona singola o zona multipla?
      * Quante risorse multimediali si trovano contemporaneamente sullo schermo?
      * Quante pagine per applicazioni interattive?
      * Definire il ciclo di interfaccia
      * Contenuti basati su dati?
   * Controllo della versione

1. **Interattivo**

   Interattivo include:
   * Tipo di touchscreen preferito?(resistivo, capacitivo, multi-touch)?
      * Tasto
      * Gesto
   * Attivazione dei dati (I/O)?
      * Invio/ricezione di comandi seriali (chiusura a contatto, PLC, ecc.)
      * I dati in entrata vengono visualizzati sullo schermo (RSS) o attivano il contenuto
      * RFID/NFC/Bluetooth/iBeacon
      * Servizi esterni (tempo, ufficio, ecc.)

1. **di authoring**

   L'ambiente sottolinea:
   * Posizione di visualizzazione?
      * Interno e esterno
      * Fuori portata o direttamente esposti
   * Requisito temporaneo speciale?
   * Prova di atti vandalici?
   * Luce ambiente elevata? Forti contrasti?

1. **Manutenzione**

   La manutenzione mette in evidenza:

   * Sono richieste guide/guide utente dettagliate per l'installazione?
   * Il dispositivo viene configurato (programmazione) prima della spedizione?
   * Dobbiamo acquisire ciascun numero di serie a scopo di tracciamento?
   * Sono previsti requisiti di alimentazione di backup (alimentatore ininterrotto)?
   * Come vengono distribuiti gli aggiornamenti di sistema? E come vengono monitorati i dispositivi da remoto? È necessaria una soluzione MDM?
