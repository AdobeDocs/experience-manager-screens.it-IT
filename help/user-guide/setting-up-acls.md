---
title: Impostazione di ACL
description: Scopri come separare i progetti utilizzando gli elenchi di controllo di accesso (ACL, Access Control List) in modo che ogni singolo utente o team gestisca il proprio progetto.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
TQID: https://experienceleague.adobe.com/jqnuLmKXfDCSHbnVTwBRBZsCyXUVn7OghNa00-62WeM
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 550
ht-degree: 2%

---

# Impostazione degli elenchi di controllo di accesso (ACL) {#setting-up-acls}

>[!IMPORTANT]
>Questo contenuto è valido per AEM on-premise/AMS (AEM 6.5LTS e AEM 6.5). Per i contenuti di AEM as a Cloud Service Screens, consulta la [guida di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Nella sezione seguente viene illustrato come separare i progetti utilizzando gli elenchi di controllo di accesso (ACL, Access Control List) in modo che ogni singolo utente o team gestisca il proprio progetto.

In qualità di amministratore di AEM, desideri garantire che i membri del team di un progetto non interferiscano con altri progetti. A ogni utente vengono assegnati ruoli specifici in base ai requisiti del progetto.

## Impostazione delle autorizzazioni {#setting-up-permissions}

I passaggi seguenti riepilogano la procedura per la configurazione di ACL per un progetto:

1. Accedi ad AEM e passa a **Strumenti** > **Sicurezza**.

   ![schermata_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Fai clic su **Gruppi** e immetti un ID (ad esempio, Acme).

   In alternativa, utilizzare questo collegamento, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Fare clic su **Salva**.

   ![schermata_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Fare clic su **Collaboratori** dall&#39;elenco e fare doppio clic su di esso.

   ![schermata_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Aggiungi **Acme** (progetto creato) a **Aggiungi membri al gruppo**. Fai clic su **Salva**.

   ![schermata_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se si desidera che i membri del team di progetto registrino i giocatori (il che comporta la creazione di un utente per ogni giocatore), individuare gli utenti-amministratori del gruppo e aggiungere il gruppo ACME agli utenti-amministratori

1. Aggiungi tutti gli utenti che lavorano al progetto **Acme** al gruppo **Acme**.

   ![schermata_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configura le autorizzazioni per il gruppo **Acme** utilizzando `(http://localhost:4502/useradmin)`.

   Fai clic sul gruppo **Acme** e fai clic sulle **autorizzazioni**.

   ![schermata_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorizzazioni {#permissions}

Nella tabella seguente viene riepilogato il percorso con le autorizzazioni a livello di progetto:

| **Percorso** | **Autorizzazione** | **Descrizione** |
|---|---|---|
| `/apps/<project>` | LEGGI | Fornire l’accesso ai file di progetto, se applicabile. |
| `/content/dam/<project>` | ALL | Fornisci l’accesso per archiviare le risorse del progetto, ad esempio immagini o video, in DAM. |
| `/content/screens/<project>` | ALL | Rimuove l’accesso a tutti gli altri progetti in /content/screens. |
| `/content/screens/svc` | LEGGI | Fornire accesso al servizio di registrazione. |
| `/libs/screens` | LEGGI | Fornire accesso a DCC. |
| `/var/contentsync/content/screens/` | ALL | Consente di aggiornare il contenuto offline del progetto. |

>[!NOTE]
>
>A volte è possibile separare le funzioni di authoring (come la gestione delle risorse e la creazione di canali) dalle funzioni di amministrazione (come la registrazione dei lettori). In questo scenario, crea due gruppi e aggiungi il gruppo dell’autore ai collaboratori e il gruppo dell’amministratore sia ai collaboratori che agli amministratori degli utenti.

### Creazione di gruppi {#creating-groups}

La creazione di un progetto dovrebbe anche creare gruppi di utenti predefiniti a cui è assegnato un set di autorizzazioni di base. Estendi le autorizzazioni ai ruoli tipici definiti in AEM Screens.

Ad esempio, puoi creare i seguenti gruppi specifici del progetto:

* Amministratori di progetto Screens
* Screens Project Operators (registrazione dei lettori e gestione di posizioni e dispositivi)
* Utenti di Screens Project (utilizzo di canali, pianificazioni e assegnazioni di canali)

Nella tabella seguente sono riepilogati i gruppi con descrizione e autorizzazioni per un progetto AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nome gruppo</strong></td>
   <td><strong>Descrizione</strong></td>
   <td><strong>Autorizzazioni</strong></td>
  </tr>
  <tr>
   <td>Amministratori Screens<br /> <em><code>screens-admins</code></em></td>
   <td>Accesso a livello di amministratore per le funzionalità di AEM Screens</td>
   <td>
    <ul>
     <li>Membro Di Collaboratori</li>
     <li>Membro di utenti-amministratori</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Utenti Screens<br /> <em><code>screens-users</code></em></td>
   <td>Crea e aggiorna canali e pianificazioni e assegna a posizioni in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Di Collaboratori</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operatori Screens<br /> <em><code>screens-operators</code></em></td>
   <td>Creare e aggiornare la struttura della posizione e registrare i lettori in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Di Collaboratori</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Lettori Screens<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>Tutti i lettori e tutti i lettori/dispositivi sono automaticamente membri dei collaboratori.</td>
   <td><p> Membro di collaboratori</p> </td>
  </tr>
 </tbody>
</table>
