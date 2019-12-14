---
title: Implementazione di Adobe Experience Platform Identity Service con Launch
description: Scopri come aggiungere l’estensione Adobe Experience Platform Identity Service e utilizzare l’azione Imposta ID cliente per raccogliere gli ID cliente. Questa lezione fa parte dell'esercitazione Implementazione di Experience Cloud nelle applicazioni Android per dispositivi mobili.
seo-description: null
seo-title: Implementazione di Adobe Experience Platform Identity Service con Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Aggiunta di Adobe Experience Platform Identity Service

Il servizio [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html) imposta un ID visitatore comune tra tutte le soluzioni Adobe per sviluppare le funzionalità di Experience Cloud, ad esempio la condivisione del pubblico tra le soluzioni.  Puoi anche inviare i tuoi ID cliente al Servizio per abilitare il targeting cross-device e le integrazioni con il sistema CRM (Customer Relationship Management).

Il servizio identità fa parte dell'estensione Mobile Core, ***pertanto l'hai già implementato quando hai installato Mobile SDK***! Al momento, questa esercitazione non include istruzioni per l'impostazione degli ID cliente. Per informazioni dettagliate su [come impostare gli ID](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/identity/identity-api-reference)cliente, consultate la documentazione.

## Passaggi di convalida

Per convalidare le chiamate al servizio identità, eseguite l'app di esempio in Android Studio, aprite la console di debug e cercate la richiesta e la risposta:

1. **Richiesta al servizio** identità (filtro Logcat a `IdentityExtension`) In questo esempio, l’ID (`d_mid`) è già stato impostato e viene ora nuovamente segnalato)

   ```java
   03-14 17:01:18.526 7743-7803/com.adobe.busbooking D/ADBMobile: IdentityExtension - Sending request (https://dpm.demdex.net/id?d_mid=59651426340521082405908216148091920022&d_ver=2&d_orgid=7ABB3E6A5A7491460A495D61%40AdobeOrg)
   ```

1. **Risposta dal servizio** identità (filtro Logcat a `IdentityExtension`). Notate come il `mid` valore corrisponde al `d_mid` valore nella richiesta precedente:

   ```java
   03-14 17:01:19.033 7743-7803/com.adobe.busbooking D/ADBMobile: IdentityExtension - Received ID response (mid: 59651426340521082405908216148091920022, blob: j8Odv6LonN4r3an7LhD3WZrU1bUpAkFkkiY1ncBR96t2PTI, hint: 9, ttl: 604800
   ```

["Add Adobe Target VEC Support" (Aggiungi supporto VEC Adobe Target) &gt;](target-vec.md)
