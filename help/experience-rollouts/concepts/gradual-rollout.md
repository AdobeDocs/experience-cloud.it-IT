---
title: Rollout graduale
description: Scopri in che modo i rollout graduali nei Rollout di esperienza consentono di inserire gradualmente la distribuzione delle funzioni in produzione in modo sicuro, con feedback in tempo reale e rischi minimi.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 2%

---


# Rollout graduale {#gradual-rollout}

Il rollout graduale di una nuova funzione viene introdotto in produzione in modo incrementale, anziché essere abilitato per tutti gli utenti contemporaneamente. Questo approccio riduce i rischi, aiuta a gestire il carico di back-end e crea un ciclo di feedback stretto prima del rilascio completo.

## Vantaggi {#benefits}

**Rete di sicurezza**
Rilasciando prima il materiale a un pubblico ridotto, puoi tenere traccia del feedback e monitorare il comportamento in produzione prima di espanderlo. In caso di problemi, l’impatto è limitato e la funzione può essere disattivata immediatamente, senza che venga apportata una modifica al codice o una ridistribuzione.

**Gestione del carico di back-end**
L’apertura di una funzione a tutti gli utenti simultaneamente può causare picchi improvvisi nel caricamento del server. Un rollout graduale distribuisce l’aumento del traffico nel tempo, consentendo una scalabilità fluida dell’infrastruttura.

**Feedback in tempo reale**
Ogni fase del rollout fa emergere feedback da parte di utenti reali. I team possono agire in base a tale feedback, perfezionando l’esperienza, risolvendo i casi limite o regolando i messaggi, prima della fase successiva.

## Come funziona {#how-it-works}

I Rollout di esperienza forniscono regole di targeting granulari per aumentare gradualmente l’esposizione degli utenti. Un rollout graduale tipico potrebbe seguire questo pattern:

1. Abilita la funzionalità per **1%** di utenti
2. Monitorare il feedback e le metriche delle prestazioni
3. Espandi a **10%**, quindi **25%** e infine **50%**
4. Raggiungi **100%** una volta stabilita l&#39;affidabilità

Ad ogni passaggio, una singola azione può mettere in pausa il rollout o disattivare completamente la funzione se si verifica un errore.

## Vedi anche {#see-also}

* [Flag di funzioni per abilitare e disabilitare le funzioni](feature-flags-to-enable-disable-features.md)
* [Gestione del rilascio](release-management.md)
