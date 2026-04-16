---
title: Guida all’avvio
description: Per integrare l’applicazione con i flag, dalla richiesta di accesso alla creazione del primo flag di funzione, segui la procedura riportata di seguito.
hide: true
exl-id: 7aa09535-45fa-4ddf-9e3f-a23f8a8ee666
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 1%

---

# Guida all’avvio {#startup-guide}

Per integrare i flag nell’applicazione, segui la procedura riportata di seguito.

## Passaggio 1: richiedere l’accesso {#step-1-access}

Richiedi l’accesso alla console Flag e unisciti al tuo team. Per istruzioni dettagliate, consulta [Richiedi accesso](../console/request-access.md).

## Passaggio 2: integrare l’applicazione {#step-2-onboard}

Dopo aver ottenuto l’accesso, accedi alla console Flag e verifica che l’applicazione sia elencata nel team. In caso contrario, chiedi all’amministratore del team di aggiungerlo. Consulta [Eseguire l&#39;onboarding dell&#39;applicazione](../applications/onboard-your-application.md).

Prima dell’onboarding, prepara quanto segue:

| Requisito | Dettagli |
|---|---|
| **ID applicazione** | Identificatore client univoco utilizzato per la chiamata delle API dei flag. Utilizza l’ID client esistente della tua applicazione, se disponibile. |
| **Client lato server** | Se esegui l’integrazione con un SDK lato server, devi disporre di un ID client amministratore con le autorizzazioni appropriate. |
| **Client desktop** | È possibile utilizzare un codice prodotto e la versione del prodotto al posto di un ID client. |

## Passaggio 3: ottieni le credenziali {#step-3-credentials}

Se esegui l’integrazione tramite un SDK lato server, è necessario un ID client del token di servizio. Per inserire nell&#39;elenco Consentiti l’ID client prima di poter effettuare chiamate API da SDK, contatta il supporto dei flag.

## Passaggio 4: integrare utilizzando un SDK {#step-4-integrate}

Segui i [passaggi di integrazione](integration-steps.md) per il tipo di applicazione. Scegli il percorso adatto al tuo stack:

* **Servizi Web** → Java SDK o Node.js SDK
* **App Web e per dispositivi mobili** → Web SDK o Mobile SDK (disponibile a breve)
* **App desktop** → SDK (disponibile a breve)

## Passaggio 5: creare e verificare il primo flag di funzione {#step-5-feature-flag}

Al termine dell’integrazione, crea il primo flag di funzione nella console e verificalo:

* [Creare il primo flag di funzione](../feature-flags/create-your-first-feature-flag.md)

## Vedi anche {#see-also}

* [Integrare i flag nell’app](integrating-in-your-app.md)
* [Passaggi dell’integrazione](integration-steps.md)
* [SDK](sdks.md)

<!-- -->
