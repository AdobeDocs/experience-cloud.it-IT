---
title: Monitorare e modificare un piano di rollout
description: Scopri come tenere traccia dell’avanzamento di un piano di rollout automatizzato nei Rollout esperienza di Adobe e come sospendere, riprendere o interrompere un piano in corso.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Monitorare e modificare un piano di rollout {#monitor-edit-rollout-plan}

Una volta che un rollout automatico è attivo, puoi tracciarne l’avanzamento e intervenire se necessario. In questa pagina viene descritto come leggere l&#39;indicatore di avanzamento, sospendere e riprendere un piano e interromperlo se necessario.

Questa pagina presuppone che tu abbia già creato e pubblicato un piano di rollout. Se non ne hai ancora configurato uno, consulta [Creare un rollout automatico](create-automated-rollout.md).

## Visualizza avanzamento rollout {#view-progress}

Dopo che il piano di rollout inizia l&#39;esecuzione, apri la scheda **Pubblico** della funzione per visualizzare lo stato corrente del piano. Il piano visualizza un indicatore di avanzamento che indica quale blocco di fase è attualmente attivo.

Utilizza l’indicatore di avanzamento per comprendere quanto segue:

* **Blocchi completati** - Tutti i blocchi di fase e di attesa sopra l&#39;indicatore sono stati eseguiti. Questi blocchi sono bloccati e non possono essere modificati.
* **Blocco corrente** — Il blocco attualmente evidenziato è la fase attiva o il periodo di attesa.
* **Blocchi imminenti** - Tutti i blocchi di fase e di attesa al di sotto dell&#39;indicatore non sono ancora stati eseguiti. che possono essere comunque modificati.

## Sospendere un piano di rollout {#pause}

Per sospendere il rollout in qualsiasi momento mentre è in corso, seleziona **Sospendi rollout** nella console.

Quando il piano viene sospeso:

* Il pubblico dell’ultimo blocco di fase completato rimane attivo. Gli utenti di quel pubblico continuano a ricevere la funzione.
* Il flag di funzione, il gruppo di funzioni o il gruppo di funzioni cross-team rimane nello stato corrente attivato o pubblicato. Continua a distribuire la funzione al pubblico attivo corrente.
* La fase successiva e i blocchi di attesa rimangono modificabili.

Per riprendere un piano in pausa, selezionare **Riprendi rollout**. Il piano continua da dove è andato a finire.

## Interrompere un piano di rollout {#abort}

Per interrompere definitivamente il piano di rollout, seleziona **Interrompi rollout** nella console.

Quando il piano viene interrotto:

* Il pubblico dell’ultimo blocco di fase completato rimane attivo e la funzione continua a essere fornita al pubblico.
* La feature stessa non è disattivata; se desiderate interrompere completamente la gestione della feature, dovete interrompere separatamente la distribuzione o disattivare il flag o il gruppo della feature.
* Non è più possibile modificare i blocchi di fase e di attesa futuri.
* Impossibile riprendere un piano interrotto.

>[!IMPORTANT]
>
>L’interruzione di un piano di rollout non disattiva automaticamente la funzione. Esegui un’azione separata sullo stato della funzione se desideri interrompere il servizio per gli utenti.

## Modificare i blocchi di fase imminenti {#edit-upcoming}

Mentre il piano è in corso (o in pausa), è comunque possibile modificare qualsiasi fase o blocco di attesa non ancora eseguito:

* Regola le regole o la percentuale di pubblico per un blocco di fase successivo.
* Modifica la durata o la data fissa di un blocco di attesa imminente.

I blocchi completati sono bloccati e non possono essere modificati.

## Vedi anche {#see-also}

* [Creare un rollout automatico](create-automated-rollout.md)
* [Concetto di rollout automatico](automated-rollout-concept.md)
* [Stati di rilascio](../feature-flags/release-states.md)
