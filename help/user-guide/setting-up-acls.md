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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Impostazione degli ACL {#setting-up-acls}

Nella sezione seguente viene illustrato come separare i progetti utilizzando ACL in modo che ogni singolo o team gestisca il proprio progetto.

In qualità di amministratore AEM, è necessario assicurarsi che i membri del team di un progetto non interferiscano con altri progetti e che a ciascuno di essi siano assegnati ruoli specifici in base ai requisiti del progetto.

## Impostazione delle autorizzazioni {#setting-up-permissions}

La procedura seguente riassume la procedura per l'impostazione di ACL per un progetto:

1. Accedi ad AEM e passa a **Strumenti** &gt; **Protezione**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Fate clic su **Gruppi** e immettete un ID (ad esempio, Acme).

   In alternativa, usa questo collegamento, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Quindi, fate clic su **Salva**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Seleziona **Collaboratori** dall’elenco e fai doppio clic su di esso.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Aggiungete l’ **Acme** (progetto creato) per **aggiungere membri al gruppo**. Fai clic su **Salva**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se desiderate che i membri del team di progetto registrino i giocatori (il che implica la creazione di un utente per ogni giocatore), trovate gli amministratori del gruppo e aggiungete il gruppo ACME agli amministratori utente

1. Aggiungete tutti gli utenti che lavoreranno sul progetto **Acme** al gruppo **Acme** .

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Impostate le autorizzazioni per il gruppo **Acme** utilizzando questo `(http://localhost:4502/useradmin)`.

   Selezionate il gruppo **Account** e fate clic sulle **autorizzazioni**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorizzazioni {#permissions}

La tabella seguente riassume il percorso con le autorizzazioni a livello di progetto:

| **Percorso** | **Autorizzazione** | **Descrizione** |
|---|---|---|
| `/apps/<project>` | LEGGI | Consente l'accesso ai file di progetto (se applicabile) |
| `/content/dam/<project>` | ALL | Consente di archiviare le risorse dei progetti, come immagini o video, in DAM |
| `/content/screens/<project>` | ALL | Rimuove l'accesso a tutti gli altri progetti in /content/screens |
| `/content/screens/svc` | LEGGI | Fornisce l'accesso al servizio di registrazione |
| `/libs/screens` | LEGGI | Fornisce l'accesso a DCC |
| `/var/contentsync/content/screens/` | ALL | Consente di aggiornare il contenuto offline per il progetto |

>[!NOTE]
>
>In alcuni casi, potete separare le funzioni di creazione (come la gestione delle risorse e la creazione dei canali) dalle funzioni di amministrazione (come la registrazione dei lettori). In questo scenario, create due gruppi e aggiungete il gruppo di autori ai collaboratori e il gruppo di amministratori sia ai collaboratori che agli amministratori utente.

### Creazione di gruppi {#creating-groups}

La creazione di un nuovo progetto deve inoltre creare gruppi di utenti predefiniti ai quali sia assegnato un set di autorizzazioni di base. Estendi le autorizzazioni ai ruoli tipici di AEM Screens.

Ad esempio, potete creare i seguenti gruppi specifici per il progetto:

* Amministratori progetto Screens
* Operatori progetto Screens (registratori e gestione di posizioni e dispositivi)
* Utenti progetto Screens (lavorare con canali, programmi e assegnazioni canale)

La tabella seguente riepiloga i gruppi con descrizione e autorizzazioni per un progetto AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nome gruppo</strong></td>
   <td><strong>Descrizione</strong></td>
   <td><strong>Autorizzazioni</strong></td>
  </tr>
  <tr>
   <td>Amministratori<br /> schermo <em>schermate-amministratori</em></td>
   <td>Accesso a livello di amministratore per le funzionalità di AEM Screens</td>
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
   <td>Utenti<br /> schermo- <em>utenti</em></td>
   <td>Creazione e aggiornamento di canali e pianificazioni e assegnazione alla posizione in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dei Collaboratori</li>
     <li>&lt;progetto&gt; /content/screens</li>
     <li>&lt;progetto&gt; /content/dam</li>
     <li>&lt;progetto&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operatori<br /> <em>schermi-operatori</em></td>
   <td>Creazione e aggiornamento della struttura della posizione e dei lettori di registro in AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dei Collaboratori</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;progetto&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Schermi Lettori<br /> <em>schermate-we-retail-devices</em></td>
   <td>Gruppi tutti i lettori e tutti i lettori/dispositivi sono automaticamente membri dei collaboratori.</td>
   <td><p> Membro dei collaboratori</p> </td>
  </tr>
 </tbody>
</table>

