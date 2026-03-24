---
title: Perché utilizzare i rollout di esperienza
description: Scopri i casi d’uso principali per i rollout di esperienza di Adobe, dal test selettivo delle funzioni alle versioni coordinate con più applicazioni.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 1%

---


# Perché utilizzare i rollout di esperienza {#why-use}

I rollout di esperienza sono lo strumento giusto quando è necessario controllare chi vede una funzione e quando, sia che si stia testando in fase di sviluppo, convalidando con un sottoinsieme di utenti o coordinando una versione di grandi dimensioni tra più team.

## Casi d’uso comuni {#use-cases}

**Test selettivi durante lo sviluppo**
Esegui il test di una funzione nella tua sessione mentre altri sviluppatori continuano il loro lavoro senza effetti. Non è richiesto alcun ramo di codice complesso.

**Rollout graduale con feedback dell&#39;utente**
Rilascia prima una funzione a un piccolo gruppo di utenti. Raccogli feedback, risolvi i problemi, quindi espandi gradualmente il pubblico prima di una versione completa.

**Rollout graduale in produzione**
Apri progressivamente una nuova funzione: 1%, 10%, 50%, quindi 100% degli utenti. Monitora le prestazioni e la risposta degli utenti in ogni fase. Se qualcosa va storto, spegnerlo immediatamente.

**Gestione del carico di back-end**
Effettua un rollout in modo incrementale per evitare picchi di traffico improvvisi sui servizi back-end, anziché esporre tutti gli utenti a una nuova funzione contemporaneamente.

**Versioni coordinate di più applicazioni**
Abilita una funzione contemporaneamente in più applicazioni e team per un set specifico di utenti. I rollout di esperienza garantiscono la coerenza sull’intera superficie di rilascio.

**Versioni posticipate**
Distribuisci il codice in produzione in anticipo, quindi attiva la funzione in un momento preciso, ad esempio all’inizio di un evento di avvio del prodotto, senza alcuna modifica del codice dell’ultimo minuto.

**Termina opzione**
Se dopo il rilascio viene rilevato un problema, disattiva immediatamente la funzione senza un hotfix o una ridistribuzione.
