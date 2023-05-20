---
title: Impostazione di ACL
seo-title: Setting up ACLs
description: Segui questa pagina per scoprire come separare i progetti utilizzando gli ACL in modo che ogni singolo utente o team gestisca il proprio progetto.
seo-description: Follow this page to learn how to segregate projects using ACLs so that each individual or team handles their own project.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 2%

---

# Impostazione di ACL {#setting-up-acls}

Nella sezione seguente viene illustrato come separare i progetti utilizzando ACL in modo che ogni singolo utente o team gestisca il proprio progetto.

In qualità di amministratore AEM, desideri che i membri del team di un progetto non interferiscano con altri progetti e che a ciascuno di essi vengano assegnati ruoli specifici in base ai requisiti del progetto.

## Impostazione delle autorizzazioni {#setting-up-permissions}

I passaggi seguenti riepilogano la procedura per la configurazione di ACL per un progetto:

1. Accedi all’AEM e passa a **Strumenti** > **Sicurezza**.

   ![screen_shot_2018-02-16alle10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Clic **Gruppi** e inserisci un ID (ad esempio, Acme).

   In alternativa, utilizza questo collegamento, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Successivamente, fare clic su **Salva**.

   ![screen_shot_2018-02-16alle12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Seleziona **Collaboratori** dall&#39;elenco e fare doppio clic su di esso.

   ![screen_shot_2018-02-18alle33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Aggiungi il **Acme** (progetto creato) in **Aggiungi membri al gruppo**. Fai clic su **Salva**.

   ![screen_shot_2018-02-18alle35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se si desidera che i membri del team di progetto registrino i giocatori (il che comporta la creazione di un utente per ogni giocatore), individuare gli utenti-amministratori del gruppo e aggiungere il gruppo ACME agli utenti-amministratori

1. Aggiungi tutti gli utenti che lavoreranno sul **Acme** Progetto per **Acme** gruppo.

   ![screen_shot_2018-02-18alle41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Impostare le autorizzazioni per il gruppo **Acme** utilizzando questo `(http://localhost:4502/useradmin)`.

   Seleziona il gruppo **Acme** e fai clic su **autorizzazioni**.

   ![screen_shot_2018-02-18alle41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorizzazioni {#permissions}

Nella tabella seguente viene riepilogato il percorso con le autorizzazioni a livello di progetto:

| **Percorso** | **Autorizzazione** | **Descrizione** |
|---|---|---|
| `/apps/<project>` | LEGGI | Consente di accedere ai file di progetto (se applicabile) |
| `/content/dam/<project>` | ALL | Consente di accedere per archiviare le risorse dei progetti, come immagini o video, in DAM |
| `/content/screens/<project>` | ALL | Rimuove l’accesso a tutti gli altri progetti in /content/screens |
| `/content/screens/svc` | LEGGI | Fornisce accesso al servizio di registrazione |
| `/libs/screens` | LEGGI | Consente di accedere a DCC |
| `/var/contentsync/content/screens/` | ALL | Consente di aggiornare il contenuto offline per il progetto |

>[!NOTE]
>
>In alcuni casi, puoi separare le funzioni di authoring (come la gestione delle risorse e la creazione di canali) dalle funzioni di amministrazione (come la registrazione dei lettori). In questo scenario, crea due gruppi e aggiungi il gruppo Author ai collaboratori e il gruppo Admin sia ai collaboratori che agli amministratori degli utenti.

### Creazione di gruppi {#creating-groups}

La creazione di un nuovo progetto dovrebbe anche creare gruppi di utenti predefiniti a cui è assegnato un set di autorizzazioni di base. È necessario estendere le autorizzazioni ai ruoli tipici di AEM Screens.

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
   <td>Amministratori Screens<br /> <em>screens-admins</em></td>
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
   <td>Utenti Screens<br /> <em>screens-users</em></td>
   <td>Crea e aggiorna canali e pianificazioni e assegna alla posizione in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Di Collaboratori</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operatori Screens<br /> <em>operatori di schermi</em></td>
   <td>Creare e aggiornare la struttura della posizione e registrare i lettori in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Di Collaboratori</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Lettori Screens<br /> <em>schermi-&lt;project&gt;-dispositivi</em></td>
   <td>Raggruppa automaticamente tutti i lettori e tutti i lettori/dispositivi appartenenti ai collaboratori.</td>
   <td><p> Membro di collaboratori</p> </td>
  </tr>
 </tbody>
</table>
