---
title: Ottenere i criteri di pubblico desiderati
description: Scopri come generare la struttura JSON corretta per i criteri di pubblico da utilizzare nelle API di gestione dei rollout di esperienza utilizzando la console e l’API delle funzioni di GET.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 1%

---


# Ottenere i criteri di pubblico desiderati {#get-audience-criteria}

Il campo dei criteri di pubblico nelle API di gestione utilizza un formato JSON strutturato che può essere complesso da scrivere a mano. L’approccio consigliato consiste nel generare il pubblico desiderato utilizzando la console e quindi recuperarne la rappresentazione JSON tramite l’API.

## Passaggi {#steps}

Per ottenere il JSON per un criterio di pubblico desiderato, segui questi passaggi:

1. Nella console Rollout esperienza, crea un flag di funzione temporaneo con i criteri di pubblico che desideri utilizzare nella chiamata API.
2. Dopo il salvataggio, annota l’ID del flag di funzione dall’URL del browser. L’ID viene visualizzato nell’URL dopo l’ID client. Ad esempio, in `.../feature-flags/1191/22080`, l&#39;ID funzionalità è `22080`.
3. Chiamare l&#39;endpoint [Get Feature by ID](feature-flags-management-api.md#get-feature-by-id) con tale ID funzionalità.
4. Nel JSON di risposta, individua il campo `audience`. Contiene l’esatta struttura dei criteri di pubblico necessaria.
5. Copiare il valore `audience`, rimuovendo l&#39;attributo `id` da ogni oggetto regola. Utilizzalo nella chiamata API per creare o aggiornare la funzione.

## Esempio {#example}

Dopo aver chiamato GET `/m/api/v1/mgmt/feature/22080`, la risposta include:

```json
{
  "audience": [
    {
      "id": 10034665,
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

Per utilizzare questo valore in una chiamata di funzione Crea, rimuovi il campo `id` dall&#39;oggetto pubblico:

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

## Vedi anche {#see-also}

* [API di gestione dei flag di funzione](feature-flags-management-api.md)
* [Ottenere l’ID client per un’applicazione](get-client-id.md)
* [API delle patch di gestione](management-patch-api.md)
