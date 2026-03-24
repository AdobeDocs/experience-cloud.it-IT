---
title: Ruoli utente
description: Scopri i cinque ruoli utente disponibili nei Rollout esperienza di Adobe e come scegliere il ruolo giusto per ogni membro del team.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---


# Ruoli utente {#user-roles}

I Rollout esperienza forniscono cinque ruoli. Ogni ruolo è progettato per un insieme specifico di responsabilità. Per impostazione predefinita, i ruoli si escludono a vicenda: un membro con il ruolo Amministratore non dispone automaticamente delle autorizzazioni di Proprietario del rilascio del prodotto. Assegnare più ruoli a un membro quando è necessario un accesso più ampio.

## Ruoli disponibili {#roles}

| Ruolo | Responsabilità |
|---|---|
| **Amministrazione** | Esegue l&#39;onboarding delle applicazioni nella console, gestisce i membri del team e approva o rifiuta le richieste di accesso. Obbligatorio prima che il team possa iniziare a utilizzare i flag di funzionalità. |
| **Proprietario versione prodotto** | Crea e aggiorna i flag di funzione e i gruppi di funzioni per la relativa applicazione. Puoi collegare i tipi di pubblico ai flag di funzione per rendere le funzioni disponibili agli utenti esterni. |
| **Sviluppatore** | Funziona in un contesto in modalità sandbox per testare le funzionalità dietro i flag di funzionalità senza influire sugli altri utenti. Può esporre un flag di funzione a un pubblico privato (ad esempio un ID utente o un indirizzo e-mail specifico) in Stage o Production. |
| **Amministratore funzionalità** | Crea e gestisce gruppi di funzioni cross-team. Utilizza questo ruolo per coordinare i flag tra le applicazioni di proprietà di team diversi. |
| **Release Manager** | Gestisce le versioni con più team e applicazioni e aggiorna le regole del pubblico che definiscono chi riceve una versione. |

## Scelta del ruolo giusto {#choosing}

Per assegnare i ruoli, attenersi alle istruzioni riportate di seguito.

* **Aggiunta o aggiornamento dei flag di funzionalità per l&#39;applicazione** → **Proprietario versione prodotto**
* **Verifica delle funzionalità privatamente senza influire sugli altri** → **Sviluppatore**
* **Gestione dei gruppi di caratteristiche per più team** → **Amministrazione funzionalità**
* **Gestione delle versioni in più team e applicazioni** → **Release Manager**
* **Onboarding di applicazioni e gestione dell&#39;appartenenza al team** → **Amministratore**

>[!NOTE]
>
>Un membro può avere più ruoli. Ad esempio, un ingegnere che esegue il test delle funzionalità e gestisce le applicazioni del team deve avere entrambi i ruoli **Sviluppatore** e **Amministratore**.

## Errore di autorizzazione {#permissions-error}

Se un membro riscontra un errore di tipo &quot;autorizzazioni insufficienti&quot; durante il tentativo di aggiornare una funzionalità o un gruppo, è necessario il ruolo **Proprietario rilascio prodotto**. Per aggiungere questo ruolo, contatta l’amministratore del team.

## Vedi anche {#see-also}

* [Aggiungere membri al team](add-team-members.md)
* [Gestire i team](manage-teams.md)
