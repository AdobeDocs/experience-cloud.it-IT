---
title: Interfaccia utente web di Adobe Campaign
description: Tabelle a 64 bit
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti di Campaign Standard migrati"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 6baa9bef7eae1ab8ffe9ecd426c6ba4580e8c9d7
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 6%

---

# Schemi a 64 bit {#sixty-four-bit-tables}

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
| nms:broadLogRcp | ID |
| nms:trackingLogRcp | ID |
| nms:excludeLogRcp | ID |
| nms:broadLogVisitor | ID |
| nms:trackingLogVisitor | ID |
| nms:propositionRcp | interfaceId |
| nms:propositionVisitor | interfaceId |
| nms:webTrackingLog | ID |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | ID |
| nms:trackingLogAppSubRcp | ID |
| nms:excludeLogAppSubRcp | ID |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
