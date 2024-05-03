---
title: Gestione dei messaggi transazionali
description: Scopri come gestire i messaggi transazionali con le API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
hidefromtoc: true
hide: true
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Gestione dei messaggi transazionali {#managing-transactional-messages}

Dopo aver creato e pubblicato un evento transazionale, devi integrarne l’attivazione nel sito web.

Ad esempio, desideri che venga attivato un evento di &quot;abbandono del carrello&quot; ogni volta che uno dei tuoi clienti abbandona il sito web prima di acquistare i prodotti nel carrello. A tal fine, in qualità di sviluppatore web, devi utilizzare l’API per messaggi transazionali REST.

1. Invia una richiesta in base al metodo POST, che attiva il [invio dell’evento transazionale](#sending-a-transactional-event).
1. La risposta alla richiesta POST contiene una chiave primaria che consente di inviare una o più richieste tramite una richiesta GET. Potrai quindi ottenere il [stato evento](#transactional-event-status).

## Invio di un evento transazionale {#sending-a-transactional-event}

L’evento transazionale viene inviato tramite una richiesta POST con la seguente struttura URL:

```
POST https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>
```

* **&lt;organization>**: l’ID ORGANIZZAZIONE personale. Fai riferimento a [questa sezione](must-read.md).

* **&lt;transactionalapi>**: gli endpoint dell’API per messaggi transazionali.

  Il nome dell’endpoint API per messaggi transazionali dipende dalla configurazione dell’istanza. Corrisponde al valore &quot;mc&quot; seguito dal tuo ID organizzazione personale. Prendiamo l’esempio dell’azienda di Geometrixx, con &quot;geometrixx&quot; come ID organizzazione. In tal caso, la richiesta POST sarebbe la seguente:

  `POST https://mc.adobe.io/geometrixx/campaign/mcgeometrixx/<eventID>`

  Durante l’anteprima API è visibile anche l’endpoint API per messaggi transazionali.

* **&lt;eventid>**: il tipo di evento che desideri inviare. Questo ID viene generato durante la creazione della configurazione dell’evento

### Intestazione richiesta POST

La richiesta deve contenere un’intestazione &quot;Content-Type: application/json&quot;.

È necessario aggiungere un set di caratteri, ad esempio **utf-8**. Questo valore dipende dall’applicazione REST in uso.

```
-X POST \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79' \
```

### Corpo della richiesta POST

I dati dell’evento sono contenuti nel corpo del POST JSON. La struttura dell’evento dipende dalla sua definizione. Il pulsante di anteprima API nella schermata di definizione delle risorse fornisce un esempio di richiesta.

Per gestire l’invio di messaggi transazionali collegati all’evento, è possibile aggiungere al contenuto dell’evento i seguenti parametri facoltativi:

* **scadenza** (facoltativo): dopo questa data, l’invio dell’evento transazionale verrà annullato.
* **pianificato** (facoltativo): da questa data, l’evento transazionale viene elaborato e il messaggio transazionale viene inviato.

>[!NOTE]
>
>I valori dei parametri &quot;scadenza&quot; e &quot;programmati&quot; seguono il formato ISO 8601. ISO 8601 specifica l&#39;uso della lettera maiuscola &quot;T&quot; per separare la data e l&#39;ora. Tuttavia, può essere rimosso dall’input o dall’output per migliorarne la leggibilità.

### Risposta alla richiesta POST

La risposta di POST restituisce lo stato dell’evento transazionale al momento della creazione. Per recuperare lo stato corrente (dati evento, stato evento...), utilizza la chiave primaria restituita dalla risposta del POST in una richiesta GET:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>/`

<br/>

***Richiesta di esempio***

POST richiede di inviare l’evento.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79'

{
  "email":"test@example.com",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}
```

Risposta alla richiesta POST.

```
{
  "PKey":"<PKEY>",
  "ctx":
  {
    "cartAmount": "",
    "lastProduct": "",
    "firstName": ""
  }
  "email":"",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "href": "mcAdobe/EVTcartAbandonment/<PKEY>",
  "serverUrl":" https://myserver.com ",
  "status":"pending",
  "type":""
}
```

### Stato degli eventi transazionali {#transactional-event-status}

Nella risposta, il campo &quot;status&quot; ti consente di sapere se l’evento è stato elaborato o meno:

* **in sospeso**: l’evento è in sospeso - l’evento assume questo stato quando è appena stato attivato.
* **elaborazione**: l’evento è in attesa di consegna; viene trasformato in un messaggio e il messaggio viene inviato.
* **in pausa**: il processo dell’evento è in pausa. Non viene più elaborato, ma mantenuto in coda nel database di Adobe Campaign.
* **elaborato**: l’evento è stato elaborato e il messaggio inviato correttamente.
* **ignorato**: l’evento è stato ignorato dalla consegna, in genere quando un indirizzo è in quarantena.
* **deliveryFailed**: si è verificato un errore di consegna durante l’elaborazione dell’evento.
* **routingFailed**: fase di routing non riuscita. Ciò può verificarsi, ad esempio, quando non è possibile trovare il tipo di evento specificato.
* **tooOld**: l’evento è scaduto prima che potesse essere elaborato; questo può accadere per vari motivi, ad esempio quando un invio non riesce più diverse volte (il che fa sì che l’evento non sia più aggiornato) o quando il server non può più elaborare gli eventi dopo che sono stati sovraccarichi.
* **targetingFailed**: Campaign Standard non è riuscito ad arricchire un collegamento utilizzato per il targeting dei messaggi.
