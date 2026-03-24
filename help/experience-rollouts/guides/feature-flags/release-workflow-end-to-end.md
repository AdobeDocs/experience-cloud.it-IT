---
title: Flusso di lavoro di rilascio end-to-end
description: Scopri il flusso di lavoro end-to-end per la gestione di una versione coordinata nei Rollout di esperienza di Adobe, dalla definizione dei flag di funzione alla pubblicazione.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---


# Flusso di lavoro di rilascio end-to-end {#release-workflow}

Questa pagina descrive l’intera sequenza di attività coinvolte in una versione coordinata gestita da un Release Manager.

## &#x200B;1. Definire i flag di funzione per applicazione {#define-flags}

Ogni team di prodotto assegna a **Proprietario della versione di prodotto** un account che accede alla console dei rollout di esperienza e crea flag di funzionalità per le applicazioni di cui è proprietario. Il team di prodotto implementa quindi la logica condizionale nel codice, posizionando le funzioni dietro questi flag.

## &#x200B;2. Creare la versione {#create-release}

La creazione di una nuova versione richiede una richiesta di supporto e non è completamente self-service. Per creare la versione, contatta il supporto Rollout esperienza. Specifica il nome della versione, il team proprietario, l’ambiente di destinazione, l’obiettivo, le applicazioni partecipanti e la durata prevista.

Una volta confermata la versione, Release Manager apre la console e completa la configurazione della versione.

## &#x200B;3. Aggiungere flag di funzione alla versione {#add-flags}

Per ogni applicazione aggiunta alla versione, il proprietario del rilascio del prodotto dell’applicazione accede e aggiunge i flag di funzione pertinenti alla versione. Questi flag rappresentano le funzioni che verranno pubblicate con la versione.

## &#x200B;4. Configurare il pubblico {#configure-audience}

Il Release Manager seleziona il pubblico per la versione, ad esempio l’1% degli utenti in un paese specifico, tutti gli utenti con un dominio e-mail specifico o un elenco di ID utente specifici. Una volta configurata, Release Manager salva e pubblica la versione, che viene pubblicata in tempo reale per il pubblico specificato.

## &#x200B;5. Espandi e gestisci il rollout {#expand}

Una volta pubblicata la versione, Release Manager può regolare le regole del pubblico per espandere gradualmente il rollout, monitorare i problemi e utilizzare i controlli dello stato di rilascio per gestire il ciclo di vita. Per informazioni dettagliate, consulta [Stati di rilascio](release-states.md).

## Punti chiave {#key-points}

* Tutte le applicazioni partecipanti distribuiscono il proprio codice in produzione in modo indipendente dietro i flag di funzionalità, senza che sia necessario un tempo di distribuzione coordinato.
* La versione è il singolo punto di controllo che attiva tutti i flag tra i team simultaneamente.
* Il targeting del pubblico per le versioni si basa sugli attributi del token di autenticazione (paese, e-mail, ID utente, percentuale).

## Vedi anche {#see-also}

* [Richiedi rilascio](request-a-release.md)
* [Aggiorna regole di pubblico della versione](update-release-audience-rules.md)
* [Stati di rilascio](release-states.md)
