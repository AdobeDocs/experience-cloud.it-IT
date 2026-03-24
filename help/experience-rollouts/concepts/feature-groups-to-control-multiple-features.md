---
title: Gruppi di feature per controllare più feature
description: Scopri come i gruppi di funzioni nei Rollout di esperienza consentono di raggruppare e gestire i relativi flag di funzione nelle applicazioni come un’unica unità.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---


# Gruppi di feature per controllare più feature {#feature-groups}

Un [flag di funzionalità](what-is-a-feature-flag.md) controlla una singola funzionalità. Quando devi gestire insieme più flag di funzionalità correlati e assicurarti che raggiungano lo stesso pubblico, utilizza un **gruppo di funzionalità**.

## Funzionamento di un gruppo di funzioni {#what-it-does}

Un gruppo di funzioni raggruppa più flag di funzioni e consente di applicare una singola regola di pubblico a tutti contemporaneamente. Ciò è utile quando una singola funzionalità rivolta all’utente si estende su più applicazioni o servizi.

Consideriamo ad esempio una funzione di collaborazione che comporta modifiche a livello di applicazione desktop, app mobile e servizio back-end. Creando un gruppo di feature con flag da tutte e tre le applicazioni, potete aprire la feature all&#39;1% degli utenti e assicurarsi che questi vedano un&#39;esperienza coerente su tutte e tre le superfici contemporaneamente.

## Raggruppamento tra applicazioni {#cross-application}

I gruppi di funzioni supportano la gestione delle funzionalità tra più applicazioni purché i flag appartengano allo **stesso team** nei rollout di esperienza. Un team può essere proprietario di più applicazioni, in modo che i flag correlati possano essere raggruppati tra loro.

## Gruppi di funzioni e versioni {#vs-releases}

| | Gruppo di funzioni | Versione |
|---|---|---|
| Portata | All’interno di un singolo team | Tra più team |
| Caso d’uso | Coordinamento dei flag all&#39;interno del team | Coordinamento di lanci con più team di grandi dimensioni |
| Privilegi richiesti | A livello di team | Più alto (Release Manager) |

Se i flag di funzionalità che desideri raggruppare appartengono ad applicazioni di proprietà di team diversi, utilizza una [versione](release-management.md) invece di un gruppo di funzionalità.
