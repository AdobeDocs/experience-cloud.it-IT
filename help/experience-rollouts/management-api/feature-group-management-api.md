---
title: API di gestione dei gruppi di funzioni
description: Riferimento API per l'API di gestione dei gruppi di funzioni dei rollout di esperienza, inclusi gli endpoint per ottenere, creare, aggiornare, eliminare e controllare i piani di rollout per i gruppi di funzioni.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 14%

---


# API di gestione dei gruppi di funzioni {#feature-group-management-api}

L’API per la gestione dei gruppi di funzioni consente di creare, leggere, aggiornare ed eliminare in modo programmatico i gruppi di funzioni nei Rollout di esperienze, inclusi i piani di rollout automatizzati e di test A/B.

**Percorso base:** `/m/api/v1/mgmt/group`

Tutte le richieste richiedono le intestazioni descritte nei [requisiti comuni](feature-management-apis-overview.md#common-requirements).

## Ottieni tutti i gruppi di funzioni {#get-all-groups}

Recupera tutti i gruppi di funzioni per l’organizzazione.

| | |
|---|---|
| **Endpoint** | `GET /m/api/v1/mgmt/group` |
| **Metodo** | GET |

### Parametri della query {#get-all-query-params}

| Parametro | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `myOrg` | Booleano | Impostare su `true` per includere le informazioni sull&#39;organizzazione. | Sì |
| `includeClientInfo` | Booleano | Impostare su `true` per includere le informazioni sull&#39;applicazione per ogni gruppo. | Sì |

### Risposta {#get-all-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è un array di oggetti del gruppo di funzioni. |

## Ottieni gruppo di funzioni per ID {#get-group-by-id}

Recupera un singolo gruppo di feature in base al relativo ID numerico.

| | |
|---|---|
| **Endpoint** | `GET /m/api/v1/mgmt/group/{groupId}` |
| **Metodo** | GET |
| **Parametro query** | `includeAnalyzeInfo=true` (facoltativo — aggiunge dati di analisi alla risposta) |

### Risposta {#get-by-id-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è un oggetto del gruppo di funzioni. |
| `400` | ID gruppo di funzioni non valido. |

## Crea gruppo di funzioni {#create-group}

Crea un nuovo gruppo di funzioni con un tipo di rollout per test A/B manuale, automatico o automatico.

| | |
|---|---|
| **Endpoint** | `POST /m/api/v1/mgmt/group` |
| **Metodo** | POST |

### Corpo della richiesta {#create-request-body}

Il corpo della richiesta utilizza l&#39;[oggetto gruppo di funzionalità](#feature-group-object). `rolloutType` in `params` è obbligatorio e determina la struttura del payload.

**Esempio — rollout manuale:**

```json
{
  "params": {
    "rolloutType": "manual",
    "label": "my-feature-group",
    "tags": [],
    "canContextOverridePUP": false
  },
  "status": "SAVED",
  "type": "group",
  "name": "my.feature.group",
  "description": "A manual feature group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{ "criteria": { "and": [{ "operator": "EQ", "attr": "COUNTRY", "val": "US", "ruleId": 1, "category": "default" }] } }],
  "clients": [],
  "org": { "id": 95 }
}
```

### Risposta {#create-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è l&#39;oggetto gruppo di feature creato. |
| `400` | Payload non valido. Per informazioni dettagliate, vedere [messaggi di errore](#error-messages). |
| `403` | Autorizzazioni insufficienti. |

## Aggiorna gruppo di funzioni {#update-group}

Aggiorna un gruppo di funzioni esistente. Passa la stessa struttura del corpo della richiesta di creazione, incluso il campo `id`.

| | |
|---|---|
| **Endpoint** | `PUT /m/api/v1/mgmt/group` |
| **Metodo** | PUT |

### Risposta {#update-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è l&#39;oggetto gruppo di funzioni aggiornato. |
| `400` | Payload non valido. |
| `403` | Autorizzazioni insufficienti. |

## Elimina gruppo di funzioni {#delete-group}

Elimina un gruppo di feature in base al relativo ID numerico.

| | |
|---|---|
| **Endpoint** | `DELETE /m/api/v1/mgmt/group/{groupId}` |
| **Metodo** | DELETE |

### Risposta {#delete-response}

| Stato | Descrizione |
|---|---|
| `204` | Operazione completata. Nessun corpo di risposta. |
| `403` | Autorizzazioni insufficienti. |

## Riferimento oggetto gruppo di feature {#feature-group-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `id` | Intero | ID gruppo di funzioni. Richiesto solo per le chiamate di aggiornamento. | Condizionale |
| `name` | Stringa | Chiave gruppo di funzioni. Massimo 50 caratteri. Pattern: `^[a-zA-Z0-9_.-]*$` | Sì (crea) |
| `clients` | Array | Applicazioni associate al gruppo. Ogni voce deve includere `id` e `imsClientId`. | Sì |
| `status` | Stringa | `"SAVED"` o `"PUBLISHED"` | Sì |
| `type` | Stringa | Sempre `"group"` per i gruppi di caratteristiche. | Sì |
| `org` | Oggetto | Dettagli organizzazione. Deve includere `id`. | Sì |
| `params` | Oggetto | Parametri di gruppo. `rolloutType` è obbligatorio (`"manual"`, `"automated"` o `"ab-testing"`). Supporta anche `label` e `tags`. | Sì |
| `audience` | Array | Regole di pubblico per i tipi di rollout manuali. | No |
| `variations` | Array | Elenco delle varianti. Vedi [Oggetto FeatureGroupVariation](#featuregroupvariation-object). | No |
| `phaseRollOutPlan` | Oggetto | Piano di rollout della fase. Richiesto per i tipi di test A/B e automatizzati. Vedere [Oggetto PhaseRollOutPlan](#phaserolloutplan-object). | Condizionale |
| `description` | Stringa | Descrizione visualizzata facoltativa. Massimo 225 caratteri. | No |

### Oggetto FeatureGroupVariation {#featuregroupvariation-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `id` | Intero | ID variante. Richiesto solo per le chiamate di aggiornamento. | Condizionale |
| `variantName` | Stringa | Nome variante. Codifica fissa a `"Variant 1"`. | Sì |
| `variantPercentage` | Decimale | Percentuale del pubblico che riceve questa variante. Deve essere maggiore di 0 e non superiore a 100. | Sì |

### Oggetto PhaseRollOutPlan {#phaserolloutplan-object}

| Campo | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `phaseRollOutBlocks` | Array | Elenco ordinato di blocchi di fase e blocchi di attesa. L&#39;ultimo blocco deve essere un blocco di fase. | Sì |
| `rollOutPlanState` | Stringa | `"DRAFT"`, `"RUNNING"`, `"PAUSED"` o `"ABORTED"` | Sì |

Ogni blocco in `phaseRollOutBlocks` è un **blocco di fase** (`isPhaseBlock: true`) contenente un `phaseRule` con criteri di pubblico o un **blocco di attesa** (`isPhaseBlock: false`) contenente un `waitRule` con un `waitDuration` (relativo) o `executionDate` (timestamp fisso).

## Messaggi di errore {#error-messages}

| Condizione | Stato | Messaggio di errore |
|---|---|---|
| Nome non valido o vuoto | 400 | `Error: Invalid value for release name.` |
| Criteri di pubblico vuoti | 400 | `Error: Release is not valid` |
| Più varianti per il tipo automatizzato | 400 | `Error: Feature variation is not valid. Variation name should be unique across variations` |
| Gruppo pubblicato senza client | 400 | `Error: At least one client must be associated with enabled feature group.` |
| L’ultimo blocco nel piano non è un blocco di fase | 400 | `Error: The last block in the Phase Rollout plan should be phase block` |
| Timeout blocco di attesa non ordinato | 400 | `Error: Wait block timings are not in order in the phase rollout plan` |
| Tipi di blocchi di attesa non coerenti | 400 | `Error: Wait block should be of same type.` |
| Modifica di un blocco di fase attivato | 400 | `Error: Activated phase block should not be changed` |
| Tipo di rollout vuoto | 400 | `Error: Rollout type cannot be empty while feature group creation` |
| Piano di fase passato con tipo manuale | 400 | `Error: PhaseRollOutPlan can't be added with manual rollout type while feature group creation` |
| Pianificazione passata con stato PUBBLICATO | 400 | `Error: Schedule can't be added in published state while release/group creation` |

## Vedi anche {#see-also}

* [Panoramica delle API di gestione delle funzioni](feature-management-apis-overview.md)
* [API di gestione dei flag di funzione](feature-flags-management-api.md)
* [API delle patch di gestione](management-patch-api.md)
