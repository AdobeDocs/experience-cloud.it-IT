---
title: Domande frequenti sulla gestione delle versioni
description: Trova le risposte alle domande comuni sulla gestione delle versioni in Rollout esperienza di Adobe.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---


# Domande frequenti sulla gestione delle versioni {#release-management-faqs}

## Come posso richiedere una versione? {#request-release}

Consulta [Richiedi una versione](request-a-release.md) per l&#39;intero processo e le informazioni da fornire.

## Quali criteri di pubblico sono supportati per le versioni? {#audience-criteria}

Le versioni supportano le seguenti regole per il pubblico:

* Tipo ID (tipo account)
* Paese
* ID utente (GUID)
* Indirizzo e-mail (elenco individuale o collettivo)
* Dominio e-mail
* IP client
* Percentuale (tutti gli utenti)
* Percentuale (solo utenti autenticati)

Puoi combinare più regole utilizzando la logica AND/OR, incluse le condizioni nidificate. Per istruzioni dettagliate sulla configurazione, consulta [Aggiornare le regole del pubblico](update-release-audience-rules.md).

## Come si aggiunge un&#39;applicazione a una versione? {#onboard-application}

Dopo aver creato la versione, aprila nella console e aggiungi l’applicazione alla configurazione della versione. Il proprietario del rilascio del prodotto per ogni applicazione può quindi aggiungere i flag di funzione pertinenti. Per la sequenza completa, vedi [Flusso di lavoro versione end-to-end](release-workflow-end-to-end.md).

## Non viene restituita una funzione per un utente idoneo. Come posso risolvere i problemi? {#troubleshoot}

Per eseguire il debug, effettua le seguenti operazioni:

1. **Verifica lo stato di rilascio.** La versione deve essere nello stato **Pubblicato** o **Rollout completo** per fornire le funzionalità. Consulta [Stati di rilascio](release-states.md).
2. **Controllare l&#39;applicazione e il flag di funzionalità.** Verifica che il flag di funzione sia stato creato per l’applicazione corretta e che l’applicazione sia associata alla versione corretta.
3. **Verificare che il flag di funzionalità sia abilitato.** Anche se la versione è attiva, non verrà visualizzato alcun flag disabilitato.
4. **Rivedi i criteri del pubblico.** Verifica che l’utente soddisfi tutte le condizioni definite nelle regole per il pubblico. Controlla nuovamente i criteri per la versione specifica a cui è associata la funzione.

## Vedi anche {#see-also}

* [Richiedi rilascio](request-a-release.md)
* [Aggiorna regole di pubblico della versione](update-release-audience-rules.md)
* [Stati di rilascio](release-states.md)
* [Flusso di lavoro di rilascio end-to-end](release-workflow-end-to-end.md)
