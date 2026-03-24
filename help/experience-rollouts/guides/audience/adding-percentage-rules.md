---
title: Aggiungere regole di percentuale nei criteri di pubblico
description: Scopri come aggiungere regole basate sulla percentuale nei criteri di pubblico in Rollout esperienza di Adobe per eseguire il targeting di percentuali di rollout diverse per segmenti di pubblico diversi.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Aggiungere regole di percentuale nei criteri di pubblico {#adding-percentage-rules}

## Quando utilizzare le regole di percentuale nella scheda Pubblico {#when-to-use}

Il campo **rollout percentuale** nella scheda Dettagli base applica una singola percentuale all&#39;intero pubblico. Ad esempio, il 50% di rollout significa che il 50% di tutti gli utenti che corrispondono ai criteri del pubblico riceve la funzione.

Tuttavia, alcuni scenari di rollout richiedono percentuali diverse per gruppi diversi, ad esempio:

* 100% degli utenti del Regno Unito e 50% degli utenti degli Stati Uniti
* Tutti gli utenti da un elenco e-mail importato più il 50% degli utenti da un paese specifico

In questi casi, utilizza la regola **Percentuale** nella sezione del profilo della scheda **Pubblico**, in combinazione con la logica nidificata.

>[!TIP]
>
>Se desideri applicare una singola percentuale all&#39;intero pubblico, ad esempio il 10% degli utenti in (Stati Uniti e Regno Unito), utilizza invece il rollout **percentuale** nella scheda Dettagli di base.

## Come aggiungere una regola percentuale {#how-to-add}

L&#39;opzione **Percentuale** è disponibile come regola nella sezione Profilo della scheda Pubblico.

1. Vai alla scheda **Pubblico** del tuo flag di funzione o gruppo di funzioni.
2. In **Profilo**, aggiungi una regola di **Percentuale** e imposta il valore desiderato.
3. Aggiungi tutte le altre condizioni di pubblico necessarie (ad esempio, una regola Country).

## Combinazione di regole percentuali con logica nidificata {#nested-logic}

Per applicare percentuali diverse a segmenti diversi, utilizza **logica nidificata** per combinare le condizioni:

1. Abilita **Logica annidata** nella sezione Regole pubblico.
2. A ogni condizione viene assegnato automaticamente un numero.
3. Immettere un&#39;espressione logica che faccia riferimento a tali numeri.

Utilizza una delle seguenti espressioni per descrivere la relazione tra le condizioni:

* `1 and (2 or 3)` — condizione 1 E (condizione 2 O condizione 3)
* `(1 and 2) or 3` — (condizione 1 E condizione 2) O condizione 3
* `(1 and 2) or (3 and 4)` — due gruppi indipendenti

## Esempi {#examples}

**Esempio 1: tutti gli utenti da un elenco importato e il 10% degli utenti da un paese specifico**

Aggiungi due regole: una per l’elenco utenti importato e una regola Percentuale (10%) combinata con una regola Paese. Usa logica nidificata: `1 or (2 and 3)`.

**Esempio 2: il 10% degli utenti statunitensi e il 20% degli utenti britannici**

Aggiungi quattro regole: Paese = Stati Uniti, Percentuale = 10%, Paese = Regno Unito, Percentuale = 20%. Usa logica nidificata: `(1 and 2) or (3 and 4)`.

## Vedi anche {#see-also}

* [Pubblico nei flag di funzione e nei gruppi di funzioni](audience-in-feature-flags-and-feature-groups.md)
* [Regole di pubblico complesse](complex-rules.md)
* [Impostare una funzione per il rollout graduale](../feature-flags/set-feature-gradual-rollout.md)
