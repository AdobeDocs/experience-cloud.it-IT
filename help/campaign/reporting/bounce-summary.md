---
title: Riepilogo messaggi non recapitati
description: Con il rapporto predefinito Riepilogo delle e-mail non consegnate, scopri lo stato delle campagne inviate e gli errori che potrebbero aver riscontrato.
audience: end-user
level: Intermediate
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: b341edad-aa82-43d8-a5a1-b33a19973a1a
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 1%

---

# Riepilogo messaggi non recapitati{#bounce-summary}

Questo rapporto descrive gli errori rigidi e morbidi riscontrati durante le consegne, nonché l’elaborazione automatica delle e-mail non consegnate.

![](assets/campaign_reports_bounces.png)

Ogni tabella è rappresentata da numeri e grafici di riepilogo. Puoi modificare la modalità di visualizzazione dei dettagli nelle rispettive impostazioni di visualizzazione.

**Partizione flop 5** elenca le cinque consegne con il maggior numero di quarantene:

La tabella **Motivi di mancato recapito** contiene i dati disponibili per i tipi di errori che hanno causato mancati recapiti per ogni consegna:

* **[!UICONTROL Utente sconosciuto]**: tipo di errore generato quando una consegna viene inviata a un indirizzo e-mail non valido.
* **[!UICONTROL Dominio non valido]**: tipo di errore generato quando una consegna viene inviata a un indirizzo e-mail il cui dominio non è corretto o non esiste più.
* **[!UICONTROL Non raggiungibile]**: tipo di errore riscontrato nella stringa di consegna del messaggio, ad esempio dominio temporaneamente non raggiungibile.
* **[!UICONTROL Account disabilitato]**: tipo di errore generato quando viene inviata una consegna a un indirizzo e-mail che non esiste più.
* **[!UICONTROL Cassetta postale piena]**: tipo di errore generato quando la casella in entrata del destinatario è piena. Ci sono cinque tentativi di recapitare il messaggio prima che questo errore venga generato.
* **[!UICONTROL Non connesso]**: tipo di errore generato quando il telefono cellulare del destinatario è spento o non è connesso a una rete al momento dell&#39;invio del messaggio.

  >[!NOTE]
  >
  >Questo tipo di errore riguarda solo le consegne sui canali mobili.

* **[!UICONTROL Rifiutato]**: tipo di errore generato quando un indirizzo viene rifiutato dal provider di servizi Internet (ISP). Ad esempio, quando una regola di sicurezza è stata applicata da un software antispam.

Nella tabella **Partizione di dominio** vengono visualizzati i problemi generali riscontrati durante le consegne in base al dominio del destinatario.
