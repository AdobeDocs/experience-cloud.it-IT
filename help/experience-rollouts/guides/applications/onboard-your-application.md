---
title: Eseguire l’onboarding dell’applicazione
description: Scopri come integrare una nuova applicazione nei Rollout esperienza di Adobe in modo che il team possa iniziare a creare e gestire i flag di funzione.
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---

# Eseguire l’onboarding dell’applicazione {#onboard-your-application}

Per aggiungere una nuova applicazione è necessario avere il ruolo **Amministratore**. Se devi verificare o aggiornare il tuo ruolo, contatta l’amministratore del team.

## Aggiungi una nuova applicazione {#add-application}

1. Accedi alla console Rollout esperienza e passa a **Amministratore > Applicazioni**.

   >[!NOTE]
   >
   >Se il pulsante **Nuova applicazione** non è visibile, verificare di essere nel team corretto e di disporre della mansione **Amministratore**.

2. Selezionare **Nuova applicazione**.

3. Seleziona il **canale** che corrisponde al tipo di applicazione (Web, mobile, desktop o servizio).

4. Fornisci le seguenti informazioni:

   | Campo | Descrizione |
   |---|---|
   | **ID applicazione** | Identificatore univoco utilizzato per chiamare i rollout di esperienza dal codice. Utilizza l’ID client dell’applicazione. |
   | **TTL** | Intervallo di polling (in secondi) per l&#39;aggiornamento della cache per applicazione. Si applica solo agli SDK lato server. |
   | **Team** | Il team che sarà proprietario e gestirà l&#39;applicazione. Solo i membri di questo team possono creare e modificare i flag di funzionalità. |

5. Seleziona **Aggiungi**. L’applicazione è ora registrata ed è pronta per la configurazione del flag di funzione.

## Cosa succede dopo {#next-steps}

Una volta che l’applicazione è stata integrata, il team può iniziare a creare i flag di funzionalità:

* [Creare il primo flag di funzione](../feature-flags/create-your-first-feature-flag.md)
* [Integrare i rollout di esperienza nell’app](../integrate/integrating-in-your-app.md)

## Vedi anche {#see-also}

* [Gestire le applicazioni](manage-applications.md)
* [Accedi alla console](../console/log-in-to-the-console.md)
