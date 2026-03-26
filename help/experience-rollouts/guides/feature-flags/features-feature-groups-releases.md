---
title: Funktionen und Funktionsgruppen
description: Erfahren Sie mehr über die Unterschiede zwischen Funktions-Flags und Funktionsgruppen bei den Rollouts für Adobe Experience Cloud und wann sie jeweils verwendet werden sollten.
source-git-commit: c654ca1507abcefcff84cef9f99830042939805d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 5%

---


# Funktionen und Funktionsgruppen {#features-feature-groups}

Erlebnis-Rollouts bietet zwei Artefakte zum Verwalten von Funktions-Rollouts. Die Auswahl des richtigen hängt vom Umfang Ihres Rollouts und der Anzahl der betroffenen Funktionen ab.

## Die beiden Artefakte {#artifacts}

**Feature Flag**
Die atomarste Einheit. Steuert ein einzelnes Feature für eine einzelne Anwendung. Kann für eine definierte Zielgruppe aktiviert oder deaktiviert werden.

**Funktionsgruppe**
Eine Sammlung von Feature Flags, die zum selben Team gehören. Ermöglicht die Verwaltung mehrerer Flags über mehrere Anwendungen hinweg als eine Einheit.

## Vergleich {#comparison}

| | Feature Flag | Funktionsgruppe |
|---|---|---|
| **Rolle zur Verwaltung der Zielgruppe erforderlich** | Produktversionsinhaber | Produktversionsinhaber |
| **Anwendungen** | Einzeln | Mehrere (dasselbe Team) |
| **Kriterien für umfangreiche Zielgruppen** | ✓ | ✓ |
| **Rollout in Prozent** | In Kombination mit beliebigen Zielgruppenkriterien | In Kombination mit beliebigen Zielgruppenkriterien |
| **A/B-Tests** | ✓ | ✓ |
| **Self-serve** | ✓ | ✓ |
| **Audit-Protokoll** | ✓ | ✓ |

## Verwendung {#when-to-use}

| Szenario | Verwenden von |
|---|---|
| Testen oder Rollout einer einzelnen Funktion für ein Programm | **Feature Flag** |
| Koordinieren mehrerer Funktionen im selben Team, gleichzeitige Live-Schaltung | **Funktionsgruppe** |

## Siehe auch {#see-also}

* [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)
* [Erstellen einer Funktionsgruppe](create-a-feature-group.md)
