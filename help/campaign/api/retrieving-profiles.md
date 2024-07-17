---
title: Recupero dei profili
description: Scopri come recuperare i profili con le API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 19679804-f728-49fa-b26e-8f31b67c29bf
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 4%

---

# Recupero di profili con API {#retrieving-profiles}

Il recupero dei profili viene eseguito con una richiesta **GET**.

Puoi quindi perfezionare la ricerca utilizzando filtri, ordinamento e impaginazione. Per ulteriori informazioni, consulta la sezione [Operazioni aggiuntive](sorting.md).

Inoltre, le API di Campaign Standard ti consentono di cercare profili in base a uno dei seguenti campi: e-mail, nome, cognome o qualsiasi campo personalizzato. Per ulteriori informazioni al riguardo, consulta [questa sezione](#searching-field).

<br/>

***Richieste di esempio***

* Esempio di richiesta GET per recuperare tutti i profili.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Risposta alla richiesta.

  ```
  {
      "content": [
          {
              "PKey": "<PKEY>",
              "firstName": "John",
              "lastName":"Doe",
              "birthDate": "1980-10-24",
              ...
          },
          ...
  }
  ```

* Richiesta di GET di esempio per recuperare i primi 10 valori e-mail.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10 \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Risposta alla richiesta. Il nodo &quot;avanti&quot; restituisce l’URL che ti consente di accedere ai 10 valori e-mail successivi.

  ```
  {
  "content": [
      "amy.dakota@mail.com",
      "kristen.smith@mail.com",
      "omalley@mail.com",
      "xander.harrys@mail.com",
      "jane.summer@mail.com",
      "gloria.boston@mail.com",
      "edward.snow@mail.com",
      "dorian.simons@mail.com",
      "peter.paolini@mail.com",
      "mingam+test08@adobe.com"
  ],
  "next": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
      lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
  }
  }
  ```

## Ricerca di profili in base a un campo {#searching-field}

Il parametro **[!UICONTROL filterType]** consente di recuperare i profili in base a uno dei seguenti campi: e-mail, nome, cognome o qualsiasi campo personalizzato aggiunto nel filtro avanzato durante l&#39;estensione della risorsa profilo.

>[!NOTE]
>
>Le ricerche fanno distinzione tra maiuscole e minuscole e vengono eseguite solo sui prefissi. Ad esempio, non potrai cercare un profilo utilizzando le ultime lettere del cognome.

***Richieste di esempio***

* Richiesta di esempio per filtrare i profili in base al nome.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John&filterType=firstName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Richiesta di esempio per filtrare i profili in base al cognome.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Miller&filterType=lastName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Richiesta di esempio per filtrare i profili in base all’e-mail.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John%40gmail.com&filterType=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Richiesta di esempio per filtrare i profili in base al campo personalizzato &quot;Hobby&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byText?cusHobby=Dancing&filterType=Hobby \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```
