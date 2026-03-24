---
title: GET Feature API v2
description: API-Referenz für die Experience Rollouts Feature API V2, mit der Feature Flags für Desktop-Programme abgerufen werden.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 12%

---


# GET Feature API v2 {#get-feature-api-v2}

Die Feature API V2 wurde für die Integration von Desktop-Programmen entwickelt. Es ruft Feature Flags und Release-Daten für den authentifizierten Benutzer ab und unterstützt neben einer Standard-Client-ID Produkt-Code und Produktversion als Anwendungs-ID.

**Endpunkt:** `GET {HOST}/fg/api/v2/feature`

Verwenden Sie `https://p13-stage.adobe.io` für die Staging- und `https://p13n.adobe.io` für die Produktion.

## Anfrage {#request}

### Anfrage-Header {#request-headers}

| Header | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `x-api-key` | Zeichenfolge | Der API-Schlüssel Ihres Programms aus der Adobe Developer Console. Muss für die Staging- und Produktionsumgebung separat bereitgestellt werden. | Ja |
| `Authorization` | Zeichenfolge | `Bearer <AccessToken>` oder `Bearer <ServiceToken>`. | Ja |
| `x-adobe-uuid` | Zeichenfolge | Eine Unique Visitor- oder Geräte-ID. Wird für den prozentualen Rollout in nicht authentifizierten Szenarien und zur Beibehaltung der Sitzungskonsistenz verwendet. | Nein |

### Abfrageparameter {#query-parameters}

| Parameter | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `clientId` | Zeichenfolge | Die Client-ID der Anwendung, wie in der Konsole „Experience Rollouts“ integriert. Es können mehrere Werte übergeben werden: `clientId=C1&clientId=C2`. | Nein |
| `p` | Zeichenfolge | Produkt, Version, Plattform, Gebietsschema-Zeichenfolge (PVPL-Format). Beispiel: `PHSP:17.0:WIN:en_US`. Es können mehrere Werte übergeben werden: `p=PHSP:17.0:WIN:en_US&p=PPRO:8:WIN:en_US`. Bei der Auswertung werden nur der Produkt-Code und die Produktversion verwendet. | Nein |
| `meta` | Boolesch | Wenn `true`, werden für jede Funktion Base64-kodierte Metadaten zurückgegeben. Standard: `false`. | Nein |
| *Kontextparameter* | K. A. | Jedes zusätzliche Schlüssel-Wert-Paar wird als Kontextvariable für die Auswertung von Zielgruppenregeln behandelt. Beispiel: `clientLanguage=ja_JP&contractCurrency=JPY`. | Nein |

>[!NOTE]
>
>Zur Identifizierung des Programms ist mindestens eine der `clientId` oder `p` erforderlich.

## Antwort {#response}

### Codes für Antwortstatus {#response-status}

| Status-Code | Beschreibung |
|---|---|
| `200 OK` | Im Antworttext zurückgegebene Feature Flag-Daten. |
| `304 Not Modified` | Das eTag entspricht dem aktuellen Server-Status. Keine Änderungen anwendbar, wie keine Änderungen. |
| `401 Unauthorized` | Das Autorisierungs-Token ist ungültig. |

### Antwort-Header {#response-headers}

| Header | Beschreibung |
|---|---|
| `x-request-id` | Eine eindeutige Anforderungskennung für das Debugging. Fügen Sie dies in jede Support-Anfrage ein. |
| `ETag` | Token, das den aktuellen Funktionsstatus für den Benutzer darstellt. In nachfolgenden Anfragen als `If-None-Match` übergeben. Gibt `304` zurück, wenn unverändert. |
| `x-adobe-fg-poll-interval` | TTL in Sekunden für den lokalen Cache des Clients. Rufen Sie die API erst nach Ablauf dieses Intervalls erneut auf. |

### Antworttext {#response-body}

Die Antwort ist ein JSON-Objekt mit den folgenden Feldern der obersten Ebene:

| Feld | Typ | Beschreibung |
|---|---|---|
| `api_version` | Zeichenfolge | API-Version. Internes Feld - keine Verarbeitung erforderlich. |
| `json_version` | Zeichenfolge | JSON-Schemaversion. Internes Feld - keine Verarbeitung erforderlich. |
| `ttl` | Ganzzahl | Zwischenspeichern der TTL in Sekunden. Standardwert: 300. |
| `clients` | Objekt | Zuordnung von Client-IDs (oder PVPL-Zeichenfolgen) zu ihren Versionsdaten. Jeder Schlüssel enthält die unten beschriebenen Felder. |

#### Antwortfelder pro Client {#per-client-fields}

| Feld | Beschreibung |
|---|---|
| `releases` | Array von Versionen, für die der Benutzer berechtigt ist. Siehe [Felder für Versionen](#releases-fields) unten. |
| `client_analytics_params` | Analytics-Konfigurationsobjekt Siehe [client_analytics_params_fields](#analytics-fields) unten. |

#### Felder für Versionen {#releases-fields}

| Feld | Beschreibung |
|---|---|
| `release_name` | Name der Version oder der Funktionsgruppe. |
| `bit_index` | Freigabe-Bit-Index. Veraltet. Kann je nach Freigabestatus `null` oder negativ sein. |
| `features` | Array von Feature Flag-Schlüsseln, für die der Benutzer geeignet ist. Ein Funktionsschlüssel wird nur angezeigt, wenn der Benutzer berechtigt ist und das Flag aktiviert ist. |
| `meta` | Optionale Base64-kodierte Metadaten. Vor der Verwendung decodieren. |
| `release_analytics_params` | Analytics-Metadaten für geeignete Funktionen. In Szenarien mit Kontrollgruppen ist `features` leer. |

#### release_analytics_params_fields {#release-analytics-params}

| Feld | Typ | Beschreibung |
|---|---|---|
| `app_id` | Ganzzahl | Anwendungs-ID. |
| `release_id` | Ganzzahl | Release-ID. |
| `bit_index` | Ganzzahl | Veraltet. |
| `variant_id` | Ganzzahl | `0` wenn Kontrollgruppe; andernfalls ungleich null. |
| `feature_id` | Ganzzahl | Interne Funktionskennung. |
| `f_key` | Zeichenfolge | Feature Flag-Schlüssel. |

#### client_analytics_params-Felder {#analytics-fields}

| Feld | Typ | Beschreibung |
|---|---|---|
| `app_id` | Ganzzahl | Anwendungs-ID. |
| `safe_event_required` | Boolesch | `true`, ob Retargeting-Ereignisse aktiviert sind. |
| `analytics_required` | Boolesch | `false`, ob die Analyse deaktiviert oder im Standardfluss ist; `true`, ob der Kinesis-Fluss aktiviert ist. |

## Beispielanfrage und -antwort {#sample}

### Beispielanforderung {#sample-request}

```http
GET /fg/api/v2/feature?clientId=MyDesktopApp&p=PHSP:17.0:WIN:en_US&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Beispielantwort {#sample-response}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "PHSP:17.0:WIN:en_US": {
      "analyticsVersion": "1.0",
      "releases": []
    },
    "MyDesktopApp": {
      "analyticsVersion": "1.0",
      "client_analytics_params": {
        "app_id": 388,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": 160,
          "release_name": "||features||",
          "features": ["feature_a", "feature_b"],
          "release_analytics_params": [
            {
              "app_id": 388,
              "release_id": -1,
              "bit_index": 160,
              "variant_id": 10031741,
              "feature_id": 2918,
              "f_key": "feature_a"
            }
          ],
          "meta": []
        }
      ]
    }
  },
  "ttl": 300
}
```

## Siehe auch {#see-also}

* [GET Feature API v3](get-feature-api-v3.md)
* [Desktop-Programme](../guides/integrate/desktop-applications.md)
* [Integrationsschritte](../guides/integrate/integration-steps.md)
