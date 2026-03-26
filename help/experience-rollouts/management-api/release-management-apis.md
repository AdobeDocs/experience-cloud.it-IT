---
title: API di gestione delle versioni
description: Riferimento API per le API di gestione delle versioni di Experience Rollout, inclusi gli endpoint per ottenere, creare e modificare versioni e gruppi di funzioni cross-team.
exl-id: e8d1d025-0645-4cf2-921f-d94c9f71282d
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 13%

---

# API di gestione delle versioni {#release-management-apis}

Le API di gestione delle versioni consentono di recuperare, creare e modificare le versioni e i gruppi di funzioni cross-team (CTFG) a livello di programmazione. Queste API utilizzano l’endpoint di gestione v2.

**Percorso base:** `/m/api/v2/mgmt/release`

Tutte le richieste richiedono le intestazioni descritte nei [requisiti comuni](feature-management-apis-overview.md#common-requirements), oltre all&#39;intestazione aggiuntiva elencata di seguito.

## Intestazione richiesta aggiuntiva {#additional-header}

| Intestazione | Descrizione | Obbligatorio |
|---|---|---|
| `x-user-context-org` | ID numerico del team dell’organizzazione. Puoi trovare questo valore nella console Rollout esperienza nelle impostazioni del team. | Sì |

## Ottieni versione per ID {#get-release}

Recupera una singola versione o un gruppo di funzioni cross-team in base al relativo ID numerico.

| | |
|---|---|
| **Endpoint** | `GET /m/api/v2/mgmt/release/{id}` |
| **Metodo** | GET |

### Parametri della query {#get-query-params}

| Parametro | Tipo | Descrizione | Predefinito |
|---|---|---|---|
| `includePermissions` | Booleano | Includi le autorizzazioni per aggiornare o eliminare questa versione. | `true` |
| `includeOrg` | Booleano | Includi informazioni sull’organizzazione per questa versione. | `true` |
| `includeAnalyzeInfo` | Booleano | Include informazioni di analisi. | `false` |

### Risposta {#get-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è un oggetto versione. Vedere [Riferimento all&#39;oggetto versione](#release-object). |
| `400` | ID versione non valido o richiesta non valida. |

## Crea versione {#create-release}

Crea una nuova versione o un gruppo di funzioni cross-team.

| | |
|---|---|
| **Endpoint** | `POST /m/api/v2/mgmt/release` |
| **Metodo** | POST |

### Corpo della richiesta {#create-request-body}

Il corpo della richiesta utilizza l&#39;oggetto [Release](#release-object). Per la creazione, `status` deve essere impostato su `"SAVED"` per i gruppi di funzioni cross-team (`CROSS_TEAM_FEATURE_GROUP` type) o `"DRAFT"` per le versioni standard (`RELEASE` type).

**Esempio: creare un gruppo di caratteristiche cross-team:**

```json
{
  "params": {
    "rolloutType": "manual",
    "cohortingType": "guid",
    "tags": [],
    "canContextOverridePUP": false,
    "label": "my-cross-team-group"
  },
  "status": "SAVED",
  "type": "CROSS_TEAM_FEATURE_GROUP",
  "name": "my-cross-team-group",
  "description": null,
  "meta": "",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{}],
  "clients": [],
  "pollInterval": 300,
  "org": { "id": "95" },
  "comment": ""
}
```

### Risposta {#create-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è l’oggetto versione creato. |
| `400` | Payload non valido. |

## Modifica versione {#edit-release}

Aggiorna una versione esistente o un gruppo di funzioni cross-team. Passa l’oggetto versione completa, incluso il campo `id`.

| | |
|---|---|
| **Endpoint** | `PUT /m/api/v2/mgmt/release/{id}` |
| **Metodo** | PUT |

### Risposta {#edit-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è l’oggetto versione aggiornato. |
| `417` | Conflitto di aggiornamenti simultanei. La versione è stata modificata tra le chiamate GET e PUT. Recupera la versione corrente e riprova. |

## Riferimento agli oggetti di rilascio {#release-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `id` | Intero | ID versione. Richiesto solo per le chiamate di aggiornamento. | Condizionale |
| `name` | Stringa | Nome della versione. Massimo 50 caratteri. Pattern: `^[a-zA-Z0-9_ ,.:()-]*$`. Deve essere univoco. | Sì |
| `description` | Stringa | Descrizione facoltativa. Massimo 255 caratteri. | No |
| `type` | Stringa | `"RELEASE"` per le versioni standard; `"CROSS_TEAM_FEATURE_GROUP"` per i gruppi di funzioni cross-team. | Sì |
| `status` | Stringa | Stato di rilascio. Per IMS: `"DRAFT"` alla creazione; `"DRAFT"`, `"SAVED"`, `"PUBLISHED"` all&#39;aggiornamento. Per CTFG: `"SAVED"` alla creazione; `"SAVED"`, `"PUBLISHED"` all&#39;aggiornamento. | Sì |
| `clients` | Array | Applicazioni associate a questa versione. Ogni voce richiede `id` (numerico) e `imsClientId` (stringa). | No |
| `audience` | Array | Elenco di regole per il pubblico. Vedi [Oggetto condizione](feature-flags-management-api.md#condition-object). | No |
| `variations` | Array | Elenco delle varianti. Durante l’invio è supportata solo 1 variante. | Obbligatorio per l’invio |
| `params` | Oggetto | Parametri di rilascio. Vedi [Campi parametri supportati](#supported-params). | Obbligatorio per l’invio |
| `org` | Oggetto | Oggetto organizzazione. Deve includere `id`. | No |

### Campi parametri supportati {#supported-params}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `label` | Stringa | Nome visualizzato. Massimo 50 caratteri. | Sì |
| `tags` | Array\&lt;Stringa\> | Tag facoltativi. Massimo 50 caratteri ciascuno. | No |
| `canContextOverridePUP` | Booleano | Se `true`, le regole di contesto sostituiscono le regole di profilo. Impostazione predefinita: `false`. | Sì |
| `isBetaRelease` | Booleano | Se `true`, contrassegna questa versione come versione beta. Impostazione predefinita: `false`. | No |

### Oggetto variante {#variation-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `id` | Intero | ID variante. Richiesto solo per le chiamate di aggiornamento. | Condizionale |
| `variantName` | Stringa | Nome variante. Massimo 50 caratteri. | Sì |
| `variantPercentage` | Doppio | Percentuale del pubblico che riceve questa variante. Intervallo: [0, 100]. | Sì |
| `features` | Array | Funzioni incluse in questa variante. Ogni voce deve includere `id`, `name`, `clientId` e `state`. | No |

## Vedi anche {#see-also}

* [Panoramica delle API di gestione delle funzioni](feature-management-apis-overview.md)
* [API di gestione dei flag di funzione](feature-flags-management-api.md)
* [API di gestione dei gruppi di funzioni](feature-group-management-api.md)
