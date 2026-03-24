---
title: Ottenere l’ID client per un’applicazione
description: Scopri come trovare l’ID client numerico per un’applicazione nella console Rollout esperienza, richiesto per la chiamata delle API di gestione.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---


# Ottenere l’ID client per un’applicazione {#get-client-id}

I flag di funzionalità e le API di gestione dei gruppi di funzionalità richiedono un `clientId` numerico per identificare l&#39;applicazione a cui appartiene la funzionalità. Questo è diverso dall’ID client IMS basato su stringhe utilizzato per l’autenticazione API.

Per trovare l’ID client numerico di un’applicazione, segui la procedura riportata di seguito.

## Passaggi {#steps}

Per trovare l’ID client numerico di un’applicazione, effettua le seguenti operazioni:

1. Accedi alla console Rollout esperienza.
2. Passa a **Funzioni e versioni**.
3. Selezionare la scheda **Flag di funzionalità**.
4. Apri il menu a discesa **Applicazione** e seleziona l&#39;applicazione di cui hai bisogno l&#39;ID client.
5. Osserva l’URL nella barra degli indirizzi del browser. Dopo `feature-flags/`, il numero visualizzato è l&#39;ID client numerico per l&#39;applicazione.

Ad esempio, se l&#39;URL termina con `.../feature-flags/1191/...`, l&#39;ID client è `1191`.

## Utilizzare l’ID client nelle chiamate API {#use-in-api}

Passa questo valore come parametro `clientId` nelle richieste API di gestione. Ad esempio, durante la creazione di un flag di funzione:

```json
{
  "name": "my-feature-flag",
  "clientId": 1191,
  "state": "disabled"
}
```

## Vedi anche {#see-also}

* [API di gestione dei flag di funzione](feature-flags-management-api.md)
* [API di gestione dei gruppi di funzioni](feature-group-management-api.md)
* [Ottenere i criteri di pubblico desiderati](get-audience-criteria.md)
