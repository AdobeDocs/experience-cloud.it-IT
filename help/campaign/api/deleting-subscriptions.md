---
title: Eliminazione di abbonamenti
description: Scopri come eliminare gli abbonamenti con API
role: Developer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti di Campaign Standard migrati"
exl-id: 76e2d102-c877-41a6-af87-2f407201a572
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Eliminazione di abbonamenti con API {#mdeleting-subscriptions-api}

<!--NOTE TO WRITER: There are two duplicate headings that seem to have the same content. Delete one? Rename if different?-->

## Eliminazione di una sottoscrizione di servizio per un profilo specifico {#deleting-service-subscription}

Questa è una procedura in tre fasi.

1. Recupera l’URL delle sottoscrizioni per il profilo desiderato.
1. Esegui una richiesta GET sull’URL degli abbonamenti.
1. Esegui una richiesta DELETE sull’URL del servizio desiderato.

Se la richiesta di eliminazione ha esito positivo, lo stato della risposta è 204 Nessun contenuto.

<br/>

***Richiesta di esempio***

I payload di esempio riportati di seguito mostrano come annullare l’abbonamento di un profilo a un servizio. Esegui prima una richiesta GET per recuperare il profilo.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce l’URL delle sottoscrizioni per il profilo.

```
  {
    ...
    "postalAddress":...,
    "preferredLanguage": "none",
    "subscriptions": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions/"
    },
  }
```

Esegui una richiesta GET sull’URL degli abbonamenti.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce l’elenco degli abbonamenti per il profilo selezionato, con un URL per ciascun servizio a cui si è iscritti.

```
...
"service": {
  "PKey": "<PKEY>",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
  "label": "Sport Newsletter",
  "name": "SVC1",
  "title": "Sport Newsletter (SVC1)"
},
...
```

Esegui una richiesta DELETE sull’URL del servizio desiderato.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->

## Eliminazione di una sottoscrizione di servizio per un profilo specifico

Questa è una procedura in tre fasi.

1. Recupera il servizio desiderato e il relativo URL di abbonamento.
1. Esegui una richiesta GET sull’URL degli abbonamenti per recuperare tutti gli abbonamenti dei profili.
1. Esegui una richiesta DELETE sull’URL di abbonamento del profilo desiderato.

Se la richiesta di eliminazione ha esito positivo, lo stato della risposta è 204 Nessun contenuto.

<br/>

***Richiesta di esempio***

Recupera il record del servizio.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce l’URL degli abbonamenti per il servizio.

```
{
  ...
  "messageType": "email",
  "mode": "newsletter",
  "name": "SVC3",
  "subScenarioEventType": "subscriptionEvent",
  "subscriptions": {
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
  },
  "targetResource": "profile",
  ...
},
```

Esegui una richiesta GET sull’URL degli abbonamenti.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce l’elenco degli abbonamenti per il servizio selezionato, con un URL (href) per ogni abbonamento al profilo.

```
{
  "PKey": "<PKEY>",
  "created": "2019-03-26 08:58:04.764Z",
  "email": "",
  "expirationDate": "",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY>",
  "metadata": "subscriptionRcp",
  "service": ...,
  "serviceName": "SVC3",
  "subscriber": ...,
  ...
}
```

Esegui una richiesta DELETE sull’URL di abbonamento del profilo desiderato.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->
