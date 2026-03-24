---
title: Panoramica delle API di gestione delle funzioni
description: Panoramica delle API di gestione dei rollout di esperienza, che consentono di creare, leggere, aggiornare ed eliminare i flag di funzione, i gruppi di funzioni e le versioni a livello di programmazione.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Panoramica delle API di gestione delle funzioni {#feature-management-apis-overview}

Le API di gestione dei rollout di esperienza consentono di gestire i flag di funzione, i gruppi di funzioni e le versioni a livello di programmazione. I team che devono automatizzare i flussi di lavoro o integrare i rollout di esperienza nelle pipeline di distribuzione esistenti possono utilizzare queste API invece della console.

>[!NOTE]
>
>L’accesso alle API di gestione tramite un token di servizio viene concesso su richiesta. Contatta il supporto dei Rollout esperienza e fornisci una giustificazione aziendale per richiedere l’accesso.

## API di gestione disponibili {#available-apis}

Sono disponibili le seguenti API di gestione:

* [API per la gestione dei flag di funzionalità](feature-flags-management-api.md): creazione, lettura, aggiornamento ed eliminazione dei flag di funzionalità per un&#39;applicazione.
* [API per la gestione dei gruppi di funzioni](feature-group-management-api.md): crea, leggi, aggiorna, elimina e controlla i piani di rollout automatizzati per i gruppi di funzioni.
* [API per la gestione delle versioni](release-management-apis.md) — Crea e modifica gruppi di funzioni e versioni cross-team.

## Requisiti comuni {#common-requirements}

Tutte le chiamate API di gestione richiedono quanto segue:

* Una **chiave API** di Adobe Developer Console — vedere [Sottoscrivi l&#39;applicazione API](../guides/integrate/subscribe-to-api-application.md).
* Token di accesso utente **IMS** o **token di servizio**, passato come `Bearer <token>` nell&#39;intestazione `Authorization`.
* Un&#39;intestazione `Content-Type: application/json`.

Il provisioning di chiavi e token API deve essere eseguito separatamente per gli ambienti di staging e produzione.

## Guide di supporto {#helper-guides}

Le seguenti guide aiutano a creare i payload API corretti:

* [Ottieni ID client per un&#39;applicazione](get-client-id.md): cerca l&#39;ID client numerico richiesto dai flag di funzionalità e dalle API di gestione dei gruppi di funzionalità.
* [Ottieni i criteri di pubblico desiderati](get-audience-criteria.md). Utilizza la console e l&#39;API GET per generare la struttura JSON corretta per i criteri di pubblico.
* [API della patch di gestione](management-patch-api.md): aggiorna singoli campi di un flag di funzionalità, di un gruppo di funzionalità o di un gruppo di funzionalità con più team senza passare l&#39;oggetto completo.

## Vedi anche {#see-also}

* [API per funzioni GET V3](../feature-api/get-feature-api-v3.md)
* [API per funzioni GET V2](../feature-api/get-feature-api-v2.md)
* [Iscriviti all’applicazione API](../guides/integrate/subscribe-to-api-application.md)
