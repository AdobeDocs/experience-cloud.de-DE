---
title: Adobe Campaign-Web-Benutzeroberfläche
description: 64-Bit-Tabellen
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
TQID: https://experienceleague.adobe.com/D0f4gYkyUcNVpGxpvj3JrBGRyIAgSq1mF7R4ld5COmk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 175
ht-degree: 17%

---

# 64-Bit-Schemata {#sixty-four-bit-tables}

Um den Übergang von Campaign Standard zu Campaign v8 zu erleichtern, wurden mehrere Tabellen von 32 auf 64 Bit geändert. Campaign Standard unterstützt 64-Bit-PK in mehreren vordefinierten Schemata, während Campaign v8 in den meisten Schemata 32-Bit-PK unterstützt.

## Einschränkungen

* Diese technische Änderung gilt nur für Kunden, die von Campaign Standard migrieren.
* Schema- und Broadlog-Erweiterung werden in 64 Bit nicht unterstützt. Es bleibt in 32 Bit.
* Protokolle zu Sendungen an technische Benutzende sind in Campaign v8 nicht verfügbar.
* Es wird nur PostgreSQL unterstützt.

## Geänderte Schemata

Im Folgenden finden Sie die Liste der Schemata, die auf 64 Bit geändert wurden, und ihrer geänderten Attribute.

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
| nms:webEvent | broadLogSrc-id, broadLogRemote-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
