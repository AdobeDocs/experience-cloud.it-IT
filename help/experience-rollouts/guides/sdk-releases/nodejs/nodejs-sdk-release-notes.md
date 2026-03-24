---
title: Note sulla versione di Node.js SDK
description: Note sulla versione di Experience Rollouts Node.js SDK, incluso un registro delle nuove funzioni, miglioramenti e correzioni di bug per tutte le versioni pubblicate.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---


# Note sulla versione di Node.js SDK {#nodejs-sdk-release-notes}

In questa pagina è elencata la cronologia delle versioni di Experience Rollouts Node.js SDK. Per la configurazione dell&#39;integrazione, consulta [Guida all&#39;integrazione di Node.js con SDK](nodejs-sdk-integration-guide.md).

## Versione 1.0.10 {#v1-0-10}

**Correzioni di bug e miglioramenti al socket**

* È stata corretta l&#39;eccezione `ESOCKETTIMEDOUT` generata durante gli aggiornamenti pianificati della cache. Il parametro `maxSockets` è stato rimosso da `featureRequestHttpParams` e `ingestAnalyticsHttpParams` in `createInstance()`.
* È stato corretto un bug a causa del quale i client memorizzabili in cache venivano erroneamente contrassegnati come non memorizzabili in cache dopo le risposte HTTP 304 (Non modificato).
* Rimosso `isReleaseBitEnabled()` — questo metodo non è più supportato.
* È stato migliorato l’output di registrazione per una diagnostica migliore.
* Le cartelle di test e di code coverage non sono più incluse nel pacchetto npm pubblicato.

## Versione 1.0.5 {#v1-0-5}

**Miglioramenti stabilità**

Correzioni generali per la gestione dell’aggiornamento della cache e casi edge di inizializzazione SDK.

## Versione 1.0.3 {#v1-0-3}

**Versione stabile iniziale**

Prima versione di produzione del SDK Node.js che supporta il recupero di flag di funzione autenticati, anonimi e di rollout completo predefiniti.

## Vedi anche {#see-also}

* [Guida all’integrazione di Node.js con SDK](nodejs-sdk-integration-guide.md)
* [Note sulla versione di Java SDK](../../sdk-releases/java/java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
