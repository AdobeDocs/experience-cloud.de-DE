---
title: Adobe Campaign Web-Benutzeroberfläche
description: 64-Bit-Tabellen
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
source-git-commit: 47b06a42fad73254025d8e21d14724f6fe93345b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 6%

---


# 64-Bit-Schemata {#64-bit-tables}

Um den Übergang von Campaign Standard zu Campaign v8 zu erleichtern, wurden mehrere Tabellen von 32 auf 64 Bit geändert. Campaign Standard unterstützt 64-Bit-PK in verschiedenen nativen Schemata, während Campaign v8 in den meisten Schemata 32-Bit-PK unterstützt.

## Einschränkungen

* Diese technische Änderung gilt nur für Kunden, die von Campaign Standard migrieren.
* Die Schema- und Broadlog-Erweiterung wird in 64 Bit nicht unterstützt. Es bleibt in 32 Bit.
* Protokolle zu Sendungen an technische Benutzer sind in Campaign v8 nicht verfügbar.
* Nur PostgreSQL wird unterstützt.

## Geänderte Schemata

Im Folgenden finden Sie eine Liste der Schemas, die in 64 Bit geändert wurden, und ihrer geänderten Attribute.

| Schemaname | Attributname |
|--- |--- |
| nms:broadLogRcp | id |
| nms:trackingLogRcp | id |
| nms:excludeLogRcp | id |
| nms:broadLogVisitor | id |
| nms:trackingLogVisitor | id |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
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


