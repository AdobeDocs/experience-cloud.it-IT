---
title: Guida all’integrazione di Java SDK
description: Scopri come integrare Experience Rollouts Java SDK nel servizio back-end per recuperare e valutare i flag di funzione.
exl-id: 7c12bd6c-1883-4f1c-985f-a2b0432e61ce
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# Guida all’integrazione di Java SDK {#java-sdk-integration-guide}

Java SDK per i rollout dell’esperienza è una libreria lato server che memorizza nella cache i dati dei flag di funzione localmente e valuta i flag senza una chiamata API sincrona a ogni richiesta. Questa guida descrive l’attuale SDK (4.x).

## Prerequisiti {#prerequisites}

Prima di integrare Java SDK, assicurati di disporre di:

* JDK 11 o versione successiva (richiesto dalla versione di SDK 3.0.0 in poi; le versioni precedenti supportano JDK 8+)
* Un sistema di build basato su Maven
* Un ID client di **chiave API** e **token servizio** dal progetto Adobe Developer Console. Per inserire nell&#39;elenco Consentiti l&#39;ID client, contatta il supporto dei rollout di esperienza
* Gli **ID client dell&#39;applicazione** registrati nella console dei rollout di esperienza - vedi [Eseguire l&#39;onboarding dell&#39;applicazione](../../applications/onboard-your-application.md)

## Aggiungere la dipendenza Maven {#maven-dependency}

Aggiungi Java SDK per i rollout di esperienza a `pom.xml` del tuo progetto:

```xml
<dependency>
  <groupId>com.adobe.cloudtech</groupId>
  <artifactId>fg-client-sdk</artifactId>
  <version>4.0.6</version>
</dependency>
```

## Inizializzare SDK {#initialize}

SDK viene inizializzato una volta all&#39;avvio dell&#39;applicazione utilizzando `FloodgateClient.createInstance()`. Il metodo accetta un oggetto `FloodgateConfiguration` generato con il generatore di configurazione.

### Implementare il callback del token di servizio {#service-token-callback}

SDK utilizza un’interfaccia di callback per recuperare un nuovo token di servizio in fase di esecuzione:

```java
private class FgConfigCallBack implements FGConfigBaseCallBack {

  @Override
  public String getIMSServiceToken() {
    // Fetch and return a valid service token
  }

  @Override
  public boolean isAnalyticsEnabled() {
    return false; // Set to true to enable analytics
  }
}
```

### Creare l’oggetto di configurazione {#configuration}

Utilizza il generatore di configurazione per configurare SDK:

```java
FloodgateConfiguration configuration = FloodgateConfiguration.FloodgateConfigurationBuilder
    .aFloodgateConfiguration(
        FgEnv.PRD,                   // Use FgEnv.STG for Stage
        "<YOUR_API_KEY>",
        Set.of("<CLIENT_ID_1>", "<CLIENT_ID_2>"),
        new FgConfigCallBack(),
        CallType.ASYNC
    )
    .withRetryPolicy(retryPolicy)    // Optional: defaults to 5 retries, 10s interval
    .build();
```

Utilizzare `FgEnv.STG` per l&#39;ambiente di staging e `FgEnv.PRD` per la produzione.

### Creare l’istanza client {#client-instance}

```java
FloodgateClient fgClient = FloodgateClient.createInstance(configuration);
```

## Recuperare i flag di funzione {#retrieve-features}

### Utente autenticato {#authenticated-user}

Utilizza un token di accesso IMS per recuperare i flag di funzione per l’utente corrente:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<USER_ACCESS_TOKEN>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Utente anonimo {#anonymous-user}

Per gli utenti non autenticati, passa un ID visitatore e il token di servizio:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withServiceToken("<SERVICE_TOKEN>")
    .withVisitorId("<VISITOR_ID>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Recuperare un flag di funzione o una versione specifica {#specific-feature}

Per recuperare un singolo flag di funzione per chiave:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<ACCESS_TOKEN>")
    .withFeatureKey("<FEATURE_KEY>")
    .build();
```

Per recuperare tramite la chiave di rilascio, sostituire `.withFeatureKey()` con `.withReleaseKey()`.

## Controlla se una funzione è abilitata {#check-feature}

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

Per i controlli basati sulle versioni:

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_RELEASE", "MY_FEATURE_FLAG");
```

## Gestione della cache {#cache-management}

SDK memorizza nella cache i dati dei flag di funzione e li aggiorna in base all’intervallo di polling impostato per applicazione nella console. Per attivare un aggiornamento della cache su richiesta:

```java
fgClient.refreshClientCache("<CLIENT_ID>");
```

### Client non memorizzabili in cache {#non-cacheable}

Per i client non memorizzabili in cache, `getFeature()` effettua ogni volta una chiamata API live. SDK continua il polling in background e passa al server basato su cache quando il client diventa memorizzabile in cache. Supportato dalla versione 0.8 di SDK in poi.

## Opzioni di configurazione {#configuration-options}

Nel generatore sono disponibili i seguenti metodi di configurazione facoltativi:

| Opzione | Metodo | Descrizione |
|---|---|---|
| Usa sempre cache | `.alwaysCache()` | Ignora la risposta di caching dall’API; da utilizzare per i flag senza regole di pubblico |
| Disattiva caching | `.neverCache()` | Disabilita la memorizzazione nella cache predefinita; utile per la logica di aggiornamento della cache personalizzata |
| Client HTTP personalizzato | `.withHttpClient(client)` | Usa il tuo client HTTP |
| Esecutore personalizzato | `.withScheduledExecutorService(executor)` | Utilizza il tuo esecutore pianificato per il polling in background |
| Includi gruppo di controllo | `.includeControlGroup()` | Restituisce i dati del gruppo di controllo nella risposta della funzione |

## Gestire gli errori {#error-handling}

Effettua il wrapping di `getFeatures()` chiamate per rilevare le eccezioni SDK:

```java
try {
  features = fgClient.getFeatures(request);
} catch (FgClientException e) {
  int statusCode = e.getStatusCode();
  // Handle error and serve default experience
} catch (FgInitException e) {
  e.printStackTrace();
}
```

## Vedi anche {#see-also}

* [Note sulla versione di Java SDK](java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [Passaggi dell’integrazione](../../integrate/integration-steps.md)
