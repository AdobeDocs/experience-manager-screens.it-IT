---
title: Utilizza il flusso di lavoro per automatizzare gli aggiornamenti delle risorse per un canale AEM Screens
seo-title: Utilizza il flusso di lavoro per automatizzare gli aggiornamenti delle risorse per un canale AEM Screens
description: Scopri come creare un flusso di lavoro per elaborare automaticamente le risorse caricate su Adobe Experience Manager e assegnarle in modo dinamico a un canale Screens. In questo esempio, quando un’immagine viene aggiunta a una cartella specifica, viene attivato un flusso di lavoro che applica una filigrana dinamica e assegna l’immagine a un canale Screens. Le lezioni apprese da questo esempio possono essere applicate a un'ampia varietà di scenari di automazione.
seo-description: Scopri come creare un flusso di lavoro per elaborare automaticamente le risorse caricate su Adobe Experience Manager e assegnarle in modo dinamico a un canale Screens. In questo esempio, quando un’immagine viene aggiunta a una cartella specifica, viene attivato un flusso di lavoro che applica una filigrana dinamica e assegna l’immagine a un canale Screens. Le lezioni apprese da questo esempio possono essere applicate a un'ampia varietà di scenari di automazione.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Sviluppo di schermi
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# Utilizza il flusso di lavoro per automatizzare gli aggiornamenti delle risorse per un canale AEM Screens {#automate-channel-updates-workflow}

Scopri come creare un flusso di lavoro per elaborare automaticamente le risorse caricate su Adobe Experience Manager e assegnarle in modo dinamico a un canale Screens. In questo esempio, quando un’immagine viene aggiunta a una cartella specifica, viene attivato un flusso di lavoro che applica una sovrapposizione di testo dinamica (processo di filigrana) e assegna l’immagine a un canale Screens. Le lezioni apprese da questo esempio possono essere applicate a un&#39;ampia varietà di scenari di automazione.

## Prerequisiti {#prerequisites}

Per completare questa esercitazione è necessario quanto segue:

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=it)
1. [AEM Service Pack 8 o superiore](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=it)
1. [AEM 6.5 Screens FP7 o versioni successive](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## Configurazione rapida {#quick-setup}

Il video seguente illustra come installare un pacchetto di codice di esempio che introdurrà un nuovo flusso di lavoro in Adobe Experience Manager. Questa funzione consente a un utente di aggiornare le proprietà di una cartella in AEM Assets in modo che punti a un canale Screens. Ogni volta che un&#39;immagine viene aggiunta a quella cartella, viene aggiunta al canale schermate specificato.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Scarica il pacchetto di codice compilato: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installa il pacchetto di cui sopra utilizzando AEM Gestione pacchetti.

## modello flusso di lavoro{#workflow-model};

È stato creato uno schema di metadati della cartella personalizzato per acquisire il canale Screens di destinazione che deve essere aggiunto alle immagini. Per automatizzare l’elaborazione delle risorse vengono utilizzati due modelli di flussi di lavoro. Il flusso di lavoro **Risorsa di aggiornamento DAM** viene modificato per chiamare un flusso di lavoro personalizzato, **Elaborazione risorsa demo Screens**, che esaminerà la cartella contenente la risorsa per determinare il canale Screens di destinazione. Anche il flusso di lavoro **Screens Demo Asset Processing** è responsabile dell’applicazione della filigrana all’immagine.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Passaggi del processo del flusso di lavoro personalizzato {#workflow-process-step}

Due passaggi del processo di flusso di lavoro personalizzato di Inspect utilizzati come parte del flusso di lavoro **Elaborazione delle risorse di dimostrazione di Screens** .

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` è un processo di flusso di lavoro personalizzato che esegue un controllo sul payload del flusso di lavoro per determinare se il payload è una risorsa e se la cartella contenitore è configurata per puntare a un canale Screens. Se i requisiti sono soddisfatti, il passaggio del processo persiste nei metadati del flusso di lavoro di due proprietà, `screen-channel` e `asset-path`.

`AddAssetToChannel.java` è un passaggio del processo di flusso di lavoro personalizzato che esamina i metadati del flusso di lavoro e aggiorna il canale Screens per fare riferimento all&#39;immagine.

1. Scarica il codice sorgente: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Decomprimi e visualizza il codice utilizzando il tuo IDE preferito.
