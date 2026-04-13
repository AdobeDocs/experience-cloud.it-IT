---
title: Funzioni e gruppi di funzioni
description: Scopri le differenze tra i flag di funzione e i gruppi di funzioni nei Rollout esperienza di Adobe e quando utilizzarli.
hide: true
exl-id: 852aa777-6f8a-47c9-bf54-e645a5ee2f3e
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 4%

---

# Funzioni e gruppi di funzioni {#features-feature-groups}

In Rollout esperienza sono disponibili due artefatti per la gestione dei rollout di funzioni. La scelta di quella giusta dipende dall’ambito del rollout e dal numero di funzioni coinvolte.

## I due artefatti {#artifacts}

**Flag di funzionalità**
L&#39;unità più atomica. Controlla una singola funzionalità per una singola applicazione. Può essere abilitato o disabilitato per un pubblico definito.

**Gruppo di caratteristiche**
Raccolta di flag di funzionalità appartenenti allo stesso team. Consente di gestire più flag in più applicazioni come singola unità.

## Confronto {#comparison}

| | Flag di funzione | Gruppo di funzioni |
|---|---|---|
| **Ruolo richiesto per gestire il pubblico** | Proprietario rilascio prodotto | Proprietario rilascio prodotto |
| **Applicazioni** | Singolo | Più (stesso team) |
| **Criteri di pubblico avanzati** | ✓ | ✓ |
| **Rollout percentuale** | Combinato con qualsiasi criterio di pubblico | Combinato con qualsiasi criterio di pubblico |
| **Test A/B** | ✓ | ✓ |
| **Self-service** | ✓ | ✓ |
| **Audit trail** | ✓ | ✓ |

## Quando utilizzarli {#when-to-use}

| Scenario | Utilizzo di |
|---|---|
| Test o rollout di una singola funzione per un&#39;applicazione | **Flag di funzionalità** |
| Coordinamento di più funzionalità nello stesso team, pubblicazione simultanea | **Gruppo di caratteristiche** |

## Vedi anche {#see-also}

* [Creare il primo flag di funzione](create-your-first-feature-flag.md)
* [Creare un gruppo di funzioni](create-a-feature-group.md)

<!-- -->
