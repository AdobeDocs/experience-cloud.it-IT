---
title: Configurazione dell’accesso API
description: Scopri come impostare l’accesso alle API di Campaign Standard.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: efbbd0cd-9c56-4ad0-8bcb-efba4b63c28b
source-git-commit: 3e7af8a9ba41ab54738fff2f69388595041a8574
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 31%

---

# Configurazione dell’accesso alle API {#setting-up-api-access}

L’accesso alle API di Adobe Campaign Standard è configurato attraverso i passaggi seguenti. Ciascuno di questi passaggi è descritto nel [Documentazione di Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md).

>[!IMPORTANT]
>
>Per gestire i certificati in [Adobe Developer](https://developer.adobe.com/), assicurati di avere **Amministratore di sistema** diritti sull&#39;organizzazione o su un [account sviluppatore](https://helpx.adobe.com/it/enterprise/using/manage-developers.html) nell’Admin Console.

1. **Verifica di disporre di un certificato digitale** oppure creane uno, se necessario. Le chiavi pubbliche e private fornite con il certificato sono necessarie nei passaggi seguenti.
1. **Creare una nuova integrazione con il servizio Adobe Campaign** in [Adobe Developer](https://developer.adobe.com/) e configurarlo. Quindi saranno generate le credenziali (chiave API, segreto client...).
1. **Crea un token web JSON (JWT)** dalle credenziali generate in precedenza e firmalo con la tua chiave privata. Il JWT codifica tutte le informazioni di identità e sicurezza necessarie ad Adobe per verificare la tua identità e concederti l’accesso all’API.

   >[!IMPORTANT]
   >
   >Il codice JWT (JSON Web Tokens) è attualmente in fase di ammortamento e viene sostituito con OAuth. La transizione viene eseguita progressivamente nelle prossime versioni di Campaign. Le credenziali dell’account di servizio (JWT) sono state contrassegnate come obsolete e continueranno a funzionare fino al 27 gennaio 2025. Pertanto, è necessario migrare l’applicazione o l’integrazione per utilizzare le nuove credenziali server-to-server OAuth prima del 27 gennaio 2025. È preferibile l’autenticazione OAuth. Troverai tutti gli elementi per migrare dall’autenticazione JWT all’autenticazione OAuth in queste pagine:
   >* [Migrazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [Implementazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [Domande frequenti su JWT obsolete](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

1. **Scambia il tuo JWT con un token di accesso** tramite una richiesta POST. Questo token di accesso dovrà essere utilizzato in ogni intestazione delle richieste API.

Per stabilire una sessione API di Adobe I/O servizio-servizio sicura, ogni richiesta a un servizio di Adobe deve includere nell’intestazione dell’autorizzazione le informazioni riportate di seguito.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;organization>**: questo è il tuo ID ORGANIZZAZIONE personale, un ID ORGANIZZAZIONE viene fornito come Adobe per ciascuna istanza:

   * &lt;organization> : istanza di produzione,
   * &lt;organization-mkt-stage>: l’istanza di stage.

  Per ottenere il valore dell’ID organizzazione, rivolgiti all’amministratore o al contatto tecnico Adobe. Puoi anche recuperarlo in Adobe I/O durante la creazione di una nuova integrazione, nell’elenco delle licenze (vedi <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">Documentazione di Adobe Developer</a>).

* **&lt;access_token>**: token di accesso personale, recuperato durante lo scambio del token web JSON tramite una richiesta POST.

* **&lt;API_KEY>**: la tua chiave API personale. Viene fornito in Adobe I/O dopo la creazione di una nuova integrazione con il servizio Adobe Campaign.

  ![testo alternativo](assets/tenant.png)

## Risoluzione dei problemi

Durante l’integrazione Adobe IO, se viene visualizzato il seguente errore:

```
{ 
"code": 502, 
"message": "Oops. Something went wrong. Check your URI and try again." 
}
```


Per verificare se il parametro CNAME è stato creato correttamente, rivolgiti al tuo amministratore o al contatto tecnico Adobe.
