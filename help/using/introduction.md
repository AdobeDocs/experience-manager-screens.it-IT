---
title: Introduzione a [!UICONTROL AEM Screens]
seo-title: Best Practices Guide for [!UICONTROL AEM Screens] Projects
description: Questa pagina è una sezione introduttiva a AEM Screens
seo-description: This page provides an introduction to AEM Screens
exl-id: 11781e0b-0aca-4d08-aaad-87a7aaf28c24
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 83%

---

# Introduzione a AEM Screens {#introduction}

**Schermi AEM (Adobe Experience Manager)** è una soluzione di digital signage che consente di creare, pubblicare e riprodurre esperienze digitali dinamiche e interattive che coinvolgono diversi tipi di schermi in un evento insieme a una strategia di marketing digitale omni-channel completa.

AEM Screens consente di creare:

* **pannelli per menu digitali dedicati;**
* **consigli sui prodotti;**
* **immagini lifestyle di sfondo.**

Inoltre, Screens offre numerose applicazioni uniche per clienti e dipendenti in base al dominio in cui vengono implementate, ad esempio:

* **display interattivi;**
* **segnaletica;**
* **branding;**
* **aggiunta di atmosfera all’ambiente.**

La creazione e la gestione di una rete di digital signage con AEM Screens è semplice e intuitiva. Un’applicazione lettore ospita canali di contenuti creati per AEM Screens dai clienti o dai partner di implementazione. Le *posizioni* gestiscono una gerarchia di posizioni predefinita e contengono visualizzazioni. Ogni *display* ha un dashboard che mostra i diversi dispositivi e schermi collegati. I contenuti per AEM Screens vengono gestiti in *canali*. *AEM Screens Player* riproduce sui display i contenuti presenti nei canali.



>[!NOTE]
>
>Per informazioni dettagliate sulle diverse funzioni di sviluppo e gestione di un progetto AEM Screens, consulta la **[Guida utente di AEM Screens](https://helpx.adobe.com/it/experience-manager/6-5/screens/user-guide.html)**.

## AEM Sites e AEM Screens {#aem-sites-screens}

>[!NOTE]
>
>Se il team di implementazione ha esperienza nell’utilizzo delle applicazioni AEM Sites, è importante comprendere la differenza tra AEM Sites e AEM Screens.

AEM Screens fornisce una piattaforma unificata di authoring/riproduzione per distribuire i contenuti ai dispositivi di digital signage negli spazi pubblici. Anche se è importante mantenere quanta più coerenza possibile tra i canali Web e quelli interni, è necessario tenere presente alcune differenze.

* **Tempo di permanenza**: in genere, le pagine Web sono progettate per fornire un’ampia gamma di informazioni che possono essere utilizzate per un periodo di tempo relativamente più lungo. Al contrario, le esperienze digitali interne dovrebbero anticipare le esigenze dell&#39;osservatore e fornire indicazioni chiare e concise utili a coinvolgere l’utente. Ciò genera esperienze più mirate, curate e contestuali.

* **Distanza di visualizzazione**: le distanze di visualizzazione sono generalmente più lunghe o più lontane rispetto alla distanza di visualizzazione tipica di una pagina web. Di conseguenza, le dimensioni del testo dovrebbero essere maggiori e la spaziatura tra testo, immagini e altri contenuti complementari dovrebbe essere verificata in base alle dimensioni dello schermo e alla posizione prevista nello spazio fisico.

* **Persistenza**: le esperienze digitali devono sempre poter essere trasmesse all’utente, a prescindere dallo stato di connessione del dispositivo di riproduzione. Il lettore deve essere progettato in modo che una o più esperienze persistano sempre e possano essere distribuite indipendentemente dallo stato di connessione del dispositivo di riproduzione.

* **Segmentazione del loop multimediale**: la configurazione di ciascun dispositivo di riproduzione con un proprio segmento di loop garantisce che i contenuti localizzati possano essere facilmente creati, pubblicati e riprodotti nell’esperienza digitale complessiva. Le risorse multimediali contenute all’interno dei canali di sequenza incorporati vengono aggiunte al segmento di loop precedente e offrono l’opportunità di impostare come destinazione un segmento di loop multimediale per ciascun raggruppamento di posizioni.

* **Esperienze interattive**: un’applicazione chiosco touch può essere creata e distribuita in un canale Screens tramite AEM e l’editor SPA. È consigliabile applicare proprietà di progettazione omni-channel coerenti, un timer di inattività per ripristinare l’esperienza e un chiaro invito all’azione per le attività che l’applicazione può eseguire. La pagina di destinazione deve essere costituita da elementi digitali chiave progettati per trasmettere valore, richiamare l’attenzione dell’utente e richiedere all’utente di interagire.

AEM Screens fornisce un’infrastruttura per distribuire contenuti ai dispositivi fisici. I contenuti vengono assegnati ai canali in Screens, che possono avere contenuti multimediali o applicazioni touch screen. In questo framework, un’applicazione AEM Sites può essere distribuita come contenuto tramite un canale.

Prima di essere rilasciata in un canale in Screens, un’AEM Sites deve essere formattata per l’utilizzo con le dimensioni del dispositivo di visualizzazione a cui è destinata.

>[!NOTE]
>Molti componenti di AEM Sites non sono compatibili con AEM Screens. AEM Screens viene fornito con molti dei propri componenti che consentono di creare esperienze digitali senza dover essere personalizzati. Se i requisiti del progetto lo consentono, utilizza la funzionalità integrata di AEM Screens laddove possibile.
