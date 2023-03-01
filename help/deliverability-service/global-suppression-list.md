---
title: Elenco di soppressione globale
description: Scopri l’elenco di soppressione globale
hide: true
exl-id: 40aef987-52a3-470b-88ca-c716a116bdfc
source-git-commit: b66e2525694c771ebb7ac5190b7259ef5658d81a
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# Elenco di soppressione globale {#global-suppression-list}

Un elenco di soppressione è costituito da indirizzi e-mail che i clienti desiderano escludere dalle consegne, in quanto l’invio a tali contatti potrebbe danneggiare la reputazione del mittente e le percentuali di consegna. Al momento, Adobe mantiene un elenco aggiornato degli indirizzi e-mail non validi noti che si sono dimostrati dannosi per il coinvolgimento e la reputazione di invio e garantisce che le e-mail non vengano inviate a tali utenti. Questo elenco viene gestito in un elenco di soppressione globale comune a tutti i clienti Adobe. Gli indirizzi e i nomi di dominio contenuti nell’elenco di soppressione globale sono nascosti. Nei rapporti di consegna è indicato solo il numero di destinatari esclusi.

È ora possibile gestire l’elenco di soppressione globale da un’interfaccia disponibile internamente. Questo elenco verrà gestito solo dai consulenti del team Deliverability. L’elenco di soppressione globale può includere indirizzi e-mail o di dominio.

## Accedere all’elenco di soppressione globale

Per accedere all’elenco dettagliato degli indirizzi e-mail e dei domini esclusi, vai a **[!UICONTROL Elenco di soppressione globale]**.

>[!CAUTION]
>
>Le autorizzazioni per visualizzare, esportare e gestire l’elenco di soppressione globale dipendono dalla lista di distribuzione a cui sono assegnati. Per saperne di più

Vengono visualizzate due schede: **[!UICONTROL E-mail]** e **[!UICONTROL Dominio]**.

Sono disponibili filtri per aiutarti a sfogliare l’elenco.

## Aggiungere indirizzi e domini

Attualmente esistono due modi per aggiungere indirizzi all’elenco di soppressione globale:

* Elenco curato dal team di recapito messaggi.
* Elenco fornito dal fornitore di servizi di terze parti Blackbox.

Puoi aggiungere indirizzi e-mail o domini [uno alla volta](#add-one-address-or-domain), o [in modalità collettiva](#upload-csv-file) tramite un caricamento di file CSV.

A questo scopo, seleziona la **[!UICONTROL Aggiungi e-mail o dominio]** , quindi seguire uno dei metodi seguenti.

### Aggiungi un indirizzo o dominio {#add-one-address-or-domain}

1. Seleziona la **[!UICONTROL Uno per uno]** opzione.

1. Scegliere il tipo di indirizzo: **[!UICONTROL Indirizzo e-mail]** o **[!UICONTROL Indirizzo del dominio]**.

1. Immetti l’indirizzo e-mail o il dominio da escludere dall’invio.

   >[!NOTE]
   >
   >Assicurati di immettere un indirizzo e-mail valido (ad esempio abc@company.com) o un dominio (ad esempio abc.company.com).

1. Se necessario, specifica un motivo.

   >[!NOTE]
   >
   >In questo campo sono consentiti tutti i caratteri stampabili ASCII compresi tra 32 e 126. L&#39;elenco completo è disponibile su [questa pagina](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} ad esempio.

1. Clic **[!UICONTROL Invia]** per confermare.

### Carica un file CSV {#upload-csv-file}

1. Seleziona la **[!UICONTROL Carica CSV]** opzione.

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

1. Inserisci nel modello CSV gli indirizzi e-mail e/o i domini che desideri aggiungere all’elenco di soppressione.

   >[!NOTE]
   >
   >Tutti i caratteri ASCII compresi tra 32 e 126 sono consentiti nel **Commento** colonna. L&#39;elenco completo è disponibile su [questa pagina](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} ad esempio.

1. Al termine, trascina e rilascia il file CSV, quindi fai clic su **[!UICONTROL Invia]** per confermare.

>[!NOTE]
>
>Al termine del caricamento, assicurati che sia riuscito controllandone lo stato dall’interfaccia. [Scopri come](#recent-uploads)

### Verifica stato caricamenti recenti {#recent-uploads}

Fai clic su **[!UICONTROL Caricamenti recenti]** per controllare lo stato degli ultimi file CSV caricati.

I possibili stati sono:

* **[!UICONTROL In sospeso]**: caricamento del file in corso.
* **[!UICONTROL Errore]**: il processo di caricamento del file non è riuscito a causa di un problema tecnico o di un errore nel formato del file.
* **[!UICONTROL Completa]**: processo di caricamento del file completato correttamente.

Durante il caricamento, se alcuni indirizzi non sono nel formato corretto, non vengono aggiunti all’elenco di soppressione globale.

In tal caso, quando il caricamento è completo, viene associato a un rapporto. Puoi scaricarlo per verificare gli errori riscontrati.

## Rimuovi indirizzi

Per rimuovere un indirizzo dall’elenco di soppressione globale, utilizza **[!UICONTROL Elimina]** pulsante.

>[!CAUTION]
>
>Gli indirizzi o i domini aggiunti automaticamente dal provider di servizi di terze parti Blackbox non possono essere rimossi dai consulenti tramite l’interfaccia. Questa operazione può essere eseguita solo tramite un ticket di back-end.
