---
title: GET Feature API v3
description: API-Referenz für die Experience Rollouts Feature API V3, mit der Feature Flags für Web- und Mobile Apps abgerufen werden.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 9%

---


# GET Feature API v3 {#get-feature-api-v3}

Die Feature API V3 ist der primäre Endpunkt zum Abrufen von Feature Flags in Web- und Mobile Apps. Gibt die Funktionen und Versionen zurück, die ein Benutzer basierend auf seiner Identität und den in der Konsole konfigurierten Zielgruppenregeln nutzen kann.

**Endpunkt:** `GET {HOST}/fg/api/v3/feature`

Verwenden Sie `https://p13-stage.adobe.io` für die Staging- und `https://p13n.adobe.io` für die Produktion.

## Anfrage {#request}

### Anfrage-Header {#request-headers}

| Header | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `x-api-key` | Zeichenfolge | Der API-Schlüssel Ihres Programms aus der Adobe Developer Console. Muss für die Staging- und Produktionsumgebung separat bereitgestellt werden. | Ja |
| `Authorization` | Zeichenfolge | **Nicht erforderlich** für nicht authentifizierte Szenarien. Verwenden Sie `Bearer <AccessToken>` für authentifizierte Benutzer. Verwenden Sie `Bearer <ServiceToken>` für serverseitige SDK-Caching-Szenarien. | Nein |
| `x-adobe-uuid` | Zeichenfolge | Eine Unique Visitor- oder Geräte-ID. Wird verwendet, um den prozentualen Rollout für nicht authentifizierte Benutzer zu unterstützen und die Konsistenz über Sitzungen und nicht authentifizierte zu authentifizierte Transitionen hinweg aufrechtzuerhalten. | Nein |

### Abfrageparameter {#query-parameters}

| Parameter | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `clientId` | Zeichenfolge | Die Client-ID Ihrer Anwendung, wie in der Konsole „Experience Rollouts“ integriert. | Ja |
| `ignore_rf` | Boolesch | Wenn `true`, werden Release-Flags ignoriert und alle Releases für den Client zurückgegeben. Standard: `false`. | Nein |
| `rf` | Zeichenfolge | Release-Flag. Wird nur verwendet, wenn `ignore_rf` `false` ist. | Nein |
| `meta` | Boolesch | Wenn `true`, werden Metadaten für jede Funktion in die Antwort aufgenommen und als Schlüssel-Wert-Paar zurückgegeben, wobei der Wert Base64-kodiert ist. Standard: `false`. | Nein |
| `userId` | Zeichenfolge | Erfordert ein Service-Token. Die GUID des Benutzers, für den Sie Feature Flags abrufen möchten. | Nein |
| *Kontextparameter* | K. A. | Alle oben nicht aufgeführten Abfrageparameter werden als Kontextvariable behandelt und zum Auswerten von Zielgruppenregeln verwendet. Übergeben Sie mehrere Werte als `?key1=val1&key2=val2`. Beispiel: `?clientLanguage=ja_JP&contractCurrency=JPY`. | Nein |

## Antwort {#response}

### Codes für Antwortstatus {#response-status}

| Status-Code | Beschreibung |
|---|---|
| `200 OK` | Im Antworttext zurückgegebene Feature Flag-Daten. |
| `304 Not Modified` | Das vom Client übergebene eTag entspricht dem neuesten Server-Status. Dies als No-op behandeln - keine Änderungen anzuwenden. |
| `400 Bad Request` | Das `clientId` wurde nicht integriert oder die Anfrage ist fehlerhaft. |
| `403 Forbidden` | Ungültiger API-Schlüssel, da die Anwendung die Experience Rollouts-API in Adobe Developer Console nicht abonniert hat. |

### Antwort-Header {#response-headers}

| Header | Beschreibung |
|---|---|
| `x-request-id` | Eine eindeutige Anforderungskennung für das Debugging. Fügen Sie dies in jede Support-Anfrage ein. |
| `ETag` | Ein Token, das den aktuellen Serverstatus für die Funktionen dieses Benutzers darstellt. Übergeben Sie diesen Wert als `If-None-Match` in nachfolgenden Anfragen. Wenn sich der Status nicht geändert hat, gibt die API `304` zurück. |
| `x-adobe-fg-poll-interval` | Die TTL (in Sekunden) für den lokalen Cache des Clients. Rufen Sie die API erst nach Ablauf dieses Intervalls erneut auf. |

### Antworttext {#response-body}

Die Antwort ist ein JSON-Objekt mit den folgenden Feldern der obersten Ebene:

| Feld | Typ | Beschreibung |
|---|---|---|
| `api_version` | Zeichenfolge | API-Version. Internes Feld - keine Verarbeitung erforderlich. |
| `json_version` | Zeichenfolge | JSON-Schemaversion. Internes Feld - keine Verarbeitung erforderlich. |
| `ttl` | Ganzzahl | Zwischenspeichern der TTL in Sekunden. Der gleiche Wert wie die `x-adobe-fg-poll-interval`-Antwortkopfzeile. Standardwert: 300. |
| `caching_enabled` | Boolesch | Wenn `true`, erfolgt die Funktionsbewertung lokal auf dem Client. Bei `false` erfolgt die Auswertung Server-seitig bei jeder Anfrage. |
| `client_analytics_params` | Objekt | Analytics-Konfiguration für das Programm. Siehe [client_analytics_params_fields](#client-analytics-params) unten. |
| `releases` | Array | Liste der Versionen und Feature Flags, für die der Benutzer berechtigt ist. Siehe [Felder für Versionen](#releases-fields) unten. |

#### client_analytics_params-Felder {#client-analytics-params}

| Feld | Beschreibung |
|---|---|
| `app_id` | Die numerische ID der Anwendung. |
| `safe_event_required` | `true`, ob Retargeting-Ereignisse für diesen Client aktiviert sind. |
| `analytics_required` | Immer in V3-Antworten `false`. |

#### Felder für Versionen {#releases-fields}

| Feld | Beschreibung |
|---|---|
| `release_name` | Der Name der Version oder Funktionsgruppe, für die der Benutzer berechtigt ist. |
| `bit_index` | Der Release-Bit-Index. Negative Werte zeigen den Status Vollständiger Rollout an. |
| `features` | Array von Feature Flag-Schlüsseln, für die der Benutzer geeignet ist. Ein Funktionsschlüssel wird nur zurückgegeben, wenn der Benutzer berechtigt ist und das Flag sich in einem aktivierten Status befindet. Dies ist das primäre Feld, um das Ihre Anwendungslogik aufgebaut werden sollte. |
| `meta` | Optionale Base64-kodierte Metadaten, die mit der Funktion verknüpft sind. Vor der Verwendung decodieren. |
| `release_analytics_params` | Array von Analytics-Metadatenobjekten für jede geeignete Funktion. Siehe [release_analytics_params_fields](#release-analytics-params) unten. In Szenarien mit Kontrollgruppen ist `features` leer. |

#### release_analytics_params_fields {#release-analytics-params}

| Feld | Typ | Beschreibung |
|---|---|---|
| `app_id` | Ganzzahl | Anwendungs-ID. |
| `release_id` | Ganzzahl | Release-ID. |
| `bit_index` | Ganzzahl | Freigabe-Bit-Index. Veraltet. |
| `variant_id` | Ganzzahl | `0`, ob der Benutzer zur Kontrollgruppe gehört; andernfalls ist der Wert ungleich null. |
| `feature_id` | Ganzzahl | Interne Funktionskennung. |
| `f_key` | Zeichenfolge | Feature Flag-Schlüssel. |

## Beispielanfrage und -antwort {#sample}

### Beispielanforderung {#sample-request}

```http
GET /fg/api/v3/feature?clientId=MyWebApp&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Beispielantwort - Benutzer in Testgruppe {#sample-response-test}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "analyticsVersion": "2.0",
      "client_analytics_params": {
        "app_id": 1378,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": ["ff1", "ff2", "ff3"],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 10040476,
              "feature_id": 26059,
              "f_key": "ff1",
              "analytics_required": true
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

### Beispielantwort - Benutzer in Kontrollgruppe {#sample-response-control}

Wenn sich ein(e) Benutzende(r) in der Kontrollgruppe befindet, ist das `features`-Array leer und `variant_id` wird `0`:

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": [],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 0,
              "feature_id": 26059,
              "f_key": "ff1"
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

## Siehe auch {#see-also}

* [GET Feature API v2](get-feature-api-v2.md)
* [Web-Anwendungen](../guides/integrate/web-applications.md)
* [Apps](../guides/integrate/mobile-applications.md)
* [Integrationsschritte](../guides/integrate/integration-steps.md)
