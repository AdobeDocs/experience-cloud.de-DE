---
title: Einführung in Experience Rollouts
description: Erfahren Sie, wie Adobe Experience Rollouts ein System mit kontrollierter Freigabe bereitstellt, um Funktionen progressiv für ausgewählte Zielgruppen bereitzustellen.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Einführung in Experience Rollouts {#introduction}

Adobe Experience Rollouts ist ein System mit kontrollierter Freigabe, mit dem Teams Funktionen bis hin zur Produktion bereitstellen und gleichzeitig genau steuern können, wer sie wann sieht. Eine Funktion kann in der Produktion und für Endbenutzer unsichtbar sein und dann für eine Zielgruppe progressiv eingeschaltet werden, ohne dass eine erneute Bereitstellung erforderlich ist.

## Von der Entwicklung zur Produktion {#dev-to-prod}

Erlebnis-Rollouts unterstützen das vollständige Journey einer Funktion von der frühesten Entwicklungsphase bis hin zur allgemeinen Verfügbarkeit:

1. **Entwicklertests**: Ein Entwickler erstellt ein Feature Flag, stellt seinen Code in jeder Umgebung bereit und testet nur für seine eigene Sitzung. Es sind keine anderen Benutzenden betroffen und es ist keine Verzweigung erforderlich.

2. **Gezielte Vorschau** - Ein Produkteigentümer verknüpft eine Zielgruppe mit der Feature Flag und stellt die Funktion einer definierten Untergruppe von Benutzern (z. B. Betateilnehmern oder einer bestimmten Region) zur Validierung und zum Feedback zur Verfügung.

3. **Schrittweiser Rollout** - Die Funktion wird nach und nach einer breiteren Zielgruppe (1 %, 10 %, 50 %, 100 %) geöffnet und kann bei jedem Schritt angehalten, angepasst oder deaktiviert werden.

4. **Allgemeine Verfügbarkeit** - Nach Abschluss der Validierung wird die Funktion allen Benutzern verfügbar gemacht.

## Kernfunktionen {#capabilities}

Experience Rollouts ist eine Feature-Management-Plattform, die Folgendes bietet:

* **Feature Flags** - Schalten Sie eine Funktion zur Laufzeit für eine Zielgruppe ein oder aus, ohne Code erneut bereitzustellen.

* **Zielgruppen-Targeting** - Kontrollieren Sie, wer eine Funktion mithilfe von Benutzerprofildaten, prozentualen Regeln, E-Mail-Adresse, E-Mail-Domain, IP-Adresse oder kontextuellen Attributen sieht.

* **Funktionsgruppen** - Bündeln Sie mehrere verwandte Funktions-Flags über Anwendungen hinweg und verwalten Sie sie als eine Einheit, um sicherzustellen, dass dieselbe Zielgruppe ein konsistentes Erlebnis sieht.

* **Versionen** - Koordinieren Sie große, teamübergreifende Rollouts, indem Sie Feature Flags aus mehreren Teams und Programmen in einem einzigen Versionsereignis gruppieren.

* **Schrittweise Rollouts** - Bereitstellung von Funktionen in der Phase, um Risiken zu reduzieren, Feedback zu sammeln und die Backend-Last zu verwalten.

* **Umschalter deaktivieren** - Schaltet alle Funktionen sofort aus, wenn ein Problem erkannt wird, ohne dass der Code geändert oder neu bereitgestellt wird.
