---
title: Creazione di un servizio con API
description: Scopri come creare un servizio con API
role: Developer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti di Campaign Standard migrati"
exl-id: 91bbce9e-a618-4be2-840b-c7d021271f4e
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Creazione di un servizio con API{#creating-a-service-api}

Creazione di servizi eseguita con una richiesta **POST** nella risorsa del servizio.

Se desideri creare il servizio con attributi specifici, aggiungili al payload. In caso contrario, il nuovo servizio verrà creato con quelli predefiniti.

<br/>

***Richiesta di esempio***

Richiesta POST di esempio per creare un servizio con attributi specifici.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
-i
-d {
-d "label": "My newsletter",
-d "messageType": "email",
-d "name": "email_newsletter",
-d "start": "2019-10-06"
-d }
```

Restituisce il servizio appena creato con gli attributi aggiornati.

```
{
    "PKey": "<PKEY>",
    "builtIn": false,
    "created": "2019-09-26 12:00:37.005Z",
    "href": "https://mc.adobe.io/<ORGANIZATION>/profileAndServices/service/@NLscZuVHxdVu9rPftvrMWFfR1zRIxQGswSOmGLrK09JTF_iWhB0JCUHEndA_vvy__k9mzOYa5NVkcWDcrK8qGh0wygahX9kRcD44kiWWSEceShn3",
    "label": "My newsletter",
    ...
}
```
