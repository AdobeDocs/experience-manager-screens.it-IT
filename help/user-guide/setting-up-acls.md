---
title: Impostazione degli ACL
seo-title: Impostazione degli ACL
description: Segui questa pagina per scoprire come separare i progetti utilizzando ACL in modo che ogni singolo utente o team gestisca il proprio progetto.
seo-description: Segui questa pagina per scoprire come separare i progetti utilizzando ACL in modo che ogni singolo utente o team gestisca il proprio progetto.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Amministrazione di schermi
role: Administrator
level: Intermedio
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# Impostazione delle ACL {#setting-up-acls}

La sezione seguente spiega come separare i progetti utilizzando ACL in modo che ogni singolo utente o team gestisca il proprio progetto.

In qualità di amministratore AEM, assicurati che i membri del team di un progetto non interferiscano con altri progetti e che a ciascuno di essi siano assegnati ruoli specifici in base ai requisiti del progetto.

## Impostazione delle autorizzazioni {#setting-up-permissions}

I passaggi seguenti riepilogano la procedura per l&#39;impostazione delle ACL per un progetto:

1. Accedi a AEM e passa a **Strumenti** > **Sicurezza**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Fai clic su **Groups** e immetti un ID (ad esempio, Acme).

   In alternativa, utilizza questo collegamento, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Successivamente, fare clic su **Salva**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Seleziona **Collaboratori** dall’elenco e fai doppio clic su di esso.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Aggiungi il **Acme** (progetto creato) a **Aggiungi membri al gruppo**. Fai clic su **Salva**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se desideri che i membri del team di progetto registrino i giocatori (che comporta la creazione di un utente per ogni giocatore), trova gli utenti-amministratori del gruppo e aggiungi il gruppo ACME agli utenti-amministratori

1. Aggiungi tutti gli utenti che lavoreranno al progetto **Acme** al gruppo **Acme** .

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Imposta le autorizzazioni per il gruppo **Acme** utilizzando questo `(http://localhost:4502/useradmin)`.

   Seleziona il gruppo **Acme** e fai clic su **permissions**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorizzazioni  {#permissions}

La tabella seguente riepiloga il percorso con le autorizzazioni a livello di progetto:

| **Percorso** | **Autorizzazione** | **Descrizione** |
|---|---|---|
| `/apps/<project>` | LETTURA | Consente l’accesso ai file di progetto (se applicabile) |
| `/content/dam/<project>` | ALL | Consente di accedere all’archivio delle risorse dei progetti, come immagini o video in DAM |
| `/content/screens/<project>` | TUTTO | Rimuove l’accesso a tutti gli altri progetti in /content/screens |
| `/content/screens/svc` | LETTURA | Accesso al servizio di registrazione |
| `/libs/screens` | LETTURA | Consente l’accesso a DCC |
| `/var/contentsync/content/screens/` | TUTTO | Consente di aggiornare il contenuto offline del progetto |

>[!NOTE]
>
>In alcuni casi, puoi separare le funzioni di authoring (come la gestione delle risorse e la creazione dei canali) dalle funzioni di amministrazione (come la registrazione dei lettori). In questo scenario, crea due gruppi e aggiungi il gruppo autori ai collaboratori e il gruppo di amministratori ai collaboratori e agli amministratori.

### Creazione di gruppi {#creating-groups}

La creazione di un nuovo progetto deve inoltre creare gruppi di utenti predefiniti a cui sia assegnato un set di autorizzazioni di base. Estendi le autorizzazioni ai ruoli tipici di AEM Screens.

Ad esempio, puoi creare i seguenti gruppi specifici per il progetto:

* Amministratori di progetto Screens
* Operatori di progetto Screens (registra lettori e gestisce posizioni e dispositivi)
* Utenti progetto Screens (lavorare con canali, pianificazioni e assegnazioni di canali)

La tabella seguente riepiloga i gruppi con descrizione e autorizzazioni per un progetto AEM Screens:

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
     <li>Membro Dei Contribuenti</li>
     <li>Membro degli utenti amministratori</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Utenti Screens<br /> <em>screens-users</em></td>
   <td>Crea e aggiorna canali e pianificazioni e assegna a posizione in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dei Contribuenti</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operatori schermo<br /> <em>screens-operator</em></td>
   <td>Crea e aggiorna la struttura della posizione e registra i lettori in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dei Contribuenti</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Lettori Screens<br /> <em>screens-&lt;project&gt;-devices</em></td>
   <td>Raggruppa automaticamente tutti i giocatori e tutti i giocatori/dispositivi sono membri dei collaboratori.</td>
   <td><p> Membro dei collaboratori</p> </td>
  </tr>
 </tbody>
</table>

