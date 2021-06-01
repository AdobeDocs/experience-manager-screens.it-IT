---
title: Nozioni di base del digital signage per [!UICONTROL AEM Screens]
seo-title: Nozioni di base del digital signage per [!UICONTROL AEM Screens]
description: La guida descrive le basi di un progetto di digital signage
seo-description: La guida descrive le basi di un progetto di digital signage
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 2%

---


# Nozioni di base di un progetto di digital signage {#basics-digital-signage}

Prima di immergerti nelle best practice di implementazione di AEM Screens, è importante considerare il progetto come un progetto di digital signage, invece di uno sviluppo software tradizionale.

Questa sezione fornisce consigli sui principali elementi chiave critici prima dell’implementazione di un progetto AEM Screens.

## Elementi chiave del digital signage {#key-elements}

Gli *elementi chiave* in un progetto di digital signage sono:

![](/help/assets/Elements-Revised.png)

La definizione degli elementi chiave è essenziale prima di implementare un progetto di digital signage:

1. **Hardware**

   L&#39;hardware definisce i componenti hardware ideali per l&#39;implementazione del progetto di digital signage:
   * Il dispositivo dispone di spazio di archiviazione sufficiente per eseguire tutte le varianti delle esperienze offline?
   * È stato consentito il tipo e la lunghezza del cavo video? Il dispositivo supporta entrambe le risoluzioni desiderate (HD, FullHD, 4K, ecc.) e i codec video che sto pianificando di implementare (h.264, h.265, ecc.)
   * Utilizzo del filo di rame fisico
   * Dimensioni degli schermi
   * Numero di schermate
      * orientation
      * proporzioni
      * preferenza di risoluzione

1. **Connettività**

   La connettività pone l’accento sulle seguenti domande:
   * Rete (cellulare o wi-fi) o indipendente?
      * è necessario consentire gli aggiornamenti dei contenuti USB?
      * è necessario consentire la raccolta dati di utilizzo?

1. **Installazione**

   L&#39;installazione include:
   * Visualizza: orizzontale o verticale
   * Come verrà montato lo schermo?
      * Verticale e orizzontale
      * Alloggio completo
      * Piastra di copertura
   * Supporto di fissaggio
   * Personale: responsabile dell&#39;installazione dell&#39;apparecchiatura e della sua connessione alla rete
   * Quanto dista la fonte di energia dal dispositivo?
   * Quanto dista il pannello fisico dal dispositivo?

1. **Contenuto**

   Il contenuto include:
   * Zona singola o zona multipla?
      * Quante risorse multimediali si trovano sullo schermo contemporaneamente?
      * Quante pagine per le applicazioni interattive?
      * Definire il loop dell’interfaccia utente
      * Contenuti basati su dati?
   * Controllo della versione

1. **Interattivo**

   Include interattivi:
   * Tipo di touchscreen preferito?(resistivo, capacitivo, multi-touch)?
      * Pressione pulsante
      * Gesto
   * Attivazione dei dati (I/O)?
      * Invio/ricezione di comandi seriali (chiusura a contatto, PLC, ecc.)
      * I dati in entrata vengono visualizzati sullo schermo (RSS) o attivano il contenuto
      * RFID/NFC/Bluetooth/iBeacon
      * Servizi esterni (meteo, traffico)

1. **di authoring**

   L&#39;ambiente sottolinea:
   * Posizione di visualizzazione?
      * Interno e esterno
      * Fuori portata o direttamente esposti
   * Requisito temp speciale?
   * Prove vandaliche?
   * Luce ambiente elevata? Contrasti forti?

1. **Manutenzione**

   La manutenzione pone l&#39;accento su:

   * Sono richieste guide dettagliate all&#39;installazione/guide utente?
   * Stiamo configurando (programmando) il dispositivo prima della spedizione?
   * È necessario acquisire ogni numero di serie a scopo di tracciamento?
   * Sono previsti requisiti di alimentazione di riserva (alimentazione non interrotta)?
   * Come vengono distribuiti gli aggiornamenti di sistema? E come vengono monitorati i dispositivi da remoto? È necessaria una soluzione MDM?
