---
title: Gestione del rilascio nei rollout di esperienza
description: Scopri come la gestione delle versioni in Rollout esperienza coordina la distribuzione di funzioni per più team tramite implementazioni in modalità scura, test di produzione e rollout graduali.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---


# Gestione del rilascio nei rollout di esperienza {#release-management}

Una versione principale tipica coinvolge più team e più applicazioni, ciascuno con le proprie tempistiche di distribuzione e dipendenze. Experience Rollouts fornisce un modello di gestione delle versioni che consente ai team di lavorare in modo indipendente, distribuendo al contempo una versione coordinata e controllata agli utenti finali.

## Funzionalità principali {#capabilities}

### Distribuzioni scure {#dark-deployments}

I team non dovranno più pianificare l’implementazione del codice con una data di pubblicazione specifica. Il codice può essere distribuito in produzione dietro i flag di funzione in qualsiasi momento. Gli utenti finali non vedranno alcuna modifica finché la versione non verrà attivata. I team possono eseguire l’implementazione al proprio ritmo, con la certezza che nulla viene esposto prematuramente.

### Test in produzione {#testing-in-production}

Una volta implementato il codice in produzione, ovvero implementato in modalità scura, i rollout di esperienza possono aprire le funzioni ai tester interni e ai team di controllo qualità. Questo consente di eseguire test completi rispetto all’ambiente di produzione e ai dati di produzione reali, senza alcun rischio di esposizione delle modifiche agli utenti finali.

### Rollout graduale {#gradual-rollout}

Quando una versione è pronta per essere pubblicata, non deve essere &quot;tutto o niente&quot;. I rollout di esperienza consentono di controllare il rollout progressivamente, a partire da una piccola percentuale di utenti, monitorare il feedback e le prestazioni ed espandere il pubblico nel tempo. In questo modo si riduce la pressione sui sistemi back-end e si lascia ai team il tempo di rispondere a qualsiasi problema prima di un&#39;esposizione completa.

### Attivazione coordinata {#coordinated-activation}

Più team sviluppano le funzioni in modo indipendente, ciascuno dietro i propri flag di funzione. Una volta che tutti i team sono pronti, Experience Rollout fornisce un singolo punto di controllo per attivare tutti i flag tra i team e le applicazioni simultaneamente, o gradualmente, in modo che la versione venga pubblicata come un’unica esperienza coesa.

## Vedi anche {#see-also}

* [Concetto di gestione del rilascio](concept-of-release-management.md)
* [Gruppi di feature per controllare più feature](feature-groups-to-control-multiple-features.md)
* [Rollout graduale](gradual-rollout.md)
