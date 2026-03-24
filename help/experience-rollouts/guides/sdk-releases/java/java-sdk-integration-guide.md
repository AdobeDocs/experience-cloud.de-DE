---
title: Java SDK-Integrationshandbuch
description: Erfahren Sie, wie Sie die Experience Rollouts Java SDK in Ihren Backend-Service integrieren, um Feature Flags abzurufen und auszuwerten.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 2%

---


# Java SDK-Integrationshandbuch {#java-sdk-integration-guide}

Experience Rollouts Java SDK ist eine Server-seitige Bibliothek, die Feature Flag-Daten lokal zwischenspeichert und Flags ohne einen synchronen API-Aufruf bei jeder Anfrage auswertet. In diesem Handbuch wird die aktuelle SDK (4.x) behandelt.

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Integration der Java-SDK Folgendes sicher:

* JDK 11 oder höher (ab SDK Version 3.0.0 erforderlich; frühere Versionen unterstützen JDK 8 oder höher)
* Ein Maven-basiertes Build-System
* Einen **API-Schlüssel** und **Service-Token** Client-ID aus Ihrem Adobe Developer Console-Projekt - siehe [API-Anwendung abonnieren](../../integrate/subscribe-to-api-application.md)
* Ihre **Anwendungs-Client** IDs) wurden in der Konsole „Experience Rollouts“ registriert. Siehe [Onboarden Ihrer Anwendung](../../applications/onboard-your-application.md)

## Hinzufügen der Maven-Abhängigkeit {#maven-dependency}

Fügen Sie die Experience Rollouts Java SDK zur `pom.xml` Ihres Projekts hinzu:

```xml
<dependency>
  <groupId>com.adobe.cloudtech</groupId>
  <artifactId>fg-client-sdk</artifactId>
  <version>4.0.6</version>
</dependency>
```

## SDK initialisieren {#initialize}

Die SDK wird einmal beim Start der Anwendung mit `FloodgateClient.createInstance()` initialisiert. Die Methode verwendet ein `FloodgateConfiguration`, das Sie mit dem Konfigurations-Builder erstellen.

### Implementieren des Service-Token-Callbacks {#service-token-callback}

SDK verwendet eine Rückruffunktion, um zur Laufzeit ein neues Service-Token abzurufen:

```java
private class FgConfigCallBack implements FGConfigBaseCallBack {

  @Override
  public String getIMSServiceToken() {
    // Fetch and return a valid service token
  }

  @Override
  public boolean isAnalyticsEnabled() {
    return false; // Set to true to enable analytics
  }
}
```

### Erstellen des Konfigurationsobjekts {#configuration}

Verwenden Sie den Konfigurations-Builder, um die SDK einzurichten:

```java
FloodgateConfiguration configuration = FloodgateConfiguration.FloodgateConfigurationBuilder
    .aFloodgateConfiguration(
        FgEnv.PRD,                   // Use FgEnv.STG for Stage
        "<YOUR_API_KEY>",
        Set.of("<CLIENT_ID_1>", "<CLIENT_ID_2>"),
        new FgConfigCallBack(),
        CallType.ASYNC
    )
    .withRetryPolicy(retryPolicy)    // Optional: defaults to 5 retries, 10s interval
    .build();
```

Verwenden Sie `FgEnv.STG` für die Staging-Umgebung und `FgEnv.PRD` für die Produktion.

### Erstellen der Client-Instanz {#client-instance}

```java
FloodgateClient fgClient = FloodgateClient.createInstance(configuration);
```

## Funktions-Flags abrufen {#retrieve-features}

### Authentifizierter Benutzer {#authenticated-user}

IMS-Zugriffstoken verwenden, um Feature Flags für den aktuellen Benutzer abzurufen:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<USER_ACCESS_TOKEN>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Anonymer Benutzer {#anonymous-user}

Übergeben Sie bei nicht authentifizierten Benutzern eine Besucher-ID und Ihr Service-Token:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withServiceToken("<SERVICE_TOKEN>")
    .withVisitorId("<VISITOR_ID>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Abrufen eines bestimmten Feature Flags oder einer Version {#specific-feature}

So rufen Sie ein Feature Flag nach Schlüssel ab:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<ACCESS_TOKEN>")
    .withFeatureKey("<FEATURE_KEY>")
    .build();
```

Um nach Versionsschlüssel abzurufen, ersetzen Sie `.withFeatureKey()` durch `.withReleaseKey()`.

## Überprüfen, ob eine Funktion aktiviert ist {#check-feature}

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

Für freigabebasierte Prüfungen:

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_RELEASE", "MY_FEATURE_FLAG");
```

## Cache-Verwaltung {#cache-management}

Die SDK speichert Feature Flag-Daten zwischen und aktualisiert sie in einem Abrufintervall, das pro Anwendung in der Konsole festgelegt wurde. So führen Sie eine On-Demand-Cache-Aktualisierung durch:

```java
fgClient.refreshClientCache("<CLIENT_ID>");
```

### Nicht zwischenspeicherbare Clients {#non-cacheable}

Für nicht zwischenspeicherbare Clients führt `getFeature()` jedes Mal einen Live-API-Aufruf durch. Die SDK führt die Hintergrundabfrage fort und wechselt zur Cache-basierten Bereitstellung, wenn der Client zwischenspeicherbar wird. Unterstützt ab SDK Version 0.8.

## Konfigurationsoptionen {#configuration-options}

Die folgenden optionalen Konfigurationsmethoden sind in Builder verfügbar:

| Option | Methode | Beschreibung |
|---|---|---|
| Cache immer verwenden | `.alwaysCache()` | Umgeht das Zwischenspeichern der Antwort von der API; verwenden Sie für Flags ohne Zielgruppenregeln |
| Zwischenspeicherung deaktivieren | `.neverCache()` | Deaktiviert das Standard-Caching; nützlich für benutzerdefinierte Cache-Aktualisierungslogik |
| Benutzerdefinierter HTTP-Client | `.withHttpClient(client)` | Eigenen HTTP-Client verwenden |
| Benutzerdefinierter Executor | `.withScheduledExecutorService(executor)` | Eigener geplanter Executor für Hintergrundabfragen verwenden |
| Kontrollgruppe einschließen | `.includeControlGroup()` | Gibt Kontrollgruppendaten in der Funktionsantwort zurück. |

## Fehler beheben {#error-handling}

`getFeatures()`-Aufrufe verarbeiten, um SDK-Ausnahmen abzufangen:

```java
try {
  features = fgClient.getFeatures(request);
} catch (FgClientException e) {
  int statusCode = e.getStatusCode();
  // Handle error and serve default experience
} catch (FgInitException e) {
  e.printStackTrace();
}
```

## Siehe auch {#see-also}

* [Java SDK - Versionshinweise](java-sdk-release-notes.md)
* [SDKs](../../integrate/sdks.md)
* [Abonnieren des API-Programms](../../integrate/subscribe-to-api-application.md)
* [Integrationsschritte](../../integrate/integration-steps.md)
