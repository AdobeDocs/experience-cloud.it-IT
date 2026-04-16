---
title: SDK
description: Scopri l’architettura di SDK in Flags e le estensioni disponibili per AEP Web SDK e AEP Mobile SDK.
hide: true
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 4%

---

# SDK {#sdks}

Flag fornisce SDK per l’integrazione di flag di funzione nelle applicazioni. I flag vengono distribuiti tramite AEP Web SDK e AEP Mobile SDK.

## Architettura SDK {#architecture}

Tutti gli SDK dei flag condividono la stessa architettura di base:

* **Inizializzazione** - SDK è configurato all&#39;avvio e si registra con il servizio Flags.
* **Recupero funzionalità**: SDK recupera i dati dei flag di funzionalità e valuta i flag localmente.
* **Memorizzazione in cache**: SDK memorizza nella cache i dati dei flag di funzionalità e li aggiorna in base a un intervallo di polling configurabile (TTL).
* **Gestione errori** - Se il servizio non è disponibile, SDK continua a fornire valutazioni dei flag di funzionalità dalla cache locale.

## SDK disponibili {#available-sdks}

### AEP Web SDK {#web-sdk}

L’estensione Flags per web si integra con Adobe Experience Platform Web SDK, consentendo la valutazione dei flag nelle applicazioni web.

### Estensione Android {#android-extension}

L&#39;estensione Flags per Android si integra con Adobe Experience Platform Mobile SDK.

Per istruzioni sulla configurazione, consulta la [Guida all&#39;integrazione dell&#39;estensione Android](../sdk-releases/android/android-extension-integration-guide.md).

### Estensione iOS {#ios-extension}

L&#39;estensione Flags per iOS si integra con Adobe Experience Platform Mobile SDK.

Per istruzioni sulla configurazione, consulta la [Guida all&#39;integrazione dell&#39;estensione iOS](../sdk-releases/ios/ios-extension-integration-guide.md).

## Vedi anche {#see-also}

* [guida all’integrazione delle estensioni Android](../sdk-releases/android/android-extension-integration-guide.md)
* [Servizi web](web-services.md)
* [Passaggi dell’integrazione](integration-steps.md)

<!-- -->
