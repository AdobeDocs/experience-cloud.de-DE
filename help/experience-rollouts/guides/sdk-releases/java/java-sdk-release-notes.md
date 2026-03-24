---
title: Java SDK - Versionshinweise
description: Versionshinweise für Experience Rollouts Java SDK mit einem Änderungsprotokoll mit neuen Funktionen, Verbesserungen und Fehlerbehebungen in allen veröffentlichten Versionen.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 2%

---


# Java SDK - Versionshinweise {#java-sdk-release-notes}

Auf dieser Seite wird der Versionsverlauf der Experience Rollouts Java-SDK aufgelistet. Informationen zum Einrichten der Integration finden Sie [Java SDK-Integrationshandbuch](java-sdk-integration-guide.md).

## Version 4.0.6 {#v4-0-6}

**Kontrollgruppendaten in Antworten**

Sie können jetzt Varianten- und Kontrollgruppendaten in der SDK-Antwort abrufen, die dem Verhalten der REST Feature APIs entsprechen. Um dies zu aktivieren, fügen Sie `.includeControlGroup()` zu Ihrem `FloodgateConfiguration` Builder hinzu.

## Version 4.0.5 {#v4-0-5}

**Stabilität und Leistungsverbesserungen**

Geringfügige interne Verbesserungen der Cache-Aktualisierungszuverlässigkeit und der Verbindungsverarbeitung.

## Version 4.0.4 {#v4-0-4}

**Richtlinienverbesserungen wiederholen**

Das standardmäßige Wiederholungsverhalten bei vorübergehenden Service-Fehlern wurde verbessert.

## Version 4.0.3 {#v4-0-3}

**Fehlerkorrekturen**

Allgemeine Stabilitätskorrekturen für Edge-Fälle bei asynchroner Initialisierung.

## Version 4.0.1 (Beta) {#v4-0-1-beta}

**Beta-Version von SDK 4.x**

Einführung von DX-Client-Unterstützung, DX-Regionskonfiguration und Unterstützung für AEP (Sandbox).

## Version 3.1.0 {#v3-1-0}

**Streaming-Unterstützung für DX-Clients**

SSE-basiertes Streaming wurde hinzugefügt, um SDK-Clients nahezu in Echtzeit über Flag-Aktualisierungen zu informieren.

## Version 3.0.x {#v3-0-x}

**Java 11-Anforderung eingeführt**

Ab Version 3.0.0 ist für SDK JDK 11 oder höher erforderlich. Frühere Hauptversionen unterstützen JDK 8+.

Einführung der Unterstützung für Verweise auf Zielgruppen für DX-Clients, sodass wiederverwendbare Zielgruppendefinitionen anhand der ID in Funktionsentitäten referenziert werden können.

## Version 2.x {#v2-x}

**Nicht zwischenspeicherbare Client-Unterstützung (ab 0.8)**

Nicht Cache-taugliche Clients können `getFeature()` Live aufrufen, anstatt aus dem SDK-Cache zu lesen. Die SDK fragt im Hintergrund weiter ab und wechselt zur Cache-basierten Bereitstellung, wenn der Client zwischenspeicherbar wird.

Zu den zusätzlichen Verbesserungen der Version 2.x gehörten neue Builder-Optionen (`alwaysCache()`-, `neverCache()`-, benutzerdefinierte HTTP-Client- und Executor-Unterstützung), Filter für Funktionen und Versionsschlüssel sowie der Abruf verkörperter Benutzender.

## Version 1.x {#v1-x}

Erste Release-Reihe. Unterstützte JDK 8+, Maven-Abhängigkeitsintegration und einfacher Abruf authentifizierter und anonymer Feature Flag.

## Siehe auch {#see-also}

* [Java SDK-Integrationshandbuch](java-sdk-integration-guide.md)
* [Versionshinweise zu Node.js SDK](../../sdk-releases/nodejs/nodejs-sdk-release-notes.md)
* [SDKs](../../integrate/sdks.md)
