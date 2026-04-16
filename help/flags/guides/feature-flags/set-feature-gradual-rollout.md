---
title: Festlegen einer Funktion für das schrittweise Rollout
description: Erfahren Sie, wie Sie unter „Flags“ einen prozentualen schrittweisen Rollout für eine Feature Flag konfigurieren.
hide: true
exl-id: 1e03c533-398d-4a83-9f4a-c0419828b460
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 3%

---

# Festlegen einer Funktion für das schrittweise Rollout {#gradual-rollout-feature}

Der prozentuale Rollout für eine Feature Flag wird auf der Registerkarte **Grundlegende Details** konfiguriert. Sie können diesen Wert jederzeit während des Rollouts nach oben oder unten anpassen.

## Funktionsweise {#how-it-works}

Wenn Sie einen prozentualen Rollout festlegen, z. B. 25 %, wird dieser Prozentsatz Ihrer definierten Zielgruppe der Funktion angezeigt. Der verbleibende Prozentsatz wird in die **Kontrollgruppe** aufgenommen, die das Standarderlebnis erhält.

Sie können den Prozentsatz im Laufe der Zeit erhöhen oder verringern, um den Rollout zu erweitern oder zu verkürzen. Durch die Reduzierung des Prozentsatzes auf 0 % wird die Funktion effektiv für alle Personen in der Zielgruppe deaktiviert, ohne dass die Markierung gelöscht wird.

## Siehe auch {#see-also}

* [Schrittweiser Rollout](../../concepts/gradual-rollout.md)
* [Festlegen einer Funktionsgruppe für das schrittweise Rollout](set-feature-group-gradual-rollout.md)
* [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)

<!-- -->
