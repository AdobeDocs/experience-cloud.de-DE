---
title: Funktionen und Funktionsgruppen
description: Erfahren Sie mehr über die Unterschiede zwischen Feature Flags und Feature Groups in Flags und wann jeder verwendet werden sollte.
hide: true
exl-id: 852aa777-6f8a-47c9-bf54-e645a5ee2f3e
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 5%

---

# Funktionen und Funktionsgruppen {#features-feature-groups}

Flags stellt zwei Artefakte zum Verwalten von Funktions-Rollouts bereit. Die Auswahl des richtigen hängt vom Umfang Ihres Rollouts und der Anzahl der betroffenen Funktionen ab.

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

<!-- -->
