---
title: Node.js-Integrationshandbuch für SDK
description: Erfahren Sie, wie Sie die Node.js-SDK zu Experience Rollouts in Ihren Backend-Service integrieren, um Feature Flags abzurufen und zu bewerten.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 2%

---


# Node.js-Integrationshandbuch für SDK {#nodejs-sdk-integration-guide}

Die Node.js-SDK in Experience Rollouts ist eine Server-seitige Bibliothek für Node.js-Services. Er speichert Feature Flag-Daten lokal zwischen und wertet Flags ohne einen synchronen API-Aufruf bei jeder Anfrage aus.

>[!NOTE]
>
>Die Node.js-SDK ist nur für die Server-seitige Verwendung konzipiert. Rufen Sie bei Client-seitigen Web-Anwendungen den REST-Endpunkt der Feature API V3 direkt auf.

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Integration von Node.js in SDK Folgendes sicher:

* Eine Server-seitige Node.js-Anwendung
* Ein **API-Schlüssel** und **Service-Token** die über Adobe Developer Console abgerufen wurden - siehe [API-Anwendung abonnieren](../../integrate/subscribe-to-api-application.md)
* Ihre **Anwendungs-Client** IDs) wurden in der Konsole „Experience Rollouts“ registriert. Siehe [Onboarden Ihrer Anwendung](../../applications/onboard-your-application.md)

## Installieren des SDK {#install}

Fügen Sie die SDK zur `package.json` Ihres Projekts hinzu:

```json
"@floodgate/fg-client-sdk": "~1.0.10"
```

Dann erfordern Sie dies in Ihrem Code:

```javascript
const { floodgateClient } = require('@floodgate/fg-client-sdk');
```

## SDK initialisieren {#initialize}

`createInstance()` einmal beim Programmstart aufrufen:

```javascript
floodgateClient.createInstance(
  {
    adobeIoApiKey: "<YOUR_API_KEY>",
    clientIds: ["<CLIENT_ID_1>", "<CLIENT_ID_2>"],
    env: "PRD",    // Use "STG" for Stage
    featureRequestHttpParams: {
      timeout: 60 * 1000  // Optional: request timeout in ms
    },
    ingestAnalyticsHttpParams: {
      timeout: 5 * 1000   // Optional: analytics timeout in ms
    }
  },
  function(cb) {
    // Fetch a fresh service token from IMS and pass it in the callback
    cb(null, SERVICE_TOKEN);
  },
  function() {
    return true;  // Return false to disable analytics
  },
  function(response) {
    // Called when the SDK initializes successfully
    console.log("SDK initialized");
  },
  function(err) {
    // Called if initialization fails
    console.error("SDK init error:", err);
  }
);
```

## Funktions-Flags abrufen {#retrieve-features}

Feature Flags werden in einem Callback asynchron zurückgegeben. Wählen Sie die entsprechende Methode basierend auf Ihrem Benutzerkontext aus.

### Authentifizierter Benutzer {#authenticated-user}

```javascript
floodgateClient.getFeatures(
  {
    userAccessToken: "<USER_ACCESS_TOKEN>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: true
  },
  function(err, features) {
    if (err) {
      // Handle error and serve default experience
      return;
    }
    const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");
    // Serve experience based on isEnabled
  }
);
```

### Anonymer Benutzer {#anonymous-user}

Wenn kein Benutzerzugriffs-Token verfügbar ist, verwenden Sie ein Release-Flag oder lassen Sie das Token weg, um vollständige Rollout-Versionen zu erhalten:

```javascript
floodgateClient.getFeatures(
  {
    releaseFlag: "<RELEASE_FLAG>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: false
  },
  callback
);
```

### Standardmäßige Versionen für den vollständigen Rollout {#default-releases}

Wenn weder ein Zugriffs-Token noch ein Release-Flag angegeben wird, gibt SDK Funktionen im Status **Vollständiger Rollout** oder **Baseline** zurück:

```javascript
floodgateClient.getFeatures(
  {
    clientId1: "<CLIENT_ID>",
    visitorId: "<VISITOR_ID>",
    meta: false
  },
  callback
);
```

## Überprüfen, ob eine Funktion aktiviert ist {#check-feature}

```javascript
const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

## Debug-Protokollierung aktivieren {#debug-logging}

Um ausführliche SDK-Protokolle zu aktivieren, übergeben Sie beim Aufruf von `createInstance()` eine Protokollierungsinstanz auf Debugging-Ebene:

```javascript
const bunyan = require('bunyan');
const logger = bunyan.createLogger({ name: "fg", sourceType: "SDK", level: "debug" });

floodgateClient.createInstance(
  { ..., log: logger },
  ...
);
```

## Siehe auch {#see-also}

* [Versionshinweise zu Node.js SDK](nodejs-sdk-release-notes.md)
* [SDKs](../../integrate/sdks.md)
* [Abonnieren des API-Programms](../../integrate/subscribe-to-api-application.md)
* [Integrationsschritte](../../integrate/integration-steps.md)
