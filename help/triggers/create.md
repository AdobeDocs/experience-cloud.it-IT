---
title: Creazione e gestione di Experience Cloud Triggers
description: Scopri l’interfaccia utente di Adobe Experience Cloud Triggers
hide: true
hidefromtoc: true
source-git-commit: ce0faf9fab45c931feb666ac0c77f5ab5c231746
workflow-type: ht
source-wordcount: '483'
ht-degree: 100%

---

# Creare un trigger di Experience Cloud {#create-triggers}

>[!NOTE]
>
> La nuova interfaccia utente di Experience Cloud Triggers offre un’esperienza intuitiva per gestire i comportamenti dei consumatori e personalizzare le esperienze utente. Per tornare all’interfaccia precedente, fai clic sul pulsante **[!UICONTROL Passa alla modalità classica]**.

Crea un trigger e configurane le condizioni. Ad esempio, puoi specificare i criteri per le regole di un attivatore durante una visita, come metriche quali abbandono del carrello o dimensioni quali il nome del prodotto. Quando le regole sono soddisfatte, il trigger viene eseguito.

1. In Experience Cloud, seleziona il menu avanzato, quindi Triggers.

   ![](assets/triggers_7.png)

1. Dalla home page di Trigger, fai clic su **[!UICONTROL Crea trigger]**, quindi specifica il tipo di trigger.

   Sono disponibili tre tipi di trigger:

   * **[!UICONTROL Abbandono:]** puoi creare un trigger che si attiva quando un visitatore visualizza un prodotto ma non aggiunge nulla al carrello.

   * **[!UICONTROL Azione:]** puoi creare trigger, ad esempio, che si attivano dopo che un utente ha effettuato un’iscrizione a una newsletter, un’iscrizione e-mail o ha usato applicazioni per le carte di credito (conferme). Se sei un rivenditore, puoi creare un trigger per un visitatore che si iscrive a un programma fedeltà. Nei contenuti multimediali e di intrattenimento, crea trigger per i visitatori che guardano un determinato show e che vorresti rispondessero a un sondaggio.

   * **[!UICONTROL Avvio e fine sessione]**: crea un trigger per gli eventi di inizio e fine sessione.

   ![](assets/triggers_1.png)

1. Aggiungi **[!UICONTROL Nome]** e **[!UICONTROL Descrizione]** al trigger.

1. Seleziona la **[!UICONTROL suite di rapporti]** di Analytics utilizzata per questo trigger. Questa impostazione identifica i dati di reporting da utilizzare.

   [Ulteriori informazioni sulla suite di rapporti](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite.html?lang=it).

1. Scegli il periodo di validità **[!UICONTROL Trigger dopo nessuna azione per]**.

1. Dalle categorie **[!UICONTROL La visita deve includere]** e **[!UICONTROL La visita non deve includere]** puoi definire i criteri o i comportamenti dei visitatori desiderati o meno. Puoi usare gli operatori logici **And** o **Or** all’interno o tra condizioni, a seconda dei criteri stabiliti.

   Ad esempio, le regole per un semplice attivatore di abbandono carrello potrebbero essere:

   * **[!UICONTROL La visita deve includere]**: `Carts (metric) Is greater or equal to 1` per eseguire il targeting dei visitatori con almeno un elemento nel carrello.
   * **[!UICONTROL La visita non deve includere]**: `Checkout (metric) Exists.` per rimuovere i visitatori che hanno acquistato gli elementi nei loro carrelli.

   ![](assets/triggers_2.png)

1. Fai clic su **[!UICONTROL Contenitore]** per stabilire e salvare regole, condizioni o filtri che definiscono un trigger. Per fare in modo che gli eventi si verifichino contemporaneamente, è necessario posizionarli nello stesso contenitore.

   Ogni contenitore elabora in modo indipendente a livello di hit, il che significa che se due contenitori sono uniti con l’operatore **[!UICONTROL And]** le regole si qualificano solo quando due risultati soddisfano i requisiti.

1. Dal campo **[!UICONTROL Metadati]**, fai clic su **[!UICONTROL + Dimension]** per scegliere una dimensione Campaign particolare o variabili rilevanti per il comportamento di un visitatore.

   ![](assets/triggers_3.png)

1. Fai clic su **[!UICONTROL Salva]**.

1. Seleziona dall’elenco il **[!UICONTROL Trigger]** appena creato per accedere al relativo rapporto di dettaglio.

   ![](assets/triggers_4.png)

1. Dalla visualizzazione dettagliata del trigger, puoi accedere ai rapporti sul numero di trigger attivati. Se necessario, puoi modificare il trigger con l’icona a forma di matita.

   ![](assets/triggers_5.png)
