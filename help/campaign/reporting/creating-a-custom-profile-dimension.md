---
title: Creazione di una dimensione di profilo personalizzata
description: Scopri come creare una dimensione di profilo personalizzata basata sui dati di profilo personalizzati.
audience: reporting
content-type: reference
level: Intermediate
source-git-commit: 5a7337c44d6ca5ee4403d9fe0b65246b629afacd
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 3%

---

# Creazione di una dimensione di profilo personalizzata{#creating-a-custom-profile-dimension}

È inoltre possibile creare e gestire i rapporti in base ai dati di profilo personalizzati creati durante l’estensione dello schema del destinatario.

* [Passaggio 1: estendere lo schema dei destinatari](##extend-schema)
* [Passaggio 2: collega il nuovo campo personalizzato](#link-custom)
* [Passaggio 3: creare un rapporto dinamico per filtrare i destinatari con la dimensione di profilo personalizzata](#create-report)

## Passaggio 1: estendere lo schema dei destinatari {#extend-schema}

Per aggiungere un nuovo campo del profilo, devi estendere lo schema, segui i passaggi seguenti:

1. Accedi a **[!UICONTROL Amministrazione]** > **[!UICONTROL Configurazione]** > **[!UICONTROL Schemi di dati]** in Esplora risorse.

   ![](assets/custom_field_1.png)

1. Identifica lo schema destinatario personalizzato e selezionalo. Se non hai ancora esteso lo schema nms:recipient integrato, fai riferimento a [questa procedura](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Aggiungi il campo personalizzato all’editor schema.

   Ad esempio, per aggiungere un campo personalizzato Fedeltà nello schema del destinatario:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Fai clic su **[!UICONTROL Salva]**.

1. Quindi, identifica lo schema broadLogRcp personalizzato e selezionalo. Se non hai ancora esteso lo schema del registro di consegna integrato, fai riferimento a [questa procedura](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Aggiungi lo stesso campo personalizzato dello schema Destinatario all’editor schema.

   ![](assets/custom_field_3.png)

1. Fai clic su **[!UICONTROL Salva]**.

1. Per applicare le modifiche apportate agli schemi, avviare la procedura guidata di aggiornamento del database tramite **[!UICONTROL Strumenti]** > **[!UICONTROL Avanzate]** > **[!UICONTROL Aggiornare la struttura del database]** ed eseguire Aggiorna la struttura del database. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Il nuovo campo del profilo è ora pronto per essere utilizzato e selezionato dai destinatari.

## Passaggio 2: collega il nuovo campo personalizzato {#link-custom}

>[!NOTE]
>
> Puoi aggiungere al rapporto dinamico solo un massimo di 20 campi personalizzati.

Ora che il campo del profilo è stato creato, è necessario collegarlo alla dimensione di reporting dinamico corrispondente.

1. Accedi a **[!UICONTROL Amministrazione]** > **[!UICONTROL Configurazione]** > **[!UICONTROL Schemi di dati]** > **[!UICONTROL Campo di reporting aggiuntivo]** in Esplora risorse.

   ![](assets/custom_field_5.png)

1. Clic **[!UICONTROL Nuovo]** per creare la dimensione di reporting dinamico corrispondente.

1. Seleziona **[!UICONTROL Modifica espressione]** e sfoglia lo schema Destinatario per trovare il campo del profilo personalizzato creato in precedenza.

   ![](assets/custom_field_6.png)

1. Fai clic su **[!UICONTROL Fine]**.

1. Digitare la dimensione **[!UICONTROL Etichetta]**, visibile in Reporting dinamico, e fai clic su **[!UICONTROL Salva]**.

   ![](assets/custom_field_7.png)

Il campo del profilo personalizzato è ora disponibile come dimensione di profilo personalizzata nei rapporti. Per eliminare la dimensione di profilo personalizzata, puoi selezionarla e fare clic sul pulsante **[!UICONTROL Elimina]** icona.

Ora che lo schema del destinatario è stato esteso con questo campo del profilo e che è stata creata la dimensione personalizzata, puoi iniziare a eseguire il targeting dei destinatari nelle consegne.

## Passaggio 3: creare un rapporto dinamico per filtrare i destinatari con la dimensione di profilo personalizzata {#create-report}

Dopo aver inviato la consegna, puoi suddividere i rapporti utilizzando la dimensione di profilo personalizzata.

1. Dalla sezione **[!UICONTROL Rapporti]** , seleziona un rapporto predefinito o fai clic sulla scheda **[!UICONTROL Crea]** per iniziare da zero.

   ![](assets/custom_field_8.png)

1. In **[!UICONTROL Dimension]** categoria, fai clic su **[!UICONTROL Profilo]** trascina e rilascia la dimensione del profilo personalizzato nella tabella a forma libera.

   ![](assets/custom_field_9.png)

1. Trascina e rilascia qualsiasi metrica per iniziare a filtrare i dati.

1. Se necessario, trascina e rilascia una visualizzazione nell’area di lavoro.
