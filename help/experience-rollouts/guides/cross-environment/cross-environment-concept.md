---
title: Concetto di ambienti diversi
description: Scopri in che modo le funzionalità tra più ambienti nei Rollout di esperienza di Adobe consentono di collegare le applicazioni tra più ambienti e gestire i flag di funzionalità in modo coerente dallo sviluppo alla produzione.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Concetto di ambienti diversi {#cross-environment-concept}

Le funzionalità tra più ambienti consentono di collegare le istanze dell’applicazione tra diversi ambienti di distribuzione, ad esempio QA, Stage e Produzione, e di gestire i flag di funzione in modo coerente tra tutti, dall’interno dei Rollout di esperienza.

## Il problema è risolto in ambienti diversi {#problem}

Senza collegamenti tra ambienti, ogni istanza dell’applicazione in Experience Rollout è completamente indipendente dalle controparti in altri ambienti. Questo crea diversi punti di attrito:

* Un&#39;applicazione con nome `my-app` in Stage non ha alcuna relazione con `my-app` in Produzione. Vengono trattate come applicazioni separate e non correlate.
* Non è possibile visualizzare lo stato di un flag di funzione nello stage mentre si lavora in produzione. Per confrontare gli stati dei flag è necessario cambiare gli ambienti manualmente.
* L&#39;importazione di una configurazione di flag di funzione da un ambiente inferiore a uno superiore richiede la ricreazione manuale.

## Funzionamento di più ambienti {#what-it-enables}

Collegando le istanze dell’applicazione in ambienti diversi, il team può:

* Definire quale degli ambienti di distribuzione dell’applicazione corrisponde a quale ambiente di Rollout esperienza
* Utilizza etichette di ambiente personalizzate (ad esempio `Dev`, `Staging`, `Prod`) che corrispondono alle convenzioni di denominazione del tuo team
* Visualizzare lo stato di un flag di funzione in tutti gli ambienti collegati da un’unica vista
* Importare i flag di funzionalità da un ambiente inferiore a uno superiore con pochi clic, senza ricrearli manualmente

## Struttura degli ambienti {#environment-structure}

I rollout di esperienza hanno due ambienti di piattaforma: **Stage** e **Produzione**. L’applicazione, tuttavia, potrebbe avere più ambienti, ad esempio QA, Staging e Produzione. Il collegamento tra più ambienti consente di decidere dove si trova ciascun ambiente dell’applicazione:

* Gli ambienti di controllo qualità e di staging possono essere ospitati nell’ambiente Experience Rollout Stage o nell’ambiente di produzione.
* Gli ambienti di produzione devono essere ospitati nell’ambiente di produzione dei rollout di esperienza.

Questa flessibilità consente di non dover eseguire una mappatura unica.

## Passaggi successivi {#next-steps}

* [Associa ambienti a un&#39;applicazione](associate-environments.md): impostare i collegamenti tra le istanze dell&#39;applicazione
* [Visualizza flag di funzionalità in ambienti diversi](view-feature-flags-across-environments.md): controlla lo stato dei flag in tutti gli ambienti collegati
* [Importa flag di funzionalità](import-feature-flags.md) — Promuovi flag di funzionalità da ambienti inferiori a superiori
