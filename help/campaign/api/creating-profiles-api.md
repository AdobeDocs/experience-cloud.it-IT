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
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Creazione di profili con API {#creating-profiles-api}

La creazione di profili viene eseguita con **POST** richiesta per la risorsa profilo.

>[!CAUTION]
>
>Se si desidera associare un <b>orgUnit</b> al profilo creato, devi estendere la risorsa profilo con questo campo e, dopo la pubblicazione dell’estensione, eseguire una richiesta POST sulla <b>ProfileAndServicesExt</b> endpoint.
>
>Per ulteriori informazioni sull’estensione della risorsa del profilo, consulta <a href="https://helpx.adobe.com/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">Documentazione di Campaign</a>.

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
