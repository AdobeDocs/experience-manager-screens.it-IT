---
title: Introduzione a [!UICONTROL AEM Screens]
seo-title: Guida alle best practice per i progetti [!UICONTROL AEM Screens]
description: Questa pagina è una sezione introduttiva di AEM Screens
seo-description: Questa pagina fornisce un'introduzione ad AEM Screens
translation-type: tm+mt
source-git-commit: 55999ae9ead7ab8986f4dcb69b0bbaa46933c9ec

---


# Introduzione a AEM Screens {#introduction}

**AEM (Adobe Experience Manager) Screens** è una soluzione di digital signage che consente di creare, pubblicare e riprodurre esperienze digitali dinamiche e interattive che coinvolgono diversi tipi di schermi per eventi in concerto con una strategia di marketing digitale omnicanale completa.

AEM Screens consente di creare:

* **schede di menu digitali dedicate**
* **raccomandazioni sui prodotti**
* **immagini stile di vita sullo sfondo**

Inoltre, Screens offre numerose applicazioni uniche per clienti e dipendenti in base al dominio in cui vengono distribuiti, ad esempio:

* **display interattivi**
* **metodo**
* **marchio**
* **aggiunta di atmosfera all'ambiente**

La creazione e la gestione di una rete di digital signage con AEM Screens è semplice e intuitiva. Un’applicazione lettore ospita canali di contenuto creati per AEM Screens dai clienti o dai partner di implementazione. *Le posizioni* gestiscono una gerarchia di posizioni predefinita e contengono visualizzazioni. Ogni *display* ha una dashboard che mostra diversi dispositivi e schermi collegati. Il contenuto per AEM Screens viene gestito nei *canali*. *AEM Screens Player* esegue il rendering del contenuto presente nei canali sui display.



>[!NOTE]
>
>Per informazioni dettagliate sulle diverse funzioni di sviluppo e gestione di un progetto AEM Screens, consulta la Guida **[utente di](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html)** AEM Screens.

## AEM Sites e AEM Screens {#aem-sites-screens}

> [!NOTE]
>
> Se il team di implementazione ha esperienza nell’utilizzo delle applicazioni AEM Sites, è importante comprendere la differenza tra AEM Sites e AEM Screens.

AEM Screens fornisce una piattaforma unificata di authoring/riproduzione per distribuire contenuti ai dispositivi di digital signage negli spazi pubblici. Anche se l'autore dell'esperienza deve sforzarsi di mantenere la coerenza tra i canali Web e interni all'evento, è necessario tenere presente alcune differenze.

* **Tempo** di permanenza: In genere, le pagine Web sono progettate per fornire un'ampia gamma di informazioni che possono essere utilizzate per un periodo di tempo relativamente più lungo. Al contrario, le esperienze digitali interne agli eventi dovrebbero anticipare le esigenze del visualizzatore e fornire indicazioni chiare e concise su come e perché l'utente dovrebbe impegnarsi. Ciò genera esperienze più mirate, curate e contestuali.

* **Distanza** di visualizzazione: Le distanze di visualizzazione sono generalmente più lunghe o più lontane rispetto alla distanza di visualizzazione tipica degli utenti con un sito Web. Di conseguenza, le dimensioni del testo dovrebbero normalmente essere maggiori e la spaziatura tra testo, immagini e altri contenuti gratuiti dovrebbe essere verificata in base alle dimensioni dello schermo e alla posizione prevista nello spazio fisico.

* **Persistenza**: Lo stato connesso del dispositivo di riproduzione non deve mai influenzare la trasmissione o meno all'utente delle esperienze digitali. Il lettore deve essere progettato in modo che una o più esperienze persistano sempre e possano essere distribuite indipendentemente dallo stato collegato del dispositivo di riproduzione.

* **Segmentazione** del ciclo multimediale: La configurazione di ciascun dispositivo di riproduzione con un proprio segmento di loop garantisce che il contenuto localizzato possa essere facilmente creato, pubblicato e riprodotto nell’esperienza digitale complessiva. Le risorse multimediali contenute all’interno dei canali di sequenza incorporati vengono aggiunte al segmento di loop precedente e offrono l’opportunità di impostare come destinazione un segmento di loop multimediale per ciascun raggruppamento di posizioni.

* **Esperienze** interattive: Un'applicazione chiosco touch può essere creata e distribuita in un canale Screens tramite AEM e l'editor SPA. È consigliabile applicare proprietà di progettazione omnicanale coerenti, un timer di inattività per ripristinare l'esperienza e una chiara chiamata all'azione per le attività che l'applicazione può eseguire. La pagina di destinazione deve essere costituita da elementi digitali chiave progettati per trasmettere valore, attirare l’utente sullo schermo e richiedere all’utente di interagire.

AEM Screens fornisce un framework per distribuire il contenuto ai dispositivi fisici. Il contenuto viene assegnato ai canali nelle schermate, che possono contenere contenuti multimediali o applicazioni per schermi touch screen. In questo framework, un'applicazione AEM Site può essere distribuita come contenuto tramite un canale.

Prima di essere rilasciato in un canale in uno schermo, un sito AEM deve essere formattato per l'uso nelle dimensioni del dispositivo di visualizzazione a cui è destinato.

> [!NOTE]
>
> Molti componenti di AEM Sites non sono compatibili con AEM Screens. AEM Screens viene fornito con molti dei propri componenti che consentono di creare esperienze digitali senza dover essere personalizzati. Se i requisiti del progetto lo consentono, utilizza la funzionalità integrata di AEM Screens laddove possibile.
