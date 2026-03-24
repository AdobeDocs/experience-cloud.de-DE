---
title: Feature Flags importieren
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts Feature Flags aus einer niedrigeren Umgebung in eine höhere Umgebung importieren, um zu vermeiden, dass Flag-Konfigurationen manuell neu erstellt werden.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---


# Feature Flags importieren {#import-feature-flags}

Mit Erlebnis-Rollouts können Sie Feature Flags aus einer niedrigeren Umgebung (z. B. Staging) in eine höhere Umgebung (z. B. Produktion) importieren. Dadurch wird vermieden, dass Flag-Konfigurationen manuell neu erstellt werden müssen, und das Risiko von Konfigurationsabweichungen zwischen Umgebungen verringert.

## Voraussetzungen {#prerequisites}

Um den Import-Workflow verwenden zu können, müssen die Anwendungsinstanzen über Umgebungen hinweg verknüpft sein. Siehe [Zuordnen von Umgebungen zu einer Anwendung](associate-environments.md).

## Schritt 1: Wechseln zur Zielumgebung und zum Programm {#step-1}

Melden Sie sich bei der Konsole für die **Ziel**-Umgebung an - die Umgebung, in die Sie Flags importieren **. Wählen Sie die Anwendung, in die Sie Flags importieren möchten, aus der Dropdown-Liste Anwendung auf der Seite Feature Flags .

>[!IMPORTANT]
>
>Ihre aktuelle Umgebung und das ausgewählte Programm müssen das **Ziel** sein - nicht die Quelle. Um beispielsweise ein Flag aus der Staging-Umgebung in die Produktion zu importieren, melden Sie sich bei der Produktionskonsole an und wählen Sie Ihre Produktionsanwendung aus.

## Schritt 2: Importdialogfeld öffnen {#step-2}

Wählen Sie **Feature Flags importieren**. Ein Dialogfeld wird geöffnet, in dem die Quellumgebung und das Programm angezeigt werden, die auf der Grundlage der für Ihr Programm konfigurierten verknüpften Umgebungen vorausgefüllt sind. Bei Bedarf können Sie die Quellumgebung und das Programm über die Dropdown-Listen im Dialogfeld ändern.

## Schritt 3: Feature Flags zum Importieren auswählen {#step-3}

Wählen Sie aus der Liste der Feature Flags in der Quellumgebung die Flags aus, die Sie importieren möchten. Sie können ein, mehrere oder alle Flags gleichzeitig auswählen.

## Schritt 4: Vorhandene Flags behandeln (falls erforderlich) {#step-4}

Wenn in der Zielumgebung bereits ein Feature Flag mit demselben Schlüssel vorhanden ist, werden Sie bei Experience Rollouts aufgefordert zu bestätigen, ob es überschrieben werden soll. Überprüfen Sie die vorhandene Flag-Konfiguration, bevor Sie bestätigen, da das Überschreiben die Einstellungen des Ziel-Flags durch die der Quelle ersetzt.

## Wichtige Hinweise {#important-notes}

Beachten Sie beim Importieren von Feature Flags Folgendes:

* Importierte Flags werden unabhängig von ihrem Status in **Quellumgebung immer** Status „AUS“ in der Zielumgebung gesetzt. Sie müssen sie nach dem Import manuell aktivieren.
* Wenn die Aktivierung einer Markierung für ein künftiges Datum und eine zukünftige Uhrzeit in der Quellumgebung geplant war, wird dieser Zeitplan **nicht** übertragen. Sie müssen bei Bedarf einen neuen Zeitplan in der Zielumgebung festlegen.

## Siehe auch {#see-also}

* [Zuordnen von Umgebungen zu einer Anwendung](associate-environments.md)
* [Anzeigen von Funktions-Flags in Umgebungen](view-feature-flags-across-environments.md)
* [Umweltübergreifendes Konzept](cross-environment-concept.md)
