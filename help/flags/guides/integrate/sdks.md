---
title: SDKs
description: Erfahren Sie mehr über die SDK-Architektur in Flags und die verfügbaren AEP Web SDK- und AEP Mobile SDK-Erweiterungen.
hide: true
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 4%

---

# SDKs {#sdks}

Flags bietet SDKs zur Integration von Feature Flags in Ihre Programme. Flags werden über die AEP Web SDK und AEP Mobile SDK bereitgestellt.

## SDK-Architektur {#architecture}

Alle Flags-SDKs verwenden dieselbe Kernarchitektur:

* **Initialisierung** - Die SDK wird beim Start konfiguriert und beim Flags-Service registriert.
* **Funktionsabruf** - Die SDK ruft Feature Flag-Daten ab und wertet Flags lokal aus.
* **Caching** - Die SDK speichert Feature Flag-Daten zwischen und aktualisiert sie in einem konfigurierbaren Abrufintervall (TTL).
* **Fehlerbehandlung** - Wenn der Dienst nicht verfügbar ist, stellt SDK weiterhin Feature Flag-Auswertungen aus dem lokalen Cache bereit.

## Verfügbare SDKs {#available-sdks}

### AEP-Web-SDK {#web-sdk}

Die Flags-Erweiterung für Web ist in Adobe Experience Platform Web SDK integriert und ermöglicht so die Bewertung von Flags in Web-Anwendungen.

### Android-Erweiterung {#android-extension}

Die Flags-Erweiterung für Android lässt sich mit Adobe Experience Platform Mobile SDK integrieren.

Einrichtungsanweisungen finden Sie im Handbuch zur Integration ](../sdk-releases/android/android-extension-integration-guide.md) Android-Erweiterungen [.

### iOS-Erweiterung {#ios-extension}

Die Flags-Erweiterung für iOS lässt sich mit Adobe Experience Platform Mobile SDK integrieren.

Einrichtungsanweisungen finden Sie im Handbuch zur Integration ](../sdk-releases/ios/ios-extension-integration-guide.md) iOS-Erweiterungen [.

## Siehe auch {#see-also}

* [Handbuch zur Integration von Android-Erweiterungen](../sdk-releases/android/android-extension-integration-guide.md)
* [Web-Dienste](web-services.md)
* [Integrationsschritte](integration-steps.md)

<!-- -->
