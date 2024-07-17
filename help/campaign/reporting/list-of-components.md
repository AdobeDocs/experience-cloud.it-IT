---
title: Elenco dei componenti
description: Qui trovi l’elenco di tutti i componenti disponibili in     Rapporti dinamici e relative definizioni.
level: Beginner
audience: end-user
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 5c58db92-7878-4c70-b076-a393f1cda8b7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 1%

---

# Elenco dei componenti {#list-of-components}

Se due componenti non sono compatibili, nella cella verrà visualizzato il valore **None**.

## Dimensioni {#dimensions}

La tabella seguente fornisce l’elenco delle dimensioni utilizzate nei rapporti e le relative definizioni.

<table> 
 <thead> 
  <tr> 
   <th> Dimension<br/> </th> 
   <th> Definizione<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Browser<br/> </td> 
   <td> Browser da cui è stato aperto o su cui è stato fatto clic il messaggio.<br/> </td> 
  </tr> 
  <tr> 
   <td> Campaign<br/> </td> 
   <td> Etichetta e ID della campagna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Consegna<br/> </td> 
   <td> Etichetta e ID della consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Dispositivo<br/> </td> 
   <td> Dispositivo da cui è stata aperta/visualizzata/su cui è stato fatto clic la notifica e-mail/SMS/push.<br/> </td> 
  </tr> 
  <tr> 
   <td> Motivo errore<br/> </td> 
   <td> Tipi di errori che hanno causato mancati recapiti per ogni consegna. Ad esempio, utente sconosciuto, dominio non valido o cassetta postale piena.<br/> </td> 
  </tr> 
  <tr> 
   <td> Nome app mobile<br/> </td> 
   <td> Nome dell'app mobile<br/> </td> 
  </tr>
  <tr> 
   <td> Piattaforma<br/> </td> 
   <td> Piattaforma del dispositivo da cui è stato aperto/visualizzato/su cui è stato fatto clic il messaggio.<br/> </td> 
  </tr> 
  <tr> 
   <td> Profilo<br/> </td> 
   <td> I campi di profilo predefiniti e personalizzati vengono raggruppati creati durante l'estensione della risorsa profilo.<br/> </td> 
  </tr> 
  <tr> 
   <td> Dominio destinatario<br/> </td> 
   <td> Dominio utilizzato per aprire l'e-mail.<br/> </td> 
  </tr> 
  <tr> 
   <td> Consegna ricorrente<br/> </td> 
   <td> Etichetta e ID della consegna ricorrente.<br/> </td> 
  </tr> 
  <tr> 
   <td> Dominio mittente<br/> </td> 
   <td> Dominio utilizzato per inviare l'e-mail.<br/> </td> 
  </tr> 
  <tr> 
   <td> IP mittente<br/> </td> 
   <td> IP utilizzato per inviare l'e-mail.<br/> </td> 
  </tr> 
  <tr> 
   <td> URL di tracciamento<br/> </td> 
   <td> URL su cui l'utente ha fatto clic dal messaggio.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tracciamento categoria URL<br/> </td> 
   <td> Categoria assegnata all'URL di tracciamento.<br/> </td> 
  </tr> 
  <tr> 
   <td> Etichetta URL di tracciamento<br/> </td> 
   <td> Etichetta fornita all'URL, ad esempio pagina mirror, contattaci o apri.<br/> </td> 
  </tr> 
  <tr> 
   <td> Consegna transazionale<br/> </td> 
   <td> Etichetta e ID della consegna transazionale.<br/> </td> 
  </tr> 
  <tr> 
   <td> Variante<br/> </td> 
   <td> Variante dell'e-mail in caso di test A/B.<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Metriche {#metrics}

Le tabelle seguenti forniscono l’elenco delle metriche utilizzate nei rapporti e le relative definizioni a seconda del tipo di consegna.

### Metriche e-mail {#email-and-sms-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metrica<br/> </th> 
   <th> Definizione<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Inserire nell'elenco Bloccati All'<br/> </td> 
   <td> Numero di destinatari che hanno dichiarato un'e-mail come posta indesiderata o posta indesiderata.<br/> </td> 
  </tr> 
  <tr> 
   <td> tasso di Inserisco nell'elenco Bloccati<br/> </td> 
   <td> Percentuale di consegne contrassegnate in base al inserisco nell'elenco Bloccati di.<br/> </td> 
  </tr> 
  <tr> 
   <td> Mancati recapiti + errori<br/> </td> 
   <td> Totale degli errori accumulati durante la consegna e l'elaborazione automatica della restituzione in relazione al numero totale di messaggi inviati.<br/> </td> 
  </tr> 
  <tr> 
   <td> Mancato recapito + Percentuale di errori<br/> </td> 
   <td> Percentuale di messaggi e-mail non recapitati rispetto a quelli inviati.<br/> </td> 
  </tr> 
  <tr> 
   <td> Fai clic su<br/> </td> 
   <td> Numero di volte in cui è stato fatto clic su un contenuto in una consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale di click-through<br/> </td> 
   <td> Percentuale di clic in una consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Consegnato<br/> </td> 
   <td> Numero di messaggi inviati correttamente, in relazione al numero totale di messaggi inviati.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale di consegna<br/> </td> 
   <td> Percentuale di messaggi inviati correttamente.<br/> </td> 
  </tr> 
  <tr> 
   <td> Mancato recapito<br/> </td> 
   <td> Numero totale di errori permanenti, ad esempio un indirizzo e-mail errato.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale mancati recapiti permanenti<br/> </td> 
   <td> Percentuale di consegne non riuscite a causa di errori permanenti.<br/> </td> 
  </tr> 
  <tr> 
   <td> Pagina mirror<br/> </td> 
   <td> Numero di destinatari che hanno fatto clic sul collegamento della pagina mirror.<br/> </td> 
  </tr> 
  <tr> 
   <td> Frequenza pagine mirror<br/> </td> 
   <td> Percentuale di clic sul collegamento della pagina mirror rispetto al totale dei messaggi di consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clic sull'offerta<br/> </td> 
   <td> Numero di volte in cui è stato fatto clic su un'offerta in una consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale di clic offerta<br/> </td> 
   <td> Percentuale di clic su un'offerta.<br/> </td> 
  </tr> 
  <tr> 
   <td> Apri<br/> </td> 
   <td> Numero di volte in cui un messaggio è stato aperto in una consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale aperture<br/> </td> 
   <td> Percentuale di messaggi aperti.<br/> </td> 
  </tr> 
  <tr> 
   <td> Elaborato/inviato<br/> </td> 
   <td> Numero totale di invii per la consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Quarantena<br/> </td> 
   <td> Numero di messaggi non recapitati che hanno portato alla quarantena dell'indirizzo.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale quarantena<br/> </td> 
   <td> Percentuale di quarantena rispetto ai messaggi inviati.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rifiutato<br/> </td> 
   <td> Numero di messaggi classificati come spam dai server SMTP.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale rifiutata<br/> </td> 
   <td> Percentuale di messaggi contrassegnati come rifiutati.<br/> </td> 
  </tr> 
  <tr> 
   <td> Mancato recapito non permanente<br/> </td> 
   <td> Numero totale di errori temporanei, ad esempio una casella in entrata completa.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale mancati recapiti non permanenti<br/> </td> 
   <td> Percentuale di consegne non riuscite a causa di un motivo temporaneo.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clic univoci<br/> </td> 
   <td> Numero di destinatari che hanno fatto clic su un contenuto in una consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Aperture univoche<br/> </td> 
   <td> Numero di destinatari che hanno aperto la consegna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Sottoscrizione univoca<br/> </td> 
   <td> Numero di destinatari che hanno fatto clic sul collegamento di annullamento dell'abbonamento.<br/> </td> 
  </tr> 
  <tr> 
   <td> Percentuale annullamenti abbonamento<br/> </td> 
   <td> Numero di annullamenti di abbonamenti univoci rispetto ai messaggi consegnati.<br/> </td> 
  </tr> 
  <tr> 
   <td> Annullamento sottoscrizione<br/> </td> 
   <td> Numero di clic sul collegamento di annullamento dell'abbonamento.<br/> </td> 
  </tr> 
 </tbody> 
</table>

<!--
### Push notification metrics {#push-notification-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bounces + Errors<br/> </td> 
   <td> Total of errors cumulated during delivery in relation to the total number of sent messages, e.g. errors from MCPNS or provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> Percentage of push notifications that bounced compared to push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and clicked on by the user. The user either wanted to view the notification, which will then be moved to Push Open tracking, or dismiss it.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> Percentage of users who interacted with the push notification.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Number of push notifications successfully sent, in relation to the total number of sent push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> Percentage of push notifications successfully sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and left untouched in the notification center. In most cases, impressions number should be similar to the delivered number. This ensures that the device got the message and relayed that information back to the server.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> Total number of push notifications delivered to the device and clicked on by users thus opening the app. This is similar to the Push Click except a Push Open will not be triggered if the notification was dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> Percentage of opened push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> Number of times a unique user interacts with the push notification, e.g. clicks on the notification or button.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens<br/> </td> 
   <td> Number of recipients who opened the delivery.<br/> </td> 
  </tr> 
 </tbody> 
</table>

### In-App metrics {#in-app-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Total number of In-App messages delivered to the device by the service provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Total of In-App messages seen by recipients depending on whether trigger criterion was met.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> Total number of recipients who clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> Percentage of users who clicked on Button 1 or Button 2 compared to users who saw the message.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> Total number of messages that recipients dismissed either by clicking the close button or auto-dismiss.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> Percentage of In-App messages that recipients dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of In-App messages sent from Adobe Campaign as part of the delivery sent process.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by a unique recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> Number of times recipients clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> Number of time recipients dismissed an In-App message.<br/> </td> 
  </tr> 
 </tbody> 
</table>
-->

## Segmenti {#segments}

La tabella seguente fornisce l’elenco dei segmenti utilizzati nei rapporti e le relative definizioni.

<table> 
 <thead> 
  <tr> 
   <th> Segmento<br/> </th> 
   <th> Definizione<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Età: Boomers 1<br/> </td> 
   <td> Destinatari nati dal 1946 al 1954.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: Boomers 2<br/> </td> 
   <td> Destinatari nati dal 1955 al 1965.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: da 18 a 25<br/> </td> 
   <td> Destinatari di età compresa tra 18 e 25 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: da 26 a 30<br/> </td> 
   <td> Destinatari di età compresa tra 26 e 30 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: da 31 a 40<br/> </td> 
   <td> Destinatari di età compresa tra 31 e 40 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: da 41 a 50<br/> </td> 
   <td> Destinatari di età compresa tra 41 e 50 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: generazione X<br/> </td> 
   <td> Destinatari nati dal 1966 al 1976.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: Generazione Y (Millennial)<br/> </td> 
   <td> Destinatari nati dal 1977 al 1994.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: generazione Z<br/> </td> 
   <td> Destinatari nati dal 1995 a oggi.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: maggiore di 50<br/> </td> 
   <td> Destinatari con età superiore a 50 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: meno di 25<br/> </td> 
   <td> Destinatari con età inferiore a 25 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: inferiore a 30<br/> </td> 
   <td> Destinatari con età inferiore a 30 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: inferiore a 40<br/> </td> 
   <td> Destinatari con età inferiore a 40 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: inferiore a 50<br/> </td> 
   <td> Destinatari con età inferiore a 50 anni.<br/> </td> 
  </tr> 
  <tr> 
   <td> Età: Generazione silenziosa<br/> </td> 
   <td> Destinatari nati nel 1945 o prima.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tutte le visite<br/> </td> 
   <td> Ogni destinatario<br/> </td> 
  </tr>
 </tbody> 
</table>
