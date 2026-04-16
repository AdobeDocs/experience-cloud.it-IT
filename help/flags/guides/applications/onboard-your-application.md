---
title: Eseguire l’onboarding dell’applicazione
description: Scopri come integrare una nuova applicazione nei flag per iniziare a creare e gestire i flag di funzioni.
hide: true
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 2%

---

# Eseguire l’onboarding dell’applicazione {#onboard-your-application}

Per aggiungere una nuova applicazione è necessario avere il ruolo **Amministratore**. Contatta l’amministratore se devi verificare o aggiornare il tuo ruolo.

## Aggiungi una nuova applicazione {#add-application}

1. Accedi alla console Flag e passa a **Rollout esperienza > Applicazioni**.

   >[!NOTE]
   >
   >Se il pulsante **Nuova applicazione** non è visibile, verificare di avere il ruolo **Amministratore di Floodgate**.

2. Selezionare **Nuova applicazione**.

3. Seleziona la **piattaforma** che corrisponde al tipo di applicazione (web o mobile).

4. Fornisci le seguenti informazioni:

   | Campo | Descrizione |
   |---|---|
   | **ID applicazione** | Identificatore univoco utilizzato per chiamare i flag dal codice. Utilizza l’ID client dell’applicazione. |
   | **TTL** | Intervallo di polling (in secondi) per l&#39;aggiornamento della cache per applicazione. Si applica solo agli SDK lato server. |

5. Seleziona **Aggiungi**. L’applicazione è ora registrata ed è pronta per la configurazione del flag di funzione.

## Cosa succede dopo {#next-steps}

Dopo aver effettuato l’onboarding dell’applicazione, puoi iniziare a creare i flag di funzione:

* [Creare il primo flag di funzione](../feature-flags/create-your-first-feature-flag.md)
* [Integrare i flag nell’app](../integrate/integrating-in-your-app.md)

## Vedi anche {#see-also}

* [Gestire le applicazioni](manage-applications.md)
* [Accedi alla console](../console/log-in-to-the-console.md)

<!-- -->
