---
title: Verwaltungs-Patch-API
description: Verwenden Sie die Experience Rollouts PATCH-API , um einzelne Felder eines Feature Flags, einer Feature Group oder einer Cross-Team Feature Group zu aktualisieren, ohne das vollständige Objekt zu übergeben.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 4%

---


# Verwaltungs-Patch-API {#management-patch-api}

Mit der PATCH-API können Sie bestimmte Felder eines Feature Flags, einer Feature Group oder einer Team-übergreifenden Feature Group aktualisieren, ohne das vollständige Objekt im Anfrageinhalt zu senden. Dies ist für zielgerichtete Aktualisierungen nützlich, z. B. zum Ändern einer Zielgruppenregel, zum Umschalten des Status oder zum Anpassen eines Änderungsprozentsatzes.

## Feature Flag PATCH {#feature-flag-patch}

Aktualisiert ein oder mehrere Felder einer Feature Flag.

| | |
|---|---|
| **Endpunkt** | `PATCH /m/api/v1/mgmt/feature/{featureFlagId}` |
| **Methode** | PATCH |

### Anfrage-Header {#ff-request-headers}

Für alle Anfragen sind die in den [Allgemeine Anforderungen“ beschriebenen ](feature-management-apis-overview.md#common-requirements) erforderlich.

### Pfadparameter {#ff-path-param}

| Parameter | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `featureFlagId` | Ganzzahl | Die numerische ID des zu aktualisierenden Feature Flags. | Ja |

### Anfragetext {#ff-request-body}

Übergeben Sie nur die Felder, die Sie aktualisieren möchten. Die Antwort gibt immer das vollständige aktualisierte Feature Flag-Objekt zurück.

**Beispiel - nur Beschreibung aktualisieren:**

```json
{
  "description": "Updated description"
}
```

**Beispiel - Entfernen einer bestehenden Audience:**

```json
{
  "audience": null
}
```

**Beispiel - Fügen Sie eine neue Zielgruppe hinzu, wenn keine existierte:**

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "DEVELOPMENT", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Beispiel - Aktualisieren einer bestehenden Zielgruppenregel:**

```json
{
  "audience": [
    {
      "id": 10020035,
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "PRODUCTION", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Beispiel - Ändern des Status und des Änderungsprozentsatzes:**

```json
{
  "state": "disabled",
  "variations": [
    {
      "id": 10017188,
      "variantName": "Variation 1",
      "variantPercentage": 80.0
    }
  ]
}
```

>[!NOTE]
>
>Schließen Sie beim Aktualisieren einer bestehenden Zielgruppenregel die `id` der Regel ein (verfügbar in der GET-Funktionsantwort), um sie an Ort und Stelle zu aktualisieren. Schließen Sie beim Aktualisieren von Varianten die `id` der Variante ein, um das Erstellen eines Duplikats zu vermeiden.

### Antwort {#ff-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist das vollständige aktualisierte Feature Flag-Objekt. |
| `400` | Ungültige Payload. |
| `403` | Unzureichende Berechtigungen. |
| `417` | Konflikt bei gleichzeitiger Aktualisierung. Aktuelle Funktion abrufen und erneut versuchen. |

## Funktionsgruppe PATCH {#feature-group-patch}

Aktualisiert ein oder mehrere Felder einer Funktionsgruppe. Die Anfrage- und Antwortstruktur ist mit dem Feature Flag PATCH identisch - nur der Endpunkt unterscheidet sich.

| | |
|---|---|
| **Endpunkt** | `PATCH /m/api/v1/mgmt/group/{featureGroupId}` |
| **Methode** | PATCH |

## Team-übergreifende Funktionsgruppe PATCH {#ctfg-patch}

Aktualisiert ein oder mehrere Felder einer Team-übergreifenden Feldergruppe. Verwendet den v2-Release-Endpunkt.

| | |
|---|---|
| **Endpunkt** | `PATCH /m/api/v2/mgmt/release/{CTFGId}` |
| **Methode** | PATCH |

## Siehe auch {#see-also}

* [Feature Flags Management-API](feature-flags-management-api.md)
* [Feature Group Management-API](feature-group-management-api.md)
* [Versionsverwaltungs-APIs](release-management-apis.md)
* [Übersicht über Feature Management-APIs](feature-management-apis-overview.md)
