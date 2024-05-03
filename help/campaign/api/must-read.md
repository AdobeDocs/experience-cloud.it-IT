---
title: Da leggere
description: Da leggere prima di utilizzare le API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Da leggere {#must-read}

## Requisiti tecnici

* Le API di Adobe Campaign devono essere utilizzate solo da server a server.
* Verifica sempre con il tuo contatto tecnico Adobe se il caso d’uso che desideri implementare è allineato alla scala consentita dalle API di Adobe Campaign.
* Per impostare un accesso AdobeIO sono necessarie autorizzazioni specifiche, contatta il supporto Adobe per eventuali problemi.

## Diritti e accesso

* Per impostazione predefinita, le API di Adobe Campaign utilizzano il contesto dell’amministratore e pertanto le unità organizzative e i ruoli non sono applicabili.
* Le API di Adobe Campaign sono escluse dal contesto del ruolo.
* Se desideri configurare le API con uno o più ruoli dell’organizzazione, rivolgiti prima al tuo Adobe di contatto tecnico.

## Rappresentazione delle risorse

Tutte le risorse API sono disponibili in **JSON** con un’estensione URL o all’interno di un’intestazione HTTP Accept:

`GET /profileAndServices/<resourceName>.json`

>[!NOTE]
>
>Senza estensione nell&#39;URL, il **il formato json è quello predefinito** per il tipo di contenuto.

<br/>

***esempio di richiesta***

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile.json \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

## Chiave principale e URL

* Non provare a creare un URL da solo. Tutti gli URL vengono restituiti dall’API. Tuttavia, è possibile creare un URL basato sul nome della risorsa di livello superiore.

* I valori di chiave primaria automatica (PKey) che illustrano gli esempi non sono destinati a funzionare in un’altra distribuzione specifica. Sono prodotti dall’API Adobe Campaign.

* I valori di chiave primaria automatica generati da Adobe Campaign non devono mai essere memorizzati in un database esterno o in un sito Web. Devi generare campi chiave specifici nella definizione del database e utilizzarli durante gli sviluppi.

## Chiavi personalizzate {#custom-keys}

Se la risorsa profilo è stata estesa con un campo chiave personalizzato, puoi utilizzare questo campo come chiave invece della chiave primaria automatica generata da Adobe Campaign:

`GET /.../profileAndServicesExt/profile/<customKey>`

Le chiavi personalizzate non possono essere modificate con un’operazione PATCH se il valore della chiave è diverso dalla chiave di origine o se si utilizza come URI la propria chiave aziendale invece di quella fornita da Adobe.

Utilizza una chiave personalizzata per **risorse di profilo di livello superiore** solo. Gli URL vengono restituiti dall’API e non devono mai essere generati da soli.

<br/>

***Richiesta di esempio***

Per recuperare le sottoscrizioni di un profilo utilizzando una chiave personalizzata, eseguire un&#39;operazione di GET sulla chiave personalizzata.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/<customKey> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Esegui una richiesta GET sull’URL di abbonamenti restituito.

```
-X GET <SUBSCRIPTION_URL> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce l’elenco delle sottoscrizioni per il profilo.

```
"service": {
"PKey": "<PKEY>",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
"label": "Sport Newsletter",
"name": "SVC1",
"title": "Sport Newsletter (SVC1)"
}
```
