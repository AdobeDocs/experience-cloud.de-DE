---
title: SDKs
description: Erfahren Sie mehr über die SDK-Architektur in Adobe Experience Rollouts und die verfügbare mobile SDK-Erweiterung für Android.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# SDKs {#sdks}

Experience Rollouts bietet SDKs zur Integration von Feature Flags in Ihre Programme. Auf dieser Seite werden die SDK-Architektur und die verfügbaren Optionen beschrieben.

## SDK-Architektur {#architecture}

Alle Experience Rollouts-SDKs verwenden dieselbe Kernarchitektur:

* **Initialization** - Die SDK wird beim Start konfiguriert und beim Experience Rollouts-Service registriert.
* **Funktionsabruf** - Die SDK ruft Feature Flag-Daten ab und wertet Flags lokal aus.
* **Caching** - Die SDK speichert Feature Flag-Daten zwischen und aktualisiert sie in einem konfigurierbaren Abrufintervall (TTL).
* **Fehlerbehandlung** - Wenn der Dienst nicht verfügbar ist, stellt SDK weiterhin Feature Flag-Auswertungen aus dem lokalen Cache bereit.

## Verfügbare SDKs {#available-sdks}

### Android-Erweiterung {#android-extension}

Die Experience Rollout-Erweiterung für Android ist mit Adobe Experience Platform Mobile SDK integriert.

Einrichtungsanweisungen finden Sie im Handbuch zur Integration [&#128279;](../sdk-releases/android/android-extension-integration-guide.md) Android-Erweiterungen .

>[!NOTE]
>
>Weitere SDK-Optionen für das Web und andere mobile Plattformen werden vorbereitet und werden in Kürze verfügbar sein. Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um frühzeitig Zugang zu erhalten.

## Siehe auch {#see-also}

* [Handbuch zur Integration von Android-Erweiterungen](../sdk-releases/android/android-extension-integration-guide.md)
* [Web-Dienste](web-services.md)
* [Integrationsschritte](integration-steps.md)
