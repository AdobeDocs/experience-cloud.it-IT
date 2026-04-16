---
title: Flag
description: Scopri come utilizzare i flag in Adobe Target per distribuire le funzioni in modo sicuro e graduale con rollout controllati, flag di funzioni e gestione mirata dell’audience.
hide: true
index: false
exl-id: c400d75d-d928-4cf6-a094-1a2f443389f0
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 1%

---

# Flag {#experience-rollouts-home}

>[!AVAILABILITY]
>
>Flag è attualmente in Beta e disponibile per i clienti Adobe Target. Contatta il tuo rappresentante Adobe per richiedere l’accesso.

I flag in Adobe Target consentono ai team di prodotto di distribuire le nuove funzioni in modo graduale e sicuro, senza ridistribuzioni o tempi di inattività. Definisci chi vede cosa, quando e a quale ritmo. Se qualcosa va storto, disattivate immediatamente la funzione. Se va bene, espandi il pubblico secondo la tua pianificazione.

## Che cosa puoi fare

**Controllo che visualizza nuove funzionalità.** Versioni di Target per utenti, organizzazioni, aree geografiche o attributi personalizzati specifici. Inizia con un piccolo gruppo, convalida l&#39;esperienza, quindi espandi, il tutto dalla console, senza modifiche al codice.

**Esegui esperimenti A/B.** Distribuisci diverse varianti a diversi segmenti del pubblico e misura le prestazioni migliori. Utilizza i risultati per prendere decisioni informate sui prodotti prima di una versione completa.

**Riduci i rischi di rilascio.** Dividi le modifiche di grandi dimensioni in rollout più piccoli e controllati. Se viene visualizzato un bug o un problema di prestazioni, disattivare solo la funzione interessata, mantenendo stabile il resto dell&#39;applicazione.

**Coordinamento tra le applicazioni.** I gruppi di funzioni consentono di gestire più flag di funzione insieme, condividendo un pubblico di rollout comune tra le applicazioni.

**Esporta i dati.** Esporta i dati dei flag nell’ambiente di reporting preferito per l’analisi e la misurazione insieme agli altri dati di Adobe.

## Aggiungi il primo flag

Il recupero del valore dai flag inizia con tre passaggi:

1. **Flag di accesso tramite Adobe Target** — sono disponibili in Adobe Target. [Richiedi l&#39;accesso](guides/console/request-access.md) e apri i flag dall&#39;interfaccia di Target.

1. **Crea e pubblica un contrassegno**. Segui la [guida Crea il tuo primo contrassegno di funzionalità](guides/feature-flags/create-your-first-feature-flag.md) per definire un contrassegno, impostare il pubblico iniziale e pubblicarlo nell&#39;ambiente.

1. **Integrare con l&#39;applicazione**: connetti l&#39;app tramite AEP Web SDK o AEP Mobile SDK in modo che possa recuperare e applicare i flag in fase di esecuzione. Inizia con [passaggi di integrazione](guides/integrate/integration-steps.md) per il tipo di applicazione.

Una volta che il primo flag è attivo, puoi perfezionarne il pubblico, configurare un rollout graduale e promuoverlo dal rollout salvato a quello completo.

## Hai bisogno di aiuto?

Se qualcosa non si comporta come previsto, contatta il rappresentante Adobe per richiedere assistenza.

<!-- 
Bob was here
-->
