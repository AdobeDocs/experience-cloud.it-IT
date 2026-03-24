---
title: Visualizzare i flag di funzione in tutti gli ambienti
description: Scopri come visualizzare lo stato dei flag di funzione in tutti gli ambienti collegati per un’applicazione nei Rollout di esperienza di Adobe.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Visualizzare i flag di funzione in tutti gli ambienti {#view-flags-across-environments}

Dopo aver collegato le istanze dell’applicazione a più ambienti, nella pagina dell’elenco dei flag di funzione viene visualizzato lo stato di ciascun flag di funzione in tutti gli ambienti collegati. In questo modo è possibile confrontare gli stati dei flag in un&#39;unica visualizzazione, ad esempio se un flag è attivato in Stage e disattivato in Produzione, senza passare da un ambiente all&#39;altro.

## Prerequisiti {#prerequisites}

Prima di poter visualizzare lo stato tra più ambienti, le istanze dell’applicazione devono essere collegate tra loro. Per istruzioni sull&#39;installazione, vedere [Associa ambienti a un&#39;applicazione](associate-environments.md).

## Come funziona {#how-it-works}

Quando si passa a **Funzionalità e versioni > Flag di funzionalità** e si seleziona un&#39;applicazione con istanze collegate, nella pagina dell&#39;elenco vengono visualizzate colonne aggiuntive per ogni ambiente collegato. Ogni colonna visualizza lo stato corrente del flag di funzione in tale ambiente.

I flag di funzionalità vengono associati in ambienti diversi in base alla **chiave**, non al nome. Ciò significa che:

* Un flag può avere un nome visualizzato diverso in ogni ambiente, purché la chiave sia la stessa.
* Il nome visualizzato in ogni colonna dell’ambiente è il nome utilizzato in tale ambiente.

## Caso d’uso {#use-case}

Un flusso di lavoro tipico consiste nello sviluppare e testare un flag di funzione in un ambiente inferiore (ad esempio, Stage), quindi verificarne lo stato prima di promuovere la configurazione in Produzione. La visibilità tra ambienti consente di verificare che il flag sia configurato correttamente nello stage prima di importarlo nell’ambiente di produzione, il tutto dall’interno della console di produzione.

## Vedi anche {#see-also}

* [Associare ambienti a un’applicazione](associate-environments.md)
* [Importa flag di funzione](import-feature-flags.md)
* [Concetto di ambienti diversi](cross-environment-concept.md)
