---
title: Interfaccia utente web di Adobe Campaign
description: Tabelle a 64 bit
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 47b06a42fad73254025d8e21d14724f6fe93345b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 1%

---


# Schemi a 64 bit {#64-bit-tables}

Per facilitare la transizione da Campaign Standard a Campaign v8, diverse tabelle sono state modificate da 32 a 64 bit. In effetti, Campaign Standard supporta la PK a 64 bit in diversi schemi predefiniti, mentre Campaign v8 supporta la PK a 32 bit nella maggior parte degli schemi.

## Limitazioni

* Questa modifica tecnica si applica solo ai clienti che eseguono la migrazione da Campaign Standard.
* Lo schema e l’estensione broadlog non sono supportati in 64 bit. Rimarrà in 32 bit.
* I registri relativi alle consegne inviate agli utenti tecnici non saranno disponibili in Campaign v8.
* È supportato solo PostgreSQL.

## Schemi modificati

Elenco degli schemi modificati a 64 bit e dei relativi attributi modificati.

| Nome dello schema | Nome attributo |
|--- |--- |
| nms:broadLogRcp | id |
| nms:trackingLogRcp | id |
| nms:excludeLogRcp | id |
| nms:broadLogVisitor | id |
| nms:trackingLogVisitor | id |
| nms:propositionRcp | interfaceId |
| nms:propositionVisitor | interfaceId |
| nms:webTrackingLog | id |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | id |
| nms:trackingLogAppSubRcp | id |
| nms:excludeLogAppSubRcp | id |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |


