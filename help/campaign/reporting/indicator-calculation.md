---
title: Calcolo indicatore
description: Comprendi i risultati dei rapporti con un elenco della formula di ogni metrica.
level: Intermediate
audience: end-user
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 031d5b692d9b9e4420b14ba1ab892fbafed57ec0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# Calcolo indicatore{#indicator-calculation}

>[!NOTE]
>
>Per elaborare e gestire in modo migliore volumi elevati e analisi in tempo reale, il reporting dinamico utilizza aggregazioni approssimative per le stime dei conteggi distinti. Le aggregazioni approssimative offrono un utilizzo limitato della memoria e sono spesso più veloci dei calcoli esatti.

Le tabelle seguenti forniscono l’elenco degli indicatori utilizzati nei diversi rapporti e la relativa formula di calcolo a seconda del tipo di consegna.

## Consegna e-mail {#email-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br/> </th> 
   <th> <strong>Nome campo</strong> <br/> </th> 
   <th> <strong>Formula di calcolo dell’indicatore</strong> <br/> </th> 
   <th> <strong>Commenti</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Account disabilitato<br/> </td> 
   <td> @disabled<br/> </td> 
   <td> count(@failureReason=4)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Inserire nell'elenco Bloccati Il<br/> </td> 
   <td> @blacklisted<br/> </td> 
   <td> count(@failureReason=8, @failureType=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> tasso di Inserisco nell'elenco Bloccati<br/> </td> 
   <td> @rateBlacklisted<br/> </td> 
   <td> @blacklisted/@sent<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa sul conteggio dei messaggi inviati (consegnati + non recapitati).<br/> </td> 
  </tr> 
  <tr> 
   <td> Mancati recapiti + errori<br/> </td> 
   <td> @bounces<br/> </td> 
   <td> count(@status=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Mancato recapito + Frequenza errori<br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> @bounces/@sent<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Clic<br/> </td> 
   <td> @clicks<br/> </td> 
   <td> count(@trackingUrlType=1 o 10 o 11)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Percentuale di click-through<br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> @uniqueclicks/@delivered<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa solo su Consegnato.<br/> </td> 
  </tr> 
  <tr> 
   <td> Consegnato<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> count(@status=1)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Percentuale consegne<br/> </td> 
   <td> @rateDelivered<br/> </td> 
   <td> @delivered/@sent<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa sul conteggio dei messaggi inviati (consegnati + non recapitati).<br/> </td> 
  </tr> 
  <tr> 
   <td> Mancato recapito permanente<br/> </td> 
   <td> @hardBounces<br/> </td> 
   <td> count(@failureType=2 E @failureReason=8)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Percentuale mancati recapiti permanenti<br/> </td> 
   <td> @rateHardBounces<br/> </td> 
   <td> @hardBounces/@sent<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa sul conteggio dei messaggi inviati (consegnati + non recapitati).<br/> </td> 
  </tr> 
  <tr> 
   <td> Dominio non valido<br/> </td> 
   <td> @invalidDomain<br/> </td> 
   <td> count(@failureReason=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Cassetta postale piena<br/> </td> 
   <td> @mailBoxFull<br/> </td> 
   <td> count(@failureReason=5)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Pagina mirror<br/> </td> 
   <td> @mirrorPage<br/> </td> 
   <td> count(@trackingUrlType=6)<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa solo su Consegnato.<br/> </td> 
  </tr> 
  <tr> 
   <td> Frequenza pagine mirror<br/> </td> 
   <td> @rateMirrorPage<br/> </td> 
   <td> @mirrorPage/@delivered<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Non connesso<br/> </td> 
   <td> @notConnected<br/> </td> 
   <td> count(@failureReason=6)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Apri<br/> </td> 
   <td> @uniqueOpens<br/> </td> 
   <td> count(@trackingUrlType=2 + univoco(@trackingUrlType=1,2,3,6,10,11) - univoco(@trackingUrlType=2))<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Percentuale aperture<br/> </td> 
   <td> @rateOpens<br/> </td> 
   <td> @opens/@delivered<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa solo su Consegnato.<br/> </td> 
  </tr> 
  <tr> 
   <td> Quarantena<br/> </td> 
   <td> @quarantine<br/> </td> 
   <td> isQuarantine=true<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Tasso di quarantena<br/> </td> 
   <td> @rateQuarantine<br/> </td> 
   <td> @quarantine/@sent<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa sul conteggio dei messaggi inviati (consegnati + non recapitati).<br/> </td> 
  </tr>
  <tr> 
   <td> Rifiutato<br/> </td> 
   <td> @rejected<br/> </td> 
   <td> count(@failureReason=20, @failureType=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Percentuale rifiutata<br/> </td> 
   <td> @rateRejected<br/> </td> 
   <td> @rejected/@sent<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa sul conteggio dei messaggi inviati (consegnati + non recapitati).<br/> </td> 
  </tr> 
  <tr> 
   <td> Elaborato/inviato<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @delivered + @bounces<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Mancato recapito non permanente<br/> </td> 
   <td> @softBounces<br/> </td> 
   <td> count(@failureType=1)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Percentuale mancati recapiti non permanenti<br/> </td> 
   <td> @rateSoftBounces<br/> </td> 
   <td> @softBounces/@sent<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa sul conteggio dei messaggi inviati (consegnati + non recapitati).<br/> </td> 
  </tr> 
  <tr> 
   <td> Clic univoci<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> I clic univoci vengono calcolati utilizzando i concetti di ThetaSketch. </a>.<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Aperture univoche<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> univoco(@trackingUrlType=1,2,3,6,10,11)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Non raggiungibile <br/> </td> 
   <td> @unreachable<br/> </td> 
   <td> count(@failureReason=3)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Annulla iscrizione<br/> </td> 
   <td> @unsubscribes<br/> </td> 
   <td> count(@trackingUrlType=3)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Percentuale di annullamento abbonamento<br/> </td> 
   <td> @rateUnsubscribes<br/> </td> 
   <td> @unsubscribes/@delivered<br/> </td> 
   <td> Il denominatore per il calcolo del tasso si basa solo su Consegnato.<br/> </td> 
  </tr> 
  <tr> 
   <td> Utente sconosciuto<br/> </td> 
   <td> @unknownUser<br/> </td> 
   <td> count(@failureReason=1)<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

<!--
## Push notification delivery {#push-notification-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> @rateDelivered<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> @opens<br/> </td> 
   <td> @count(status=open)<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> @rateOpens<br/> </td> 
   <td> (@opens/@delivered)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique opens<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> Unique opens is calculated using ThetaSketch concepts of unique RecipientIds.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> @clicks<br/> </td> 
   <td> @count(status=interact)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> Unique clicks is calculated using ThetaSketch concepts.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> (@interact/@delivered)*100<br/> </td> 
  </tr> 
 </tbody> 
</table>

## In-App delivery {#in-app-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
   <th> <strong>Comments</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
   <td> sent=delivered<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
   <td> delivered=sent<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=view) or @count(status=button 1 click + button 2 click + dismissals)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> @inappclicks<br/> </td> 
   <td> @count (status=click)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> @uniqueinapp<br/> </td> 
   <td> @unique(@count (status=clicks))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> @inappclickthrough<br/> </td> 
   <td> Total clicks on Button 1 or Button 2/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> @dismissal<br/> </td> 
   <td> @count (status=close)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> @uniquedismissal<br/> </td> 
   <td> @unique(@count (status=close))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> @dismissalrate<br/> </td> 
   <td> Total close/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>
-->