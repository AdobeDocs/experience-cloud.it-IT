---
title: Ordinamento
description: Scopri come eseguire le operazioni di ordinamento
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 7db25b8d-a6f1-4151-bf37-c47e9991ae48
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 10%

---

# Ordinamento

L’ordinamento è disponibile per impostazione predefinita in ordine crescente. Per ordinare in ordine decrescente, aggiungi **%20desc** al **_ordina** valore del parametro.

Per sapere se un campo può essere ordinato, controlla il parametro &quot;sortable&quot; nei metadati della risorsa. Per ulteriori informazioni al riguardo, consulta [questa sezione](metadata-mechanism.md).

<br/>

***Richieste di esempio***

* Richiesta di GET di esempio per recuperare le e-mail nel database in ordine alfabetico.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Risposta alla richiesta.

  ```
  {
  "content": [
      "adam@email.com",
      "allison.durance@example.com",
      "amy.dakota@mail.com",
      "andrea.johnson@mail.com",
      ...
  ]
  ...
  }
  ```

* Richiesta di GET di esempio per recuperare l’e-mail nel database in ordine alfabetico decrescente.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email%20desc \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Risposta alla richiesta.

  ```
  {
  "content": [
      "tombinder@example.com",
      "tombinder@example.com",
      "timross@example.com",
      "john.smith@example.com",
      ...
  ]
  }
  ```
