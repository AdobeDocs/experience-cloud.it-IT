---
title: Recommendations e limitazioni
description: Recommendations e limitazioni durante la migrazione alle API REST di Campaign v8.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
mini-toc-levels: 1
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 45acebb1-9325-4e26-8fe9-cc73f745d801
source-git-commit: 952706ffafc1e7cd6a759bfbbb9c9200191544d9
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 1%

---

# Recommendations e limitazioni {#limitations}

## Autorizzazioni e sicurezza {#permissions}

### Mappatura dei profili di prodotto

In Campaign Standard, ti era stato concesso l’accesso alle API con un ruolo di amministratore elevato, indipendentemente dal profilo di prodotto assegnato. Campaign v8 introduce un diverso set di profili di prodotto, che richiede la mappatura dai profili di prodotto di Campaign Standard a Campaign v8.

Con la migrazione, due profili di prodotto vengono aggiunti agli account tecnici esistenti o precreati: Amministratore e Centro messaggi (per accedere alle API transazionali). Rivedi la mappatura del profilo di prodotto e assegna il profilo di prodotto necessario se non desideri che il profilo di prodotto Amministratore sia mappato con il tuo account tecnico.

### ID tenant

Dopo la migrazione, per eventuali integrazioni future, si consiglia di utilizzare l&#39;ID tenant **Campaign v8** negli URL REST, sostituendo l&#39;ID tenant Campaign Standard precedente.

### Utilizzo chiave

La gestione dei valori PKey varia tra Campaign Standard e Campaign v8. Se memorizzi le PKeys con Campaign Standard, assicurati che l’implementazione formi dinamicamente le successive chiamate API utilizzando le PKeys o gli href ottenuti da precedenti chiamate API.

## API disponibili {#deprecated}

Per il momento, è possibile utilizzare le API REST elencate di seguito:

* **Profili**
* **Servizi e abbonamenti**
* **Risorse personalizzate**
* **Flussi di lavoro**
* **Messaggi transazionali**

>[!AVAILABILITY]
>
>Per il momento, **Messaggi transazionali** REST API non è disponibile.
>
>Le API REST elencate di seguito sono obsolete e non sono disponibili per l’uso:
>* Storico dei dati marketing
>* Unità organizzative
>* Gestione della privacy

## Filtro

* Per utilizzare i filtri nei payload API REST, è necessario modificarli in Campaign v8 e fornire un nome da utilizzare nei payload. A tale scopo, accedere ai parametri aggiuntivi del filtro dalla scheda **[!UICONTROL Parametri]** e specificare il nome desiderato nel campo **[!UICONTROL Nome filtro nell&#39;API REST]**.

  ![](assets/api-filtering.png)


* Il prefisso &quot;by&quot; necessario per utilizzare i filtri personalizzati non è più necessario. Il nome del filtro deve essere utilizzato così com’è nelle richieste.

  Esempio:

  `GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/<customFilterName>?<customFilterparam>=<customFilterValue>`

## Campi di database rilasciati

Alcuni campi del database vengono eliminati durante la migrazione. Quando si utilizza un campo rilasciato, le API REST restituiscono valori vuoti. In futuro, tutti i campi rilasciati diventeranno obsoleti e verranno rimossi.

## POST con risorse collegate

Quando si utilizza il seguente formato del corpo della richiesta, con &quot;vehicleOwner&quot; che rappresenta il collegamento a &quot;nms:recipient&quot;:

```
{
    "vehicleNumber": "20009",
    "vehicleName": "Model E",
    "vehicleOwner":{
        "firstName":"tester 11",
        "lastName":"Smith 11"
    }
}
```

Le informazioni sul collegamento vengono ignorate. Di conseguenza, viene generato un nuovo record in &quot;cusVehicle&quot; contenente solo i valori &quot;vehicleNumber&quot; e &quot;vehicleName&quot;. Tuttavia, il collegamento rimane nullo, con conseguente impostazione di &quot;vehicleOwner&quot; su null.

In Campaign v8, quando si utilizza la stessa struttura del corpo della richiesta e il &quot;veicolo&quot; è collegato a un profilo, si verifica un errore. Questo errore si verifica perché la proprietà &quot;firstName&quot; non è riconosciuta come valida per &quot;cusVehicle&quot;. Tuttavia, un corpo della richiesta che include solo gli attributi senza il collegamento funziona senza alcun problema.

## Operazioni PATCH

* Campaign v8 non supporta PATCH con un corpo di richiesta vuoto: restituisce lo stato 204 Nessun contenuto.
* Campaign Standard supporta PATCH su elementi/attributi all’interno di uno schema, ma non in Campaign v8 è supportata alcuna operazione PATCH sulla posizione. Se si tenta di individuare un PATCH nel percorso, si verifica un errore interno del server 500 con un messaggio di errore che indica che la proprietà &#39;zipCode&#39; non è valida per la risorsa &#39;profile&#39;.

## Risposte REST

La sezione seguente elenca differenze minori tra le risposte REST di Campaign Standard e v8.

* Per i record a GET singolo, la risposta include il href nella risposta.
* Quando viene eseguita una query con l’attributo, Campaign v8 fornisce i valori Count e Pagination nella risposta.
* Dopo le operazioni POST, i valori delle risorse collegate vengono restituiti nella risposta.

## Codici di errore e messaggi

La sezione seguente elenca le differenze tra i codici di errore e i messaggi di Campaign Standard e Campaign v8.

| Scenario | Campaign Standard | Campaign v8 |
|  ---  |  ---  |  ---  |
| Usa una chiave PKey non valida nel corpo della richiesta | 500 - Attributo &#39;O5iRp40EGA&#39; sconosciuto (vedi definizione dello schema &#39;Profiles (nms:recipient)&#39;). XTK-170036 Impossibile analizzare l’espressione &quot;@id = @O5iRp40EGA&quot;. | 404 - Impossibile decrittografare PKey. (PKey=@jksad) |
| Usa una chiave PKey non valida nell&#39;URI | 500 - Attributo &#39;O5iRp40EGA&#39; sconosciuto (vedi definizione dello schema &#39;Profiles (nms:recipient)&#39;). XTK-170036 Impossibile analizzare l’espressione &quot;@id = @O5iRp40EGA&quot;. | 404 - Impossibile decrittografare PKey. (PKey=@jksad) Endpoint non supportato. (endpoint=rest/profileAndServices/profile/@jksad) |
| Utilizzo di due diverse chiavi non elaborate nell’URI e nel corpo della richiesta | 500 - RST-360011 Si è verificato un errore. Contattare l&#39;amministratore. RST-360012 Operazione non coerente sulla risorsa &#39;service&#39;. Impossibile aggiornare la chiave &#39;SVC3&#39; a &#39;SVC4&#39;. | 500 - Si è verificato un errore - contatta l’amministratore. |
| Utilizzo di PKey nell’URI e di una PKey non elaborata diversa nel corpo della richiesta | 500 - Esiste già un &quot;Servizio&quot; con la stessa chiave &quot;SVC4&quot;. Errore PGS-220000 PostgreSQL: ERRORE: il valore di chiave duplicato viola il vincolo univoco &quot;nmsservice_name&quot; DETAIL: la chiave (sname)=(SVC4) esiste già. | 500 - Si è verificato un errore - contatta l’amministratore. |
| Utilizzo di un raw-id non esistente nell’URI | 404 - RST-360011 Si è verificato un errore. Contattare l&#39;amministratore. Impossibile trovare il documento con il percorso &quot;Servizio&quot; dalla chiave &quot;adobe_nl:0&quot; (documento con schema &quot;servizio&quot; e nome &quot;adobe_nl&quot;) | 404 - Impossibile trovare il documento con il percorso &quot;Service&quot; dalla chiave &quot;adobe_nl&quot; (documento con schema &quot;service&quot; e nome &quot;adobe_nl&quot;) |
| Utilizzo di un raw-id non esistente nel corpo della richiesta | 404 - RST-360011 Si è verificato un errore. Contattare l&#39;amministratore. Impossibile trovare il documento con il percorso &quot;Servizio&quot; dalla chiave &quot;adobe_nl&quot; (documento con schema &quot;servizio&quot; e nome &quot;adobe_nl&quot;) | 404 - Impossibile trovare il documento con il percorso &quot;Service&quot; dalla chiave &quot;adobe_nl&quot; (documento con schema &quot;service&quot; e nome &quot;adobe_nl&quot;) |
| - | 500 - RST-360011 Si è verificato un errore. Contattare l&#39;amministratore. | 500 - Si è verificato un errore - contatta l’amministratore. |
| Inserisci un profilo/servizio con un valore enum di genere (o altro) non valido | 500 - RST-360011 Si è verificato un errore. Contattare l&#39;amministratore. Il valore &#39;invalid&#39; non è valido per l&#39;enumerazione &#39;nms:recipient:gender&#39; del campo &#39;@gender&#39; | 500 - Si è verificato un errore. Contattare l&#39;amministratore. |

## Profilo - Fuso orario

Con Campaign Standard, il fuso orario viene visualizzato come parte della risposta JSON di **profileAndServices/profile** chiamate REST API.

Con Campaign v8, il fuso orario viene visualizzato all’utente solo come parte delle chiamate REST API **profileAndServicesExt/profile**. Non fa parte delle chiamate REST API di **profileAndServices/profile** poiché è in fase di aggiunta in uno schema esteso.

## Flussi di lavoro - Attivazione segnale esterno

L’API del flusso di lavoro di Campaign Standard GET restituisce i nomi dei parametri, come le variabili dell’istanza del flusso di lavoro e i relativi tipi di dati (booleano, stringa, ecc.). Viene utilizzato per creare un corpo di richiesta JSON formattato in modo appropriato quando si attiva il segnale tramite una chiamata API POST.

Campaign v8 non supporta le variabili dell’istanza del flusso di lavoro per la pubblicità, ma si aspetta che gli sviluppatori sappiano di cosa si tratta. Di conseguenza, dopo la migrazione, le informazioni sui parametri nel corpo della richiesta POST dovranno essere costruite senza la disponibilità di informazioni sui parametri nella risposta API GET.

<!--## Transactional messages

* With Campaign Standard, a POST request returns empty fields for elements and attributes in the request body. With Campaign v8, the response returns values that match the ones in the request body instead.

* When publishing an event configuration, the API preview panel displays the REST URL alongside the request body syntax.

    Since Campaign v8 does not support event configuration fields definition (event creation is just adding a value to eventType enumeration), there is no API preview panel when adding an event type. The REST URL is displayed  in the transactional message user interface once an event transactional message is published.-->
