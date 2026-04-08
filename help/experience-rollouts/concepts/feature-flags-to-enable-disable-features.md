---
title: Feature Flags zum Aktivieren und Deaktivieren von Features
description: Erfahren Sie, wie Sie mit Funktions-Flags in Erlebnis-Rollouts die Funktionsverfügbarkeit steuern, Abhängigkeiten verwalten und das Bereitstellungsrisiko reduzieren können.
exl-id: 627775e8-9b17-4bc7-9565-07a438ae8ed7
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Feature Flags zum Aktivieren und Deaktivieren von Features {#feature-flags}

Mit Feature Flags können Sie Anwendungsfunktionen zur Laufzeit aktivieren oder deaktivieren, ohne Code erneut bereitstellen zu müssen. Sie trennen außerdem Code-Bereitstellungen von der Funktionsverfügbarkeit: Neuer Code kann hinter einem Flag in der Produktion bereitgestellt und erst aktiviert werden, wenn Sie bereit sind.

Diese Praxis reduziert das Risiko erheblich. Entwickler können mit Agilität und Zuversicht aufbauen, während Produkt-Teams die Kontrolle über den Zeitpunkt und die Zielgruppe jeder Funktionsveröffentlichung behalten.

## Verwalten von Abhängigkeiten während der Entwicklung {#manage-dependencies}

Feature Flags helfen beim Verwalten von Abhängigkeiten beim Testen in schnellen Entwicklungszyklen. Entwickler verbringen weniger Zeit mit dem Lösen von Zusammenführungskonflikten und der Umgestaltung und mehr Zeit mit der Bereitstellung von Funktionen.

Da die Funktionsverfügbarkeit außerhalb des Codes gesteuert wird, können mehrere Funktionen parallel entwickelt werden - ohne komplexe Verzweigungen. Einzelne Funktionen können unabhängig voneinander vor- oder zurückgesetzt werden, ohne dass andere laufende Funktionen betroffen sind.

## Dunkle Bereitstellungen {#dark-deployments}

Da Entscheidungen live außerhalb der Codebasis aktiviert und deaktiviert werden, können Sie Code in der Produktion bereitstellen und dabei die Funktion für Endbenutzer unsichtbar lassen. Dies wird als &quot;**-Bereitstellung“**.

Mit dunklen Bereitstellungen können Sie Code sicher in die Produktion verschieben, in der Live-Umgebung unter realen Bedingungen testen und bei Bedarf live schalten - nicht, wenn der Bereitstellungsplan Sie dazu zwingt.

## Schrittweiser Rollout {#gradual-rollout}

Wenn Sie zur Veröffentlichung bereit sind, können Sie eine Feature Flag verwenden, um einen **schrittweisen Rollout“ durchzuführen:** Sie die Funktion für 1 % der Benutzer, messen Sie Feedback und Leistung und erhöhen Sie dann schrittweise.

Dieser rollierende Ansatz bietet Ihnen eine engere Kontrolle über das Erlebnis, das Sie bereitstellen, und eine schnellere Feedback-Schleife mit echten Benutzern, sodass Ihre Teams schnell reagieren können, bevor eine vollständige Version veröffentlicht wird.

## Schalter umlegen {#kill-switch}

Wenn eine Veröffentlichung nicht wie geplant verläuft - ungünstiges Feedback, ein Fehler oder ein Leistungsproblem - können Sie die Funktion sofort deaktivieren, indem Sie das Feature Flag als **Kill Switch“**. Code-Änderungen oder eine erneute Bereitstellung sind nicht erforderlich.

## Lebenszyklus von Feature Flag {#lifecycle}

Eine Feature Flag in Experience Rollouts folgt diesem typischen Lebenszyklus:

1. Ein Entwickler erstellt ein Feature Flag und testet es isoliert, ohne es für andere Benutzer verfügbar zu machen.
2. Ein Produkteigentümer verknüpft eine Zielgruppe mit der Markierung, wodurch die Funktion für eine definierte Gruppe externer Benutzer sichtbar wird.
3. Das Flag wird optional einer [Funktionsgruppe“ hinzugefügt, &#x200B;](feature-groups-to-control-multiple-features.md) es zusammen mit zugehörigen Flags verwaltet werden soll.
