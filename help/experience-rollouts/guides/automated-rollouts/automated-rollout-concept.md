---
title: Automatisiertes Rollout-Konzept
description: Erfahren Sie, wie automatisierte Rollouts in Adobe Experience Rollouts funktionieren, einschließlich Phasenblöcken, Warteblöcken und wie der Rollout-Plan automatisch verläuft.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 2%

---


# Automatisiertes Rollout-Konzept {#automated-rollout-concept}

Mit einem automatisierten Rollout können Sie Ihren gesamten schrittweisen Rollout-Plan in einem Schritt definieren. Anstatt manuell zur Konsole zurückzukehren, um Ihre Zielgruppe für jede Phase zu erweitern, konfigurieren Sie alle Phasen und deren Zeitpläne im Voraus und die Rollouts für Erlebnisse durchlaufen sie automatisch.

Automatisierte Rollouts werden für Feature Flags, Feature Groups und Team-übergreifende Feature Groups unterstützt.

## Funktionsweise {#how-it-works}

Ein Rollout-Plan besteht aus **Phasenblöcken** und **Warteblöcken** die nacheinander ausgeführt werden:

* **Phasenblock** - Definiert die Zielgruppenkriterien für eine Phase des Rollouts. Wenn der Plan einen Phasenblock erreicht, wird diese Zielgruppe zur aktiven Zielgruppe für die Funktion.
* **Warteblock** - Definiert die Pause zwischen zwei Phasenblöcken. Ein Warteblock kann entweder eine relative Dauer (z. B. „Warten 3 Tage„) oder ein festes Datum und eine feste Uhrzeit sein.

Der Plan beginnt, wenn Sie die Funktion veröffentlichen oder für ein Datum in der Zukunft planen. Erlebnis-Rollouts wechselt entsprechend dem konfigurierten Zeitplan automatisch von einem Block zum nächsten.

## Phasenblockverhalten {#phase-block-behavior}

Jeder nachfolgende Phasenblock wird mit der Zielgruppe aus der vorherigen Phase vorab ausgefüllt. Dies erleichtert die Erstellung inkrementell erweiterter Rollouts, bei denen jede neue Phase neben neuen auch alle vorherigen Zielgruppen umfasst.

>[!IMPORTANT]
>
>Zielgruppenregeln in jedem Phasenblock sind bearbeitbar. Daher müssen Sie sicherstellen, dass Sie beim Hinzufügen neuer Phasen keine Zielgruppenkriterien aus vorherigen Phasen löschen. Die Reduzierung des Zielgruppenumfangs während des Rollouts kann dazu führen, dass Benutzer unerwartet den Zugriff auf eine Funktion verlieren.

## Status des Rollout-Plans {#rollout-plan-states}

Sobald ein Rollout-Plan live ist, kann er sich in einem von drei Status befinden:

| Land | Beschreibung |
|---|---|
| **In Bearbeitung** | Der Plan wird ausgeführt. Eine Fortschrittsanzeige in der Konsole zeigt an, welcher Phasenblock aktuell aktiv ist. Alle abgeschlossenen Blöcke sind gesperrt und können nicht bearbeitet werden. |
| **Ausgesetzt** | Der Plan ist zurückgestellt. Die Zielgruppe aus dem zuletzt abgeschlossenen Phasenblock bleibt aktiv. Zukünftige Phasen- und Warteblöcke können während der Pause noch bearbeitet werden. |
| **abgebrochen** | Der Plan wurde dauerhaft gestoppt. Die Zielgruppe aus dem zuletzt abgeschlossenen Phasenblock bleibt aktiv. Weitere Änderungen am Plan sind nicht zulässig. Durch Abbrechen des Plans wird die Funktion nicht deaktiviert. Sie müssen den Funktionsstatus separat ändern, wenn Sie sie nicht mehr bereitstellen möchten. |

## Siehe auch {#see-also}

* [Erstellen eines automatisierten Rollouts](create-automated-rollout.md)
* [Überwachen und Bearbeiten eines Rollout-Plans](monitor-edit-rollout-plan.md)
* [Festlegen einer Funktion für das schrittweise Rollout](../feature-flags/set-feature-gradual-rollout.md)
