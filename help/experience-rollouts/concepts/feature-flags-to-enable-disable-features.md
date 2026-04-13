---
title: Flag di funzioni per abilitare e disabilitare le funzioni
description: Scopri in che modo i flag di funzionalità nei Rollout di esperienza consentono di controllare la disponibilità delle funzionalità, gestire le dipendenze e ridurre i rischi di distribuzione.
hide: true
exl-id: 627775e8-9b17-4bc7-9565-07a438ae8ed7
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Flag di funzioni per abilitare e disabilitare le funzioni {#feature-flags}

I flag di funzione consentono di attivare o disattivare le funzioni dell’applicazione in fase di esecuzione senza ridistribuire il codice. Separano inoltre le distribuzioni del codice dalla disponibilità delle funzioni: il nuovo codice può essere distribuito in produzione dietro un flag e attivato solo quando sei pronto.

Questa pratica riduce notevolmente i rischi. Gli sviluppatori possono creare con agilità e affidabilità, mentre i team di prodotto mantengono il controllo sulla tempistica e sul pubblico di ogni versione di funzioni.

## Gestire le dipendenze durante lo sviluppo {#manage-dependencies}

I flag di funzione consentono di gestire le dipendenze durante i test in cicli di sviluppo rapidi. Gli sviluppatori dedicano meno tempo alla risoluzione dei conflitti di unione e al refactoring, oltre a dedicare più tempo alla distribuzione delle funzioni.

Poiché la disponibilità delle funzioni è controllata al di fuori del codice, è possibile sviluppare più funzioni in parallelo, senza ramificazioni complesse. Le singole feature possono essere spostate in avanti o indietro in modo indipendente, senza influire sulle altre feature in corso.

## Distribuzioni scure {#dark-deployments}

Poiché abilita e disabilita le decisioni live al di fuori della base di codice, puoi distribuire il codice in produzione mantenendo la funzione invisibile agli utenti finali. Questa è una **distribuzione scura**.

Le distribuzioni scure consentono di inviare il codice in modo sicuro alla produzione, testarlo nell’ambiente live in condizioni reali e andare &quot;live&quot; quando lo desideri, non quando la pianificazione della distribuzione lo richiede.

## Rollout graduale {#gradual-rollout}

Quando sei pronto per il rilascio, puoi utilizzare un flag di funzione per eseguire un **rollout graduale**: apri la funzione all&#39;1% degli utenti, misura il feedback e le prestazioni, quindi aumenta progressivamente.

Questo approccio continuo ti offre un controllo più stretto sull’esperienza fornita e un ciclo di feedback più rapido con utenti reali, in modo che i team possano rispondere rapidamente prima di una versione completa.

## Interruttore di arresto {#kill-switch}

Se una versione non va come pianificato (feedback sfavorevole, bug o problemi di prestazioni) puoi disattivare immediatamente la funzionalità utilizzando il flag di funzionalità come **kill switch**. Non è necessaria alcuna modifica o ridistribuzione del codice.

## Ciclo di vita flag di funzione {#lifecycle}

Un flag di funzione in Experience Rollout segue questo tipico ciclo di vita:

1. Uno sviluppatore crea un flag di funzione e lo sottopone a test in isolamento, senza esporlo ad altri utenti.
2. Un proprietario del prodotto collega un pubblico al flag, rendendo la funzione visibile a un set definito di utenti esterni.
3. Facoltativamente, il contrassegno viene aggiunto a un [gruppo di caratteristiche](feature-groups-to-control-multiple-features.md) da gestire insieme ai contrassegni correlati.

<!-- -->
