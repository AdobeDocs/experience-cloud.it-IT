---
title: Elenco di soppressione globale
description: Scopri l’elenco di soppressione globale
hide: true
exl-id: 40aef987-52a3-470b-88ca-c716a116bdfc
source-git-commit: b66e2525694c771ebb7ac5190b7259ef5658d81a
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 100%

---

# Elenco di soppressione globale {#global-suppression-list}

Un elenco di soppressione è costituito da indirizzi e-mail che i clienti desiderano escludere dalle consegne, in quanto l’invio a tali contatti potrebbe danneggiare la reputazione del mittente e i tassi di consegna. Al momento, Adobe possiede un elenco aggiornato di indirizzi e-mail non validi noti, che hanno dimostrato di essere deleteri per il coinvolgimento e la reputazione e garantisce che tali indirizzi non ricevano e-mail. Tale elenco viene gestito in un elenco di soppressione globale comune a tutti i clienti di Adobe. Gli indirizzi e i nomi di dominio contenuti nell’elenco di soppressione globale sono nascosti. Nei rapporti sulle consegne è indicato solo il numero di destinatari esclusi.

È ora possibile gestire l’elenco di soppressione globale da un’interfaccia disponibile internamente. Questo elenco sarà gestito solo dai consulenti del servizio di recapito dei messaggi. L’elenco di soppressione globale può includere indirizzi e-mail o di dominio.

## Accesso all’elenco di soppressione globale

Per accedere all’elenco dettagliato degli indirizzi e-mail e dei domini esclusi, vai all‘**[!UICONTROL Elenco di soppressione globale]**.

>[!CAUTION]
>
>Le autorizzazioni per visualizzare, esportare e gestire l’elenco di soppressione globale dipendono dalla lista di distribuzione a cui si è assegnati. Ulteriori informazioni

Vengono visualizzate due schede: **[!UICONTROL E-mail]** e **[!UICONTROL Dominio]**.

Sono disponibili alcuni filtri che consentono di sfogliare l’elenco.

## Aggiungere indirizzi e domini

Per aggiungere gli indirizzi all’elenco di soppressione globale attualmente sono disponibili due modi:

* Elenco curato dal team di recapito dei messaggi.
* Elenco fornito dal fornitore di servizi di terze parti Blackbox.

È possibile aggiungere indirizzi e-mail o domini [uno alla volta](#add-one-address-or-domain) oppure [in blocco](#upload-csv-file) tramite il caricamento di un file CSV.

Per farlo, seleziona il pulsante **[!UICONTROL Aggiungi e-mail o dominio]** e poi esegui uno dei metodi seguenti.

### Aggiungi un indirizzo o un dominio {#add-one-address-or-domain}

1. Seleziona l’opzione **[!UICONTROL uno alla volta]**.

1. Scegli il tipo di indirizzo: **[!UICONTROL Indirizzo e-mail]** o **[!UICONTROL Indirizzo di dominio]**.

1. Inserisci l’indirizzo e-mail o il dominio che desideri escludere dall’invio.

   >[!NOTE]
   >
   >Assicurati di inserire un indirizzo e-mail valido (ad esempio abc@company.com) o un dominio (ad esempio abc.company.com).

1. Se necessario, specifica un motivo.

   >[!NOTE]
   >
   >In questo campo sono consentiti tutti i caratteri ASCII stampabili compresi tra 32 e 126. L&#39;elenco completo è disponibile su [questa pagina](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} di esempio.

1. Fai clic su **[!UICONTROL Invia]** per confermare.

### Caricare un file CSV {#upload-csv-file}

1. Seleziona l’opzione **[!UICONTROL Carica CSV]**.

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
   >Tutti i caratteri ASCII compresi tra 32 e 126 sono consentiti nella colonna **Commento**. L&#39;elenco completo è disponibile su [questa pagina](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"} di esempio.

1. Al termine, trascina il file CSV, quindi fai clic su **[!UICONTROL Invia]** per confermare.

>[!NOTE]
>
>Una volta completato il caricamento, accertati che sia riuscito controllandone lo stato dall’interfaccia. [Scopri come](#recent-uploads)

### Controllare lo stato dei caricamenti recenti {#recent-uploads}

Fai clic sul pulsante **[!UICONTROL Caricamenti recenti]** per controllare lo stato dei file CSV caricati più recenti.

Gli stati possibili sono:

* **[!UICONTROL In sospeso]**: il caricamento del file è in elaborazione.
* **[!UICONTROL Errore]**: il processo di caricamento dei file non è riuscito a causa di un problema tecnico o di un errore di formato del file.
* **[!UICONTROL Completato]**: il processo di caricamento del file è stato completato.

Durante il caricamento, se alcuni indirizzi non sono nel formato corretto, non vengono aggiunti all’elenco di soppressione globale.

In tal caso, una volta completato il caricamento, viene associato a un rapporto. È possibile scaricarlo per verificare gli errori rilevati.

## Rimuovere gli indirizzi

Per rimuovere un indirizzo dall’elenco di soppressione globale, utilizza il pulsante **[!UICONTROL Elimina]**.

>[!CAUTION]
>
>Gli indirizzi o i domini aggiunti automaticamente dal fornitore di servizi di terze parti Blackbox non possono essere rimossi dai consulenti tramite l’interfaccia. Questo può essere effettuato solamente tramite un ticket di back-end.
