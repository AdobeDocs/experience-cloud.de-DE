---
title: Funktionen, Funktionsgruppen und Versionen
description: Erfahren Sie mehr über die Unterschiede zwischen Feature Flags, Feature Groups, Team-übergreifenden Feature Groups und Releases in den Rollouts von Adobe Experience Platform und wann jede Funktion verwendet werden sollte.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 2%

---


# Funktionen, Funktionsgruppen und Versionen {#features-feature-groups-releases}

Erlebnis-Rollouts bietet vier Artefakte zur Verwaltung von Funktions-Rollouts. Die Auswahl des richtigen Elements hängt vom Umfang des Rollouts, der Anzahl der beteiligten Teams und der benötigten Zielgruppen-Targeting-Funktionen ab.

## Die vier Artefakte {#artifacts}

**Feature Flag**
Die atomarste Einheit. Steuert ein einzelnes Feature für ein einzelnes Programm, das einem Team gehört. Kann für eine definierte Zielgruppe aktiviert oder deaktiviert werden.

**Funktionsgruppe**
Eine Sammlung von Feature Flags, die zum selben Team gehören. Ermöglicht die Verwaltung mehrerer Flags über mehrere Anwendungen hinweg in einem Team als eine Einheit.

**Team-übergreifende Funktionsgruppe**
Erweitert Funktionsgruppenfunktionen auf mehrere Teams und Programme. Self-Service und unterstützt umfangreiche Zielgruppenkriterien, unterstützt jedoch nicht das Caching.

**Release**
Konzipiert für große, koordinierte Rollouts über mehrere Teams und Anwendungen hinweg. Verwendet Zielgruppen-Targeting mit Authentifizierungs-Token. Unterstützt das Zwischenspeichern auf dem Server SDK.

## Vergleich {#comparison}

| | Feature Flag | Funktionsgruppe | Team-übergreifende Funktionsgruppe | -Version |
|---|---|---|---|---|
| **Rolle zur Verwaltung der Zielgruppe erforderlich** | Produktversionsinhaber | Produktversionsinhaber | Feature Admin | Versionsverwalter |
| **Anwendungen** | Einzeln | Mehrere (dasselbe Team) | Mehrere (teamübergreifend) | Mehrere (teamübergreifend) |
| **Teams** | Einzeln | Einzeln | Teamübergreifend | Teamübergreifend |
| **Kriterien für umfangreiche Zielgruppen** | ✓ | ✓ | ✓ | Limited |
| **Rollout in Prozent** | In Kombination mit beliebigen Zielgruppenkriterien | In Kombination mit beliebigen Zielgruppenkriterien | In Kombination mit beliebigen Zielgruppenkriterien | Kombiniert mit festen Zielgruppenkriterien |
| **A/B-Tests** | ✓ | ✓ | ✗ | ✗ |
| **Caching auf dem Server SDK** | Nur standardmäßige Ein-/Aus-Flags | Keine Zwischenspeicherung | Keine Zwischenspeicherung | Alle Versionen werden lokal zwischengespeichert |
| **Self-serve** | ✓ | ✓ | ✓ | Erfordert Support-Anfrage |
| **Audit-Protokoll** | ✓ | ✓ | ✓ | ✓ |

## Verwendung {#when-to-use}

| Szenario | Verwenden von |
|---|---|
| Testen oder Rollout einer einzelnen Funktion für ein Programm | **Feature Flag** |
| Koordinieren mehrerer Funktionen im selben Team, gleichzeitige Live-Schaltung | **Funktionsgruppe** |
| Koordinieren von Funktionen über Anwendungen hinweg in verschiedenen Teams hinweg, mit umfassender Zielgruppenbestimmung | **Team-übergreifende Funktionsgruppe** |
| Große koordinierte Version über mehrere Teams hinweg mit Caching auf SDK-Ebene | **Release** |

## Siehe auch {#see-also}

* [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)
* [Erstellen einer Funktionsgruppe](create-a-feature-group.md)
* [Erstellen einer Team-übergreifenden Funktionsgruppe](create-cross-team-feature-group.md)
* [Versionen und teamübergreifende Funktionsgruppen](releases-and-cross-team-feature-groups.md)
