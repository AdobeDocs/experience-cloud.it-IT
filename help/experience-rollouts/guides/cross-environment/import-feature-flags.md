---
title: Importa flag di funzione
description: Scopri come importare i flag di funzioni da una sandbox a un’altra in Adobe Experience Rollout per evitare di ricreare manualmente le configurazioni dei flag.
hide: true
exl-id: 37c84d75-a565-4202-8c99-f630e05b6bb6
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 1%

---

# Importa flag di funzione {#import-feature-flags}

I rollout di esperienza consentono di importare flag di funzioni da una sandbox (ad esempio, sandbox 1) a un’altra (ad esempio, sandbox 2). In questo modo si evita di dover ricreare manualmente le configurazioni dei flag e si riduce il rischio di spostamenti di configurazione tra le sandbox.

## Passaggio 1: passare alla sandbox e all’applicazione di destinazione {#step-1}

Accedi alla console per la sandbox **destinazione**, la sandbox in cui desideri importare i flag *in*. Selezionare l&#39;applicazione in cui si desidera importare i flag dal menu a discesa dell&#39;applicazione nella pagina Flag funzione.

>[!IMPORTANT]
>
>La sandbox corrente e l&#39;applicazione selezionata devono essere la **destinazione**, non l&#39;origine. Ad esempio, per importare un flag dalla sandbox 1 alla sandbox 2, accedi alla console sandbox 2 e seleziona l’applicazione sandbox 2.

## Passaggio 2: aprire la finestra di dialogo di importazione {#step-2}

Selezionare **Importa contrassegni funzionalità**. Viene visualizzata una finestra di dialogo che mostra la sandbox e l’applicazione di origine, precompilate in base alle applicazioni disponibili. Se necessario, puoi modificare la sandbox e l’applicazione di origine dai menu a discesa nella finestra di dialogo.

## Passaggio 3: selezionare i flag di feature da importare {#step-3}

Dall’elenco dei flag di funzione nella sandbox di origine, seleziona i flag che desideri importare. È possibile selezionare uno, più o tutti i contrassegni contemporaneamente.

## Passaggio 4: selezionare lo stato dei flag di funzionalità da importare {#step-4}

Utilizza il menu a discesa per scegliere come importare i flag di funzionalità: **Enabled**, **Disabled** o nel loro **stato corrente**. Per impostazione predefinita, i flag di funzionalità vengono importati nello stato **Disabled**.

## Note importanti {#important-notes}

Durante l&#39;importazione dei flag di feature, tenete presente quanto segue:

* Se nella sandbox di destinazione esiste già un flag di funzione con la stessa chiave, non verrà importato.

## Vedi anche {#see-also}

* [Funzioni e gruppi di funzioni](../feature-flags/features-feature-groups-releases.md)
* [Creare il primo flag di funzione](../feature-flags/create-your-first-feature-flag.md)

<!-- -->
