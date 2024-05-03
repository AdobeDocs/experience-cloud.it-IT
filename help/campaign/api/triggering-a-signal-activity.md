---
title: Attivazione di attività di segnale
description: Scopri come attivare un’attività di segnale con le API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# Attivazione di attività di segnale {#triggering-a-signal-activity}

In un flusso di lavoro Adobe Campaign Standard possono essere presenti uno o più **Segnale esterno** attività. Queste attività sono &quot;listener&quot; che attendono di essere attivate.

Le API Campaign Standard consentono di attivare un’ **Segnale esterno** per chiamare un flusso di lavoro. La chiamata API può includere parametri che verranno acquisiti nelle variabili degli eventi del flusso di lavoro (un nome di pubblico per il target, un nome di file da importare, una parte del contenuto del messaggio, ecc.). In questo modo, puoi integrare facilmente le automazioni di Campaign con il sistema esterno.

>[!NOTE]
>
>Le attività di segnale esterno non possono essere attivate più spesso di ogni 10 minuti e il flusso di lavoro di destinazione deve essere già in esecuzione.

Per attivare un flusso di lavoro, effettua le seguenti operazioni:

1. Eseguire una **GET** richiesta al flusso di lavoro di recuperare l’URL del trigger dell’attività External signal.

   `GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>`

1. Eseguire una **POST** richiesta dell’URL restituito per attivare l’attività del segnale, con **&quot;source&quot;** nel payload. Questo attributo è obbligatorio e consente di indicare l’origine della richiesta di attivazione.

Se desideri chiamare il flusso di lavoro con i parametri, aggiungili al payload con **&quot;parameters&quot;** attributo. La sintassi è costituita dal nome del parametro seguito dal relativo valore (sono supportati i tipi seguenti: **stringa**, **numero**, **booleano** e **data/ora**).

```
  -X POST <TRIGGER_URL>
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -H 'Content-Type: application/json;charset=utf-8' \
  -H 'Content-Length:79' \
  -i
  -d {
  -d    "source":"<SOURCE>",
  -d    "parameters":{
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",  
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>"
  -d    }
  -d }
```

>[!NOTE]
>
>Quando aggiungi un parametro al payload, assicurati che i relativi **nome** e **tipo** I valori sono coerenti con le informazioni dichiarate nell’attività External signal. Inoltre, la dimensione del payload non deve superare i 64 Ko.

<br/>

***Richiesta di esempio***

Esegui una richiesta di GET sul flusso di lavoro.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce l’attività del segnale del flusso di lavoro e l’URL del trigger associato.

```
{
"PKey": "<PKEY>",
"activities": {
  "activity": {
    "signal1": {
      ...
      "trigger": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger/"
        },
        ...
      }
    }
  }
}
```

Per attivare un’attività di segnale, esegui una richiesta POST sull’URL del trigger con la &quot;sorgente&quot;. Aggiungi gli attributi &quot;parameters&quot; se desideri chiamare il flusso di lavoro con i parametri.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{
-d "source":"API",
-d "parameters":{
-d    "audience":"audience",
-d    "email":"anna.varney@mail.com",
-d    "template":"05",
-d    "contentURL":"http://www.adobe.com",
-d    "test":"true",
-d    "segmentCode":"my segment",
-d    "attribute":"2019-04-03 08:17:19.100Z"}
-d  }'
```

<!-- + réponse -->

Se uno dei parametri non è dichiarato nell’attività External signal, la richiesta POST restituisce l’errore seguente, che indica quale parametro risulta mancante.

```
RST-360011 An error has occurred - please contact your administrator.
'contentURL' parameter isn't defined in signal activity.
XTK-170006 Unable to parse expression 'HandleTrigger(@name, $(source), $({parameters}))'.
RST-360000 Error while assessing 'HandleTrigger(@name, $(source), $({parameters}))' expression ('xtk:workflow:execution/activities/signal/trigger' resource)
```
