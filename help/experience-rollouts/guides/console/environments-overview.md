---
title: Umgebungen – Übersicht
description: Erfahren Sie mehr über die Staging- und Produktionsumgebungen in Adobe Experience Rollouts und wann jede Umgebung verwendet werden sollte.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 4%

---


# Umgebungen – Übersicht {#environments}

Erlebnis-Rollouts bietet separate Umgebungen, damit Sie Ihre Feature Flags überprüfen können, bevor Sie Änderungen an Ihre Live-Benutzer weiterleiten.

## Verfügbare Umgebungen {#available-environments}

| Umgebung | Zweck |
|---|---|
| **stage** | Tests und Validierung. Verwenden Sie diese Umgebung, um Feature Flags zu konfigurieren und zu testen, bevor sie in der Produktion aktiviert werden. |
| **Produktion** | Live-Rollouts. Hier konfigurierte Funktions-Flags werden mit Ihrer tatsächlichen Benutzerbasis verglichen. |

>[!IMPORTANT]
>
>In der Phase vorgenommene Änderungen werden nicht automatisch in die Produktion übernommen. Funktions-Flags und Zielgruppenregeln müssen in jeder Umgebung separat konfiguriert werden.

## Auswählen einer Umgebung {#selecting}

Wählen Sie nach der Anmeldung bei der Konsole „Experience Rollouts“ die Umgebung über den Umgebungsumschalter oben in der Benutzeroberfläche aus. Stellen Sie sicher, dass Sie in der richtigen Umgebung arbeiten, bevor Sie Feature Flags erstellen oder ändern.

## Best Practices {#best-practices}

Befolgen Sie diese Empfehlungen, um Konfigurationsfehler zu vermeiden und Ihre Produktions-Audience zu schützen:

* Erstellen und testen Sie Feature Flags immer zuerst in **Staging**.
* Validieren Sie die Zielgruppenregeln, prozentualen Rollouts und die Zielgruppenbestimmungslogik im Staging, bevor Sie sie in der Produktion replizieren.
* Verwenden Sie den [umgebungsübergreifenden Workflow](../cross-environment/cross-environment-concept.md), um den Flag-Status in allen Umgebungen anzuzeigen und zu verwalten.

## Siehe auch {#see-also}

* [Melden Sie sich bei der Konsole an](log-in-to-the-console.md)
* [Zuordnen von Umgebungen zu einer Anwendung](../cross-environment/associate-environments.md)
* [Anzeigen von Funktions-Flags in Umgebungen](../cross-environment/view-feature-flags-across-environments.md)
