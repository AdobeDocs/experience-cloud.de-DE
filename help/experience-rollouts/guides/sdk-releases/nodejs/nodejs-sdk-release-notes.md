---
title: Versionshinweise zu Node.js SDK
description: Versionshinweise für die Node.js-SDK zu Experience Rollouts mit einem Änderungsprotokoll mit neuen Funktionen, Verbesserungen und Fehlerbehebungen in allen veröffentlichten Versionen.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---


# Versionshinweise zu Node.js SDK {#nodejs-sdk-release-notes}

Auf dieser Seite wird der Versionsverlauf der Node.js-SDK zu Experience Rollouts aufgelistet. Informationen zum Einrichten der Integration finden Sie unter [Node.js SDK-Integrationshandbuch](nodejs-sdk-integration-guide.md).

## Version 1.0.10 {#v1-0-10}

**Fehlerbehebungen und Socket-Verbesserungen**

* Fehlerkorrektur - Bei geplanten Cache-Aktualisierungen tritt jetzt kein `ESOCKETTIMEDOUT` mehr auf. Der `maxSockets` Parameter wurde aus `featureRequestHttpParams` und `ingestAnalyticsHttpParams` in `createInstance()` entfernt.
* Es wurde ein Fehler behoben, durch den zwischenspeicherbare Clients nach HTTP 304-Antworten (Nicht geändert) fälschlicherweise als nicht zwischenspeicherbar gekennzeichnet wurden.
* `isReleaseBitEnabled()` entfernt - diese Methode wird nicht mehr unterstützt.
* Verbesserte Protokollierungsausgabe für bessere Diagnose.
* Test- und Abdeckungsordner sind nicht mehr im veröffentlichten npm-Paket enthalten.

## Version 1.0.5 {#v1-0-5}

**Stabilitätsverbesserungen**

Allgemeine Fehlerbehebungen für die Cache-Aktualisierungsverarbeitung und Edge-Fälle zur SDK-Initialisierung.

## Version 1.0.3 {#v1-0-3}

**Erste stabile Version**

Erste Produktionsversion der Node.js-SDK, die den Abruf authentifizierter, anonymer und standardmäßiger Full-Rollout-Feature-Flags unterstützt.

## Siehe auch {#see-also}

* [Node.js-Integrationshandbuch für SDK](nodejs-sdk-integration-guide.md)
* [Java SDK - Versionshinweise](../../sdk-releases/java/java-sdk-release-notes.md)
* [SDKs](../../integrate/sdks.md)
