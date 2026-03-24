---
title: Feature Flags Management-API
description: API-Referenz für die Experience Rollouts Feature Flags Management-API, einschließlich Endpunkten zum Abrufen, Erstellen, Aktualisieren und Löschen von Feature Flags für eine Anwendung.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 14%

---


# Feature Flags Management-API {#feature-flags-management-api}

Mit der Feature Flags Management-API können Sie Feature Flags für Ihre Anwendungen in Experience Rollouts programmgesteuert erstellen, lesen, aktualisieren und löschen.

**Basispfad:** `/m/api/v1/mgmt/feature`

Für alle Anfragen sind die in den [Allgemeine Anforderungen“ beschriebenen ](feature-management-apis-overview.md#common-requirements) erforderlich.

## Alle Feature Flags abrufen {#get-all-features}

Ruft alle Feature Flags für ein bestimmtes Programm ab.

| | |
|---|---|
| **Endpunkt** | `GET /m/api/v1/mgmt/feature` |
| **Methode** | GET |

### Abfrageparameter {#get-all-query-params}

| Parameter | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `clientId` | Ganzzahl | Numerische ID der Anwendung. Siehe [Client-ID abrufen](get-client-id.md). Erforderlich, wenn `imsClientId` nicht angegeben ist. | bedingt |
| `imsClientId` | Zeichenfolge | Client-ID im Zeichenfolgenformat der Anwendung. Erforderlich, wenn `clientId` nicht angegeben ist. | bedingt |
| `nonReleaseFeature` | Boolesch | Wenn auf `true` gesetzt, werden unabhängige Feature Flags einbezogen, die mit keiner Gruppe oder Version verknüpft sind. Erforderlich für API-basierte Workflows. | Ja |

### Antwort {#get-all-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext enthält eine Liste von Feature Flag-Objekten. |

Der Antworttext enthält ein `features`-Array. Jedes Element ist ein Feature Flag-Objekt mit den Feldern, die in der [FeatureDTO-Objektreferenz](#featuredto-object) beschrieben sind.

**Beispielantwort:**

```json
{
  "features": [
    {
      "id": 22079,
      "name": "new.FF.1",
      "clientId": 1191,
      "state": "enabled",
      "description": "first feature flag",
      "release": { "id": 2631, "name": "FF.group", "status": "SAVED" },
      "audience": null,
      "params": { "label": "new FF 1", "rolloutType": "manual" }
    },
    {
      "id": 22080,
      "name": "new.FF.2",
      "clientId": 1191,
      "state": "enabled",
      "description": "second feature flag",
      "audience": [
        {
          "id": 10034665,
          "criteria": { "and": [{ "operator": "EQ", "attr": "LOCALE", "val": "EN" }] }
        }
      ]
    }
  ]
}
```

## Feature Flag nach ID abrufen {#get-feature-by-id}

Ruft ein einzelnes Feature Flag anhand seiner numerischen ID ab.

| | |
|---|---|
| **Endpunkt** | `GET /m/api/v1/mgmt/feature/{featureId}` |
| **Methode** | GET |

### Antwort {#get-by-id-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist ein einzelnes [FeatureDTO-Objekt](#featuredto-object). |
| `400` | Ungültige Feature ID. |

## Feature Flag erstellen {#create-feature}

Erstellt ein neues Feature Flag.

| | |
|---|---|
| **Endpunkt** | `POST /m/api/v1/mgmt/feature` |
| **Methode** | POST |

### Anfragetext {#create-request-body}

Der Anfragetext ist ein „FeatureDTO[Objekt](#featuredto-object). Die folgenden Felder sind für die Erstellung erforderlich:

| Feld | Erforderlich | Anmerkungen |
|---|---|---|
| `name` | Ja | Feature Flag-Schlüssel. Maximal 50 Zeichen. Muster: `^[a-zA-Z0-9_.-]*$` |
| `clientId` | Ja | Numerische Anwendungs-ID. Siehe [Client-ID abrufen](get-client-id.md). |
| `state` | Ja | `"enabled"` oder `"disabled"` |

### Antwort {#create-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext enthält `{ "generatedFeatureId": <id> }`. |
| `400` | Ungültige Payload. |
| `403` | Unzureichende Berechtigungen für diese Client- oder Zielgruppenregel. |
| `417` | Benutzende mit der Rolle Entwickler können eine Funktion nicht mit einer öffentlichen Regel speichern. Es ist mindestens eine Zielgruppenregel erforderlich. |

**Beispielanfrage:**

```json
{
  "name": "my-new-feature",
  "clientId": 1191,
  "state": "disabled",
  "description": "A new feature flag",
  "meta": "VGVzdA==",
  "audience": [
    {
      "criteria": {
        "and": [{ "operator": "EQ", "attr": "COUNTRY", "category": "default", "ruleId": 1, "val": "US" }]
      }
    }
  ],
  "variations": [{ "variantPercentage": 100, "variantName": "Variation 1" }],
  "params": { "label": "My New Feature", "tags": [] }
}
```

## Feature Flag aktualisieren {#update-feature}

Aktualisiert ein vorhandenes Feature Flag. Übergeben Sie das vollständige [FeatureDTO-Objekt](#featuredto-object) einschließlich des `id`.

| | |
|---|---|
| **Endpunkt** | `PUT /m/api/v1/mgmt/feature` |
| **Methode** | PUT |

### Antwort {#update-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist das aktualisierte FeatureDTO-Objekt. |
| `400` | Ungültige Payload. |
| `403` | Unzureichende Berechtigungen. |
| `417` | Konflikt bei gleichzeitiger Aktualisierung. Rufen Sie zuerst die aktuelle Funktion ab und versuchen Sie es erneut mit dem neuesten `version` aus `params`. |

## Feature Flag löschen {#delete-feature}

Löscht ein Feature Flag anhand seiner numerischen ID.

| | |
|---|---|
| **Endpunkt** | `DELETE /m/api/v1/mgmt/feature/{featureId}` |
| **Methode** | DELETE |

### Antwort {#delete-response}

| Status | Beschreibung |
|---|---|
| `204` | Erfolgreich. Kein Antworttext. |
| `403` | Unzureichende Berechtigungen. |

## FeatureDTO-Objektverweis {#featuredto-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `id` | Ganzzahl | Feature Flag-ID. Nur für Update-Aufrufe erforderlich. | bedingt |
| `name` | Zeichenfolge | Feature Flag-Schlüssel (in API-Antworten zurückgegeben). Maximal 50 Zeichen. Muster: `^[a-zA-Z0-9_.-]*$` | Ja (erstellen) |
| `clientId` | Ganzzahl | Numerische Anwendungs-ID. | Ja |
| `state` | Zeichenfolge | `"enabled"` oder `"disabled"` | Ja |
| `meta` | Zeichenfolge | Mit der Funktion in API-Antworten zurückgegebene Base64-kodierte Metadaten. Max. 1024 Zeichen. | Nein |
| `description` | Zeichenfolge | Beschreibung anzeigen. Maximal 225 Zeichen. | Nein |
| `audience` | Array | Liste der Zielgruppenregeln. Siehe [FeatureRule-Objekt](#featurerule-object). Verwenden Sie [Abrufen der gewünschten Zielgruppenkriterien](get-audience-criteria.md) um dies zu generieren. | Nein |
| `variations` | Array | Liste der Varianten. Max. 3. Siehe [FeatureVariation-Objekt](#featurevariation-object). | Nein |
| `params` | Objekt | Zusätzliche Metadaten. Unterstützte Schlüssel: `label` (Anzeigename in der Benutzeroberfläche), `tags` (Zeichenfolgen-Array). | Nein |
| `release` | Objekt | Freigabe-/Gruppenzuordnung. `null` , wenn das Flag nicht in einer Gruppe ist. Schreibgeschützt. | Nein |

### FeatureVariation-Objekt {#featurevariation-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `id` | Ganzzahl | Varianten-ID. Nur für Update-Aufrufe erforderlich. | bedingt |
| `variantName` | Zeichenfolge | Variantenname. Feste Werte: `"Variation 1"`, `"Variation 2"`, `"Variation 3"`. | Ja |
| `variantPercentage` | Dezimal | Prozentsatz der Zielgruppe, die diese Variante erhält. Muss größer als 0 und nicht größer als 100 sein, mit bis zu 2 Dezimalstellen. | Ja |

### FeatureRule-Objekt {#featurerule-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `id` | Ganzzahl | Regel-ID Nur für Update-Aufrufe erforderlich. Setzen Sie diesen Wert auf `null` , wenn Sie eine neue Regel hinzufügen. | bedingt |
| `criteria` | Objekt | Bedingungsobjekt, das die Zielgruppenregel definiert. Siehe [Bedingungsobjekt](#condition-object). | Ja |

### Bedingungsobjekt {#condition-object}

| Feld | Typ | Beschreibung |
|---|---|---|
| `and` | Array\&lt;condition\> | Alle Bedingungen müssen erfüllt sein. |
| `or` | Array\&lt;condition\> | Mindestens eine Bedingung muss erfüllt sein. |
| `not` | Bedingung | Diese Bedingung muss „false“ sein. |
| `attr` | Zeichenfolge | Das auszuwertende Benutzerattribut (z. B. `COUNTRY`, `LOCALE`). |
| `operator` | Zeichenfolge | Vergleichsoperator (z. B. `EQ`, `IN`, `LT`). |
| `val` | Zeichenfolge | Der zu vergleichende Wert. |
| `meta` | Objekt | Optionale Bedingungs-Metadaten. `desc` -Feld legt die Anzeigebeschriftung in der Benutzeroberfläche fest. |

In jeder Bedingung muss entweder `and`, `or` oder `not` oder eine Kombination aus `attr`, `operator` und `val` angegeben werden.

## Siehe auch {#see-also}

* [Übersicht über Feature Management-APIs](feature-management-apis-overview.md)
* [Verwaltungs-Patch-API](management-patch-api.md)
* [Client-ID für ein Programm abrufen](get-client-id.md)
* [Abrufen der gewünschten Zielgruppenkriterien](get-audience-criteria.md)
