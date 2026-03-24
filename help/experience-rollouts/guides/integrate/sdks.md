---
title: SDKs
description: Erfahren Sie mehr über die SDK-Architektur in Adobe Experience Rollouts und die verfügbaren SDKs für Java und Node.js.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 2%

---


# SDKs {#sdks}

Experience Rollouts bietet Server-seitige SDKs für die Backend-Service-Integration. Auf dieser Seite werden die SDK-Architektur und die verfügbaren Optionen beschrieben.

## SDK-Architektur {#architecture}

Alle Experience Rollouts-SDKs verwenden dieselbe Kernarchitektur:

* **Initialization** - Die SDK wird über einen `createInstance()` Aufruf konfiguriert, der ein Singleton-Objekt zurückgibt.
* **Funktionsabruf** - Die `getFeatures()` Methode ruft Feature Flag-Daten von der SDK ab.
* **Caching** - Die SDK speichert Antworten vom Experience Rollouts-Service zwischen. Ein Cache-Manager aktualisiert den Cache in einem konfigurierbaren Abrufintervall (TTL).
* **Fehlerbehandlung** - Wenn der Service eine 503 zurückgibt, behält der Cache-Manager die vorhandenen zwischengespeicherten Daten bei und führt die Bereitstellung von Feature Flag-Auswertungen fort. Wenn sich die Daten seit dem letzten Aufruf (304) nicht geändert haben, wird der Cache nicht aktualisiert.

## Voraussetzungen {#prerequisites}

Bevor Sie eine SDK integrieren, stellen Sie Folgendes sicher:

1. **Anwendungs-ID** - Die Client-ID für jede Anwendung, die in der Experience Rollouts-Konsole integriert ist.
2. **Service-Token** - Wird von SDK zum Aufrufen der Experience Rollouts-APIs im Hintergrund verwendet.
3. **API-Schlüssel** - Wird zusammen mit dem Service-Token für die API-Authentifizierung verwendet.

## Verfügbare SDKs {#available-sdks}

### Java-SDK {#java-sdk}

Die Java-SDK wird über Maven verteilt. Fügen Sie die Abhängigkeit zum zu integrierenden `pom.xml` Ihres Projekts hinzu. Bei Spring-basierten Anwendungen richtet die Maven-Abhängigkeit automatisch den SDK-Cache ein, bevor die Anwendung vollständig geladen ist.

Wichtige Spezifikationen für die Java-SDK:

* **Unterstütztes JDK:** JDK 8 und höher
* **Nicht zwischenspeicherbare Clients:** Wird ab SDK-Version 0.8 unterstützt. Bei nicht zwischenspeicherbaren Clients führt `getFeature()` einen Live-API-Aufruf durch, anstatt aus dem Cache zu lesen. Die SDK fragt im Hintergrund weiter ab und wechselt zur Cache-basierten Bereitstellung, wenn der Client zwischenspeicherbar wird.

Anweisungen zum Einrichten finden [ im Java](../sdk-releases/java/java-sdk-integration-guide.md)Handbuch zur SDK-Integration.

### Node.js-SDK {#nodejs-sdk}

Die Node.js-SDK wird über npm verteilt.

Anweisungen zum Einrichten finden [ im Handbuch ](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)Node.js-SDK-Integration“.

## Auswählen zwischen SDK und REST-API {#sdk-vs-api}

| Szenario | Empfehlung |
|---|---|
| Backend-Java- oder Node.js-Service | Verwenden des entsprechenden SDK für automatisches Caching und vereinfachte Integration |
| Andere Backend-Sprache | Direktes Verwenden der Feature API V3 - siehe den Abschnitt zur Feature API dieses Handbuchs |
| Web oder Mobile App | Direktes Verwenden der Feature API V3 - siehe den Abschnitt zur Feature API dieses Handbuchs |
| Desktop-Programm | Direktes Verwenden der Feature API V2 - siehe den Abschnitt zur Feature API dieses Handbuchs |

## Siehe auch {#see-also}

* [Web-Dienste](web-services.md)
* [Integrationsschritte](integration-steps.md)
* [Java SDK-Integrationshandbuch](../sdk-releases/java/java-sdk-integration-guide.md)
* [Node.js-Integrationshandbuch für SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
