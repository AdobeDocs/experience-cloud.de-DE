---
title: Versionsverwaltungs-APIs
description: API-Referenz für die Experience Rollouts-APIs zur Versionsverwaltung, einschließlich Endpunkten zum Abrufen, Erstellen und Bearbeiten von Versionen und Team-übergreifenden Funktionsgruppen.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 15%

---


# Versionsverwaltungs-APIs {#release-management-apis}

Mit den Release-Management-APIs können Sie Versionen und Team-übergreifende Funktionsgruppen (CTFG) programmgesteuert abrufen, erstellen und bearbeiten. Diese APIs verwenden den v2-Verwaltungsendpunkt.

**Basispfad:** `/m/api/v2/mgmt/release`

Bei allen Anfragen sind die unter „Allgemeine [&quot; beschriebenen ](feature-management-apis-overview.md#common-requirements) sowie die unten aufgeführten zusätzlichen Kopfzeilen erforderlich.

## Zusätzliche erforderliche Kopfzeile {#additional-header}

| Header | Beschreibung | Erforderlich |
|---|---|---|
| `x-user-context-org` | Die numerische Team-ID für Ihre Organisation. Diesen Wert finden Sie in der Konsole „Erlebnis-Rollouts“ in Ihren Team-Einstellungen. | Ja |

## Veröffentlichung nach ID abrufen {#get-release}

Ruft eine einzelne Release- oder Team-übergreifende Funktionsgruppe anhand ihrer numerischen ID ab.

| | |
|---|---|
| **Endpunkt** | `GET /m/api/v2/mgmt/release/{id}` |
| **Methode** | GET |

### Abfrageparameter {#get-query-params}

| Parameter | Typ | Beschreibung | Standard |
|---|---|---|---|
| `includePermissions` | Boolesch | Schließen Sie Berechtigungen zum Aktualisieren oder Löschen dieser Version ein. | `true` |
| `includeOrg` | Boolesch | Schließen Sie Organisationsdaten für diese Version ein. | `true` |
| `includeAnalyzeInfo` | Boolesch | Analytics-Informationen einschließen. | `false` |

### Antwort {#get-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist ein Release-Objekt (siehe [Release-Objektreferenz](#release-object). |
| `400` | Ungültige Release-ID oder fehlerhafte Anfrage. |

## Version erstellen {#create-release}

Erstellt eine neue Version oder eine Team-übergreifende Funktionsgruppe.

| | |
|---|---|
| **Endpunkt** | `POST /m/api/v2/mgmt/release` |
| **Methode** | POST |

### Anfragetext {#create-request-body}

Der Anfragetext verwendet das [Release-Objekt](#release-object). Zur Erstellung müssen `status` für Team-übergreifende Funktionsgruppen (`CROSS_TEAM_FEATURE_GROUP`) auf `"SAVED"` oder für Standardversionen (`RELEASE`) auf `"DRAFT"` gesetzt werden.

**Beispiel - Erstellen einer Team-übergreifenden Funktionsgruppe:**

```json
{
  "params": {
    "rolloutType": "manual",
    "cohortingType": "guid",
    "tags": [],
    "canContextOverridePUP": false,
    "label": "my-cross-team-group"
  },
  "status": "SAVED",
  "type": "CROSS_TEAM_FEATURE_GROUP",
  "name": "my-cross-team-group",
  "description": null,
  "meta": "",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{}],
  "clients": [],
  "pollInterval": 300,
  "org": { "id": "95" },
  "comment": ""
}
```

### Antwort {#create-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist das erstellte Release-Objekt. |
| `400` | Ungültige Payload. |

## Version bearbeiten {#edit-release}

Aktualisiert eine vorhandene Version oder eine Team-übergreifende Funktionsgruppe. Übergeben Sie das vollständige Release-Objekt einschließlich des Felds `id` .

| | |
|---|---|
| **Endpunkt** | `PUT /m/api/v2/mgmt/release/{id}` |
| **Methode** | PUT |

### Antwort {#edit-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist das aktualisierte Release-Objekt. |
| `417` | Konflikt bei gleichzeitiger Aktualisierung. Die Version wurde zwischen Ihren GET- und PUT-Aufrufen geändert. Aktuelle Version abrufen und erneut versuchen. |

## Objektreferenz freigeben {#release-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `id` | Ganzzahl | Release-ID. Nur für Update-Aufrufe erforderlich. | bedingt |
| `name` | Zeichenfolge | Name der Version. Maximal 50 Zeichen. Muster: `^[a-zA-Z0-9_ ,.:()-]*$`. Muss eindeutig sein. | Ja |
| `description` | Zeichenfolge | Optionale Beschreibung. Maximal 255 Zeichen. | Nein |
| `type` | Zeichenfolge | `"RELEASE"` für Standardversionen; `"CROSS_TEAM_FEATURE_GROUP"` für Team-übergreifende Funktionsgruppen. | Ja |
| `status` | Zeichenfolge | Freigabestatus. Für IMS: `"DRAFT"` bei Erstellung; `"DRAFT"`, `"SAVED"`, `"PUBLISHED"` bei Aktualisierung. Für CTFG: `"SAVED"` bei Erstellung; `"SAVED"`, `"PUBLISHED"` bei Aktualisierung. | Ja |
| `clients` | Array | Mit dieser Version verknüpfte Anwendungen. Jeder Eintrag erfordert `id` (numerisch) und `imsClientId` (Zeichenfolge). | Nein |
| `audience` | Array | Liste der Zielgruppenregeln. Siehe [Bedingungsobjekt](feature-flags-management-api.md#condition-object). | Nein |
| `variations` | Array | Liste der Varianten. Während der Übermittlung wird nur eine Variante unterstützt. | Zur Übermittlung erforderlich |
| `params` | Objekt | Versionsparameter. Siehe [Unterstützte Parameterfelder](#supported-params). | Zur Übermittlung erforderlich |
| `org` | Objekt | Organisationsobjekt Muss `id` enthalten. | Nein |

### Unterstützte Parameterfelder {#supported-params}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `label` | Zeichenfolge | Anzeigename. Maximal 50 Zeichen. | Ja |
| `tags` | Array\&lt;String\> | Optionale Tags. Pro maximal 50 Zeichen. | Nein |
| `canContextOverridePUP` | Boolesch | Wenn `true`, setzen Kontextregeln Profilregeln außer Kraft. Standard: `false`. | Ja |
| `isBetaRelease` | Boolesch | Falls `true`, wird dies als Beta-Version markiert. Standard: `false`. | Nein |

### Variantenobjekt {#variation-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `id` | Ganzzahl | Varianten-ID. Nur für Update-Aufrufe erforderlich. | bedingt |
| `variantName` | Zeichenfolge | Variantenname. Maximal 50 Zeichen. | Ja |
| `variantPercentage` | Double | Prozentsatz der Zielgruppe, die diese Variante erhält. Bereich: [0, 100 ]. | Ja |
| `features` | Array | In dieser Variante enthaltene Funktionen. Jeder Eintrag muss `id`, `name`, `clientId` und `state` enthalten. | Nein |

## Siehe auch {#see-also}

* [Übersicht über Feature Management-APIs](feature-management-apis-overview.md)
* [Feature Flags Management-API](feature-flags-management-api.md)
* [Feature Group Management-API](feature-group-management-api.md)
* [Erstellen einer Team-übergreifenden Funktionsgruppe](../guides/feature-flags/create-cross-team-feature-group.md)
