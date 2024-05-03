---
title: Endpoint
description: Ulteriori informazioni sugli endpoint API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 9%

---

# Endpoint {#endpoints}

Gli endpoint disponibili per l’API REST di Adobe Campaign:

* **/profileAndServices**: interagisce con i campi predefiniti. I campi estesi non sono accessibili con questo endpoint.
* **/profileAndServicesExt**: interagisce con i campi personalizzati aggiunti durante l’estensione della risorsa personalizzata Profilo o Servizi. Per ulteriori informazioni sulle risorse personalizzate, consulta [questa sezione](custom-resources.md).
* **/&lt;transactionalapi>**: interagisce con l’API dei messaggi transazionali (il nome dell’endpoint dell’API dei messaggi transazionali dipende dalla configurazione dell’istanza). Per ulteriori informazioni al riguardo, consulta [questa sezione](managing-transactional-messages.md).
* **/workflow/execution**: interagisce con i flussi di lavoro. Per ulteriori informazioni al riguardo, consulta [questa sezione](controlling-a-workflow.md).

Per impostazione predefinita, le risorse principali disponibili per **profileAndServices** e **profileAndServicesExt** Le API sono:

* **/profile**: interagisce con i profili dal database di Campaign. Per aggiungere profili a un servizio, utilizza **/service** endpoint. Per ulteriori informazioni sui profili in Campaign, consulta [Documentazione di Campaign](https://helpx.adobe.com/campaign/standard/audiences/using/about-profiles.html).
* **/service**: gestisci i servizi di abbonamento. Per ulteriori informazioni sui servizi in Campaign, consulta [Documentazione di Campaign](https://helpx.adobe.com/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>Tutte le altre risorse estese o create sono disponibili tramite **ProfileAndServicesExt** Solo API. Devono essere collegate al **Profilo** per essere accessibile.
