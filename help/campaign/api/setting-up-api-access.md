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
source-git-commit: 18979fea28f4f3adce1139293203a59876831313
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 27%

---

# Configurazione dell’accesso alle API {#setting-up-api-access}

L’accesso alle API di Adobe Campaign Standard è configurato attraverso i passaggi seguenti. Ognuno di questi passaggi è descritto nella [documentazione di Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md).

>[!IMPORTANT]
>
>Per gestire i certificati in [Adobe Developer](https://developer.adobe.com/), assicurati di disporre dei diritti di **amministratore di sistema** per l&#39;organizzazione o di un account [sviluppatore](https://helpx.adobe.com/it/enterprise/using/manage-developers.html) nell&#39;Admin Console.

1. **Verifica di disporre di un certificato digitale** oppure creane uno, se necessario. Le chiavi pubbliche e private fornite con il certificato sono necessarie nei passaggi seguenti.
1. **Crea una nuova integrazione con il servizio Adobe Campaign** in [Adobe Developer](https://developer.adobe.com/) e configuralo. Quindi saranno generate le credenziali (chiave API, segreto client...).
1. **Crea una credenziale da server a server OAuth** seguendo questi [passaggi di implementazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

   >[!IMPORTANT]
   >
   >Il codice JWT (JSON Web Tokens) è attualmente in fase di ammortamento e viene sostituito con OAuth. La transizione viene eseguita progressivamente nelle prossime versioni di Campaign. Le credenziali dell’account di servizio (JWT) sono state contrassegnate come obsolete e continueranno a funzionare fino al 27 gennaio 2025. Pertanto, è necessario migrare l’applicazione o l’integrazione per utilizzare le nuove credenziali server-to-server OAuth prima del 27 gennaio 2025. È preferibile l’autenticazione OAuth. Troverai tutti gli elementi per migrare dall’autenticazione JWT all’autenticazione OAuth in queste pagine:
   >* [Migrazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [Implementazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [Domande frequenti su JWT obsolete](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

Per stabilire una sessione API di Adobe I/O servizio-servizio sicura, ogni richiesta a un servizio di Adobe deve includere nell’intestazione dell’autorizzazione le informazioni riportate di seguito.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;ORGANIZZAZIONE>**: questo è il tuo ID organizzazione personale; per Adobe viene fornito un ID organizzazione per ciascuna istanza:

   * &lt;ORGANIZZAZIONE> : l’istanza di produzione,
   * &lt;ORGANIZATION-market-stage>: l’istanza di stage.

  Per ottenere il valore dell’ID organizzazione, rivolgiti all’amministratore o al contatto tecnico Adobe. Puoi anche recuperarlo in Adobe I/O durante la creazione di una nuova integrazione, nell&#39;elenco delle licenze (consulta la <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">documentazione di Adobe Developer</a>).

* **&lt;ACCESS_TOKEN>**: token di accesso personale recuperato durante lo scambio del token Web JSON tramite una richiesta POST.

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
