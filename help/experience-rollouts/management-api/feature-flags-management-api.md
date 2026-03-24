---
title: API di gestione dei flag di funzione
description: Riferimento API per l'API di gestione dei flag di funzione dei rollout di esperienza, inclusi gli endpoint per ottenere, creare, aggiornare ed eliminare i flag di funzione per un'applicazione.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 12%

---


# API di gestione dei flag di funzione {#feature-flags-management-api}

L’API di gestione dei flag di funzione consente di creare, leggere, aggiornare ed eliminare in modo programmatico i flag di funzione per le applicazioni in Rollout esperienza.

**Percorso base:** `/m/api/v1/mgmt/feature`

Tutte le richieste richiedono le intestazioni descritte nei [requisiti comuni](feature-management-apis-overview.md#common-requirements).

## Ottieni tutti i flag di funzionalità {#get-all-features}

Recupera tutti i flag di funzionalità per un&#39;applicazione specificata.

| | |
|---|---|
| **Endpoint** | `GET /m/api/v1/mgmt/feature` |
| **Metodo** | GET |

### Parametri della query {#get-all-query-params}

| Parametro | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `clientId` | Intero | ID numerico dell’applicazione. Vedi [Ottieni ID client](get-client-id.md). Obbligatorio se `imsClientId` non viene fornito. | Condizionale |
| `imsClientId` | Stringa | ID client dell’applicazione in formato stringa. Obbligatorio se `clientId` non viene fornito. | Condizionale |
| `nonReleaseFeature` | Booleano | Impostare su `true` per includere flag di funzionalità indipendenti non associati ad alcun gruppo o versione. Richiesto per flussi di lavoro basati su API. | Sì |

### Risposta {#get-all-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta contiene un elenco di oggetti flag di feature. |

Il corpo della risposta contiene un array `features`. Ogni elemento è un oggetto flag di funzionalità con i campi descritti nel riferimento all&#39;oggetto [FeatureDTO](#featuredto-object).

**Risposta di esempio:**

```json
{
  "features": [
    {
      "id": 22079,
      "name": "new.FF.1",
      "clientId": 1191,
      "state": "enabled",
      "description": "first feature flag",
      "release": { "id": 2631, "name": "FF.group", "status": "SAVED" },
      "audience": null,
      "params": { "label": "new FF 1", "rolloutType": "manual" }
    },
    {
      "id": 22080,
      "name": "new.FF.2",
      "clientId": 1191,
      "state": "enabled",
      "description": "second feature flag",
      "audience": [
        {
          "id": 10034665,
          "criteria": { "and": [{ "operator": "EQ", "attr": "LOCALE", "val": "EN" }] }
        }
      ]
    }
  ]
}
```

## Ottieni flag di funzione per ID {#get-feature-by-id}

Recupera un singolo flag di funzione dal relativo ID numerico.

| | |
|---|---|
| **Endpoint** | `GET /m/api/v1/mgmt/feature/{featureId}` |
| **Metodo** | GET |

### Risposta {#get-by-id-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è un singolo oggetto [FeatureDTO](#featuredto-object). |
| `400` | ID funzione non valido. |

## Crea flag di funzione {#create-feature}

Crea un nuovo flag di funzione.

| | |
|---|---|
| **Endpoint** | `POST /m/api/v1/mgmt/feature` |
| **Metodo** | POST |

### Corpo della richiesta {#create-request-body}

Il corpo della richiesta è un oggetto [FeatureDTO](#featuredto-object). Per la creazione sono necessari i seguenti campi:

| Campo | Obbligatorio | Note |
|---|---|---|
| `name` | Sì | Chiave flag di funzione. Massimo 50 caratteri. Pattern: `^[a-zA-Z0-9_.-]*$` |
| `clientId` | Sì | ID numerico dell’applicazione. Vedi [Ottieni ID client](get-client-id.md). |
| `state` | Sì | `"enabled"` o `"disabled"` |

### Risposta {#create-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta contiene `{ "generatedFeatureId": <id> }`. |
| `400` | Payload non valido. |
| `403` | Autorizzazioni insufficienti per questa regola client o pubblico. |
| `417` | Gli utenti con il ruolo Sviluppatore non possono salvare una funzione con una regola pubblica. È necessaria almeno una regola di pubblico. |

**Richiesta di esempio:**

```json
{
  "name": "my-new-feature",
  "clientId": 1191,
  "state": "disabled",
  "description": "A new feature flag",
  "meta": "VGVzdA==",
  "audience": [
    {
      "criteria": {
        "and": [{ "operator": "EQ", "attr": "COUNTRY", "category": "default", "ruleId": 1, "val": "US" }]
      }
    }
  ],
  "variations": [{ "variantPercentage": 100, "variantName": "Variation 1" }],
  "params": { "label": "My New Feature", "tags": [] }
}
```

## Flag di funzione di aggiornamento {#update-feature}

Aggiorna un flag di funzione esistente. Passa l&#39;oggetto [FeatureDTO completo](#featuredto-object) incluso il campo `id`.

| | |
|---|---|
| **Endpoint** | `PUT /m/api/v1/mgmt/feature` |
| **Metodo** | PUT |

### Risposta {#update-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è l&#39;oggetto FeatureDTO aggiornato. |
| `400` | Payload non valido. |
| `403` | Autorizzazioni insufficienti. |
| `417` | Conflitto di aggiornamenti simultanei. Recupera prima la funzionalità corrente e riprova con il valore `version` più recente da `params`. |

## Elimina flag di funzione {#delete-feature}

Elimina un flag di funzione in base al relativo ID numerico.

| | |
|---|---|
| **Endpoint** | `DELETE /m/api/v1/mgmt/feature/{featureId}` |
| **Metodo** | DELETE |

### Risposta {#delete-response}

| Stato | Descrizione |
|---|---|
| `204` | Operazione completata. Nessun corpo di risposta. |
| `403` | Autorizzazioni insufficienti. |

## Riferimento a un oggetto FeatureDTO {#featuredto-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `id` | Intero | ID del flag della funzione. Richiesto solo per le chiamate di aggiornamento. | Condizionale |
| `name` | Stringa | Chiave del flag della funzione (restituita nelle risposte API). Massimo 50 caratteri. Pattern: `^[a-zA-Z0-9_.-]*$` | Sì (crea) |
| `clientId` | Intero | ID numerico dell’applicazione. | Sì |
| `state` | Stringa | `"enabled"` o `"disabled"` | Sì |
| `meta` | Stringa | Metadati con codifica Base64 restituiti con la funzione nelle risposte API. Massimo 1024 caratteri. | No |
| `description` | Stringa | Visualizza la descrizione. Massimo 225 caratteri. | No |
| `audience` | Array | Elenco di regole per il pubblico. Vedi [Oggetto FeatureRule](#featurerule-object). Utilizza [Ottieni i criteri di pubblico desiderati](get-audience-criteria.md) per generare questo elemento. | No |
| `variations` | Array | Elenco delle varianti. Max 3. Vedi [Oggetto FeatureVariation](#featurevariation-object). | No |
| `params` | Oggetto | Metadati aggiuntivi Chiavi supportate: `label` (nome visualizzato nell&#39;interfaccia utente), `tags` (array di stringhe). | No |
| `release` | Oggetto | Associazione rilascio/gruppo. `null` se il flag non è incluso in un gruppo. Sola lettura. | No |

### Oggetto FeatureVariation {#featurevariation-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `id` | Intero | ID variante. Richiesto solo per le chiamate di aggiornamento. | Condizionale |
| `variantName` | Stringa | Nome variante. Valori corretti: `"Variation 1"`, `"Variation 2"`, `"Variation 3"`. | Sì |
| `variantPercentage` | Decimale | Percentuale del pubblico che riceve questa variante. Deve essere maggiore di 0 e non superiore a 100, con un massimo di 2 cifre decimali. | Sì |

### Oggetto FeatureRule {#featurerule-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `id` | Intero | ID regola. Richiesto solo per le chiamate di aggiornamento. Impostato su `null` quando si aggiunge una nuova regola. | Condizionale |
| `criteria` | Oggetto | Oggetto condizione che definisce la regola del pubblico. Vedi [Oggetto condizione](#condition-object). | Sì |

### Oggetto condizione {#condition-object}

| Campo | Tipo | Descrizione |
|---|---|---|
| `and` | Array\&lt;Condizione\> | Tutte le condizioni devono essere vere. |
| `or` | Array\&lt;Condizione\> | Almeno una condizione deve essere vera. |
| `not` | Condizione | Questa condizione deve essere false. |
| `attr` | Stringa | Attributo utente da valutare (ad esempio, `COUNTRY`, `LOCALE`). |
| `operator` | Stringa | Operatore di confronto, ad esempio `EQ`, `IN`, `LT`. |
| `val` | Stringa | Valore con cui confrontare. |
| `meta` | Oggetto | Metadati condizione facoltativi. `desc` imposta l’etichetta di visualizzazione nell’interfaccia utente. |

In ogni condizione è necessario specificare uno dei valori `and`, `or` o `not` oppure una combinazione di `attr`, `operator` e `val`.

## Vedi anche {#see-also}

* [Panoramica delle API di gestione delle funzioni](feature-management-apis-overview.md)
* [API delle patch di gestione](management-patch-api.md)
* [Ottenere l’ID client per un’applicazione](get-client-id.md)
* [Ottenere i criteri di pubblico desiderati](get-audience-criteria.md)
