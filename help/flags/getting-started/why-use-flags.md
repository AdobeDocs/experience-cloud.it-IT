---
title: Perché utilizzare i flag
description: Scopri i casi d’uso principali per i flag in Adobe Target, dal test selettivo delle funzioni alle versioni coordinate con più applicazioni.
hide: true
exl-id: c39c6b34-2024-4c38-b2f2-a9b58f5eff63
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# Perché utilizzare i flag {#why-use}

Flag è lo strumento giusto quando è necessario controllare chi vede una funzione e quando, sia che si stia testando in fase di sviluppo, convalidando con un sottoinsieme di utenti o coordinando una versione di grandi dimensioni tra più team.

## Casi d’uso comuni {#use-cases}

**Test selettivi durante lo sviluppo**
Esegui il test di una funzione nella tua sessione mentre altri sviluppatori continuano il loro lavoro senza effetti. Non è richiesto alcun ramo di codice complesso.

**Rollout graduale con feedback dell&#39;utente**
Rilascia prima una funzione a un piccolo gruppo di utenti. Raccogli feedback, risolvi i problemi, quindi espandi gradualmente il pubblico prima di una versione completa.

**Rollout graduale in produzione**
Apri progressivamente una nuova funzione: 1%, 10%, 50%, quindi 100% degli utenti. Monitora le prestazioni e la risposta degli utenti in ogni fase. Se qualcosa va storto, spegnerlo immediatamente.

**Gestione del carico back-end**
Effettua un rollout in modo incrementale per evitare picchi di traffico improvvisi sui servizi back-end, anziché esporre tutti gli utenti a una nuova funzione contemporaneamente.

**Rilasci coordinati di più applicazioni**
Abilita una funzione contemporaneamente in più applicazioni e team per un set specifico di utenti. I flag garantiscono coerenza sull’intera superficie di rilascio.

**Versioni differite**
Distribuisci il codice in produzione in anticipo, quindi attiva la funzione in un momento preciso, ad esempio all’inizio di un evento di avvio del prodotto, senza alcuna modifica del codice dell’ultimo minuto.

**Termina opzione**
Se dopo il rilascio viene rilevato un problema, disattiva immediatamente la funzione senza un hotfix o una ridistribuzione.

<!-- -->
