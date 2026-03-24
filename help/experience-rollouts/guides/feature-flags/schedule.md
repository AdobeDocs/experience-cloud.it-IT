---
title: Pianificazione
description: Scopri come pianificare un flag di funzione, un gruppo di funzioni o un gruppo di funzioni multi-team da attivare automaticamente in una data e un’ora future nei Rollout di esperienza di Adobe.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 2%

---


# Pianificazione {#schedule}

La pianificazione è una funzione opzionale che consente di impostare una data e un’ora future per l’attivazione automatica di un flag di funzione, un gruppo di funzioni o un gruppo di funzioni cross-team. L’attivazione/disattivazione manuale rimane disponibile e non è necessario sostituirla con una pianificazione.

La pianificazione è supportata per:

* Flag di funzioni
* Gruppi di funzioni
* Gruppi di funzioni cross-team (pianifica la transizione allo stato **Pubblica**)

## Passaggio 1: impostare la pianificazione {#set-schedule}

1. Apri il flag di funzione, il gruppo di funzioni o il gruppo di funzioni cross-team nella console.
2. Seleziona il pulsante **Pianifica** sul lato destro dello schermo.
3. Nel pop-up, imposta la **data e ora di inizio** e seleziona il **fuso orario**.

## Passaggio 2: salvare {#save}

Seleziona **Imposta pianificazione**, quindi salva le impostazioni. La pianificazione ha effetto solo dopo il salvataggio.

## Dopo aver impostato una pianificazione {#after-schedule-set}

Una volta salvate, la data e l&#39;ora pianificate vengono visualizzate nel flag di feature o nella vista gruppo di feature.

Se si tenta di attivare/disattivare lo stato manualmente mentre una pianificazione è attiva, viene visualizzato un avviso che richiede se si desidera ignorare la pianificazione o annullare l&#39;azione.

## Alla data e ora pianificate {#on-schedule}

Al momento programmato, il flag di funzione o il gruppo di funzioni si attiva automaticamente (passa allo stato ON). Per i gruppi di funzioni cross-team, lo stato passa a **Pubblicato**.

Dopo l&#39;attivazione della pianificazione, il pulsante **Pianificazione** è disabilitato. Le pianificazioni possono essere impostate solo quando il flag di funzione o il gruppo di funzioni è disattivato (o salvato, per i gruppi di funzioni cross-team).

## Vedi anche {#see-also}

* [Creare il primo flag di funzione](create-your-first-feature-flag.md)
* [Creare un gruppo di funzioni](create-a-feature-group.md)
* [Creare un gruppo di funzioni cross-team](create-cross-team-feature-group.md)
