---
title: Applicazioni desktop
description: Scopri come integrare i rollout di esperienza di Adobe in un’applicazione desktop utilizzando la funzione API V2.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 1%

---


# Applicazioni desktop {#desktop-applications}

Le applicazioni desktop si integrano con i rollout di esperienza effettuando chiamate API REST dirette. Utilizza l&#39;API **Feature V2** per i client desktop.

Consulta **API di funzionalità GET V2** nella sezione API di funzionalità di questa guida per il riferimento API completo.

## Requisiti di integrazione {#requirements}

I client desktop devono:

* **Rispetta il valore TTL** restituito nella risposta API. Il TTL definisce per quanto tempo il client deve memorizzare in cache i dati dei flag di funzione prima di richiamare nuovamente l’API. Implementa un test case che convalida questo comportamento per garantire che le versioni precedenti dell’applicazione entrino correttamente in modalità di sospensione quando non vengono forniti flag di funzione.
* **Gestione corretta degli scenari di errore HTTP**. Crea un set di funzioni di fallback in modo che l’applicazione rimanga funzionante se l’API non è temporaneamente disponibile.
* **Gestisci un piano di test dell&#39;integrazione dettagliato** che copra sia i requisiti di TTL che quelli per la gestione degli errori di cui sopra.

## ID applicazione {#app-id}

I client desktop possono utilizzare **codice prodotto e versione prodotto** come identificatore dell&#39;applicazione quando chiamano l&#39;API, invece di un ID client standard.

## Vedi anche {#see-also}

* [Passaggi dell’integrazione](integration-steps.md)
* [Guida all’avvio](startup-guide.md)
