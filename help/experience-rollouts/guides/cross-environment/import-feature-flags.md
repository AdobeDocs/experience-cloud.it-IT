---
title: Importa flag di funzione
description: Scopri come importare i flag di funzioni da un ambiente inferiore a un ambiente superiore nei Rollout esperienza di Adobe per evitare di ricreare manualmente le configurazioni dei flag.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---


# Importa flag di funzione {#import-feature-flags}

I rollout di esperienza consentono di importare i flag di funzione da un ambiente inferiore (ad esempio, Stage) a un ambiente superiore (ad esempio, Produzione). In questo modo si evita di dover ricreare manualmente le configurazioni dei flag e si riduce il rischio di spostamenti di configurazione tra gli ambienti.

## Prerequisiti {#prerequisites}

Per utilizzare il flusso di lavoro di importazione, le istanze dell’applicazione devono essere collegate tra gli ambienti. Vedi [Associare ambienti a un&#39;applicazione](associate-environments.md).

## Passaggio 1: passare all&#39;ambiente e all&#39;applicazione di destinazione {#step-1}

Accedi alla console per l&#39;ambiente **destination**, l&#39;ambiente in cui desideri importare i flag *in*. Selezionare l&#39;applicazione in cui si desidera importare i flag dal menu a discesa dell&#39;applicazione nella pagina Flag funzione.

>[!IMPORTANT]
>
>L&#39;ambiente corrente e l&#39;applicazione selezionata devono essere la **destinazione**, non l&#39;origine. Ad esempio, per importare un flag da Stage in Produzione, accedi alla console Produzione e seleziona l’applicazione Produzione.

## Passaggio 2: aprire la finestra di dialogo di importazione {#step-2}

Selezionare **Importa contrassegni funzionalità**. Viene visualizzata una finestra di dialogo che mostra l’ambiente e l’applicazione di origine, precompilati in base agli ambienti collegati configurati per l’applicazione. Se necessario, puoi modificare l’ambiente e l’applicazione di origine dai menu a discesa nella finestra di dialogo.

## Passaggio 3: selezionare i flag di feature da importare {#step-3}

Dall&#39;elenco dei flag di funzionalità nell&#39;ambiente di origine, selezionare i flag che si desidera importare. È possibile selezionare uno, più o tutti i contrassegni contemporaneamente.

## Passaggio 4: gestire i flag esistenti (se necessario) {#step-4}

Se nell’ambiente di destinazione esiste già un flag di funzione con la stessa chiave, ai Rollout esperienza verrà richiesto di confermare se sovrascriverlo. Rivedi la configurazione del flag esistente prima di confermare, poiché la sovrascrittura sostituirà le impostazioni del flag di destinazione con quelle della sorgente.

## Note importanti {#important-notes}

Durante l&#39;importazione dei flag di feature, tenete presente quanto segue:

* I flag importati sono sempre impostati sullo stato **OFF** nell&#39;ambiente di destinazione, indipendentemente dal loro stato nell&#39;ambiente di origine. È necessario abilitarli manualmente dopo l’importazione.
* Se è stata pianificata l&#39;attivazione di un flag in una data e un&#39;ora future nell&#39;ambiente di origine, tale pianificazione è **non** riportata. Se necessario, imposta una nuova pianificazione nell’ambiente di destinazione.

## Vedi anche {#see-also}

* [Associare ambienti a un’applicazione](associate-environments.md)
* [Visualizzare i flag di funzione in tutti gli ambienti](view-feature-flags-across-environments.md)
* [Concetto di ambienti diversi](cross-environment-concept.md)
