---
title: Rapporto notifiche push
description: Con il rapporto preconfigurato Notifica push, scopri come le notifiche push hanno avuto esito positivo.
level: Intermediate
audience: end-user
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 1%

---

# Rapporto notifiche push{#push-notification-report}

>[!CAUTION]
>
>Tieni presente che devi trascinare la **[!UICONTROL Tipo di messaggio]** metriche alle tabelle per suddividere i dati in base ai tipi di consegna, in questo caso le consegne di notifiche push.

Il **Notifica push** Il rapporto fornisce dettagli sulle prestazioni di marketing delle notifiche push in Adobe Campaign. Questo rapporto predefinito consente di comprendere come gli utenti interagiscono con le notifiche push, le app mobili e le consegne.

![](assets/dynamic_report_push.png)

Ogni tabella è rappresentata da numeri e grafici di riepilogo. Puoi modificare la modalità di visualizzazione dei dettagli nelle rispettive impostazioni di visualizzazione.

Prima tabella **Riepilogo coinvolgimento notifiche push** è suddiviso in tre categorie: per giorno, per app mobile e per consegna. Contiene i dati disponibili per la reattività del destinatario alla consegna:

* **[!UICONTROL Elaborato/inviato]**: numero totale di notifiche push inviate.
* **[!UICONTROL Consegnato]**: numero di notifiche push inviate correttamente, in relazione al numero totale di notifiche push inviate.
* **[!UICONTROL Impression]**: numero di volte in cui una notifica push è stata recapitata al dispositivo e lasciata intatta nel centro notifiche. Nella maggior parte dei casi, il numero di impression deve essere simile al numero consegnato. In questo modo il dispositivo riceve il messaggio e invia nuovamente tali informazioni al server.
* **[!UICONTROL Impression univoche]**: numero di impression per destinatario.
* **[!UICONTROL Percentuale di click-through]**: percentuale di utenti che hanno interagito con la notifica push.
* **[!UICONTROL Percentuale aperture]**: percentuale di notifiche push aperte.

![](assets/dynamic_report_push_2.png)

La seconda tabella **Notifica push Clic e aperture** è suddiviso in tre categorie: per giorno, per app mobile e per consegna. Contiene i dati disponibili per il comportamento del destinatario per consegna:

* **[!UICONTROL Impression]**: totale delle notifiche push visualizzate dai destinatari.
* **[!UICONTROL Impression univoche]**: numero di impression per destinatario.
* **[!UICONTROL Clic]**: numero di volte in cui una notifica push è stata recapitata al dispositivo e su cui l’utente ha fatto clic. L’utente desidera visualizzare la notifica, che verrà quindi spostata nel tracciamento push aperto, oppure ignorarla.
* **[!UICONTROL Clic univoci]**: numero di volte in cui un utente univoco interagisce con la notifica push, ad esempio facendo clic sulla notifica o sul pulsante.
* **[!UICONTROL Apri]**: numero totale di notifiche push inviate al dispositivo e su cui gli utenti hanno fatto clic, con conseguente apertura dell’app. È simile al Clic push, tranne per il fatto che l’apertura push non viene attivata se la notifica viene chiusa.
* **[!UICONTROL Aperture univoche]**: numero di destinatari che hanno aperto la consegna.
