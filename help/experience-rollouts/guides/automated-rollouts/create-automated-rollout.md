---
title: Creare un rollout automatico
description: Scopri come configurare un piano di rollout automatizzato in Rollout esperienza di Adobe con blocchi di fase e blocchi di attesa in modo che il pubblico si espanda automaticamente nel tempo.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Creare un rollout automatico {#create-automated-rollout}

Un rollout automatico consente di definire tutte le fasi di rollout e i relativi programmi in un’unica sessione. I Rollout dell’esperienza passano automaticamente da una fase all’altra, senza richiedere di tornare alla console per ogni passaggio. Per una panoramica, consulta il [concetto di rollout automatico](automated-rollout-concept.md).

I rollout automatizzati sono supportati per i flag di funzione, i gruppi di funzioni e i gruppi di funzioni cross-team.

## Passaggio 1: abilitare il rollout automatico {#enable-automated-rollout}

Durante la creazione di un nuovo flag di funzionalità, gruppo di funzionalità o gruppo di funzionalità tra team, apri la scheda **Dettagli di base** e individua l&#39;opzione **Seleziona il tipo di rollout**. Il valore predefinito è **Manuale**. Per abilitare un piano di rollout automatico, selezionare **Rollout automatico**.

>[!NOTE]
>
>Quando selezioni Rollout automatico, il campo percentuale di rollout in Dettagli di base viene automaticamente impostato su 100% e diventa non modificabile. Puoi controllare la percentuale di ogni fase singolarmente nella scheda Pubblico.

## Passaggio 2: creare il piano di rollout {#build-rollout-plan}

Apri la scheda **Pubblico** e abilita l&#39;interruttore **Fasi**. In questo modo vengono attivati i controlli **Aggiungi blocco fase** e **Aggiungi blocco attesa**.

Per creare il piano di rollout, aggiungi blocchi di fase e attesa nell’ordine in cui desideri che vengano eseguiti:

### Aggiungere un blocco di fase {#add-phase-block}

Un blocco di fase definisce i criteri di pubblico per una fase del rollout. Il blocco della prima fase viene configurato utilizzando i criteri di pubblico già presenti nella pagina. Per ogni blocco di fase successivo, il pubblico della fase precedente viene prepopolato come punto di partenza.

Configura il pubblico per ogni blocco di fase:

* **Percentuale** — Imposta la percentuale del pubblico definito che riceve la funzione in questa fase.
* **Regole per il pubblico** - Aggiungi regole basate su profili, contesti o segmenti per eseguire il targeting di utenti specifici.

>[!IMPORTANT]
>
>Ogni fase successiva deve ampliare, e non sostituire, il pubblico della fase precedente. Non rimuovere le regole del pubblico dalle fasi precedenti quando ne configuri di successive, in quanto ciò potrebbe inavvertitamente escludere gli utenti che già ricevevano la funzione.

### Aggiungi un blocco di attesa {#add-wait-block}

Un blocco di attesa definisce la pausa tra due blocchi di fase. Dopo aver aggiunto un blocco di attesa, seleziona una delle opzioni seguenti:

| Opzione | Descrizione |
|---|---|
| **Attendi** | Una durata relativa — ad esempio, attendere 2 giorni, attendere 4 ore. I rollout esperienza avanzano al blocco di fase successivo dopo la scadenza di questa durata. |
| **Attendi** | Una data e un’ora fisse. I Rollout esperienza avanzano al blocco di fase successivo nel momento specificato. |

### Aggiungere blocchi di fase successivi {#add-subsequent-phases}

Ripeti il processo per aggiungere blocchi di fase e blocchi di attesa aggiuntivi fino a quando non viene configurato il piano di rollout completo.

## Passaggio 3: pianificare o pubblicare il rollout {#schedule-or-publish}

Una volta completato il piano di rollout, scegli come attivarlo:

* **Pianificazione** — Imposta una data e un&#39;ora future per l&#39;avvio automatico del rollout. Per informazioni dettagliate, consulta [Pianificazione](../feature-flags/schedule.md).
* **Pubblica manualmente** — Attiva il flag di funzionalità o sposta il gruppo di funzionalità nello stato **Pubblica** per avviarlo immediatamente.

Il piano inizia l’esecuzione dal blocco della prima fase. È possibile monitorare e modificare il piano attivo in qualsiasi momento. Consulta [Monitorare e modificare un piano di rollout](monitor-edit-rollout-plan.md).

## Vedi anche {#see-also}

* [Concetto di rollout automatico](automated-rollout-concept.md)
* [Monitorare e modificare un piano di rollout](monitor-edit-rollout-plan.md)
* [Impostare una funzione per il rollout graduale](../feature-flags/set-feature-gradual-rollout.md)
* [Criteri di pubblico](../audience/audience-in-feature-flags-and-feature-groups.md)
