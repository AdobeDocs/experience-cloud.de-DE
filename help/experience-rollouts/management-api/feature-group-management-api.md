---
title: Feature Group Management-API
description: API-Referenz für die Experience Rollouts-Funktionsgruppen-Management-API, einschließlich Endpunkten zum Abrufen, Erstellen, Aktualisieren, Löschen und Steuern von Rollout-Plänen für Funktionsgruppen.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 17%

---


# Feature Group Management-API {#feature-group-management-api}

Mit der Feature Group Management API können Sie in Experience Rollouts Funktionsgruppen programmgesteuert erstellen, lesen, aktualisieren und löschen, einschließlich automatisierter und A/B-Test-Rollout-Pläne.

**Basispfad:** `/m/api/v1/mgmt/group`

Für alle Anfragen sind die in den [Allgemeine Anforderungen“ beschriebenen &#x200B;](feature-management-apis-overview.md#common-requirements) erforderlich.

## Alle Funktionsgruppen abrufen {#get-all-groups}

Ruft alle Funktionsgruppen für Ihre Organisation ab.

| | |
|---|---|
| **Endpunkt** | `GET /m/api/v1/mgmt/group` |
| **Methode** | GET |

### Abfrageparameter {#get-all-query-params}

| Parameter | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `myOrg` | Boolesch | Legen Sie hierfür `true` fest, um Unternehmensinformationen einzuschließen. | Ja |
| `includeClientInfo` | Boolesch | Legen Sie hierfür `true` fest, um Anwendungsinformationen für jede Gruppe einzuschließen. | Ja |

### Antwort {#get-all-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist ein Array von Merkmalgruppen-Objekten. |

## Funktionsgruppe nach ID abrufen {#get-group-by-id}

Ruft eine einzelne Funktionsgruppe anhand ihrer numerischen ID ab.

| | |
|---|---|
| **Endpunkt** | `GET /m/api/v1/mgmt/group/{groupId}` |
| **Methode** | GET |
| **Abfrageparameter** | `includeAnalyzeInfo=true` (optional - fügt der Antwort Analysedaten hinzu) |

### Antwort {#get-by-id-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist ein Objekt der Funktionsgruppe . |
| `400` | Ungültige Funktionsgruppen-ID. |

## Funktionsgruppe erstellen {#create-group}

Erstellt eine neue Funktionsgruppe mit dem Rollout-Typ „Manueller Test“, „Automatisierter Test“ oder „A/B-Test“.

| | |
|---|---|
| **Endpunkt** | `POST /m/api/v1/mgmt/group` |
| **Methode** | POST |

### Anfragetext {#create-request-body}

Der Anfragetext verwendet das [Objekt der Funktionsgruppe](#feature-group-object). Die `rolloutType` in `params` ist obligatorisch und bestimmt die Struktur der Payload.

**Beispiel - manueller Rollout:**

```json
{
  "params": {
    "rolloutType": "manual",
    "label": "my-feature-group",
    "tags": [],
    "canContextOverridePUP": false
  },
  "status": "SAVED",
  "type": "group",
  "name": "my.feature.group",
  "description": "A manual feature group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{ "criteria": { "and": [{ "operator": "EQ", "attr": "COUNTRY", "val": "US", "ruleId": 1, "category": "default" }] } }],
  "clients": [],
  "org": { "id": 95 }
}
```

### Antwort {#create-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist das erstellte Objekt der Funktionsgruppe . |
| `400` | Ungültige Payload — Einzelheiten finden Sie [Fehlermeldungen](#error-messages). |
| `403` | Unzureichende Berechtigungen. |

## Funktionsgruppe aktualisieren {#update-group}

Aktualisiert eine vorhandene Funktionsgruppe. Übergeben Sie dieselbe Struktur wie der Text der Erstellungsanfrage, einschließlich des Felds `id` .

| | |
|---|---|
| **Endpunkt** | `PUT /m/api/v1/mgmt/group` |
| **Methode** | PUT |

### Antwort {#update-response}

| Status | Beschreibung |
|---|---|
| `200` | Erfolgreich. Der Antworttext ist das aktualisierte Objekt der Funktionsgruppe . |
| `400` | Ungültige Payload. |
| `403` | Unzureichende Berechtigungen. |

## Funktionsgruppe löschen {#delete-group}

Löscht eine Funktionsgruppe anhand ihrer numerischen ID.

| | |
|---|---|
| **Endpunkt** | `DELETE /m/api/v1/mgmt/group/{groupId}` |
| **Methode** | DELETE |

### Antwort {#delete-response}

| Status | Beschreibung |
|---|---|
| `204` | Erfolgreich. Kein Antworttext. |
| `403` | Unzureichende Berechtigungen. |

## Objektverweis für Funktionsgruppen {#feature-group-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `id` | Ganzzahl | Funktionsgruppen-ID. Nur für Update-Aufrufe erforderlich. | bedingt |
| `name` | Zeichenfolge | Funktionsgruppenschlüssel. Maximal 50 Zeichen. Muster: `^[a-zA-Z0-9_.-]*$` | Ja (erstellen) |
| `clients` | Array | Der Gruppe zugeordnete Anwendungen Jeder Eintrag muss `id` und `imsClientId` enthalten. | Ja |
| `status` | Zeichenfolge | `"SAVED"` oder `"PUBLISHED"` | Ja |
| `type` | Zeichenfolge | Immer für Funktionsgruppen `"group"`. | Ja |
| `org` | Objekt | Organisationsdetails. Muss `id` enthalten. | Ja |
| `params` | Objekt | Gruppenparameter. `rolloutType` ist obligatorisch (`"manual"`, `"automated"` oder `"ab-testing"`). Unterstützt auch `label` und `tags`. | Ja |
| `audience` | Array | Zielgruppenregeln für manuelle Rollout-Typen. | Nein |
| `variations` | Array | Liste der Varianten. Siehe [FeatureGroupVariation-Objekt](#featuregroupvariation-object). | Nein |
| `phaseRollOutPlan` | Objekt | Rollout-Plan für die Phase Erforderlich für automatisierte Tests und A/B-Tests. Siehe [PhaseRollOutPlan-Objekt](#phaserolloutplan-object). | bedingt |
| `description` | Zeichenfolge | Optionale Anzeigebeschreibung. Maximal 225 Zeichen. | Nein |

### FeatureGroupVariation-Objekt {#featuregroupvariation-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `id` | Ganzzahl | Varianten-ID. Nur für Update-Aufrufe erforderlich. | bedingt |
| `variantName` | Zeichenfolge | Variantenname. Hartcodiert zu `"Variant 1"`. | Ja |
| `variantPercentage` | Dezimal | Prozentsatz der Zielgruppe, die diese Variante erhält. Muss größer als 0 und nicht größer als 100 sein. | Ja |

### PhaseRollOutPlan-Objekt {#phaserolloutplan-object}

| Feld | Typ | Beschreibung | Erforderlich |
|---|---|---|---|
| `phaseRollOutBlocks` | Array | Sortierte Liste der Phasenblöcke und Warteblöcke. Der letzte Block muss ein Phasenblock sein. | Ja |
| `rollOutPlanState` | Zeichenfolge | `"DRAFT"`, `"RUNNING"`, `"PAUSED"` oder `"ABORTED"` | Ja |

Jeder Block in `phaseRollOutBlocks` ist entweder ein **Phasenblock** (`isPhaseBlock: true`) mit einem `phaseRule` mit Zielgruppenkriterien oder ein **Warteblock** (`isPhaseBlock: false`) mit einem `waitRule` mit entweder einem `waitDuration` (relativen) oder `executionDate` (festem Zeitstempel).

## Fehlermeldungen {#error-messages}

| Bedingung | Status | Fehlermeldung |
|---|---|---|
| Ungültiger oder leerer Name | 400 | `Error: Invalid value for release name.` |
| Leere Zielgruppenkriterien | 400 | `Error: Release is not valid` |
| Mehrere Varianten für automatisierten Typ | 400 | `Error: Feature variation is not valid. Variation name should be unique across variations` |
| Veröffentlichte Gruppe ohne Clients | 400 | `Error: At least one client must be associated with enabled feature group.` |
| Letzter Block im Plan ist kein Phasenblock | 400 | `Error: The last block in the Phase Rollout plan should be phase block` |
| Warteblock-Zeitüberschreitung | 400 | `Error: Wait block timings are not in order in the phase rollout plan` |
| Inkonsistente Warteblocktypen | 400 | `Error: Wait block should be of same type.` |
| Bearbeiten eines aktivierten Phasenblocks | 400 | `Error: Activated phase block should not be changed` |
| Leerer Rollout-Typ | 400 | `Error: Rollout type cannot be empty while feature group creation` |
| Phasenplan mit manuellem Typ bestanden | 400 | `Error: PhaseRollOutPlan can't be added with manual rollout type while feature group creation` |
| Zeitplan mit dem Status VERÖFFENTLICHT bestanden | 400 | `Error: Schedule can't be added in published state while release/group creation` |

## Siehe auch {#see-also}

* [Übersicht über Feature Management-APIs](feature-management-apis-overview.md)
* [Feature Flags Management-API](feature-flags-management-api.md)
* [Verwaltungs-Patch-API](management-patch-api.md)
