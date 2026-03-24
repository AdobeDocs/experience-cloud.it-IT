---
title: Concetto di rollout automatico
description: Scopri come funzionano i rollout automatizzati nei Rollout di esperienza Adobe, inclusi i blocchi di fase, i blocchi di attesa e come il piano di rollout avanza automaticamente.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 2%

---


# Concetto di rollout automatico {#automated-rollout-concept}

Un rollout automatizzato consente di definire l’intero piano di rollout graduale in un’unica operazione. Invece di tornare manualmente alla console per espandere il pubblico per ogni fase, puoi configurare tutte le fasi e le relative pianificazioni in anticipo e i Rollout dell’esperienza avanzano attraverso di esse automaticamente.

I rollout automatizzati sono supportati per i flag di funzione, i gruppi di funzioni e i gruppi di funzioni cross-team.

## Come funziona {#how-it-works}

Un piano di rollout è costituito da **blocchi di fase** e **blocchi di attesa** eseguiti in sequenza:

* **Blocco di fase**: definisce i criteri di pubblico per una fase del rollout. Quando il piano raggiunge un blocco di fase, tale pubblico diventa il pubblico attivo per la funzione.
* **Blocco di attesa**: definisce la pausa tra due blocchi di fase. Un blocco di attesa può essere una durata relativa (ad esempio, &quot;attesa di 3 giorni&quot;) o una data e un’ora fisse.

Il piano inizia quando si pubblica la funzione o la si pianifica per una data futura. I Rollout esperienza si spostano automaticamente da un blocco all’altro in base alla pianificazione configurata.

## Comportamento blocco fase {#phase-block-behavior}

Ogni blocco di fase successivo viene precompilato con il pubblico della fase precedente. In questo modo è più facile creare rollout con espansione incrementale in cui ogni nuova fase include tutti i gruppi di pubblico precedenti oltre a quelli nuovi.

>[!IMPORTANT]
>
>Le regole del pubblico in ciascun blocco di fase sono modificabili, pertanto devi assicurarti di non eliminare i criteri del pubblico dalle fasi precedenti quando ne aggiungi di nuovi. La riduzione dell’ambito del pubblico a metà del rollout può causare la perdita imprevista dell’accesso a una funzione da parte degli utenti.

## Stati del piano di rollout {#rollout-plan-states}

Una volta che un piano di rollout è attivo, può essere in uno dei tre stati seguenti:

| Stato | Descrizione |
|---|---|
| **In corso** | Il piano è in esecuzione. Un indicatore di avanzamento nella console mostra quale blocco di fase è attualmente attivo. Tutti i blocchi completati sono bloccati e non possono essere modificati. |
| **In pausa** | Il piano è in attesa. Il pubblico dell’ultimo blocco di fase completato rimane attivo. I blocchi di fase e attesa futuri possono ancora essere modificati mentre sono in pausa. |
| **Interrotto** | Il piano è stato interrotto definitivamente. Il pubblico dell’ultimo blocco di fase completato rimane attivo. Non sono consentite ulteriori modifiche al piano. L&#39;interruzione del piano non comporta la disattivazione della feature, ma è necessario modificare separatamente lo stato della feature se si desidera interrompere il servizio. |

## Vedi anche {#see-also}

* [Creare un rollout automatico](create-automated-rollout.md)
* [Monitorare e modificare un piano di rollout](monitor-edit-rollout-plan.md)
* [Impostare una funzione per il rollout graduale](../feature-flags/set-feature-gradual-rollout.md)
