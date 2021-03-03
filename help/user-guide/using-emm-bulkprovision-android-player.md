---
title: Utilizzo di MDM o EMM per il provisioning in serie di Android Player
seo-title: Provisioning in blocco di Android Player utilizzando EMM o MDM
description: Segui questa pagina per informazioni sul provisioning in serie di Android Player utilizzando EMM o MDM
translation-type: tm+mt
source-git-commit: 793507b266b99051544b377e4a7effb92dc6feb6
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# Provisioning in blocco di Android Player utilizzando Enterprise Mobility Management {#bulk-provisioning}

Quando si distribuisce il lettore Android in blocco, diventa noioso registrare manualmente ogni singolo lettore con AEM. Si consiglia vivamente di utilizzare una soluzione EMM (Enterprise Mobility Management) come VMWare Airwatch, MobileIron o Samsung Knox per il provisioning e la gestione remota dell&#39;implementazione. AEM Screens Android Player supporta lo standard di settore EMM AppConfig per consentire il provisioning remoto.

## Implementazione del provisioning in blocco di Android Player utilizzando Enterprise Mobility Management {#implementation}

Segui i passaggi seguenti per consentire il provisioning in massa in Android Player:

1. Assicurati che il tuo dispositivo Android supporti i servizi Google Play.
1. Registrati i tuoi dispositivi Android Player con la tua soluzione EMM preferita che supporta AppConfig.
1. Accedi alla tua console EMM e estrae l’applicazione AEM Screens Player da Google Play.
1. Seleziona la configurazione gestita (o l&#39;opzione correlata).
1. Ora dovresti visualizzare un elenco delle opzioni del lettore che possono essere configurate (come il codice di registrazione del server e in serie).
1. Configura questi parametri, salva e distribuisci il criterio sui dispositivi.

   >[!NOTE]
   >I dispositivi devono ricevere l&#39;applicazione insieme alla configurazione e puntare al server AEM corretto con la configurazione selezionata. Se hai scelto di configurare il codice di registrazione in serie e lo hai mantenuto come configurato in AEM, il lettore dovrebbe essere in grado di registrarsi automaticamente. Se hai configurato una visualizzazione predefinita, può anche scaricare e mostrare alcuni contenuti predefiniti (che possono essere successivamente modificati secondo le tue esigenze).

Inoltre, è necessario verificare con il fornitore EMM il supporto AppConfig. I più popolari come [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Ferro mobile](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) e [Samsung Knox&lt;a8 11/> tra gli altri supportano questo standard di settore.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)


