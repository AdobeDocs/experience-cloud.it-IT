---
title: Rollout dell’esperienza Adobe
description: Scopri come utilizzare i Rollout di esperienza di Adobe per distribuire le funzioni in modo sicuro e graduale con rollout controllati, flag di funzioni e gestione mirata dell’audience.
exl-id: c400d75d-d928-4cf6-a094-1a2f443389f0
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# Rollout dell’esperienza Adobe {#experience-rollouts-home}

I rollout di esperienza Adobe consentono ai team di prodotto di distribuire le nuove funzioni in modo graduale e sicuro, senza ridistribuzioni o tempi di inattività. Definisci chi vede cosa, quando e a quale ritmo. Se qualcosa va storto, disattivate immediatamente la funzione. Se va bene, espandi il pubblico secondo la tua pianificazione.

## Che cosa puoi fare

**Controllo che visualizza nuove funzionalità.** Versioni di Target per utenti, organizzazioni, aree geografiche o attributi personalizzati specifici. Inizia con un piccolo gruppo, convalida l&#39;esperienza, quindi espandi, il tutto dalla console, senza modifiche al codice.

**Esegui esperimenti A/B.** Distribuisci diverse varianti a diversi segmenti del pubblico e misura le prestazioni migliori. Utilizza i risultati per prendere decisioni informate sui prodotti prima di una versione completa.

**Riduci i rischi di rilascio.** Dividi le modifiche di grandi dimensioni in rollout più piccoli e controllati. Se viene visualizzato un bug o un problema di prestazioni, disattivare solo la funzione interessata, mantenendo stabile il resto dell&#39;applicazione.

**Coordinazione tra team.** I gruppi di funzioni cross-team consentono a più team di partecipare a un’unica versione coordinata, ciascuno dei quali gestisce i propri flag di funzione condividendo al contempo una pianificazione di rollout e un pubblico comuni.

## Integrare la prima funzionalità

Per ottenere valore dai rollout di esperienza, segui tre passaggi:

1. **Configura il team e l&#39;applicazione** — [Richiedi l&#39;accesso](guides/console/request-access.md) alla console, quindi [onboarding dell&#39;applicazione](guides/applications/onboard-your-application.md) in modo che i rollout dell&#39;esperienza sappiano quali client distribuire.

2. **Crea e pubblica un flag di funzionalità**. Segui la [guida Crea il tuo primo flag di funzionalità](guides/feature-flags/create-your-first-feature-flag.md) per definire un flag, impostare il pubblico iniziale e pubblicarlo nell&#39;ambiente.

3. **Integrare con l&#39;applicazione**: connetti l&#39;app all&#39;API Experience Rollouts o a SDK in modo che possa recuperare e applicare i flag di funzionalità in fase di esecuzione. Inizia con [passaggi di integrazione](guides/integrate/integration-steps.md) per il tipo di applicazione.

Una volta che il primo flag è attivo, puoi perfezionarne il pubblico, configurare un rollout graduale e promuoverlo dal rollout salvato a quello completo.

## Hai bisogno di aiuto?

Se qualcosa non si comporta come previsto, nella [guida alla risoluzione dei problemi](guides/support/troubleshooting.md) vengono descritti i problemi più comuni. Per qualsiasi altra cosa, [contatta l&#39;assistenza](guides/support/contact-support.md).
