---
title: API per funzioni GET V2
description: Riferimento API per l'API della funzione Rollout esperienza V2, utilizzata per recuperare i flag di funzione per le applicazioni desktop.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 11%

---


# API per funzioni GET V2 {#get-feature-api-v2}

La funzione API V2 è progettata per l’integrazione con le applicazioni desktop. Recupera i flag di funzione e i dati sulla versione per l’utente autenticato, supportando il codice prodotto e la versione del prodotto come identificatore dell’applicazione oltre a un ID client standard.

**Endpoint:** `GET {HOST}/fg/api/v2/feature`

Utilizza `https://p13-stage.adobe.io` per staging e `https://p13n.adobe.io` per produzione.

## Richiesta {#request}

### Intestazioni di richiesta {#request-headers}

| Intestazione | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `x-api-key` | Stringa | Chiave API dell&#39;applicazione da Adobe Developer Console. Il provisioning deve essere eseguito separatamente per Stage e Production. | Sì |
| `Authorization` | Stringa | `Bearer <AccessToken>` o `Bearer <ServiceToken>`. | Sì |
| `x-adobe-uuid` | Stringa | Un ID dispositivo o visitatore univoco. Utilizzato per il rollout percentuale in scenari non autenticati e per mantenere la fedeltà della sessione. | No |

### Parametri della query {#query-parameters}

| Parametro | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `clientId` | Stringa | L’ID client dell’applicazione, come integrato nella console dei rollout di esperienza. È possibile trasmettere più valori: `clientId=C1&clientId=C2`. | No |
| `p` | Stringa | Product, version, platform, locale string (formato PVPL). Esempio: `PHSP:17.0:WIN:en_US`. È possibile trasmettere più valori: `p=PHSP:17.0:WIN:en_US&p=PPRO:8:WIN:en_US`. Nella valutazione vengono utilizzati solo il codice prodotto e la versione del prodotto. | No |
| `meta` | Booleano | Se `true`, per ogni funzionalità vengono restituiti metadati con codifica Base64. Impostazione predefinita: `false`. | No |
| *Parametri di contesto* | N/D | Qualsiasi coppia chiave-valore aggiuntiva viene trattata come una variabile di contesto per la valutazione delle regole del pubblico. Esempio: `clientLanguage=ja_JP&contractCurrency=JPY`. | No |

>[!NOTE]
>
>È necessario almeno uno di `clientId` o `p` per identificare l&#39;applicazione.

## Risposta {#response}

### Codici di stato delle risposte {#response-status}

| Codice di stato | Descrizione |
|---|---|
| `200 OK` | Dati del flag di funzione restituiti nel corpo della risposta. |
| `304 Not Modified` | ETag corrisponde allo stato corrente del server. Considera come un no-op — nessuna modifica da applicare. |
| `401 Unauthorized` | Token di autorizzazione non valido. |

### Intestazioni di risposta {#response-headers}

| Intestazione | Descrizione |
|---|---|
| `x-request-id` | Identificatore di richiesta univoco per il debug. Includilo in qualsiasi richiesta di supporto. |
| `ETag` | Token che rappresenta lo stato corrente della funzione per l’utente. Passa come `If-None-Match` nelle richieste successive. Restituisce `304` se non viene modificato. |
| `x-adobe-fg-poll-interval` | TTL in secondi per la cache locale del client. Richiama nuovamente l’API solo dopo la scadenza di questo intervallo. |

### Corpo della risposta {#response-body}

La risposta è un oggetto JSON con i seguenti campi di livello principale:

| Campo | Tipo | Descrizione |
|---|---|---|
| `api_version` | Stringa | Versione API. Campo interno: nessuna elaborazione richiesta. |
| `json_version` | Stringa | Versione schema JSON. Campo interno: nessuna elaborazione richiesta. |
| `ttl` | Intero | Cache TTL in secondi. Valore predefinito: 300. |
| `clients` | Oggetto | Mappa degli ID client (o stringhe PVPL) ai dati della loro versione. Ogni chiave contiene i campi descritti di seguito. |

#### Campi di risposta per client {#per-client-fields}

| Campo | Descrizione |
|---|---|
| `releases` | Array di versioni a cui l’utente è idoneo. Vedi i campi [release](#releases-fields) di seguito. |
| `client_analytics_params` | Oggetto di configurazione di Analytics. Consulta i [campi client_analytics_params](#analytics-fields) di seguito. |

#### campi delle versioni {#releases-fields}

| Campo | Descrizione |
|---|---|
| `release_name` | Nome della versione o del gruppo di funzioni. |
| `bit_index` | Rilascia indice di bit. Obsoleto. Può essere `null` o negativo a seconda dello stato di rilascio. |
| `features` | Matrice di chiavi di flag di funzione a cui l’utente è idoneo. Una chiave di funzione viene visualizzata solo se l’utente è idoneo e il flag è abilitato. |
| `meta` | Metadati con codifica Base64 opzionali. Decodificare prima di utilizzare. |
| `release_analytics_params` | Metadati di Analytics per le funzioni idonee. Negli scenari del gruppo di controllo, `features` è vuoto. |

#### campi release_analytics_params {#release-analytics-params}

| Campo | Tipo | Descrizione |
|---|---|---|
| `app_id` | Intero | ID applicazione. |
| `release_id` | Intero | ID versione. |
| `bit_index` | Intero | Obsoleto. |
| `variant_id` | Intero | `0` se Gruppo di controllo; diverso da zero in caso contrario. |
| `feature_id` | Intero | ID funzione interno. |
| `f_key` | Stringa | Chiave flag di funzione. |

#### campi client_analytics_params {#analytics-fields}

| Campo | Tipo | Descrizione |
|---|---|---|
| `app_id` | Intero | ID applicazione. |
| `safe_event_required` | Booleano | `true` se gli eventi di retargeting sono abilitati. |
| `analytics_required` | Booleano | `false` se l&#39;analisi è disabilitata o nel flusso predefinito; `true` se il flusso Kinesis è abilitato. |

## Richiesta di esempio e risposta {#sample}

### Richiesta di esempio {#sample-request}

```http
GET /fg/api/v2/feature?clientId=MyDesktopApp&p=PHSP:17.0:WIN:en_US&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Risposta di esempio {#sample-response}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "PHSP:17.0:WIN:en_US": {
      "analyticsVersion": "1.0",
      "releases": []
    },
    "MyDesktopApp": {
      "analyticsVersion": "1.0",
      "client_analytics_params": {
        "app_id": 388,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": 160,
          "release_name": "||features||",
          "features": ["feature_a", "feature_b"],
          "release_analytics_params": [
            {
              "app_id": 388,
              "release_id": -1,
              "bit_index": 160,
              "variant_id": 10031741,
              "feature_id": 2918,
              "f_key": "feature_a"
            }
          ],
          "meta": []
        }
      ]
    }
  },
  "ttl": 300
}
```

## Vedi anche {#see-also}

* [API per funzioni GET V3](get-feature-api-v3.md)
* [Applicazioni desktop](../guides/integrate/desktop-applications.md)
* [Passaggi dell’integrazione](../guides/integrate/integration-steps.md)
