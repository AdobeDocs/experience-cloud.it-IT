---
title: Domande frequenti sulla gestione dei team
description: Risposte alle domande frequenti sulla gestione di team, membri e ruoli nei Rollout esperienza di Adobe.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---


# Domande frequenti sulla gestione dei team {#team-management-faq}

## Sto tentando di aggiungere un utente, ma la ricerca non restituisce alcun risultato {#user-not-found}

Ciò può verificarsi nell’ambiente di staging se l’utente non ha mai effettuato l’accesso a Staging in precedenza. Per risolvere questo problema, chiedi all’utente di accedere alla console Stage almeno una volta per creare il proprio account nel sistema di identità di Stage. Dopo aver effettuato l&#39;accesso, riprovare a cercarli.

## Sono un amministratore, ma non posso creare o modificare i flag di funzione {#admin-cannot-edit-flags}

I ruoli nei rollout di esperienza si escludono a vicenda. Il ruolo **Amministratore** concede le autorizzazioni di gestione del team ma non include le autorizzazioni di un **proprietario del rilascio del prodotto**. Per creare e modificare i flag di funzionalità, un membro deve avere il ruolo **Proprietario versione prodotto** oltre al ruolo **Amministratore**.

Per assegnare altri ruoli, contatta l’amministratore del team. Consulta [Ruoli utente](user-roles.md) per una descrizione dettagliata delle funzionalità di ogni ruolo.

## Gli amministratori hanno una gerarchia? Un amministratore può sostituire un altro? {#admin-hierarchy}

No. I team nei Rollout di esperienza hanno una struttura piatta. Tutti i membri con il ruolo **Amministratore** dispongono delle stesse autorizzazioni e possono gestire le rispettive configurazioni. Non esiste un flusso di lavoro di approvazione gerarchico tra gli amministratori.

## Come rimuovere un membro dal team? {#remove-member}

I membri vengono rimossi tramite il sistema di gestione degli accessi. In qualità di amministratore, cerca il record di accesso del membro per il tuo team e revoca il suo ruolo. Se non sai come eseguire questa operazione, contatta il team di gestione degli accessi della tua organizzazione.

## Un membro può avere più ruoli? {#multiple-roles}

Sì. Assegnare più ruoli a un membro quando le responsabilità si estendono su più funzioni. Ad esempio, un membro del team che gestisce il team e crea i flag di funzionalità deve avere entrambi i ruoli **Amministratore** e **Proprietario rilascio prodotto**.

## Vedi anche {#see-also}

* [Ruoli utente](user-roles.md)
* [Aggiungere membri al team](add-team-members.md)
* [Gestire i team](manage-teams.md)
