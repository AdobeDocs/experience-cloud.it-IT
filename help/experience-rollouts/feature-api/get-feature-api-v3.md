---
title: API per funzioni GET V3
description: Riferimento API per l’API della funzione Rollout esperienza V3, utilizzata per recuperare i flag di funzione per le applicazioni web e mobili.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 9%

---


# API per funzioni GET V3 {#get-feature-api-v3}

La funzione API V3 è l’endpoint primario per il recupero dei flag di funzione nelle applicazioni web e mobili. Restituisce le funzioni e i rilasci a cui un utente è idoneo, in base alla sua identità e alle regole per il pubblico configurate nella console.

**Endpoint:** `GET {HOST}/fg/api/v3/feature`

Utilizza `https://p13-stage.adobe.io` per staging e `https://p13n.adobe.io` per produzione.

## Richiesta {#request}

### Intestazioni di richiesta {#request-headers}

| Intestazione | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `x-api-key` | Stringa | Chiave API dell&#39;applicazione da Adobe Developer Console. Il provisioning deve essere eseguito separatamente per Stage e Production. | Sì |
| `Authorization` | Stringa | **Non obbligatorio** per scenari non autenticati. Utilizza `Bearer <AccessToken>` per gli utenti autenticati. Utilizza `Bearer <ServiceToken>` per scenari di caching SDK lato server. | No |
| `x-adobe-uuid` | Stringa | Un ID dispositivo o visitatore univoco. Utilizzato per supportare il rollout percentuale per gli utenti non autenticati e per mantenere la coerenza tra le sessioni e le transizioni da non autenticato a autenticato. | No |

### Parametri della query {#query-parameters}

| Parametro | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `clientId` | Stringa | L’ID client dell’applicazione, acquisito nella console dei rollout di esperienza. | Sì |
| `ignore_rf` | Booleano | Se `true`, i flag di rilascio vengono ignorati e vengono restituite tutte le versioni per il client. Impostazione predefinita: `false`. | No |
| `rf` | Stringa | Flag di rilascio. Utilizzato solo quando `ignore_rf` è `false`. | No |
| `meta` | Booleano | Se `true`, i metadati per ogni funzione sono inclusi nella risposta e restituiti come coppia chiave-valore in cui il valore è codificato in Base64. Impostazione predefinita: `false`. | No |
| `userId` | Stringa | Richiede un token di servizio. GUID dell&#39;utente per il quale si desidera recuperare i flag di funzionalità. | No |
| *Parametri di contesto* | N/D | Qualsiasi parametro di query non elencato sopra viene trattato come una variabile di contesto e utilizzato per valutare le regole del pubblico. Passa più valori come `?key1=val1&key2=val2`. Esempio: `?clientLanguage=ja_JP&contractCurrency=JPY`. | No |

## Risposta {#response}

### Codici di stato delle risposte {#response-status}

| Codice di stato | Descrizione |
|---|---|
| `200 OK` | Dati del flag di funzione restituiti nel corpo della risposta. |
| `304 Not Modified` | L&#39;ETag passato dal client corrisponde all&#39;ultimo stato del server. Consideralo come un no-op — nessuna modifica da applicare. |
| `400 Bad Request` | `clientId` non è stato acquisito o la richiesta non è valida. |
| `403 Forbidden` | Chiave API non valida o l’applicazione non è abbonata all’API Experience Rollouts in Adobe Developer Console. |

### Intestazioni di risposta {#response-headers}

| Intestazione | Descrizione |
|---|---|
| `x-request-id` | Identificatore di richiesta univoco per il debug. Includilo in qualsiasi richiesta di supporto. |
| `ETag` | Token che rappresenta lo stato corrente del server per le funzionalità dell&#39;utente. Passa questo valore come `If-None-Match` nelle richieste successive. Se lo stato non è cambiato, l&#39;API restituisce `304`. |
| `x-adobe-fg-poll-interval` | TTL (in secondi) per la cache locale del client. Richiama nuovamente l’API solo dopo la scadenza di questo intervallo. |

### Corpo della risposta {#response-body}

La risposta è un oggetto JSON con i seguenti campi di livello principale:

| Campo | Tipo | Descrizione |
|---|---|---|
| `api_version` | Stringa | Versione API. Campo interno: nessuna elaborazione richiesta. |
| `json_version` | Stringa | Versione schema JSON. Campo interno: nessuna elaborazione richiesta. |
| `ttl` | Intero | Cache TTL in secondi. Stesso valore dell&#39;intestazione di risposta `x-adobe-fg-poll-interval`. Valore predefinito: 300. |
| `caching_enabled` | Booleano | Se `true`, la valutazione delle funzionalità viene eseguita localmente sul client. Se `false`, la valutazione viene eseguita lato server su ogni richiesta. |
| `client_analytics_params` | Oggetto | Configurazione di Analytics per l’applicazione. Consulta i [campi client_analytics_params](#client-analytics-params) di seguito. |
| `releases` | Array | Elenco delle versioni e dei flag di funzioni a cui l’utente è idoneo. Vedi i campi [release](#releases-fields) di seguito. |

#### campi client_analytics_params {#client-analytics-params}

| Campo | Descrizione |
|---|---|
| `app_id` | ID numerico dell’applicazione. |
| `safe_event_required` | `true` se gli eventi di retargeting sono abilitati per questo client. |
| `analytics_required` | Sempre `false` nelle risposte V3. |

#### campi delle versioni {#releases-fields}

| Campo | Descrizione |
|---|---|
| `release_name` | Il nome della versione o del gruppo di funzioni a cui l’utente è idoneo. |
| `bit_index` | Indice dei bit di rilascio. I valori negativi indicano uno stato di rollout completo. |
| `features` | Matrice di chiavi di flag di funzione a cui l’utente è idoneo. Una chiave di funzione viene restituita solo se l’utente è idoneo e il flag è in uno stato abilitato. Questo è il campo principale su cui deve essere basata la logica dell’applicazione. |
| `meta` | Metadati opzionali con codifica Base64 associati alla funzione. Decodificare prima di utilizzare. |
| `release_analytics_params` | Array di oggetti metadati di Analytics per ogni funzione idonea. Consulta i campi [release_analytics_params](#release-analytics-params) di seguito. Negli scenari del gruppo di controllo, `features` è vuoto. |

#### campi release_analytics_params {#release-analytics-params}

| Campo | Tipo | Descrizione |
|---|---|---|
| `app_id` | Intero | ID applicazione. |
| `release_id` | Intero | ID versione. |
| `bit_index` | Intero | Rilascia indice di bit. Obsoleto. |
| `variant_id` | Intero | `0` se l&#39;utente fa parte del gruppo di controllo; diverso da zero in caso contrario. |
| `feature_id` | Intero | ID funzione interno. |
| `f_key` | Stringa | Chiave flag di funzione. |

## Richiesta di esempio e risposta {#sample}

### Richiesta di esempio {#sample-request}

```http
GET /fg/api/v3/feature?clientId=MyWebApp&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Risposta di esempio: utente nel gruppo di test {#sample-response-test}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "analyticsVersion": "2.0",
      "client_analytics_params": {
        "app_id": 1378,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": ["ff1", "ff2", "ff3"],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 10040476,
              "feature_id": 26059,
              "f_key": "ff1",
              "analytics_required": true
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

### Risposta di esempio: utente nel gruppo di controllo {#sample-response-control}

Quando un utente si trova nel gruppo di controllo, l&#39;array `features` è vuoto e `variant_id` è `0`:

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": [],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 0,
              "feature_id": 26059,
              "f_key": "ff1"
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

## Vedi anche {#see-also}

* [API per funzioni GET V2](get-feature-api-v2.md)
* [Applicazioni web](../guides/integrate/web-applications.md)
* [Applicazioni mobili](../guides/integrate/mobile-applications.md)
* [Passaggi dell’integrazione](../guides/integrate/integration-steps.md)
