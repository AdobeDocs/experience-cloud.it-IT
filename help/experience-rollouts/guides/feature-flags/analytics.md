---
title: Analytics
description: Scopri come abilitare e utilizzare la dashboard di analisi integrata in Rollout esperienza di Adobe per monitorare le prestazioni dei flag di funzione e misurare l’impatto del rollout.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 1%

---


# Analytics {#analytics}

Rollout esperienza fornisce analisi integrate per flag di funzione, gruppi di funzioni, gruppi di funzioni incrociati e versioni. Utilizza il dashboard di Analytics per comprendere quanti utenti partecipano al rollout e come si confrontano le varianti e i gruppi di controllo.

## Abilita analisi {#enable}

Analytics deve essere abilitato a due livelli:

1. **Livello applicazione** - Contatta il supporto Rollout esperienza per abilitare Analytics per la tua applicazione.
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
