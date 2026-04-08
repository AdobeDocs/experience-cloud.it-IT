---
title: Gruppi di feature per controllare più feature
description: Scopri come i gruppi di funzioni nei Rollout di esperienza consentono di raggruppare e gestire i relativi flag di funzione nelle applicazioni come un’unica unità.
exl-id: dfeb7eff-34f1-4cb5-9c3e-a40d1eda3016
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Gruppi di feature per controllare più feature {#feature-groups}

Un [flag di funzionalità](what-is-a-feature-flag.md) controlla una singola funzionalità. Quando devi gestire insieme più flag di funzionalità correlati e assicurarti che raggiungano lo stesso pubblico, utilizza un **gruppo di funzionalità**.

## Funzionamento di un gruppo di funzioni {#what-it-does}

Un gruppo di funzioni raggruppa più flag di funzioni e consente di applicare una singola regola di pubblico a tutti contemporaneamente. Ciò è utile quando una singola funzionalità rivolta all’utente si estende su più applicazioni o servizi.

Consideriamo ad esempio una funzione di collaborazione che comporta modifiche a livello di applicazione desktop, app mobile e servizio back-end. Creando un gruppo di feature con flag da tutte e tre le applicazioni, potete aprire la feature all&#39;1% degli utenti e assicurarsi che questi vedano un&#39;esperienza coerente su tutte e tre le superfici contemporaneamente.

## Raggruppamento tra applicazioni {#cross-application}

I gruppi di funzioni supportano la gestione delle funzioni tra più applicazioni. È possibile raggruppare i flag correlati in più applicazioni.

