---
title: Analytics
description: Scopri come abilitare e utilizzare la dashboard di analisi integrata in Flag per monitorare le prestazioni dei flag di funzione e misurare l’impatto del rollout.
hide: true
exl-id: edddca99-f263-461b-a16f-b46ee7c15f6c
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---

# Analytics {#analytics}

Flag fornisce analisi integrate per flag di funzione, gruppi di funzioni, gruppi di funzioni incrociati e versioni. Utilizza il dashboard di Analytics per comprendere quanti utenti partecipano al rollout e come si confrontano le varianti e i gruppi di controllo. Puoi anche esportare i dati dei flag nell’ambiente di reporting preferito per l’analisi insieme agli altri dati di Adobe.

## Abilita analisi {#enable}

Analytics deve essere abilitato a due livelli:

1. **Livello applicazione** - Supporto dei flag di contatto per abilitare l&#39;analisi per l&#39;applicazione.
2. **Livello flag di funzionalità**: una volta che Analytics è abilitato per l&#39;applicazione, selezionare la casella di controllo **Abilita analisi** nella scheda **Dettagli di base** di ogni flag di funzionalità che si desidera monitorare.

>[!NOTE]
>
>Per impostazione predefinita, Analytics può essere abilitato per un massimo di 20 flag di funzione per applicazione. Se devi aumentare questo limite, contatta l’assistenza.

## Visualizzare la dashboard di Analytics {#dashboard}

Una volta abilitata l’analisi, tutti i flag di funzione, i gruppi di funzioni e le versioni dell’applicazione avvieranno il tracciamento dei dati. Accedi al dashboard selezionando **Risultati** sul flag di funzionalità, sul gruppo di funzionalità o sulla versione che desideri analizzare.

Il dashboard visualizza:

* **Partecipanti** — Numero totale di utenti qualificati per la funzionalità (combinazione variante + gruppo di controllo)
* **Gruppo di controllo** — Numero di utenti assegnati al gruppo di controllo (utenti che hanno ricevuto l&#39;esperienza predefinita)
* **Grafico a livello di giorno**: grafici a linee giornalieri che mostrano l&#39;iscrizione alla variante e al gruppo di controllo nel tempo; gli indicatori indicano quando la configurazione del flag di funzione è stata aggiornata
* **Analisi a livello di variante** — Conteggio cumulativo degli utenti iscritti al gruppo di controllo e a ogni variante

Per gruppi di funzioni e versioni, seleziona l&#39;elenco a discesa **Risultati** per scegliere un&#39;applicazione e visualizzare le analisi per tale applicazione. Analytics è disponibile solo per le applicazioni per le quali è abilitato.

## Vedi anche {#see-also}

* [Creare il primo flag di funzione](create-your-first-feature-flag.md)
* [Test A/B con flag di funzione](a-b-testing.md)
* [Creare un gruppo di funzioni](create-a-feature-group.md)

<!-- -->
