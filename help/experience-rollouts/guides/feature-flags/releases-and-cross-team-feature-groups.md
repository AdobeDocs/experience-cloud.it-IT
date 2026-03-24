---
title: Versioni e gruppi di funzioni cross-team
description: Scopri la differenza tra le versioni e i gruppi di funzioni cross-team nei Rollout esperienza di Adobe e quando utilizzarli per rollout coordinati di più team.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---


# Versioni e gruppi di funzioni cross-team {#releases-and-cross-team}

Entrambe le versioni e i gruppi di funzioni cross-team supportano rollout coordinati tra più team e applicazioni. La scelta giusta dipende dai requisiti di caching, dalle esigenze di targeting del pubblico e dal livello di controllo che desideri sul processo.

## Gruppi di funzioni cross-team {#cross-team-feature-groups}

Un gruppo di funzioni cross-team consente di raggruppare i flag di funzioni di applicazioni di proprietà di team diversi e gestirli in base a criteri di pubblico avanzati.

Caratteristiche principali:

* **Self-service**: nessuna richiesta di supporto necessaria per crearne una
* **Destinazione di tipi di pubblico avanzati**: supporta l&#39;insieme completo di criteri di pubblico (attributi di profilo, variabili di contesto, rollout percentuale)
* **Nessun limite** sul numero che puoi creare
* **Nessun caching** - Le valutazioni dei flag di funzionalità richiedono una chiamata API; il caching a livello di SDK non è supportato

Per istruzioni dettagliate sulla creazione, consulta [Creare un gruppo di funzioni per più team](create-cross-team-feature-group.md).

## Versioni {#releases}

Una versione è progettata per lanci coordinati di grandi dimensioni in cui è richiesto il caching a livello di SDK. Le versioni utilizzano il targeting del pubblico basato su token di autenticazione.

Caratteristiche principali:

* **Richiede una richiesta di supporto** — Le versioni non sono completamente self-service; contatta il supporto dei rollout di esperienza per crearne una
* **Memorizzazione in cache di SDK** - Tutti i dati di versione vengono memorizzati nella cache locale nel SDK del server, riducendo le chiamate API
* **Criteri di pubblico limitati** — Le regole del pubblico si basano su token di autenticazione (paese, e-mail, ID utente, percentuale, ecc.)
* **Rilasci attivi limitati**: è possibile che esista un numero finito di rilasci attivi alla volta; è possibile pianificare la chiusura o la previsione dei rilasci entro tre mesi

## Confronto {#comparison}

| | Gruppo di funzioni cross-team | Versione |
|---|---|---|
| Self-service | ✓ | Richiede una richiesta di supporto |
| Criteri per un pubblico ricco | ✓ | Limitato |
| Test A/B | ✗ | ✗ |
| Memorizzazione in cache di SDK | ✗ | ✓ |
| Limite attivo | Nessun limite | Limitato |

## Consiglio {#recommendation}

Se il tuo caso d&#39;uso prevede un targeting di pubblico avanzato e la gestione self-service, utilizza un **gruppo di funzioni cross-team**. Se i servizi di back-end richiedono il caching a livello di SDK e sono sufficienti i criteri di pubblico più semplici per le versioni, utilizza una **versione**.

## Vedi anche {#see-also}

* [Funzioni, gruppi di funzioni e versioni](features-feature-groups-releases.md)
* [Creare un gruppo di funzioni cross-team](create-cross-team-feature-group.md)
* [Richiedi rilascio](request-a-release.md)
