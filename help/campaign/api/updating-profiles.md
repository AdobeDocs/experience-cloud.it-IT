---
title: Aggiornamento dei profili
description: Scopri come aggiornare i profili con le API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: fa3796ee-a00c-4d70-bf3d-e8d2099f1116
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---

# Aggiornamento dei profili con le API{#updating-profiles-api}

Aggiornamento dei profili eseguito con una richiesta **PATCH**.

`https://mc.adobe.io/<ORGANIZATION>/campaign/<apiName>/<resourceName>/<PKEY>`

1. Il primo passaggio consiste nel **recuperare il profilo**.

1. In una seconda richiesta, esegui una **richiesta PATCH** sul profilo con le informazioni completate nel payload.

1. Per verificare se la richiesta PATCH ha aggiornato il profilo, possiamo eseguire una richiesta GET finale.

<br/>

***Richiesta di esempio***

Richiesta di GET di esempio per recuperare un profilo.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Risposta alla richiesta.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "Amy",
            "lastName":"Dakota",
            "birthDate": "1980-10-24",
            ...
        }
    ]
}
```

PATCH richiede di aggiornare l’attributo &quot;phone&quot;.

```
-X PATCH https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-d '{"phone":"3301020304"}'
```

Restituisce la PKEY e l’URL per recuperare il profilo aggiornato.

```
{
    "PKey": "<PKEY>",
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/@2v1dr3ZKJveMDhAdh0MPnh9hNQQ93qb7AW6BNVVKknjwXvTZRBAgUqz1SNcB4ZndgjqOofx3BwBZYBftlmObISoM3rs"
}
```
