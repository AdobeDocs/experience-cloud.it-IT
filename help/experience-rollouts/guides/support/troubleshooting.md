---
title: Risoluzione dei problemi
description: Utilizza il workbench Rollout esperienza per diagnosticare i problemi di valutazione dei flag di funzione per utenti specifici, incluso il controllo delle funzioni abilitate, disabilitate o senza corrispondenza per una determinata identità utente.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# Risoluzione dei problemi {#troubleshooting}

I Rollout esperienza includono uno strumento di diagnostica integrato denominato **Workbench funzionalità** che consente di comprendere esattamente quali flag di funzionalità riceve un utente specifico e perché. Utilizzalo per esaminare i rapporti di comportamento delle funzioni imprevisto senza dover riprodurre problemi nel codice.

## Accedere al workbench delle funzioni {#access-workbench}

Per aprire il workbench delle funzionalità, effettuare le seguenti operazioni:

1. Accedi alla console Rollout esperienza.
2. Passa a **Workbench > Utenti finali** dal menu principale.
3. Selezionare la scheda **Funzionalità**.

## Immettere un&#39;identità utente {#input-identity}

Per cercare le valutazioni dei flag di funzione per un utente specifico, immettere le seguenti informazioni nel modulo del workbench:

* **Tipo ID** — selezionare il tipo di identificatore in uso. I tipi supportati includono e-mail, GUID e ID visitatore. Puoi anche inserire un **flag di rilascio** direttamente per cercare quali versioni sono state abilitate per un utente in base al loro valore di flag.
* **Valore ID** - Immettere l&#39;identificatore dell&#39;utente. Se selezioni e-mail come tipo di ID, tieni presente che più GUID possono essere associati allo stesso indirizzo e-mail. Viene fornito un elenco a discesa GUID che consente di passare da un GUID associato all&#39;altro.
* **Tipo di origine autenticazione** - Selezionare se applicabile all&#39;integrazione.
* **Variabili di contesto**: fornire facoltativamente coppie chiave-valore di contesto che influiscono sulla valutazione delle regole del pubblico (ad esempio, paese, tipo di dispositivo).
* **Team e applicazione**: selezionare il team e l&#39;applicazione per cui si desidera recuperare i flag di funzionalità. Per impostazione predefinita, il team corrente e una delle sue applicazioni sono preselezionati.

Dopo aver compilato il modulo, seleziona **Recupera funzionalità**.

## Interpretare i risultati {#interpret-results}

I risultati dipendono dal tipo di ID immesso.

### Ricerca e-mail o GUID {#email-guid-lookup}

Quando si cerca un utente per e-mail o GUID, nei risultati vengono visualizzate due sezioni:

**Flag di rilascio**

In questa sezione vengono visualizzati tre elenchi per il team e l&#39;applicazione selezionati:

* **Abilitato** — Versioni attualmente attive per questo utente.
* **Disabilitato** — Versioni esistenti ma non abilitate per questo utente.
* **Non utilizzato** — Bit di rilascio a cui non è associata alcuna versione.

Le versioni associate al team e all’applicazione attualmente selezionati vengono visualizzate nella parte superiore di ogni elenco.

**Flag e gruppi di caratteristiche**

In questa sezione sono elencati tutti i flag di funzionalità del team e dell&#39;applicazione selezionati attualmente abilitati per l&#39;utente. Ogni voce mostra:

* Chiave e nome flag di funzione
* Gruppo di funzioni (se il flag appartiene a uno)
* Variante (se è configurato il test A/B)
* Se il flag è collegato al pubblico

È inoltre possibile selezionare **Mostra richiesta/risposta** per verificare la richiesta e la risposta API esatte che ha prodotto i risultati.

### E-mail non autonoma o ID non GUID {#non-self-lookup}

Se l&#39;e-mail immessa non è di tua proprietà o se viene utilizzato un tipo di ID non GUID, viene visualizzata solo la sezione **Flag di funzionalità e gruppi**.

### Ricerca flag di rilascio {#release-flag-lookup}

Quando immetti un **flag di rilascio** come tipo ID, viene visualizzata solo la sezione **Flag di rilascio**, in cui sono elencate le versioni abilitate e disabilitate per l&#39;utente associato a tale flag.

## Problemi comuni {#common-issues}

La tabella seguente descrive i problemi comuni e come analizzarli utilizzando il workbench.

| Sintomo | Cosa controllare |
|---|---|
| L’utente non riceve un flag di funzione consigliato | Verifica la selezione del team e dell’applicazione. Verifica che l’ID dell’utente corrisponda al tipo di regola per il pubblico (e-mail, GUID, ecc.). Verificare che la funzionalità sia nello stato **Pubblicazione** o **Rollout completo**. |
| La funzione è attivata in modo imprevisto per tutti gli utenti | Conferma che alla funzione non siano applicate regole per il pubblico o che la percentuale sia impostata su 100%. Verifica se la funzionalità è nello stato **Rollout completo**. |
| La regola del pubblico non corrisponde | Utilizza il workbench con variabili di contesto per confermare che i valori passati in fase di esecuzione corrispondano a quelli configurati nella regola del pubblico. |
| Lo stato del flag della funzione è corretto, ma l’utente continua a visualizzare il comportamento precedente | Controlla il TTL configurato per l’applicazione. SDK memorizza nella cache i dati della funzione e li aggiorna solo all’intervallo di polling configurato. |

## Vedi anche {#see-also}

* [Ottieni supporto](get-support.md)
* [Contatta l’assistenza](contact-support.md)
* [Aggiorna regole di pubblico della versione](../feature-flags/update-release-audience-rules.md)
* [Stati di rilascio](../feature-flags/release-states.md)
