---
title: Panoramica sugli ambienti
description: Scopri gli ambienti di staging e produzione nei Rollout esperienza di Adobe e quando utilizzarli.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 4%

---


# Panoramica sugli ambienti {#environments}

I Rollout esperienza forniscono ambienti separati che consentono di convalidare i flag di funzione prima di promuovere le modifiche per gli utenti live.

## Ambienti disponibili {#available-environments}

| Ambiente | Scopo |
|---|---|
| **Fase** | Test e convalida. Utilizza questo ambiente per configurare e testare i flag di funzione prima di abilitarli in produzione. |
| **Produzione** | Rollout live. I flag di funzioni configurati qui vengono valutati in base alla base di utenti reale. |

>[!IMPORTANT]
>
>Le modifiche apportate in Stage non vengono automaticamente riportate in Production. I flag di funzione e le regole per il pubblico devono essere configurati separatamente in ogni ambiente.

## Selezione di un ambiente {#selecting}

Dopo aver effettuato l’accesso alla console Rollout esperienza, seleziona l’ambiente dallo switcher dell’ambiente nella parte superiore dell’interfaccia. Prima di creare o modificare i flag di feature, accertatevi di lavorare nell&#39;ambiente corretto.

## Best practice {#best-practices}

Segui questi consigli per evitare errori di configurazione e proteggere il pubblico di produzione:

* Crea ed esegui il test dei flag di funzionalità in **Stage**.
* Convalida le regole del pubblico, la percentuale di rollout e la logica di targeting nello stage prima della replica in produzione.
* Utilizza il [flusso di lavoro tra ambienti](../cross-environment/cross-environment-concept.md) per visualizzare e gestire lo stato dei flag tra ambienti diversi.

## Vedi anche {#see-also}

* [Accedi alla console](log-in-to-the-console.md)
* [Associare ambienti a un’applicazione](../cross-environment/associate-environments.md)
* [Visualizzare i flag di funzione in tutti gli ambienti](../cross-environment/view-feature-flags-across-environments.md)
