---
title: Paginazione
description: Scopri come eseguire le operazioni di impaginazione.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: d6ebce3c-1e84-4b3b-a68d-90df4680af64
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# Paginazione

Per impostazione predefinita, 25 risorse vengono caricate in un elenco.

Il **_lineCount** consente di limitare il numero di risorse elencate nella risposta.  È quindi possibile utilizzare **avanti** per visualizzare i risultati successivi.

>[!NOTE]
>
>Utilizza sempre il valore URL restituito in **avanti** per eseguire una richiesta di impaginazione.
>
>Il **_lineStart** viene calcolata e deve essere sempre utilizzata all’interno dell’URL restituito nella **avanti** nodo.

<br/>

***Richiesta di esempio***

Richiesta di GET di esempio per visualizzare 1 record della risorsa profilo.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_lineCount=1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Risposta alla richiesta, con **avanti** per eseguire la paginazione.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "John",
            "lastName":"Doe",
            "birthDate": "1980-10-24",
            ...
        }
    ],
    "next": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
        lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
    }
    ...
}
```

Per impostazione predefinita, il **avanti** Il nodo non è disponibile quando si interagisce con tabelle con grandi quantità di dati. Per poter eseguire l’impaginazione, devi aggiungere **_forcePagination=true** parametro per l’URL della chiamata.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>Il numero di record al di sopra dei quali una tabella viene considerata grande è definito in Campaign Standard **XtkBigTableThreshold** opzione. Il valore predefinito è 100.000 record.
