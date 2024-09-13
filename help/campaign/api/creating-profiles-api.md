---
title: Creazione di profili con API
description: Scopri come creare profili con le API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 69e8d034-6bdd-4b82-bcd7-1ef4be0a59b3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Creazione di profili con API {#creating-profiles-api}

La creazione dei profili viene eseguita con una richiesta **POST** nella risorsa profilo.

>[!CAUTION]
>
>Se si desidera associare una <b>orgUnit</b> al profilo creato, è necessario estendere la risorsa profilo a questo campo e, dopo la pubblicazione dell&#39;estensione, eseguire una richiesta POST sull&#39;endpoint <b>ProfileAndServicesExt</b>.
>
>Per ulteriori informazioni sull&#39;estensione della risorsa del profilo, consulta la <a href="https://helpx.adobe.com/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">documentazione di Campaign</a>.

<br/>

***Richiesta di esempio***

Esempio di richiesta POST per creare un profilo con l’e-mail &quot;john.doe@mail.com&quot;.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

Restituisce il nuovo profilo creato, con l’indirizzo e-mail &quot;john.doe@mail.com&quot;.

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```