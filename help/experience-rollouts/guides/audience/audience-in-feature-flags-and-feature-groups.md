---
title: Pubblico nei flag di funzione e nei gruppi di funzioni
description: Scopri come definire i criteri di pubblico per i flag di funzione e i gruppi di funzioni nei Rollout di esperienza di Adobe utilizzando gli attributi di profilo, i segmenti e il calcolatore del pubblico.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Pubblico nei flag di funzione e nei gruppi di funzioni {#audience-overview}

I Rollout esperienza forniscono un targeting avanzato del pubblico per i flag di funzione e i gruppi di funzioni. Puoi combinare attributi di profilo, variabili di contesto e segmenti di pubblico per controllare con precisione quali utenti ricevono una funzione.

## Regole del profilo {#profile-rules}

Le regole di profilo consentono di eseguire il targeting degli utenti in base ad attributi quali paese, dominio e-mail, tipo di account, ID utente e altro ancora. Puoi combinare più attributi utilizzando gli operatori AND/OR e creare una logica nidificata per scenari di targeting complessi.

Per aggiungere le regole di profilo, vai alla scheda **Pubblico** di un flag di funzionalità o di un gruppo di funzionalità e aggiungi le condizioni in **Profilo**.

Puoi salvare un set di regole per il pubblico come **Pubblico** riutilizzabile da utilizzare in più flag e gruppi.

Per il targeting basato sul contesto (ad esempio, il targeting in base al linguaggio attivo dell&#39;utente o al tipo di client), vedi [Usa contesto nelle regole per il pubblico](using-context-in-audience-rules.md).

## Segmenti {#segments}

I flag di funzione e i gruppi di funzioni supportano i segmenti di pubblico. I segmenti ti consentono di:

* Utilizzare una singola definizione di pubblico predefinita per più flag e gruppi di funzioni
* Includi **criteri basati su eventi** nel targeting del pubblico, operazione impossibile con le sole regole di profilo

Per utilizzare un segmento, vai alla scheda **Pubblico** e seleziona uno o più segmenti dall&#39;elenco. Puoi combinare più segmenti utilizzando gli operatori AND/OR e aggiungere insieme a essi ulteriori filtri di profilo o di contesto.

>[!NOTE]
>
>Per creare segmenti di pubblico è necessario il ruolo **Gestione test** o superiore.

## Calcolatore del pubblico {#audience-calculator}

Dopo aver definito i criteri di pubblico, seleziona **Calcola** nella barra inferiore per ottenere un conteggio stimato degli utenti idonei. Questo consente di convalidare la portata del targeting prima di attivare la funzione.

>[!NOTE]
>
>Il calcolatore del pubblico non restituisce un valore quando le variabili di contesto sono incluse nei criteri, perché i valori di contesto sono determinati in fase di esecuzione e non possono essere previsti in anticipo.

## Vedi anche {#see-also}

* [Usa contesto nelle regole del pubblico](using-context-in-audience-rules.md)
* [Aggiungere regole di percentuale nei criteri di pubblico](adding-percentage-rules.md)
* [Regole di pubblico complesse](complex-rules.md)
* [Creare il primo flag di funzione](../feature-flags/create-your-first-feature-flag.md)
