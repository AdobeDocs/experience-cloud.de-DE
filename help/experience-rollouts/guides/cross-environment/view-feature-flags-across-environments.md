---
title: Anzeigen von Funktions-Flags in Umgebungen
description: Erfahren Sie, wie Sie den Status von Feature Flags in allen verknüpften Umgebungen für eine Anwendung in den Rollouts von Adobe Experience Platform anzeigen.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Anzeigen von Funktions-Flags in Umgebungen {#view-flags-across-environments}

Nachdem Sie Ihre Anwendungsinstanzen über Umgebungen hinweg verknüpft haben, zeigt Experience Rollouts den Status der einzelnen Feature Flag für alle verknüpften Umgebungen direkt auf der Seite mit den Feature Flags an. Dadurch erhalten Sie eine einzige Ansicht, um die Flaggenzustände zu vergleichen, beispielsweise ob eine Markierung in der Staging- und in der Produktionsumgebung EIN oder AUS ist, ohne die Umgebung zu wechseln.

## Voraussetzungen {#prerequisites}

Ihre Anwendungsinstanzen müssen umgebungsübergreifend verknüpft sein, damit der umgebungsübergreifende Status sichtbar ist. Siehe [Zuordnen von Umgebungen zu einer Anwendung](associate-environments.md) für Einrichtungsanweisungen.

## Funktionsweise {#how-it-works}

Wenn Sie zu **Funktionen und Versionen > Feature Flags** navigieren und ein Programm auswählen, das verknüpfte Instanzen hat, zeigt die Auflistungsseite zusätzliche Spalten für jede verknüpfte Umgebung an. Jede Spalte zeigt den aktuellen Status des Feature Flags in dieser Umgebung an.

Funktions-Flags werden von Umgebung zu Umgebung nach **Schlüssel** zugeordnet, nicht nach ihrem Namen. Das bedeutet:

* Ein Flag kann in jeder Umgebung einen anderen Anzeigenamen haben, sofern der Schlüssel derselbe ist.
* Der in den einzelnen Umgebungsspalten angezeigte Name ist der in dieser Umgebung verwendete Name.

## Anwendungsfall {#use-case}

Ein typischer Workflow besteht darin, ein Feature Flag in einer niedrigeren Umgebung (z. B. Staging) zu entwickeln und zu testen und dann seinen Status zu überprüfen, bevor die Konfiguration zur Produktion weitergeleitet wird. Durch die umgebungsübergreifende Sichtbarkeit können Sie bestätigen, dass das Flag in der Staging-Umgebung korrekt konfiguriert ist, bevor Sie es in die Produktion importieren - und das alles über die Produktionskonsole.

## Siehe auch {#see-also}

* [Zuordnen von Umgebungen zu einer Anwendung](associate-environments.md)
* [Feature Flags importieren](import-feature-flags.md)
* [Umweltübergreifendes Konzept](cross-environment-concept.md)
