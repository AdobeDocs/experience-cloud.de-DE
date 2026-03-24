---
title: Versionsverwaltung in Experience Rollouts
description: Erfahren Sie, wie die Versionsverwaltung in Experience Rollouts die Bereitstellung von Funktionen für mehrere Teams durch dunkle Bereitstellungen, Produktionstests und schrittweise Rollouts koordiniert.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---


# Versionsverwaltung in Experience Rollouts {#release-management}

Eine typische Hauptversion umfasst mehrere Teams und mehrere Programme mit jeweils eigenen Bereitstellungszeitplänen und Abhängigkeiten. Experience Rollouts bietet ein Versionsverwaltungsmodell, das es Teams ermöglicht, unabhängig zu arbeiten und gleichzeitig eine koordinierte, kontrollierte Version für Endbenutzer bereitzustellen.

## Wichtigste Funktionen {#capabilities}

### Dunkle Bereitstellungen {#dark-deployments}

Teams müssen ihre Code-Bereitstellung nicht mehr mit einem bestimmten Tag der Live-Schaltung zeitlich planen. Code kann jederzeit hinter Feature Flags in der Produktion bereitgestellt werden. Endbenutzern werden erst dann Änderungen angezeigt, wenn die Version aktiviert wurde. Teams können in ihrem eigenen Tempo bereitstellen, zuversichtlich, dass nichts vorzeitig offen gelegt wird.

### Tests in der Produktion {#testing-in-production}

Nach der Bereitstellung des Codes in der Produktion - dunkel bereitgestellt - können bei Erlebnis-Rollouts die Funktionen für interne Tester und QA-Teams geöffnet werden. Dies ermöglicht vollständige Tests mit der Produktionsumgebung und echten Produktionsdaten, ohne dass das Risiko besteht, dass die Endbenutzer auf Änderungen stoßen.

### Schrittweiser Rollout {#gradual-rollout}

Wenn eine Version bereit für die Live-Schaltung ist, muss sie nicht Alles-oder-Nichts sein. Mit Erlebnis-Rollouts können Sie den Rollout schrittweise steuern - beginnend mit einem kleinen Prozentsatz an Benutzenden, zur Überwachung des Feedbacks und der Leistung und zur Erweiterung der Zielgruppe im Laufe der Zeit. Dies reduziert die Belastung für Backend-Systeme und gibt Teams Zeit, auf alle Probleme zu reagieren, bevor sie vollständig freigeschaltet werden.

### Koordinierte Aktivierung {#coordinated-activation}

Mehrere Teams entwickeln Funktionen unabhängig voneinander, jeweils hinter ihren eigenen Feature Flags. Sobald alle Teams bereit sind, bieten Erlebnis-Rollouts einen einzigen Kontrollpunkt, um alle Flags über Teams und Anwendungen hinweg gleichzeitig oder schrittweise zu aktivieren, sodass die Version als ein zusammenhängendes Erlebnis live geschaltet wird.

## Siehe auch {#see-also}

* [Konzept der Versionsverwaltung](concept-of-release-management.md)
* [Funktionsgruppen zur Steuerung mehrerer Funktionen](feature-groups-to-control-multiple-features.md)
* [Schrittweiser Rollout](gradual-rollout.md)
