---
title: Benchmark SDK
description: Rivedi i risultati del benchmarking Java SDK per i rollout di esperienza Adobe, incluse le misurazioni dei tempi di risposta tra diversi numeri di flag di funzioni in condizioni di carico tipiche.
source-git-commit: 8b8b5db1a28af3a3ac29aecf26482f70eb84c714
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 7%

---


# Benchmark SDK {#sdk-benchmarking}

Il benchmark Experience Rollouts Java SDK fornisce ai team di integrazione una stima affidabile delle risorse e dei tempi di risposta previsti quando SDK viene eseguito all’interno della propria infrastruttura.

## Ambiente di test {#test-environment}

Il benchmarking è stato eseguito su un&#39;applicazione Spring Boot con la seguente configurazione fissa:

* **Core CPU:** 8
* **Memoria JVM:** 4096 MB

## Presupposti del test {#test-assumptions}

Le seguenti condizioni sono state mantenute costanti in tutte le esecuzioni di benchmark:

* Flag di funzioni testati: da 8 a 128
* Variabili di contesto per flag di funzione: 2 (tipo `STRING`, lunghezza 36 caratteri)
* Carico medio: 15.000 richieste al minuto (RPM)
* Thread attivi: 100

## Risultati {#results}

La tabella seguente mostra il tempo di risposta del 99,99° percentile per le chiamate `getFeatures()` con l&#39;aumento del numero di flag di funzione:

| Numero di flag di funzione | Variabili di contesto per flag | Tempo di risposta (ms, p99.99) |
|---|---|---|
| 8 | 2 | &lt; 0.5 |
| 16 | 2 | &lt; 0.5 |
| 32 | 2 | &lt; 0.5 |
| 64 | 2 | &lt; 1 |
| 128 | 2 | &lt; 1 |

## Interpretazione dei risultati {#interpretation}

I parametri di riferimento di cui sopra rappresentano le prestazioni nelle condizioni di prova specifiche descritte. Poiché SDK viene eseguito all&#39;interno dell&#39;infrastruttura dell&#39;applicazione, i tempi di risposta effettivi variano in base a fattori specifici dell&#39;ambiente:

* CPU disponibile e numero di core
* Dimensione heap JVM e comportamento di Garbage Collection
* Disponibilità del thread e cambio di contesto
* Carico di sistema corrente al momento della richiesta

Utilizza questi dati come base di pianificazione anziché come obiettivi prestazionali garantiti per l’ambiente di produzione.

## Vedi anche {#see-also}

* [Guida all’integrazione di Java SDK](java/java-sdk-integration-guide.md)
* [Note sulla versione di Java SDK](java/java-sdk-release-notes.md)
* [SDK](../integrate/sdks.md)
