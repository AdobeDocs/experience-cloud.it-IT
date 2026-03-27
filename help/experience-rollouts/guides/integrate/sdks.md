---
title: SDK
description: Scopri l’architettura di SDK nei Rollout di esperienze Adobe e gli SDK disponibili per Java e Node.js.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 2%

---

# SDK {#sdks}

Experience Rollouts fornisce SDK lato server per l’integrazione del servizio back-end. Questa pagina descrive l’architettura di SDK e le opzioni disponibili.

## Architettura SDK {#architecture}

Tutti gli SDK di Rollout esperienza condividono la stessa architettura di base:

* **Inizializzazione**: SDK è configurato tramite una chiamata `createInstance()` che restituisce un oggetto singleton.
* **Recupero funzionalità**: il metodo `getFeatures()` recupera i dati del flag di funzionalità da SDK.
* **Memorizzazione in cache**: SDK memorizza nella cache le risposte del servizio Rollout esperienza. Cache Manager aggiorna la cache in base a un intervallo di polling configurabile (TTL).
* **Gestione errori** - Se il servizio restituisce un 503, Gestione cache mantiene i dati memorizzati nella cache esistenti e continua a fornire le valutazioni dei flag di funzionalità. Se i dati non sono cambiati dall’ultima chiamata (304), la cache non viene aggiornata.

## Prerequisiti {#prerequisites}

Prima di integrare un SDK, assicurati di disporre dei seguenti elementi:

1. **ID applicazione**: l&#39;ID client di ogni applicazione caricata nella console dei rollout di esperienza.
2. **Token di servizio** - Utilizzato da SDK per chiamare le API Experience Rollouts in background.
3. **Chiave API**: utilizzata insieme al token del servizio per l&#39;autenticazione API.

## SDK disponibili {#available-sdks}

### SDK Java {#java-sdk}

Java SDK viene distribuito tramite Maven. Aggiungi la dipendenza a `pom.xml` del progetto per l&#39;integrazione. Per le applicazioni basate su Spring, la dipendenza Maven imposta automaticamente la cache di SDK prima che l’applicazione venga completamente caricata.

Specifiche chiave per Java SDK:

* **JDK supportato:** JDK 8 e versioni successive
* **Client non memorizzabili in cache:** supportati a partire dalla versione 0.8 di SDK. Per i client non memorizzabili in cache, `getFeature()` effettua una chiamata API in tempo reale invece di leggere dalla cache. SDK continua il polling in background e passa al server basato su cache se il client diventa memorizzabile in cache.

Per istruzioni sull&#39;installazione, consulta la [Guida all&#39;integrazione di Java SDK](../sdk-releases/java/java-sdk-integration-guide.md).

### SDK di Node.js {#nodejs-sdk}

Il SDK di Node.js è distribuito tramite npm.

Per istruzioni sull&#39;installazione, consulta la [Guida all&#39;integrazione di Node.js con SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md).

## Vedi anche {#see-also}

* [Servizi web](web-services.md)
* [Passaggi dell’integrazione](integration-steps.md)
* [Guida all’integrazione di Java SDK](../sdk-releases/java/java-sdk-integration-guide.md)
* [Guida all’integrazione di Node.js con SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
