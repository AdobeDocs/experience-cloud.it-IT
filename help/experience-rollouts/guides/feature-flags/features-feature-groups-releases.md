---
title: Funzioni, gruppi di funzioni e versioni
description: Scopri le differenze tra i flag di funzioni, i gruppi di funzioni, i gruppi di funzioni cross-team e le versioni nei Rollout esperienza di Adobe e quando utilizzarli.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 2%

---


# Funzioni, gruppi di funzioni e versioni {#features-feature-groups-releases}

In Rollout esperienza sono disponibili quattro artefatti per la gestione dei rollout di funzioni. La scelta di quella giusta dipende dall’ambito del rollout, dal numero di team coinvolti e dalle funzionalità di targeting del pubblico necessarie.

## I quattro artefatti {#artifacts}

**Flag di funzionalità**
L&#39;unità più atomica. Controlla una singola funzionalità per una singola applicazione, di proprietà di un unico team. Può essere abilitato o disabilitato per un pubblico definito.

**Gruppo di caratteristiche**
Raccolta di flag di funzionalità appartenenti allo stesso team. Consente di gestire più flag in più applicazioni in un unico team come singola unità.

**Gruppo di caratteristiche cross-team**
Estende le funzionalità dei gruppi di funzioni a più team e applicazioni. È self-service e supporta criteri di pubblico avanzati, ma non supporta la memorizzazione in cache.

**Versione**
Progettato per rollout di grandi dimensioni e coordinati tra più team e applicazioni. Utilizza il targeting del pubblico basato su token di autenticazione. Supporta il caching sul SDK del server.

## Confronto {#comparison}

| | Flag di funzione | Gruppo di funzioni | Gruppo di funzioni cross-team | Versione |
|---|---|---|---|---|
| **Ruolo richiesto per gestire il pubblico** | Proprietario rilascio prodotto | Proprietario rilascio prodotto | Amministratore funzionalità | Release Manager |
| **Applicazioni** | Singolo | Più (stesso team) | Più (cross-team) | Più (cross-team) |
| **Team** | Singolo | Singolo | Cross-team | Cross-team |
| **Criteri di pubblico avanzati** | ✓ | ✓ | ✓ | Limitato |
| **Rollout percentuale** | Combinato con qualsiasi criterio di pubblico | Combinato con qualsiasi criterio di pubblico | Combinato con qualsiasi criterio di pubblico | Combinato con criteri di pubblico fissi |
| **Test A/B** | ✓ | ✓ | ✗ | ✗ |
| **Memorizzazione in cache nel server SDK** | Solo flag di attivazione/disattivazione predefiniti | Nessun caching | Nessun caching | Tutte le versioni memorizzate nella cache locale |
| **Self-service** | ✓ | ✓ | ✓ | Richiede una richiesta di supporto |
| **Audit trail** | ✓ | ✓ | ✓ | ✓ |

## Quando utilizzarli {#when-to-use}

| Scenario | Utilizzo di |
|---|---|
| Test o rollout di una singola funzione per un&#39;applicazione | **Flag di funzionalità** |
| Coordinamento di più funzionalità nello stesso team, pubblicazione simultanea | **Gruppo di caratteristiche** |
| Coordinamento delle funzioni tra le applicazioni in diversi team, con targeting avanzato | **Gruppo di caratteristiche cross-team** |
| Rilascio coordinato su più team, con caching a livello di SDK | **Versione** |

## Vedi anche {#see-also}

* [Creare il primo flag di funzione](create-your-first-feature-flag.md)
* [Creare un gruppo di funzioni](create-a-feature-group.md)
* [Creare un gruppo di funzioni cross-team](create-cross-team-feature-group.md)
* [Versioni e gruppi di funzioni cross-team](releases-and-cross-team-feature-groups.md)
