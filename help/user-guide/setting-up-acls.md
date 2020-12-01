---
title: Impostazione degli ACL
seo-title: Impostazione degli ACL
description: Segui questa pagina per apprendere come separare i progetti utilizzando ACL in modo che ogni singolo o team gestisca il proprio progetto.
seo-description: Segui questa pagina per apprendere come separare i progetti utilizzando ACL in modo che ogni singolo o team gestisca il proprio progetto.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
translation-type: tm+mt
source-git-commit: 8356d5eb9449fd31d293c030620588e47fa6513e
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 1%

---


# Impostazione di ACL {#setting-up-acls}

Nella sezione seguente viene illustrato come separare i progetti utilizzando ACL in modo che ogni singolo o team gestisca il proprio progetto.

In qualità di amministratore AEM, assicuratevi che i membri del team di un progetto non interferiscano con altri progetti e che a ciascuno di essi siano assegnati ruoli specifici in base ai requisiti del progetto.

## Impostazione delle autorizzazioni {#setting-up-permissions}

La procedura seguente riassume la procedura per l&#39;impostazione di ACL per un progetto:

1. Accedete a AEM e andate a **Strumenti** > **Sicurezza**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Fare clic su **Groups** e inserire un ID (ad esempio, Acme).

   In alternativa, utilizzare questo collegamento, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Successivamente, fare clic su **Salva**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Selezionare **Collaboratori** dall&#39;elenco e fare doppio clic su di esso.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Aggiungete il **Acme** (progetto creato) a **Aggiungi membri al gruppo**. Fai clic su **Salva**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se desiderate che i membri del team di progetto registrino i giocatori (il che implica la creazione di un utente per ogni giocatore), trovate gli amministratori del gruppo e aggiungete il gruppo ACME agli amministratori utente

1. Aggiungete tutti gli utenti che lavoreranno sul progetto **Acme** al gruppo **Acme**.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Impostare le autorizzazioni per il gruppo **Acme** utilizzando questo `(http://localhost:4502/useradmin)`.

   Selezionare il gruppo **Acme** e fare clic su **permissions**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorizzazioni  {#permissions}

La tabella seguente riassume il percorso con le autorizzazioni a livello di progetto:

| **Percorso** | **Autorizzazione** | **Descrizione** |
|---|---|---|
| `/apps/<project>` | LEGGI | Consente l&#39;accesso ai file di progetto (se applicabile) |
| `/content/dam/<project>` | ALL | Consente di archiviare le risorse dei progetti, come immagini o video, in DAM |
| `/content/screens/<project>` | ALL | Rimuove l&#39;accesso a tutti gli altri progetti in /content/screens |
| `/content/screens/svc` | LEGGI | Fornisce l&#39;accesso al servizio di registrazione |
| `/libs/screens` | LEGGI | Fornisce l&#39;accesso a DCC |
| `/var/contentsync/content/screens/` | ALL | Consente di aggiornare il contenuto offline per il progetto |

>[!NOTE]
>
>In alcuni casi, potete separare le funzioni di creazione (come la gestione delle risorse e la creazione dei canali) dalle funzioni di amministrazione (come la registrazione dei lettori). In questo scenario, create due gruppi e aggiungete il gruppo di autori ai collaboratori e il gruppo di amministratori sia ai collaboratori che agli amministratori utente.

### Creazione di gruppi {#creating-groups}

La creazione di un nuovo progetto deve inoltre creare gruppi di utenti predefiniti ai quali sia assegnato un set di autorizzazioni di base. È necessario estendere le autorizzazioni ai ruoli tipici di  AEM Screens.

Ad esempio, potete creare i seguenti gruppi specifici per il progetto:

* Amministratori progetto Screens
* Operatori progetto Screens (registratori e gestione di posizioni e dispositivi)
* Utenti del progetto Screens (lavorare con canali, programmi e assegnazioni di canali)

Nella tabella seguente sono riepilogati i gruppi con descrizione e autorizzazioni per un progetto AEM Screens :

<table>
 <tbody>
  <tr>
   <td><strong>Nome gruppo</strong></td>
   <td><strong>Descrizione</strong></td>
   <td><strong>Autorizzazioni </strong></td>
  </tr>
  <tr>
   <td>Amministratori dello schermo<br /> <em>schermi-amministratori</em></td>
   <td>Accesso a livello di amministratore per  funzionalità AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dei Collaboratori</li>
     <li>Membro di amministratori utente</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Utenti dello schermo<br /> <em>screen-users</em></td>
   <td>Creare e aggiornare canali e pianificazioni e assegnarli alla posizione in  AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dei Collaboratori</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operatori dello schermo<br /> <em>schermate-operatori</em></td>
   <td>Creare e aggiornare la struttura della posizione e registrare i lettori in  AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dei Collaboratori</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Players<br /> <em>schermate-&lt;progetto&gt;-devices</em></td>
   <td>Gruppi tutti i lettori e tutti i lettori/dispositivi sono automaticamente membri dei collaboratori.</td>
   <td><p> Membro dei collaboratori</p> </td>
  </tr>
 </tbody>
</table>

