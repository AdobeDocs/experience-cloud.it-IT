---
title: Risoluzione dei problemi di reporting dinamico
description: Qui trovi le domande comuni relative al reporting dinamico.
audience: end-user
level: Intermediate
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: a58fc8fd-e510-45ef-8fe9-c75ff4498113
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 1%

---

# Risoluzione dei problemi{#troubleshooting}

In questa sezione trovi le domande comuni relative al reporting dinamico.

## Per aperture univoche e clic univoci, il conteggio nella riga aggregata non corrisponde a quelli nelle singole righe {#unique-open-clicks-no-match}

Si tratta di un comportamento previsto.
Per spiegare questo comportamento, prendiamo l’esempio seguente.

Viene inviata un’e-mail ai profili P1 e P2.

P1 apre l’e-mail due volte il primo giorno e poi tre volte il secondo giorno.

Invece, P2 apre l’e-mail una volta il primo giorno e non la riapre nei giorni successivi.
Ecco una rappresentazione visiva dell’interazione dei profili con l’e-mail inviata:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Giorno</strong> <br/> </th> 
   <th align="center"> <strong>Aperture</strong> <br/> </th> 
   <th align="center"> <strong>Aperture univoche</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> Giorno 1<br/> </td> 
   <td align="center"> 2 + 1 = 3<br/> </td> 
   <td align="center"> 1 + 1 = 2<br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> Giorno 2<br/> </td> 
   <td align="center"> 3 + 0 = 3<br/> </td> 
   <td align="center"> 1 + 0 = 1<br/> </td> 
  </tr>
 </tbody> 
</table>

Per comprendere il numero complessivo di aperture univoche, è necessario sommare i conteggi delle righe di **[!UICONTROL aperture univoche]** che ci danno il valore 3. Tuttavia, poiché l’e-mail era destinata solo a 2 profili, il tasso di apertura dovrebbe mostrare il 150%.

Per non ottenere una percentuale superiore a 100, la definizione di **[!UICONTROL Aperture univoche]** viene mantenuta come il numero di broadLog univoci aperti. In questo caso, anche se P1 ha aperto l’e-mail il Giorno 1 e il Giorno 2, l’apertura univoca sarà comunque 1.

Questo determina la seguente tabella:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong></strong> <br/> </th> 
   <th align="center"> <strong>Aperture</strong> <br/> </th> 
   <th align="center"> <strong>Aperture univoche</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong> Giorno </strong><br/> </td> 
   <td align="center"> <strong> 6 </strong><br/> </td> 
   <td align="center"> <strong> 2</strong><br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Giorno 1<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 2<br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Giorno 2<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>I conteggi univoci si basano su uno schizzo basato su HLL, che può causare lievi imprecisioni in conteggi elevati.

## I conteggi aperti non corrispondono al conteggio del database {#open-counts-no-match-database}

Ciò può essere dovuto al fatto che, nel reporting dinamico, vengono utilizzate euristiche per tenere traccia delle aperture anche quando non è possibile tenere traccia dell&#39;azione **[!UICONTROL Apri]**.

Ad esempio, se un utente ha disabilitato le immagini sul proprio client e fa clic su un collegamento nell&#39;e-mail, **[!UICONTROL Apri]** potrebbe non essere tracciato dal database, ma **[!UICONTROL Fai clic]**.

Pertanto, i conteggi dei registri di tracciamento **[!UICONTROL Open]** potrebbero non avere lo stesso conteggio nel database.

Tali occorrenze vengono aggiunte come **&quot;un clic e-mail implica l&#39;apertura di un messaggio e-mail&quot;**.

>[!NOTE]
>
>Poiché i conteggi univoci si basano su uno schizzo basato su HLL, è possibile riscontrare incoerenze minori tra i conteggi.

## Come vengono calcolati i conteggi per le consegne ricorrenti/transazionali? {#counts-recurring-deliveries}

Quando si utilizzano consegne ricorrenti e transazionali, i conteggi vengono attribuiti sia alle consegne padre che a quelle figlio.
Possiamo prendere l&#39;esempio di una consegna ricorrente denominata **R1** impostata per essere eseguita ogni giorno il giorno 1 (RC1), il giorno 2 (RC2) e il giorno 3 (RC3).
Supponiamo che solo una singola persona abbia aperto tutte le consegne dei bambini più volte. In questo caso, le singole consegne secondarie ricorrenti mostreranno il conteggio di **[!UICONTROL Open]** come 1 per ciascuna.
Tuttavia, poiché la stessa persona ha fatto clic su tutte le consegne, anche la consegna ricorrente principale avrà **[!UICONTROL Aperto univoco]** come 1.

I rapporti devono avere un aspetto simile al seguente:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Consegna</strong> <br/> </th> 
   <th align="center"> <strong>Inviato</strong> <br/> </th> 
   <th align="center"> <strong>Consegnato</strong> <br/> </th>
   <th align="center"> <strong>Aperture</strong> <br/> </th> 
   <th align="center"> <strong>Aperture univoche</strong> <br/> </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong>R1</strong><br/> </td> 
   <td align="center"> <strong>100</strong><br/> </td> 
   <td align="center"> <strong>90</strong><br/> </td> 
   <td align="center"> <strong>10</strong><br/> </td> 
   <td align="center"> <strong>3</strong><br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> RC1<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 6<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr>
    <tr> 
   <td align="center"> RC2<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 30<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
    <tr> 
   <td align="center"> RC3<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Qual è il significato dei colori nella tabella dei rapporti? {#reports-color-signification}

I colori visualizzati nei rapporti sono randomizzati e non possono essere personalizzati. Rappresentano una barra di avanzamento e vengono visualizzati per aiutarti a evidenziare meglio il valore massimo raggiunto nei rapporti.

Nell&#39;esempio seguente, la cella è dello stesso colore poiché il relativo valore è 100%.

![](assets/troubleshooting_1.png)

Se si modifica la **[!UICONTROL Formattazione condizionale]** in personalizzata, quando il valore raggiunge il limite superiore la cella diventerà più verde. Mentre, se raggiunge il limite inferiore, diventa più rosso.

In questo caso, ad esempio, il **[!UICONTROL limite superiore]** è impostato su 500 e il **[!UICONTROL limite inferiore]** è impostato su 0.

![](assets/troubleshooting_2.png)

## Perché il valore N/D viene visualizzato nei rapporti?

![](assets/troubleshooting_3.png)

Il valore **N/A** può talvolta essere visualizzato nei report dinamici. Questo può essere visualizzato per tre motivi:

* La consegna è stata eliminata ed è visualizzata come **N/A** per non causare discrepanze nei risultati.
* Quando trascini e rilasci la dimensione **[!UICONTROL Consegna transazionale]** nei rapporti, il valore **N/A** potrebbe apparire come risultato. Questo accade perché il rapporto dinamico recupera ogni consegna anche se non è transazionale. Ciò può verificarsi anche quando si trascina la dimensione **[!UICONTROL Delivery]** nel report e in questo caso il valore **N/A** rappresenta le consegne transazionali.
* Quando una dimensione viene utilizzata con una metrica non correlata alla dimensione. Nell&#39;esempio seguente viene aggiunto un raggruppamento con la dimensione **[!UICONTROL URL di tracciamento]** anche se il conteggio di **[!UICONTROL Clic]** è impostato su 0 in questa consegna.

  ![](assets/troubleshooting_4.png)

## I rapporti delle consegne mostrano dati incompleti quando si utilizza la mappatura Target personalizzata

Se utilizzi mappature di destinazione personalizzate importate nelle consegne e nei diversi rapporti non vengono visualizzati dati, potrebbe significare che gli arricchimenti dei rapporti non sono stati creati per tali mappature di destinazione.

Per risolvere il problema:

* Dopo aver importato la mappatura di Target da un XML, dovrai importare anche l’arricchimento per reporting.

* Invece di importare la mappatura Target, puoi crearla direttamente nell’interfaccia utente web di Adobe Campaign, creando automaticamente l’arricchimento per reporting.

## Discrepanza tra il numero di intestazione della colonna e la somma delle righe

È prevista una discrepanza tra il numero di intestazione della colonna e la somma di tutte le righe nei seguenti casi:

* **Metriche univoche**: l&#39;utilizzo di metriche univoche può modificare il conteggio totale visualizzato nell&#39;intestazione, in quanto si basa sugli ID dei destinatari anziché sulla semplice somma dei conteggi delle righe. Di conseguenza, un singolo profilo potrebbe attivare numerosi eventi tra diverse dimensioni, portando a più righe nel set di dati. Tuttavia, nell’intestazione di, ogni profilo viene conteggiato una sola volta.

  Ad esempio:

   * Se un profilo A apre un’e-mail in tre giorni diversi, la suddivisione per giorno mostrerà A in tre righe, ma nell’intestazione, A conterà come 1.

   * Se il profilo A fa clic su tre diversi collegamenti in un’e-mail nello stesso giorno, la suddivisione per URL di tracciamento mostrerà A in tre righe, ma nell’intestazione, A conta come 1. Lo stesso vale per i raggruppamenti per dispositivo e browser.

* **Metriche aperte**: il conteggio delle aperture è determinato aggregando il totale degli eventi di apertura effettivi e degli eventi di clic univoci (per ID destinatario), esclusi i casi in cui non si è verificato un evento di apertura poiché non è possibile fare clic su un collegamento e-mail senza un evento di apertura.

  Ad esempio:

   * Quando il profilo A apre un’e-mail tracciata (con URL U1), si registra come evento aperto con l’URL indicato come nullo. Se si fa clic su U1 in un secondo momento, viene generato un evento clic. Anche se il clic di A su U1 viene conteggiato come evento aperto, non esiste un evento aperto specifico per U1. Quindi, A viene conteggiato una sola volta nel conteggio unico di apertura.

   * Un profilo R apre un’e-mail il giorno 1, registra un evento aperto e fa clic su un collegamento. Nei due giorni successivi, R riapre l’e-mail e fa di nuovo clic sul collegamento, generando ogni giorno un evento di clic. Mentre il coinvolgimento di R viene tracciato ogni giorno nel numero aperto, R viene conteggiato solo una volta nell’intestazione della colonna, concentrandosi su impegni univoci.

* **Evento negato**: nei report, per evento negato si intendono i tentativi di consegna inizialmente contrassegnati come riusciti, ma alla fine non riusciti dopo nuovi tentativi. Questi sono indicati da un conteggio di -1. Per evitare confusione, questi conteggi negativi vengono esclusi dai numeri della metrica di consegna visualizzati. Di conseguenza, il totale di tutte le righe per la metrica di consegna potrebbe non corrispondere al numero di intestazione della colonna.
