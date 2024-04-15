---
title: Utilizza il flusso di lavoro per automatizzare gli aggiornamenti delle risorse per un canale AEM Screens
description: Scopri come creare un flusso di lavoro per elaborare automaticamente le risorse caricate in Adobe Experience Manager e assegnarle in modo dinamico a un canale Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 1%

---


# Utilizza il flusso di lavoro per automatizzare gli aggiornamenti delle risorse per un canale AEM Screens {#automate-channel-updates-workflow}

Scopri come creare un flusso di lavoro per elaborare automaticamente le risorse caricate in Adobe Experience Manager e assegnarle in modo dinamico a un canale Screens. In questo esempio, quando un’immagine viene aggiunta a una cartella specifica, viene attivato un flusso di lavoro che applica una sovrapposizione di testo dinamica (processo di filigrana) e assegna l’immagine a un canale Screens. Le lezioni apprese da questo esempio possono essere applicate a un’ampia varietà di scenari di automazione.

## Prerequisiti {#prerequisites}

Per completare questa esercitazione, è necessario quanto segue:

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65)
1. [AEM Service Pack 8 o superiore](https://experienceleague.adobe.com/it/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7 o superiore](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## Configurazione rapida {#quick-setup}

Il video seguente illustra come installare un pacchetto di codice di esempio che introduce un nuovo flusso di lavoro in Adobe Experience Manager. Questa funzione consente a un utente di aggiornare le proprietà di una cartella in AEM Assets per puntare a un canale Screens. Ogni volta che un’immagine viene aggiunta a tale cartella, viene aggiunta al canale AEM Screens specificato.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Scarica il pacchetto di codice compilato: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installa il pacchetto di cui sopra utilizzando Gestione pacchetti AEM.

## Modello flusso di lavoro {#workflow-model}

È stato creato uno schema di metadati di cartelle personalizzato per acquisire il canale Screens di destinazione in cui aggiungere le immagini. Per automatizzare l’elaborazione delle risorse vengono utilizzati due modelli di flusso di lavoro. Il **Aggiorna risorsa DAM** il flusso di lavoro è stato modificato per chiamare un flusso di lavoro personalizzato, **Elaborazione risorse demo Screens** che controlla la cartella contenitore della risorsa per determinare il canale Schermi di destinazione. Il **Elaborazione risorse demo Screens** workflow è anche responsabile dell&#39;applicazione della filigrana all&#39;immagine.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Passaggi del processo di flusso di lavoro personalizzato {#workflow-process-step}

Inspect: due passaggi del processo di flusso di lavoro personalizzati utilizzati come parte del **Elaborazione risorse demo Screens** flusso di lavoro.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

Il `AssetProcessingCheck.java` il flusso di lavoro personalizzato è un processo che esegue un controllo sul payload del flusso di lavoro. Determina se il payload è una risorsa e se la cartella contenitore è configurata per puntare a un canale AEM Screens. Se i requisiti sono soddisfatti, il passaggio del processo mantiene due proprietà: `screen-channel` e `asset-path`, ai metadati del flusso di lavoro.

Il `AddAssetToChannel.java` il flusso di lavoro personalizzato è una fase del processo che controlla i metadati del flusso di lavoro e aggiorna il canale AEM Screens in modo che faccia riferimento all’immagine.

1. Scarica il codice sorgente: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Decomprimi e visualizza il codice utilizzando l’IDE preferito.
