---
title: Usa contesto nelle regole del pubblico
description: Scopri come utilizzare le variabili di contesto nelle regole del pubblico per i flag di funzione e i gruppi di funzioni nei Rollout di esperienza di Adobe.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Usa contesto nelle regole del pubblico {#context-in-audience-rules}

Le variabili di contesto sono valori forniti dall’applicazione client in fase di esecuzione. Consentono di eseguire il targeting degli utenti in base a informazioni dinamiche a livello di sessione, come il linguaggio attivo dell’utente, il tipo di dispositivo o lo stato dell’applicazione, criteri che non fanno parte del profilo persistente dell’utente.

Le variabili di contesto sono rilevanti per i client web, desktop e mobili.

## Funzionamento delle variabili di contesto {#how-context-works}

L’applicazione trasmette le variabili di contesto ai Rollout esperienza durante la valutazione di un flag di funzione. Nella console puoi definire le regole che controllano questi valori, che verranno utilizzate dalla piattaforma al momento della valutazione per determinare se l’utente è idoneo.

Se definisci le condizioni nelle sezioni **Profilo** e **Contesto** delle regole del pubblico, tutte le condizioni del profilo vengono combinate con tutte le condizioni di contesto utilizzando la logica AND.

## Tipi di variabili di contesto {#variable-types}

### Tipo predefinito (elenco) {#predefined-type}

Variabile di contesto con un set fisso di valori consentiti, ad esempio un elenco di lingue o paesi.

Operatori disponibili: **Is**, **Is not equal to**, **Exists**, **In**

### Tipo intero {#integer-type}

Variabile di contesto contenente un valore numerico.

Operatori disponibili: **maggiore di**, **maggiore o uguale a**, **uguale a**, **minore di**, **minore o uguale a**

### Tipo di stringa {#string-type}

Variabile di contesto contenente un valore di testo in formato libero.

Operatori disponibili: **Is**, **Is not equal to**

## Aggiunta di una variabile di contesto {#adding-context-variable}

Per aggiungere una variabile di contesto a una regola di pubblico:

1. Apri il flag di funzione o il gruppo di funzioni nella console.
2. Passa alla scheda **Pubblico**.
3. In **Contesto**, aggiungi una nuova condizione.
4. Seleziona la variabile di contesto, l’operatore e il valore.

Se la variabile di contesto necessaria non viene visualizzata nell&#39;elenco, è possibile crearne una nuova in modo autonomo dalla sezione gestione delle variabili di contesto della console.

>[!NOTE]
>
>Quando le variabili di contesto sono incluse nei criteri di pubblico, il **Calcolatore pubblico** non restituisce un conteggio stimato, perché i valori di contesto sono determinati in fase di esecuzione e non possono essere previsti in anticipo.

## Vedi anche {#see-also}

* [Pubblico nei flag di funzione e nei gruppi di funzioni](audience-in-feature-flags-and-feature-groups.md)
* [Aggiungere regole di percentuale nei criteri di pubblico](adding-percentage-rules.md)
* [Regola del pubblico con variabile di contesto IP client](clientip-rule.md)
