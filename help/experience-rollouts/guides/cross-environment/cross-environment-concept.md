---
title: Umweltübergreifendes Konzept
description: Erfahren Sie, wie Sie mit den umgebungsübergreifenden Funktionen in Adobe Experience Rollouts Anwendungen umgebungsübergreifend verknüpfen und Feature Flags von der Entwicklung bis zur Produktion konsistent verwalten können.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Umweltübergreifendes Konzept {#cross-environment-concept}

Mit umgebungsübergreifenden Funktionen können Sie Ihre Anwendungsinstanzen in verschiedenen Bereitstellungsumgebungen wie QA, Staging und Produktion verknüpfen und Feature Flags in allen Umgebungen von Experience Rollouts aus konsistent verwalten.

## Das Problem wird umgebungsübergreifend gelöst {#problem}

Ohne umgebungsübergreifende Verknüpfung ist jede Anwendungsinstanz in Experience Rollouts völlig unabhängig von den entsprechenden Instanzen in anderen Umgebungen. Dadurch entstehen mehrere Reibungspunkte:

* Ein Programm mit dem Namen `my-app` in Staging hat keine Beziehung zu `my-app` in der Produktion. Sie werden als separate, nicht verwandte Anwendungen behandelt.
* Während der Arbeit in der Produktionsumgebung können Sie den Status eines Feature Flags in der Staging-Umgebung nicht anzeigen. Sie müssen Umgebungen manuell wechseln, um Flaggenstatus zu vergleichen.
* Das Importieren einer Feature Flag-Konfiguration aus einer niedrigeren Umgebung in eine höhere Umgebung erfordert manuelle Neuerstellung.

## Was umgebungsübergreifende Lösungen ermöglichen {#what-it-enables}

Durch die umgebungsübergreifende Verknüpfung von Anwendungsinstanzen kann Ihr Team:

* Definieren, welche Bereitstellungsumgebungen Ihres Programms welchen Experience Rollouts-Umgebungen zugeordnet sind
* Verwenden Sie benutzerdefinierte Umgebungsbezeichnungen (z. B. `Dev`, `Staging`, `Prod`), die den Namenskonventionen Ihres Teams entsprechen
* Anzeigen des Status eines Feature Flags über alle verknüpften Umgebungen hinweg in einer einzigen Ansicht
* Feature Flags mit wenigen Klicks von einer niedrigeren Umgebung in eine höhere Umgebung importieren - ohne sie manuell neu zu erstellen

## Strukturierung von Umgebungen {#environment-structure}

Experience Rollouts verfügt über zwei Plattformumgebungen: **Staging** und **Produktion**. Ihre Anwendung verfügt jedoch möglicherweise über mehr Umgebungen, z. B. QS, Staging und Produktion. Mithilfe der umgebungsübergreifenden Verknüpfung können Sie entscheiden, wo die einzelnen Umgebungen Ihres Programms leben:

* QA- und Staging-Umgebungen können entweder in der Staging- oder Produktionsumgebung von Experience Rollouts gehostet werden.
* Produktionsumgebungen müssen in der Produktionsumgebung von Experience Rollouts gehostet werden.

Diese Flexibilität bedeutet, dass Sie nicht zu einer universellen Zuordnung gezwungen sind.

## Nächste Schritte {#next-steps}

* [Umgebungen einer Anwendung zuordnen](associate-environments.md) - Richten Sie die Links zwischen Ihren Anwendungsinstanzen ein
* [Anzeigen von Funktions-Flags in Umgebungen](view-feature-flags-across-environments.md) - Überwachen des Flag-Status in allen verknüpften Umgebungen
* [Feature Flags importieren](import-feature-flags.md) - Leiten Sie Feature Flags von niedrigeren zu höheren Umgebungen hoch
