---
title: Concetto di gestione del rilascio
description: Scopri come la gestione delle versioni in Rollout esperienza aiuta a coordinare rollout di funzioni ampi e tra team attraverso il flag di funzioni.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Concetto di gestione del rilascio {#concept-of-release-management}

Le versioni di grandi dimensioni condividono alcune problematiche comuni: il coinvolgimento di più team, le pianificazioni in conflitto e le dipendenze sono difficili da coordinare. La gestione dei rilasci affronta queste problematiche fornendo un modo strutturato per implementare le modifiche in modo fluido.

## Che cosa significa Release Management {#what-it-means}

La gestione delle versioni copre il coordinamento di una versione end-to-end, dal momento in cui i team iniziano a sviluppare dietro i flag di funzionalità al momento in cui la funzione è completamente disponibile per tutti gli utenti.

Consente ai team di:

* Distribuzione indipendente alla produzione, al proprio ritmo, senza rivelare funzionalità agli utenti finali
* Vai in diretta solo quando tutti i team partecipanti sono pronti
* Esegui gradualmente il rollout della versione a un sottoinsieme di utenti prima della disponibilità completa

## Funzionamento in Rollout esperienza {#how-it-works}

La gestione del rilascio in Experience Rollouts si basa sul concetto di [segnalazione di funzioni](what-is-a-feature-flag.md). Ogni team distribuisce il proprio codice in produzione dietro un flag di funzione. Una versione è quindi una **raccolta di flag di funzionalità definiti in più applicazioni e team**.

Quando tutti i team sono pronti, la versione può essere attivata in un’unica operazione, o implementata gradualmente, senza che sia necessario ridistribuire o coordinare i tempi di distribuzione dei singoli team.

Questo approccio fornisce:

* **Distribuzione indipendente**: i team eseguono la distribuzione in base alla propria pianificazione senza influire su altri team o utenti finali.
* **Attivazione coordinata** - Tutti i flag di una versione vengono attivati insieme quando la versione diventa attiva.
* **Rollout graduale**: la versione può essere aperta progressivamente a percentuali crescenti di utenti.

Per informazioni dettagliate sulla configurazione delle versioni in Experience Rollouts, consulta [Gestione delle versioni](release-management.md).
