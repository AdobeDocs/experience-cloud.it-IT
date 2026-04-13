---
title: Introduzione ai rollout di esperienza
description: Scopri come Adobe Experience Rollouts fornisce un sistema di rilascio controllato per distribuire progressivamente funzioni a tipi di pubblico mirati.
hide: true
exl-id: befe7899-096d-4f74-a5a2-35b1fc3cbc58
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Introduzione ai rollout di esperienza {#introduction}

Adobe Experience Rollouts è un sistema a rilascio controllato che consente ai team di implementare funzioni fino alla produzione mantenendo un controllo preciso su chi le visualizzerà e quando. Una funzione può essere in produzione e invisibile agli utenti finali, quindi attivata progressivamente per un pubblico mirato, senza alcuna ridistribuzione.

## Dallo sviluppo alla produzione {#dev-to-prod}

I rollout di esperienza supportano il percorso completo di una funzione, dalla fase di sviluppo iniziale fino alla disponibilità generale:

1. **Test per sviluppatori**: uno sviluppatore crea un flag di funzionalità, distribuisce il codice in qualsiasi ambiente ed esegue test solo sulla propria sessione. Il problema non riguarda nessun altro utente e non è richiesta alcuna diramazione.

2. **Anteprima mirata**: il proprietario di un prodotto collega un pubblico al flag della funzione, rendendola disponibile a un sottoinsieme definito di utenti (ad esempio, partecipanti alla versione beta o un&#39;area specifica) per la convalida e il feedback.

3. **Rollout graduale**: la funzione viene aperta progressivamente a un pubblico più ampio, pari a 1%, 10%, 50%, 100%, con la possibilità di sospendere, regolare o disattivare la funzione in qualsiasi momento.

4. **Disponibilità generale** - Al termine della convalida, la funzionalità sarà disponibile per tutti gli utenti.

## Funzionalità di base {#capabilities}

Experience Rollout è una piattaforma di gestione delle funzioni che fornisce:

* **Flag di funzionalità** — Attiva o disattiva qualsiasi funzionalità in fase di esecuzione per un pubblico di destinazione, senza ridistribuire il codice.

* **Destinazione pubblico**: controllo che visualizza una funzionalità utilizzando dati del profilo utente, regole basate su percentuali, indirizzo e-mail, dominio e-mail, indirizzo IP o attributi contestuali.

* **Gruppi di funzioni**: raggruppamento di più flag di funzioni correlati in più applicazioni e gestione in un&#39;unica unità, per garantire che lo stesso pubblico veda un&#39;esperienza coerente.

* **Versioni**: coordina rollout di grandi dimensioni tra team raggruppando i flag di funzionalità di più team e applicazioni in un unico evento di rilascio.

* **Rollout graduali**: distribuzione delle funzionalità in fasi incrementale per ridurre i rischi, raccogliere feedback e gestire il carico di back-end.

* **Interrompi commutatore**: disattivare immediatamente qualsiasi funzionalità se viene rilevato un problema, senza modificare o ridistribuire il codice.

<!-- -->
