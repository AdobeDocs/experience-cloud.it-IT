---
title: Creare un gruppo di funzioni cross-team
description: Scopri come creare un gruppo di funzioni cross-team nei Rollout di esperienza Adobe per coordinare i flag di funzioni tra le applicazioni di proprietà di team diversi.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# Creare un gruppo di funzioni cross-team {#create-cross-team-feature-group}

## Prerequisiti {#prerequisites}

Prima di creare un gruppo di funzioni cross-team, verifica quanto segue:

* Accesso alla console. Vedere [Accesso alla console](../console/log-in-to-the-console.md)
* Appartieni a un team e la tua applicazione è integrata
* Hai il ruolo di **Amministratore funzionalità**. Vedi [Ruoli utente](../teams/user-roles.md)
* Hai creato i flag di funzionalità da includere. Consulta [Creare il tuo primo flag di funzionalità](create-your-first-feature-flag.md)

Un gruppo di funzioni cross-team consente di raggruppare i flag di funzioni dalle applicazioni a più team con targeting di pubblico avanzato. A differenza delle versioni, è completamente self-service e non ha alcun limite sul numero che puoi creare. Consulta [Versioni e gruppi di funzioni cross-team](releases-and-cross-team-feature-groups.md) per un confronto.

## Passaggio 1: creare il gruppo di funzioni cross-team {#create}

Avvia il processo di creazione dalla sezione Versioni della console:

1. Passa a **Funzioni e versioni > Versioni** nella console.
2. Selezionare **Nuovo gruppo di caratteristiche (Cross-Team)**.

## Passaggio 2: dettagli di base {#basic-details}

Specifica un titolo, una chiave, una descrizione e, facoltativamente, un tag. Configura le seguenti opzioni:

* **Rollout percentuale**: imposta la quantità di pubblico che riceve la funzione.
* **Tipo di rollout** — Impostato su Manuale. La percentuale viene gestita passo dopo passo con l’avanzamento del rollout.

>[!NOTE]
>
>Il test A/B non è supportato per i gruppi di funzioni cross-team. Per eseguire i test A/B, utilizzare un [gruppo di funzionalità](create-a-feature-group.md) standard (le applicazioni devono appartenere allo stesso team).

## Passaggio 3: pubblico {#audience}

Nella scheda **Pubblico**, abilita **Regole pubblico** e configura:

* **Segmenti** — Seleziona un segmento di pubblico predefinito.
* **Filtri aggiuntivi** — Aggiungere direttamente criteri basati su profili o contesti.
* **Applicazioni** — Seleziona una o più applicazioni dal tuo team o da altri team.

>[!IMPORTANT]
>
>L’aggiunta di un’applicazione da un altro team concede agli amministratori delle funzioni di quel team il diritto di aggiungere flag di funzione per la loro applicazione a questo gruppo di funzioni cross-team. Non puoi aggiungere i flag di funzione autonomamente.

## Passaggio 4: Caratteristiche {#features}

Nella scheda **Funzionalità** è disponibile una casella per ogni applicazione inclusa:

* Per le applicazioni del tuo team, puoi aggiungere direttamente i flag di funzione.
* Per le applicazioni di altri team, queste caselle sono disattivate e gli amministratori delle funzioni del rispettivo team devono aggiungere i propri flag.

>[!IMPORTANT]
>
>Un flag di funzione può essere gestito solo tramite un metodo alla volta. L’aggiunta di un flag a un gruppo di funzioni cross-team rimuove qualsiasi rollout di pubblico o percentuale impostato direttamente sul flag. I flag già presenti in un’altra versione o in un altro gruppo di funzioni non verranno visualizzati.

## Passaggio 5: pianificazione (facoltativo) {#schedule}

È possibile pianificare l&#39;attivazione del gruppo di funzioni di più team in una data e un&#39;ora future. Per informazioni dettagliate, consulta [Pianificazione](schedule.md).

## Gestione degli stati {#states}

Il team che crea il gruppo di funzioni cross-team ne è il proprietario e può gestirne lo stato. I membri amministratori delle funzionalità del team proprietario possono effettuare la transizione tra gli stati utilizzando il menu a discesa Stato:

| Stato | Descrizione |
|---|---|
| **Salva** | Salvato e non live. Tutte le modifiche sono consentite. |
| **Pubblica** | Live per il pubblico configurato. Gli amministratori delle funzionalità possono continuare ad aggiornare i criteri del pubblico e la percentuale di rollout. |
| **Rollout completo** | Disponibile per tutti gli utenti. Non è possibile limitare ulteriormente il pubblico dopo questo punto. |
| **Previsione** | L&#39;impostazione predefinita è ora Feature. Il gruppo di funzioni cross-team è chiuso. |
| **Interrompi** | Il rollout viene interrotto. Nessun utente riceve funzionalità da questo gruppo. |

## Domande frequenti {#faqs}

**Esiste un limite al numero di gruppi di funzioni cross-team?**
No. A differenza delle versioni, non esiste alcun limite. Archivia o disabilita i gruppi quando non è più necessario.

**Qual è la differenza tra una versione e un gruppo di funzioni?**
Consulta [Versioni e gruppi di funzioni cross-team](releases-and-cross-team-feature-groups.md) per un confronto dettagliato.

## Vedi anche {#see-also}

* [Versioni e gruppi di funzioni cross-team](releases-and-cross-team-feature-groups.md)
* [Creare un gruppo di funzioni](create-a-feature-group.md)
