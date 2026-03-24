---
title: API delle patch di gestione
description: Utilizza l’API PATCH dei rollout esperienza per aggiornare singoli campi di un flag di funzione, un gruppo di funzioni o un gruppo di funzioni cross-team senza passare l’oggetto completo.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 3%

---


# API delle patch di gestione {#management-patch-api}

L’API di PATCH consente di aggiornare campi specifici di un flag di funzione, un gruppo di funzioni o un gruppo di funzioni cross-team senza inviare l’oggetto completo nel corpo della richiesta. Questa funzione è utile per gli aggiornamenti mirati, come la modifica di una regola di pubblico, l’attivazione di uno stato o la regolazione di una percentuale di variazione.

## Flag di funzione PATCH {#feature-flag-patch}

Aggiorna uno o più campi di un flag di funzione.

| | |
|---|---|
| **Endpoint** | `PATCH /m/api/v1/mgmt/feature/{featureFlagId}` |
| **Metodo** | PATCH |

### Intestazioni di richiesta {#ff-request-headers}

Tutte le richieste richiedono le intestazioni descritte nei [requisiti comuni](feature-management-apis-overview.md#common-requirements).

### Parametro percorso {#ff-path-param}

| Parametro | Tipo | Descrizione | Obbligatorio |
|---|---|---|---|
| `featureFlagId` | Intero | ID numerico del flag di funzione da aggiornare. | Sì |

### Corpo della richiesta {#ff-request-body}

Passa solo i campi che desideri aggiornare. La risposta restituisce sempre l’oggetto flag di funzione aggiornato completo.

**Esempio - solo descrizione aggiornamento:**

```json
{
  "description": "Updated description"
}
```

**Esempio — rimuovere il pubblico esistente:**

```json
{
  "audience": null
}
```

**Esempio — aggiungere un nuovo pubblico quando non ne esisteva alcuno:**

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "DEVELOPMENT", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Esempio — aggiorna una regola di pubblico esistente:**

```json
{
  "audience": [
    {
      "id": 10020035,
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "PRODUCTION", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Esempio — modifica stato e percentuale di variazione:**

```json
{
  "state": "disabled",
  "variations": [
    {
      "id": 10017188,
      "variantName": "Variation 1",
      "variantPercentage": 80.0
    }
  ]
}
```

>[!NOTE]
>
>Quando aggiorni una regola di pubblico esistente, includi `id` della regola (disponibile dalla risposta della funzione di GET) per aggiornarla. Quando aggiorni le varianti, includi `id` della variante per evitare di creare un duplicato.

### Risposta {#ff-response}

| Stato | Descrizione |
|---|---|
| `200` | Operazione completata. Il corpo della risposta è l&#39;oggetto flag di funzione aggiornato completo. |
| `400` | Payload non valido. |
| `403` | Autorizzazioni insufficienti. |
| `417` | Conflitto di aggiornamenti simultanei. Recuperate la feature corrente e riprovate. |

## Gruppo di funzioni PATCH {#feature-group-patch}

Aggiorna uno o più campi di un gruppo di funzioni. La struttura delle richieste e delle risposte è uguale a quella del flag di funzione PATCH, ma solo l’endpoint è diverso.

| | |
|---|---|
| **Endpoint** | `PATCH /m/api/v1/mgmt/group/{featureGroupId}` |
| **Metodo** | PATCH |

## PATCH per gruppi di funzioni cross-team {#ctfg-patch}

Aggiorna uno o più campi di un gruppo di funzioni cross-team. Utilizza l’endpoint di versione v2.

| | |
|---|---|
| **Endpoint** | `PATCH /m/api/v2/mgmt/release/{CTFGId}` |
| **Metodo** | PATCH |

## Vedi anche {#see-also}

* [API di gestione dei flag di funzione](feature-flags-management-api.md)
* [API di gestione dei gruppi di funzioni](feature-group-management-api.md)
* [API di gestione delle versioni](release-management-apis.md)
* [Panoramica delle API di gestione delle funzioni](feature-management-apis-overview.md)
