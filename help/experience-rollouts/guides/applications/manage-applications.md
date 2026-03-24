---
title: Gestire le applicazioni
description: Scopri come gestire le applicazioni nei Rollout di esperienza di Adobe, aggiungendo nuove applicazioni e comprendendo la proprietà del team.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---


# Gestire le applicazioni {#manage-applications}

Una **applicazione** in Experience Rollouts rappresenta il servizio o il prodotto che si desidera controllare con i flag di funzionalità. Prima che il team possa creare flag di funzionalità, devi integrare almeno un&#39;applicazione nella console.

## Chi può gestire le applicazioni {#permissions}

Solo i membri con il ruolo **Amministratore** possono aggiungere o modificare applicazioni. Se non disponi di questo ruolo, contatta l’amministratore del team.

## Aggiunta di un’applicazione {#add-application}

Per aggiungere un&#39;applicazione al tuo team, consulta [Eseguire l&#39;onboarding dell&#39;applicazione](onboard-your-application.md) per istruzioni dettagliate.

## Proprietà team {#team-ownership}

Ogni applicazione appartiene esattamente a un team. Solo i membri del team possono gestire i flag di funzionalità dell&#39;applicazione.

Questo modello di proprietà influisce anche sulla struttura dei gruppi di feature:

* **All&#39;interno del team**: un proprietario del rilascio di un prodotto può raggruppare i flag di funzionalità tra le applicazioni appartenenti allo stesso team. Consulta [Gruppi di funzionalità per controllare più funzionalità](../../concepts/feature-groups-to-control-multiple-features.md).
* **Tra team**: se è necessario raggruppare i flag di funzionalità di applicazioni di proprietà di team diversi, utilizzare un gruppo di funzionalità tra team che richiede il ruolo di **Amministratore funzionalità**.

## Vedi anche {#see-also}

* [Eseguire l’onboarding dell’applicazione](onboard-your-application.md)
* [Gruppi di feature per controllare più feature](../../concepts/feature-groups-to-control-multiple-features.md)
* [Ruoli utente](../teams/user-roles.md)
