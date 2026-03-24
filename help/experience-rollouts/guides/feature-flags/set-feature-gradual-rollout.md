---
title: Impostare una funzione per il rollout graduale
description: Scopri come configurare un rollout graduale basato su percentuali per un flag di funzione nei Rollout di esperienza di Adobe.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 3%

---


# Impostare una funzione per il rollout graduale {#gradual-rollout-feature}

Il rollout percentuale per un flag di funzionalità è configurato nella scheda **Dettagli di base**. Puoi regolare questo valore verso l’alto o verso il basso in qualsiasi momento con l’avanzare del rollout.

## Come funziona {#how-it-works}

Quando imposti un rollout percentuale (ad esempio, 25%), tale percentuale del pubblico definito viene esposta alla funzione. La percentuale rimanente viene inserita nel **gruppo di controllo**, che riceve l&#39;esperienza predefinita.

Puoi aumentare o diminuire la percentuale nel tempo per espandere o contrarre il rollout. Se si riduce la percentuale allo 0%, la funzione viene disattivata per tutti gli utenti del pubblico senza eliminare il flag.

## Vedi anche {#see-also}

* [Rollout graduale](../../concepts/gradual-rollout.md)
* [Impostare un gruppo di funzioni per il rollout graduale](set-feature-group-gradual-rollout.md)
* [Creare il primo flag di funzione](create-your-first-feature-flag.md)
