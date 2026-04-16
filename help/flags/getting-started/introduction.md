---
title: Einführung in Flags
description: Erfahren Sie, wie Flags in Adobe Target ein kontrolliertes Freigabesystem bereitstellt, mit dem Funktionen progressiv für Zielgruppen bereitgestellt werden können.
hide: true
exl-id: befe7899-096d-4f74-a5a2-35b1fc3cbc58
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Einführung in Flags {#introduction}

>[!AVAILABILITY]
>
>Flags sind derzeit in Beta verfügbar und stehen Adobe Target-Kunden zur Verfügung. Wenden Sie sich an den Adobe-Support, um Zugriff zu erhalten.

Flags in Adobe Target sind ein System mit gesteuerter Freigabe, mit dem Teams Funktionen bis hin zur Produktion bereitstellen und gleichzeitig genau steuern können, wer sie wann sieht. Eine Funktion kann in der Produktion und für Endbenutzer unsichtbar sein und dann für eine Zielgruppe progressiv eingeschaltet werden, ohne dass eine erneute Bereitstellung erforderlich ist.

## Von der Entwicklung zur Produktion {#dev-to-prod}

Flags unterstützt das vollständige Journey einer Funktion von der frühesten Entwicklungsphase bis hin zur allgemeinen Verfügbarkeit:

1. **Entwicklertests**: Ein Entwickler erstellt ein Feature Flag, stellt seinen Code in jeder Umgebung bereit und testet nur für seine eigene Sitzung. Es sind keine anderen Benutzenden betroffen und es ist keine Verzweigung erforderlich.

2. **Gezielte Vorschau** - Ein Produkteigentümer verknüpft eine Zielgruppe mit der Feature Flag und stellt die Funktion einer definierten Untergruppe von Benutzern (z. B. Betateilnehmern oder einer bestimmten Region) zur Validierung und zum Feedback zur Verfügung.

3. **Schrittweiser Rollout** - Die Funktion wird nach und nach einer breiteren Zielgruppe (1 %, 10 %, 50 %, 100 %) geöffnet und kann bei jedem Schritt angehalten, angepasst oder deaktiviert werden.

4. **Allgemeine Verfügbarkeit** - Nach Abschluss der Validierung wird die Funktion allen Benutzern verfügbar gemacht.

## Kernfunktionen {#capabilities}

Flags ist eine Feature-Management-Plattform, die Folgendes bietet:

* **Feature Flags** - Schalten Sie eine Funktion zur Laufzeit für eine Zielgruppe ein oder aus, ohne Code erneut bereitzustellen.

* **Zielgruppen-Targeting** - Kontrollieren Sie, wer eine Funktion mithilfe von Benutzerprofildaten, prozentualen Regeln, E-Mail-Adresse, E-Mail-Domain, IP-Adresse oder kontextuellen Attributen sieht.

* **Funktionsgruppen** - Bündeln Sie mehrere verwandte Funktions-Flags über Anwendungen hinweg und verwalten Sie sie als eine Einheit, um sicherzustellen, dass dieselbe Zielgruppe ein konsistentes Erlebnis sieht.

* **Versionen** - Koordinieren Sie große, teamübergreifende Rollouts, indem Sie Feature Flags aus mehreren Teams und Programmen in einem einzigen Versionsereignis gruppieren.

* **Schrittweise Rollouts** - Bereitstellung von Funktionen in der Phase, um Risiken zu reduzieren, Feedback zu sammeln und die Backend-Last zu verwalten.

* **Umschalter deaktivieren** - Schaltet alle Funktionen sofort aus, wenn ein Problem erkannt wird, ohne dass der Code geändert oder neu bereitgestellt wird.

* **AEP SDK-Unterstützung** - Flags werden über die AEP Web SDK und AEP Mobile SDK bereitgestellt, wodurch eine konsistente Flagauswertung über Web- und Mobile Apps hinweg ermöglicht wird.

<!-- -->
