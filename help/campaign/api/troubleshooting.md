---
title: Risoluzione dei problemi API
description: Ulteriori informazioni sui problemi comuni relativi alle API di Campaign Standard
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 404356cd-021f-4739-a88f-b8b1b79e19bc
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Risoluzione dei problemi API {#troubleshooting}

* **Quando si accede alla console Adobe.io viene visualizzato il seguente errore: &quot;La console Adobe I/O è disponibile solo per alcuni membri degli account enterprise. Se ritieni di dover accedere, contatta l’amministratore di sistema.&quot;**

Puoi creare le chiavi API solo per le organizzazioni di cui sei amministratore. Se questo messaggio viene visualizzato e desideri creare le chiavi API e chiedere a uno degli amministratori dell’organizzazione.

* **Quando effettui una richiesta a Adobe.io ottieni {&quot;error_code&quot;:&quot;403023&quot;,&quot;message&quot;:&quot;Profile is not valid&quot;}**

Ciò significa che esiste un problema con il provisioning IMS del prodotto Campaign specifico: il team IMS deve risolverlo.

Per ottenere ulteriori dettagli, puoi chiamare l’API IMS con il token per visualizzare l’aspetto del profilo IMS: per poter instradare la richiesta, è necessario disporre di un prodCtx in cui il valore organization_id sia uguale a quello inserito nell’URL, ad Adobe.io.
Se manca, è necessario correggere il provisioning IMS.

```
-X GET https://mc.adobe.io/{ORGANIZATION}/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Restituisce il seguente errore.

```
{"error_code":"403023","message":"Profile is not valid"}
```

Verifica il tuo profilo IMS con questa richiesta.

```
-X GET https://ims-na1.adobelogin.com/ims/profile/v1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Nella risposta, il valore ORGANIZATION_ID deve essere lo stesso nella prima richiesta GET.

```
{
  "countryCode": "FR",
  "mrktPermEmail": null,
  "projectedProductContext": [
    {
    "prodCtx": {
      "statusCode": "ACTIVE",
      "ident": "ZQ9FRQK7BF09YXAESFY9DDQP1G",
      "modDts": 1448307260000,
      "organization_id": "actest",
      "owningEntity": "6096892F54B5819E0A4C98A2@AdobeOrg",
      "serviceCode": "dma_tartan",
      "label": "Adobe Marketing Cloud",
      "serviceLevel": "standard",
      "createDts": 1421181343000,
      "deal_id": " "
      }
    }
  ]
}
```

* **Quando effettui una richiesta a Adobe.io ottieni {&quot;code&quot;:500, &quot;message&quot;:&quot;Oops. Si è verificato un errore. Controlla l’URI e riprova.&quot;}**

Adobe.io dichiara l’URI non valido: probabilmente l’URI richiesto non è valido. Su Adobe.io, quando selezioni il servizio Campaign, ottieni un selettore con un elenco di possibili organization_ids. Devi verificare che quello scelto sia quello inserito nell’URL.

* **Quando effettui una richiesta a Adobe.io ottieni {&quot;error_code&quot;:&quot;401013&quot;,&quot;message&quot;:&quot;Token OAuth non valido&quot;}**

Il token non è valido (per generare un token viene utilizzata una chiamata IMS non corretta) oppure il token è scaduto.

* **Non visualizzo il mio profilo dopo la creazione**

A seconda della configurazione dell’istanza, il profilo creato deve essere associato a un **orgUnit**. Per informazioni su come aggiungere questo campo nella creazione, consulta [questa sezione](creating-profiles-api.md).

<!-- * (error duplicate key : quand tu crées un profile qui existe déjà , il faut faire un patch pour updater le profile plutôt qu’un POST)

With Curl
List all profiles

Create a profile

Update the mobilePhone attribute of a profile

API Calls on Service

GET the list of services

-->

<!--

How to find and use a filter?
Error codes:

* PAtch sur Age = message d'erreur :
500
Cannot update the 'age' property that is read-only
'age' property is not valid for the 'profile' resource.
-->

<!--
How to filter a list of subscribed profiles with available profile filters ? by date (by les filtres dispo sur la ressource) ?

Pattern classique :

recupérer la liste des subscriptions filtrées d'un profile
1) get sur profile
2) recup PKey
3) get sur PKey
4) get sur href des subscriptions

Comment savoir quel filtre appliquer ?

1) get sur metadata de profile
2) retourne description de la collection subscription
3) get sur la valeur du champ resTarget
4) get sur le href dans filters
5) retourne les filtres applicables sur l'url des data.

-->
