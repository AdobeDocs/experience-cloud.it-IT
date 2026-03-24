---
title: Iscriviti all’applicazione API in Adobe Developer Console
description: Scopri come abbonare l’applicazione all’API di Rollout esperienza tramite Adobe Developer Console in modo da poter chiamare gli endpoint dei flag di funzione.
source-git-commit: 120a2ea34682c878aaf6f6cb75504a8704d10e3d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 3%

---


# Iscriviti all’applicazione API in Adobe Developer Console {#subscribe-to-api}

Per richiamare l&#39;API Experience Rollouts dalla tua applicazione, devi abbonarti tramite [Adobe Developer Console](https://developer.adobe.com/console). In questo modo, all’applicazione viene assegnato un ID client che Experience Rollout utilizza per identificare il chiamante.

## Prerequisiti {#prerequisites}

Prima di iscriverti, conferma quanto segue:

* L&#39;applicazione è stata integrata nella console Rollout esperienza. Consulta [Eseguire l&#39;onboarding dell&#39;applicazione](../applications/onboard-your-application.md)
* Accesso a Adobe Developer Console per la tua organizzazione

## Iscriviti all’API Rollout di esperienza {#subscribe}

Per abbonare l’applicazione all’API dei rollout di esperienza, effettua le seguenti operazioni:

1. Vai a [Adobe Developer Console](https://developer.adobe.com/console) e accedi con le credenziali della tua organizzazione.
2. Seleziona il progetto o creane uno nuovo.
3. Selezionare **Aggiungi API**.
4. Cerca e seleziona **API rollout esperienza**.
5. Segui le istruzioni per configurare l’API e generare le credenziali.
6. Tieni presente l&#39;**ID client** generato per il progetto. Questo è l’identificatore utilizzato quando chiami l’API dei rollout di esperienza e quando esegui l’onboarding dell’applicazione nella console dei rollout di esperienza.

## Integrazioni SDK lato server {#server-sdk}

Se esegui l&#39;integrazione utilizzando Java SDK o Node.js SDK, oltre a una chiave API è necessario un ID client **service token**. Il token di servizio consente a SDK di chiamare le API di Rollout esperienza in background.

>[!NOTE]
>
>Gli ID client SDK lato server devono essere inseriti nell&#39;elenco Consentiti dal supporto dei rollout di esperienza prima di poter effettuare chiamate API. Contatta il supporto dopo aver completato la configurazione di Developer Console.

## Vedi anche {#see-also}

* [Guida all’avvio](startup-guide.md)
* [SDK](sdks.md)
* [Eseguire l’onboarding dell’applicazione](../applications/onboard-your-application.md)
* [Passaggi dell’integrazione](integration-steps.md)
