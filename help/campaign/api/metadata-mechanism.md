---
title: Meccanismo metadati
description: Ulteriori informazioni sul meccanismo dei metadati.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti di Campaign Standard migrati"
exl-id: 58ec0999-b28a-4198-8d57-729b074c6a6d
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 1%

---

# Meccanismo metadati {#metadata-mechanism}

È possibile recuperare i metadati delle risorse utilizzando **resourceType** in una richiesta GET:

`GET /profileAndServices/resourceType/<resourceName>`

La risposta restituisce i metadati principali dalla risorsa (tutti gli altri campi sono descrittivi o interni):

* Il nodo **Content** restituisce i campi della risorsa. Per ogni campo del nodo **content**, sono disponibili i campi seguenti:

   * &quot;apiName&quot;: nome dell’attributo utilizzato nelle API.
   * &quot;type&quot;: definizione di tipo di alto livello (stringa, numero, collegamento, raccolta, enumerazione...).
   * &quot;dataPolicy&quot;: il valore del campo deve seguire le regole dei criteri specificate. Ad esempio, se la regola dataPolicy è impostata su &quot;email&quot;, il valore deve essere un messaggio e-mail valido. Durante un PATCH o un POST, DataPolicy può controllare il valore o modificarlo per la trasformazione (ad esempio SmartCase).
   * &quot;category&quot;: fornisce la categoria del campo nell’editor delle query.
   * &quot;resType&quot;: il tipo tecnico.

     Se &quot;type&quot; viene completato con il valore &quot;link&quot; o &quot;collection&quot;, il valore resTarget corrisponde al nome della risorsa di destinazione del collegamento.
Se &quot;type&quot; viene completato con il valore &quot;enumeration&quot;, viene aggiunto un campo &quot;values&quot; e ogni valore di enumerazione è descritto nel nodo **values**.

* Il nodo **Filters** restituisce l&#39;URL per recuperare i filtri associati. Per ulteriori informazioni sui filtri, consulta [questa sezione](filtering.md).

<!-- créer une section au même niveau sur les liens -->
<!-- dans l'exemple: birthdate, email +  mettre 2 liens : un de type 1-1 , 1-N
si on prend l'exemple de l'org unit, on aura un bon exemple lien -->
<!-- plus reparler du node Data -->

<br/>

***Richiesta di esempio***

Esegui una richiesta GET sulla risorsa.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce la descrizione completa della risorsa profilo.

```
{
...
"content": {
  "email": {...},
    ...
    },
"data": "/profileAndServices/profile/",
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>"
    },
"help": "Identified profiles",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/metadata",
"label": "Profiles",
"mandatory": false,
"name": "profile",
"pkgStatus": "never",
"readOnly": false,
"schema": "nms:recipient",
"type": "item"
}
```
