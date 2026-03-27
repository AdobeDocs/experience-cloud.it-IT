---
title: Guida all’integrazione di Node.js con SDK
description: Scopri come integrare Experience Rollouts Node.js SDK nel servizio back-end per recuperare e valutare i flag di funzioni.
exl-id: 063829fe-6933-45ff-add4-285ca7391778
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---

# Guida all’integrazione di Node.js con SDK {#nodejs-sdk-integration-guide}

Il SDK Node.js di Experience Rollouts è una libreria lato server destinata ai servizi Node.js. Memorizza nella cache i dati dei flag di funzione localmente e valuta i flag senza una chiamata API sincrona a ogni richiesta.

>[!NOTE]
>
>Il SDK di Node.js è progettato solo per l’utilizzo lato server. Per le applicazioni web lato client, utilizza il web SDK. La documentazione di Web SDK è in fase di preparazione e sarà presto disponibile.

## Prerequisiti {#prerequisites}

Prima di integrare Node.js SDK, assicurati di disporre di:

* Un’applicazione lato server Node.js
* Chiave **API** e token **servizio** ottenuti tramite Adobe Developer Console. Per inserire nell&#39;elenco Consentiti l&#39;ID client, contatta il supporto dei rollout di esperienza
* Gli **ID client dell&#39;applicazione** registrati nella console dei rollout di esperienza - vedi [Eseguire l&#39;onboarding dell&#39;applicazione](../../applications/onboard-your-application.md)

## Installare SDK {#install}

Aggiungi il SDK al `package.json` del tuo progetto:

```json
"@floodgate/fg-client-sdk": "~1.0.10"
```

Quindi richiedilo nel codice:

```javascript
const { floodgateClient } = require('@floodgate/fg-client-sdk');
```

## Inizializzare SDK {#initialize}

Chiamare `createInstance()` una volta all&#39;avvio dell&#39;applicazione:

```javascript
floodgateClient.createInstance(
  {
    adobeIoApiKey: "<YOUR_API_KEY>",
    clientIds: ["<CLIENT_ID_1>", "<CLIENT_ID_2>"],
    env: "PRD",    // Use "STG" for Stage
    featureRequestHttpParams: {
      timeout: 60 * 1000  // Optional: request timeout in ms
    },
    ingestAnalyticsHttpParams: {
      timeout: 5 * 1000   // Optional: analytics timeout in ms
    }
  },
  function(cb) {
    // Fetch a fresh service token from IMS and pass it in the callback
    cb(null, SERVICE_TOKEN);
  },
  function() {
    return true;  // Return false to disable analytics
  },
  function(response) {
    // Called when the SDK initializes successfully
    console.log("SDK initialized");
  },
  function(err) {
    // Called if initialization fails
    console.error("SDK init error:", err);
  }
);
```

## Recuperare i flag di funzione {#retrieve-features}

I flag di funzionalità vengono restituiti in modo asincrono in un callback. Scegli il metodo appropriato in base al contesto dell’utente.

### Utente autenticato {#authenticated-user}

```javascript
floodgateClient.getFeatures(
  {
    userAccessToken: "<USER_ACCESS_TOKEN>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: true
  },
  function(err, features) {
    if (err) {
      // Handle error and serve default experience
      return;
    }
    const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");
    // Serve experience based on isEnabled
  }
);
```

### Utente anonimo {#anonymous-user}

Se non è disponibile alcun token di accesso utente, utilizza un flag di versione o ometti il token per ricevere le versioni di rollout completo:

```javascript
floodgateClient.getFeatures(
  {
    releaseFlag: "<RELEASE_FLAG>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: false
  },
  callback
);
```

### Versioni predefinite di rollout completo {#default-releases}

Se non viene fornito né un token di accesso né un flag di versione, SDK restituisce le funzionalità in **Rollout completo** o stato **Previsione**:

```javascript
floodgateClient.getFeatures(
  {
    clientId1: "<CLIENT_ID>",
    visitorId: "<VISITOR_ID>",
    meta: false
  },
  callback
);
```

## Controlla se una funzione è abilitata {#check-feature}

```javascript
const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

## Abilita registrazione debug {#debug-logging}

Per abilitare i registri dettagliati di SDK, passare un&#39;istanza del logger a livello di debug quando si chiama `createInstance()`:

```javascript
const bunyan = require('bunyan');
const logger = bunyan.createLogger({ name: "fg", sourceType: "SDK", level: "debug" });

floodgateClient.createInstance(
  { ..., log: logger },
  ...
);
```

## Vedi anche {#see-also}

* [Note sulla versione di Node.js SDK](nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [Passaggi dell’integrazione](../../integrate/integration-steps.md)
