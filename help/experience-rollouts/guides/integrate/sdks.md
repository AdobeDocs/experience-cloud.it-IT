---
title: SDK
description: Scopri l’architettura di SDK in Adobe Experience Rollouts e l’estensione per SDK mobile disponibile per Android.
hide: true
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# SDK {#sdks}

Experience Rollouts fornisce SDK per l’integrazione di flag di funzioni nelle applicazioni. Questa pagina descrive l’architettura di SDK e le opzioni disponibili.

## Architettura SDK {#architecture}

Tutti gli SDK di Rollout esperienza condividono la stessa architettura di base:

* **Inizializzazione** — SDK è configurato all&#39;avvio e si registra con il servizio Rollout esperienza.
* **Recupero funzionalità**: SDK recupera i dati dei flag di funzionalità e valuta i flag localmente.
* **Memorizzazione in cache**: SDK memorizza nella cache i dati dei flag di funzionalità e li aggiorna in base a un intervallo di polling configurabile (TTL).
* **Gestione errori** - Se il servizio non è disponibile, SDK continua a fornire valutazioni dei flag di funzionalità dalla cache locale.

## SDK disponibili {#available-sdks}

### Estensione Android {#android-extension}

L’estensione Experience Rollout per Android si integra con Adobe Experience Platform Mobile SDK.

Per istruzioni sulla configurazione, consulta la [Guida all&#39;integrazione dell&#39;estensione Android](../sdk-releases/android/android-extension-integration-guide.md).

>[!NOTE]
>
>Ulteriori opzioni SDK per il web e altre piattaforme mobili sono in preparazione e saranno presto disponibili. Contatta il tuo rappresentante Adobe per ricevere assistenza all’accesso anticipato.

## Vedi anche {#see-also}

* [guida all’integrazione delle estensioni Android](../sdk-releases/android/android-extension-integration-guide.md)
* [Servizi web](web-services.md)
* [Passaggi dell’integrazione](integration-steps.md)

<!-- -->
