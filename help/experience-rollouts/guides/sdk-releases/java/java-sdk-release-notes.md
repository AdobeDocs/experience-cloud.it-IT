---
title: Note sulla versione di Java SDK
description: Note sulla versione di Java SDK per i rollout di esperienza, incluso un registro delle modifiche con nuove funzioni, miglioramenti e correzioni di bug per tutte le versioni pubblicate.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 2%

---


# Note sulla versione di Java SDK {#java-sdk-release-notes}

In questa pagina è elencata la cronologia delle versioni di Experience Rollouts Java SDK. Per la configurazione dell&#39;integrazione, vedere [Guida all&#39;integrazione di Java SDK](java-sdk-integration-guide.md).

## Versione 4.0.6 {#v4-0-6}

**Dati del gruppo di controllo nelle risposte**

Nella risposta di SDK è ora possibile recuperare i dati dei gruppi di controllo e delle varianti, in modo che corrispondano al comportamento delle API delle funzioni REST. Per abilitare questa funzione, aggiungi `.includeControlGroup()` al generatore `FloodgateConfiguration`.

## Versione 4.0.5 {#v4-0-5}

**Miglioramenti di stabilità e prestazioni**

Minori miglioramenti interni all&#39;affidabilità dell&#39;aggiornamento della cache e alla gestione delle connessioni.

## Versione 4.0.4 {#v4-0-4}

**Miglioramenti dei criteri per i tentativi**

È stato migliorato il comportamento predefinito dei nuovi tentativi in caso di errori di servizio transitori.

## Versione 4.0.3 {#v4-0-3}

**Correzioni di bug**

Correzioni generali di stabilità per casi edge nell’inizializzazione asincrona.

## Versione 4.0.1 (Beta) {#v4-0-1-beta}

**Versione Beta di SDK 4.x**

Sono stati introdotti il supporto client DX, la configurazione dell’area geografica DX e il supporto AEP (sandbox).

## Versione 3.1.0 {#v3-1-0}

**Supporto streaming per client DX**

È stata aggiunta la funzionalità di streaming basata su SSE per notificare ai clienti SDK gli aggiornamenti dei flag in tempo reale.

## Versione 3.0.x {#v3-0-x}

**È stato introdotto il requisito Java 11**

A partire dalla versione 3.0.0, SDK richiede JDK 11 o versione successiva. Le versioni principali precedenti supportano JDK 8+.

È stato introdotto il supporto pubblico per riferimento per i client DX, che consente di fare riferimento tramite ID alle definizioni di pubblico riutilizzabili nelle entità funzionali.

## Versione 2.x {#v2-x}

**Supporto client non memorizzabile in cache (da 0.8)**

I client non memorizzabili in cache possono chiamare `getFeature()` in tempo reale invece di leggere dalla cache di SDK. SDK continua il polling in background e passa al server basato su cache quando il client diventa memorizzabile in cache.

Ulteriori miglioramenti alla versione 2.x includono nuove opzioni del generatore (`alwaysCache()`, `neverCache()`, supporto client HTTP personalizzato e supporto dell&#39;esecutore), il filtro delle funzioni e delle chiavi di rilascio e il recupero di utenti impersonati.

## Versione 1.x {#v1-x}

Serie della versione iniziale. JDK 8+ supportato, integrazione delle dipendenze Maven e recupero di base dei flag di funzione autenticati e anonimi.

## Vedi anche {#see-also}

* [Guida all’integrazione di Java SDK](java-sdk-integration-guide.md)
* [Note sulla versione di Node.js SDK](../../sdk-releases/nodejs/nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
