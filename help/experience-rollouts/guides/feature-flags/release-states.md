---
title: Stati di rilascio
description: Scopri gli stati del ciclo di vita di una versione in Rollout esperienza di Adobe, compreso cosa significa ogni stato e quali transizioni sono consentite.
hide: true
exl-id: c1311353-9c36-43c5-8e75-3b3ee225da41
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 3%

---

# Stati di rilascio {#release-states}

Un Release Manager può aggiornare lo stato di una versione direttamente dalla barra di navigazione della console. Lo stato controlla se la versione è live, limitata ai test, completamente implementata o chiusa.

## Stati disponibili {#states}

| # | Stato | Descrizione | Modifiche consentite |
|---|---|---|---|
| 1 | **Bozza** | La versione viene salvata nel sistema ma non è ancora attiva. Non vengono applicate regole per il pubblico. | Sono consentite tutte le modifiche (versione, funzioni, pubblico). |
| 2 | **Salvato** | La versione viene registrata e le viene assegnato uno slot. Questa versione non è ancora visibile agli utenti. | Sono consentite tutte le modifiche. |
| 3 | **Pubblicato** | La versione è live per il pubblico specificato. Gli utenti che soddisfano i criteri di pubblico ricevono le funzioni. | Sono consentite tutte le modifiche. |
| 4 | **Rollout completo** | La versione è disponibile per tutti gli utenti indipendentemente dalle regole per i tipi di pubblico. Tutte le regole del pubblico vengono rimosse. | Sono consentite modifiche alle funzioni. Il pubblico non può essere modificato. |
| 5 | **Approvato** | Tutti gli utenti ora dispongono delle funzioni di questa versione come comportamento predefinito. Il codice condizionale può essere rimosso. Lo slot di rilascio viene liberato. | Nessuna modifica consentita. |
| 6 | **Interrotto** | La versione è stata interrotta. Nessun utente riceve funzionalità da questa versione. Lo slot di rilascio viene liberato. | Nessuna modifica consentita. |

## Transizioni consentite {#transitions}

Non tutte le transizioni di stato sono consentite. Comprendere i percorsi consentiti consente di pianificare il rollout ed evitare errori durante la gestione delle modifiche dello stato:

* Una versione può progredire attraverso gli stati: Bozza → Salvato → Pubblicato → Rollout completo → Approvato
* È possibile interrompere una versione da Bozza, Salvata, Pubblicata o Rollout completo
* Una volta approvato o interrotto, non sono consentite ulteriori modifiche

## Capacità di rilascio {#capacity}

Il numero di versioni attive (salvate o pubblicate) è limitato in qualsiasi momento. Per liberare la capacità:

* Sposta le versioni completate in **Previste** dopo che tutte le applicazioni partecipanti avranno rimosso il proprio codice condizionale.
* **Interrompi** versioni non riuscite e non continuate.

Pianifica l’approvazione o l’interruzione delle versioni entro tre mesi.

## Vedi anche {#see-also}

* [Richiedi rilascio](request-a-release.md)
* [Flusso di lavoro di rilascio end-to-end](release-workflow-end-to-end.md)
* [Aggiorna regole di pubblico della versione](update-release-audience-rules.md)

<!-- -->
