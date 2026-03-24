---
title: Aggiorna regole di pubblico della versione
description: Scopri come configurare e aggiornare i criteri di pubblico per una versione in Rollout esperienza di Adobe, inclusi i tipi di regole supportati e come combinarli.
source-git-commit: bb4541dd7a77edadded2edbc9c71905cf70f2e24
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 3%

---


# Aggiorna regole di pubblico della versione {#update-release-audience-rules}

## Accedere alle impostazioni del pubblico {#access}

Per iniziare a configurare il destinatario della versione, passa alle impostazioni relative al pubblico nella console:

1. Apri la versione nella console Rollout esperienza.
2. Passa alla scheda **Pubblico**.
3. Attiva l&#39;interruttore accanto a **Regole pubblico**.
4. Seleziona se aggiungere **regole di inclusione** (chi deve ricevere la versione) o **regole di esclusione** (chi non deve riceverla).

## Criteri di pubblico supportati {#criteria}

### Tipo ID {#id-type}

Puoi indirizzare l’attività agli utenti in base al loro tipo di account (ad esempio, account personali o aziendali).

### Paese {#country}

Puoi indirizzare l’attività agli utenti in base al loro paese registrato.

### ID utente {#user-id}

Eseguire il targeting di utenti specifici in base al loro identificatore utente univoco (GUID).

### Indirizzo e-mail {#email}

Effettua il targeting degli utenti in base al loro indirizzo e-mail esatto. Per aggiungere più indirizzi e-mail contemporaneamente, seleziona **in** dal menu a discesa operatore (anziché **is**), quindi:

* Immettere un elenco di indirizzi separato da virgole nella casella di testo oppure
* Caricare un file `.txt` con un indirizzo per riga oppure
* Carica un file `.csv` con l&#39;elenco degli indirizzi

Se l’elenco è molto grande, suddividilo in batch più piccoli.

### Dominio e-mail {#email-domain}

Eseguire il targeting di tutti gli utenti il cui indirizzo e-mail appartiene a un dominio specifico (ad esempio, `yourcompany.com`).

### IP client {#client-ip}

Puoi indirizzare l’attività agli utenti in base al loro indirizzo IP client.

### Percentuale {#percentage}

Esegui il targeting di una percentuale casuale di tutti gli utenti, inclusi gli utenti non autenticati.

### Percentuale (solo autenticato) {#percentage-auth}

Esegui il targeting solo di una percentuale casuale di utenti autenticati. Gli utenti non autenticati sono esclusi.

## Combinazione di più regole {#combining-rules}

Puoi combinare più criteri di pubblico utilizzando la logica AND/OR.

**Esempi:**

* Per eseguire il targeting solo degli account enterprise di un dominio specifico, combinare la regola del tipo **ID** con la regola del dominio **E-mail** utilizzando AND.
* Per eseguire il targeting del 10% degli utenti da un paese specifico, combina la regola **Paese** con la regola **Percentuale**.

Utilizzare le icone **+/-** per aggiungere o rimuovere condizioni. Per duplicare una condizione, seleziona l’icona di duplicazione accanto a una regola esistente. Per la logica nidificata complessa, abilitare **Logica nidificata** e immettere un&#39;espressione valida nella casella di testo.

## Vedi anche {#see-also}

* [Richiedi rilascio](request-a-release.md)
* [Flusso di lavoro di rilascio end-to-end](release-workflow-end-to-end.md)
* [Stati di rilascio](release-states.md)
