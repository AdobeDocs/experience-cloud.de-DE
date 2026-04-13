---
title: Schrittweiser Rollout
description: Erfahren Sie, wie Sie durch schrittweise Rollouts in Erlebnis-Rollouts die Funktionsbereitstellung sicher, mit Echtzeit-Feedback und minimalem Risiko in die Produktion einstufen können.
hide: true
exl-id: ede24236-de19-4008-893c-e67bd82e23e3
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 2%

---

# Schrittweiser Rollout {#gradual-rollout}

Bei einem schrittweisen Rollout wird eine neue Funktion schrittweise in die Produktion eingeführt, anstatt sie für alle Benutzer gleichzeitig zu aktivieren. Dieser Ansatz reduziert Risiken, hilft bei der Verwaltung der Backend-Last und schafft eine enge Feedback-Schleife vor der vollständigen Veröffentlichung.

## Vorteile {#benefits}

**Sicherheitsnetz**
Indem Sie Inhalte zuerst für eine kleine Zielgruppe freigeben, können Sie Feedback verfolgen und das Verhalten in der Produktion überwachen, bevor Sie die Erweiterung durchführen. Wenn Probleme auftreten, sind die Auswirkungen begrenzt und die Funktion kann sofort deaktiviert werden - ohne Code-Änderung oder Neubereitstellung.

**Backend-Lastverwaltung**
Das gleichzeitige Öffnen einer Funktion für alle Benutzer kann zu plötzlichen Spitzen bei der Server-Auslastung führen. Ein schrittweiser Rollout verteilt den Anstieg des Traffics über die Zeit und ermöglicht so eine reibungslose Skalierung der Infrastruktur.

**Echtzeitfeedback**
Jede Phase des Rollouts zeigt das Feedback echter Benutzer. Teams können vor der nächsten Phase auf dieses Feedback reagieren - das Erlebnis verfeinern, Sonderfälle beheben oder das Messaging anpassen.

## Funktionsweise {#how-it-works}

Erlebnis-Rollouts bieten granulare Zielgruppenbestimmungsregeln, um die Anwenderexposition Schritt für Schritt zu erhöhen. Ein typischer schrittweiser Rollout folgt möglicherweise diesem Muster:

1. Aktivieren Sie die Funktion für **1 %** der Benutzer
2. Überwachen von Feedback und Leistungsmetriken
3. Erweitern Sie auf **10%**, dann **25%**, dann **50%**
4. 100 **erreichen** sobald die Konfidenz hergestellt ist

Bei jedem Schritt kann eine einzelne Aktion den Rollout anhalten oder die Funktion vollständig deaktivieren, wenn etwas schief geht.

## Siehe auch {#see-also}

* [Feature Flags zum Aktivieren und Deaktivieren von Features](feature-flags-to-enable-disable-features.md)

<!-- -->
