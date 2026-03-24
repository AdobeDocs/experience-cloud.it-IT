---
title: Che cos’è un flag di funzione
description: Scopri cosa sono i flag di funzione e come ti consentono di attivare o disattivare le funzioni dell’applicazione in fase di esecuzione senza ridistribuirle.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Che cos’è un flag di funzione {#what-is-a-feature-flag}

Un flag di funzione è un meccanismo che consente di attivare o disattivare le funzioni dell’applicazione in fase di esecuzione, senza ridistribuire il codice.

I flag di funzionalità disassociano **distribuzione codice** dalla **disponibilità funzionalità**. Puoi inviare il nuovo codice in produzione con la funzione nascosta dietro un flag, quindi accenderlo ogni volta che sei pronto, per tutti gli utenti o per un sottoinsieme target.

Questa separazione riduce significativamente i rischi. Gli sviluppatori possono creare e distribuire continuamente con interruzioni minime, mentre i team di prodotto mantengono il pieno controllo su quando e a chi una funzione diventa visibile.

>[!NOTE]
>
>In Rollout esperienza, un flag di funzione è l’unità di controllo della funzione più atomica. Può essere utilizzato da solo per eseguire il targeting di una singola funzionalità o combinato con altri flag in un [gruppo di funzionalità](feature-groups-to-control-multiple-features.md) o [versione](release-management.md).
