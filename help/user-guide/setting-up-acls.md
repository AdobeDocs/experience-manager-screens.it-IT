---
title: Impostazione di ACL
description: Scopri come separare i progetti utilizzando gli ACL in modo che ogni singolo utente o team gestisca il proprio progetto.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 2%

---

# Impostazione di ACL {#setting-up-acls}

Nella sezione seguente viene illustrato come separare i progetti utilizzando ACL in modo che ogni singolo utente o team gestisca il proprio progetto.

In qualità di amministratore AEM, desideri garantire che i membri del team di un progetto non interferiscano con altri progetti e che a ciascuno degli utenti siano assegnati ruoli specifici in base ai requisiti del progetto.

## Impostazione delle autorizzazioni {#setting-up-permissions}

I passaggi seguenti riepilogano la procedura per la configurazione di ACL per un progetto:

1. Accedi all’AEM e passa a **Strumenti** > **Sicurezza**.

   ![screen_shot_2018-02-16alle10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Clic **Gruppi** e inserisci un ID (ad esempio, Acme).

   In alternativa, utilizza questo collegamento, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Quindi, fai clic su **Salva**.

   ![screen_shot_2018-02-16alle12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Clic **Collaboratori** dall&#39;elenco e fare doppio clic su di esso.

   ![screen_shot_2018-02-18alle33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Aggiungi il **Acme** (progetto che hai creato) a **Aggiungi membri al gruppo**. Fai clic su **Salva**.

   ![screen_shot_2018-02-18alle35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se si desidera che i membri del team di progetto registrino i giocatori (il che comporta la creazione di un utente per ogni giocatore), individuare gli utenti-amministratori del gruppo e aggiungere il gruppo ACME agli utenti-amministratori

1. Aggiungi tutti gli utenti che lavorano su **Acme** Progetto per **Acme** gruppo.

   ![screen_shot_2018-02-18alle41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Impostare le autorizzazioni per il gruppo **Acme** utilizzando questo `(http://localhost:4502/useradmin)`.

   Fai clic sul gruppo **Acme** e fai clic su **autorizzazioni**.

   ![screen_shot_2018-02-18alle41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorizzazioni {#permissions}

Nella tabella seguente viene riepilogato il percorso con le autorizzazioni a livello di progetto:

| **Percorso** | **Autorizzazione** | **Descrizione** |
|---|---|---|
| `/apps/<project>` | LEGGI | Fornisce l&#39;accesso ai file di progetto, se applicabile. |
| `/content/dam/<project>` | ALL | Consente di accedere per archiviare le risorse del progetto, come immagini o video, in DAM. |
| `/content/screens/<project>` | ALL | Rimuove l’accesso a tutti gli altri progetti in /content/screens. |
| `/content/screens/svc` | LEGGI | Fornisce l’accesso al servizio di registrazione. |
| `/libs/screens` | LEGGI | Consente di accedere a DCC. |
| `/var/contentsync/content/screens/` | ALL | Consente di aggiornare il contenuto offline del progetto. |

>[!NOTE]
>
>A volte è possibile separare le funzioni di authoring (come la gestione delle risorse e la creazione di canali) dalle funzioni di amministrazione (come la registrazione dei lettori). In questo scenario, crea due gruppi e aggiungi il gruppo Author ai collaboratori e il gruppo Admin sia ai collaboratori che agli amministratori degli utenti.

### Creazione di gruppi {#creating-groups}

La creazione di un progetto dovrebbe anche creare gruppi di utenti predefiniti a cui è assegnato un set di autorizzazioni di base. Estendi le autorizzazioni ai ruoli tipici definiti in AEM Screens.

Ad esempio, puoi creare i seguenti gruppi specifici del progetto:

* Amministratori progetto Screens
* Operatori di progetto Screens (registrazione dei lettori e gestione di posizioni e dispositivi)
* Utenti del progetto Screens (utilizzo di canali, pianificazioni e assegnazioni di canali)

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
   <td>Raggruppa automaticamente tutti i lettori e tutti i lettori/dispositivi sono membri dei collaboratori.</td>
   <td><p> Membro di collaboratori</p> </td>
  </tr>
 </tbody>
</table>
