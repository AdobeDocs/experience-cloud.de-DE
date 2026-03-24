---
title: Konzept der Versionsverwaltung
description: Erfahren Sie, wie die Versionsverwaltung in Erlebnis-Rollouts durch Feature Flagging die Koordination großer, teamübergreifender Funktions-Rollouts ermöglicht.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Konzept der Versionsverwaltung {#concept-of-release-management}

Große Versionen haben einige gemeinsame Herausforderungen: Mehrere Teams sind beteiligt, Konflikte werden geplant und Abhängigkeiten sind schwer zu koordinieren. Das Versionsmanagement adressiert diese Herausforderungen, indem es eine strukturierte Möglichkeit bietet, Änderungen reibungslos einzuführen.

## Was Versionsverwaltung bedeutet {#what-it-means}

Die Versionsverwaltung koordiniert die komplette Veröffentlichung - von dem Zeitpunkt, an dem Teams hinter Feature Flags entwickeln, bis zu dem Zeitpunkt, an dem die Funktion für alle Benutzer verfügbar ist.

Sie ermöglicht Teams Folgendes:

* Unabhängige Bereitstellung für die Produktion in ihrem eigenen Tempo, ohne den Endbenutzern Funktionen zu offenbaren
* Nur live schalten, wenn alle teilnehmenden Teams bereit sind
* Schrittweises Rollout der Version für eine Untergruppe von Benutzern vor der vollständigen Verfügbarkeit

## Funktionsweise in Experience Rollouts {#how-it-works}

Die Versionsverwaltung in Experience Rollouts basiert auf dem Konzept der [Feature Flagging](what-is-a-feature-flag.md). Jedes Team stellt seinen Code hinter einem Feature Flag in der Produktion bereit. Eine Version ist dann eine **Sammlung von Feature Flags, die für mehrere Programme und Teams definiert**.

Wenn alle Teams bereit sind, kann die Version in einem einzigen Vorgang aktiviert - oder schrittweise eingeführt - werden, ohne dass ein einzelnes Team die Bereitstellung neu bereitstellen oder den Bereitstellungszeitpunkt koordinieren muss.

Dieser Ansatz bietet:

* **Unabhängige Bereitstellung** - Teams werden nach ihrem eigenen Zeitplan bereitgestellt, ohne dass andere Teams oder Endbenutzer betroffen sind.
* **Koordinierte Aktivierung** - Alle Flags in einer Version werden zusammen aktiviert, wenn die Version live geschaltet wird.
* **Schrittweiser Rollout** - Die Version kann schrittweise geöffnet werden, sodass mehr Benutzende den Überblick behalten.

Weitere Informationen zum Konfigurieren von Versionen in Experience Rollouts finden Sie unter [Versionsverwaltung](release-management.md).
