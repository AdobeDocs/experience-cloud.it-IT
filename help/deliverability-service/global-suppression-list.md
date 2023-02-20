---
title: Elenco globale di soppressione
description: Scopri l’elenco di soppressione globale
hide: true
source-git-commit: a946cfb1027896f6e45aaf88d25ad7114d6b5ac6
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# Elenco globale di soppressione {#global-suppression-list}

Un elenco di soppressione è costituito da indirizzi e-mail che i clienti desiderano escludere dalle consegne, in quanto l’invio a tali contatti potrebbe danneggiare la reputazione e i tassi di consegna di invio. Al momento, Adobe conserva un elenco aggiornato di indirizzi e-mail noti e non validi, che si sono dimostrati dannosi per l’impegno e la reputazione dell’e-mail, e garantisce che le e-mail non vengano recapitate a tali indirizzi. Questo elenco viene gestito in un elenco di soppressione globale comune a tutti i clienti di Adobe. Gli indirizzi e i nomi di dominio contenuti nell’elenco di soppressione globale sono nascosti. Nei rapporti di consegna è indicato solo il numero di destinatari esclusi.

È ora possibile gestire l’elenco di soppressione globale da un’interfaccia disponibile internamente. Questo elenco sarà gestito solo dai consulenti del recapito messaggi. L’elenco di soppressione globale può includere indirizzi e-mail o di dominio.

## Accedere all’elenco di soppressione globale

Per accedere all’elenco dettagliato degli indirizzi e-mail e dei domini esclusi, passa a **[!UICONTROL Elenco di soppressione globale]**.

>[!CAUTION]
>
>Le autorizzazioni per visualizzare, esportare e gestire l’elenco di soppressione globale dipendono dalla lista di distribuzione a cui sei assegnato. Per saperne di più

Vengono visualizzate due schede: **[!UICONTROL E-mail]** e **[!UICONTROL Dominio]**.

Sono disponibili filtri che consentono di sfogliare l’elenco.

## Aggiungi indirizzi e domini

Al momento sono disponibili due modi per aggiungere gli indirizzi all’elenco di soppressione globale:

* Elenco curato dal team di recapito messaggi.
* Elenco fornito dal provider di servizi di terze parti Blackbox.

Puoi aggiungere indirizzi e-mail o domini [una per volta](#add-one-address-or-domain)oppure [in modalità collettiva](#upload-csv-file) tramite caricamento di file CSV.

A questo scopo, seleziona la **[!UICONTROL Aggiungi e-mail o dominio]** quindi seguire uno dei metodi seguenti.

### Aggiungi un indirizzo o un dominio {#add-one-address-or-domain}

1. Seleziona la **[!UICONTROL Uno ad uno]** opzione .

1. Scegli il tipo di indirizzo: **[!UICONTROL Indirizzo e-mail]** o **[!UICONTROL Indirizzo di dominio]**.

1. Immetti l’indirizzo e-mail o il dominio da escludere dall’invio.

   >[!NOTE]
   >
   >Assicurati di inserire un indirizzo e-mail valido (ad esempio abc@company.com) o un dominio (ad esempio abc.company.com).

1. Se necessario, specifica un motivo.

   >[!NOTE]
   >
   >In questo campo sono consentiti tutti i caratteri ASCII stampabili compresi tra 32 e 126. L&#39;elenco completo è disponibile all&#39;indirizzo [questa pagina](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} ad esempio.

1. Fai clic su **[!UICONTROL Invia]** per confermare.

### Caricare un file CSV {#upload-csv-file}

1. Seleziona la **[!UICONTROL Carica CSV]** opzione .

1. Scarica il modello CSV da utilizzare, che include le colonne e il formato seguenti:

   ```
   TYPE,VALUE,COMMENT
   EMAIL,abc@somedomain.com,Comment
   DOMAIN,somedomain.com,Comment
   ```
   >[!CAUTION]
   >
   >Non modificare i nomi delle colonne nel modello CSV.
   >
   >La dimensione del file non deve superare 1 MB.

1. Compila il modello CSV con gli indirizzi e-mail e/o i domini che desideri aggiungere all’elenco di soppressione.

   >[!NOTE]
   >
   >Tutti i caratteri ASCII compresi tra 32 e 126 sono consentiti nella variabile **Commento** colonna. L&#39;elenco completo è disponibile all&#39;indirizzo [questa pagina](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} ad esempio.

1. Al termine, trascina e rilascia il file CSV, quindi fai clic su **[!UICONTROL Invia]** per confermare.

>[!NOTE]
>
>Al termine del caricamento, accertati che sia stato eseguito correttamente controllandone lo stato dall’interfaccia. [Scopri come](#recent-uploads)

### Controlla lo stato dei caricamenti recenti {#recent-uploads}

Fai clic sul pulsante **[!UICONTROL Caricamenti recenti]** per controllare lo stato dei file CSV più recenti caricati.

Gli stati possibili sono:

* **[!UICONTROL In sospeso]**: Elaborazione del caricamento del file in corso.
* **[!UICONTROL Errore]**: Il processo di caricamento dei file non è riuscito a causa di un problema tecnico o di un errore di formato del file.
* **[!UICONTROL Completa]**: Il processo di caricamento dei file è stato completato.

Durante il caricamento, se alcuni indirizzi non sono nel formato corretto, non vengono aggiunti all’elenco di soppressione globale.

In tal caso, al termine del caricamento, il report viene associato a un report. Puoi scaricarlo per verificare gli errori rilevati.

## Rimuovi indirizzi

Per rimuovere un indirizzo dall&#39;elenco di soppressione globale, utilizza **[!UICONTROL Elimina]** pulsante .

>[!CAUTION]
>
>Gli indirizzi o i domini aggiunti automaticamente dal provider di servizi di terze parti Blackbox non possono essere rimossi dai consulenti tramite l&#39;interfaccia . Questo può essere fatto solo tramite un ticket di backend.

