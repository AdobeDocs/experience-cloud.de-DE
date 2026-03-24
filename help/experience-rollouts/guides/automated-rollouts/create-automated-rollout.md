---
title: Erstellen eines automatisierten Rollouts
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts einen automatisierten Rollout-Plan mit Phasenblöcken und Warteblöcken konfigurieren, damit Ihre Zielgruppe im Laufe der Zeit automatisch erweitert wird.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Erstellen eines automatisierten Rollouts {#create-automated-rollout}

Bei einem automatisierten Rollout können Sie alle Rollout-Phasen und deren Zeitpläne in einer Sitzung definieren. Erlebnis-Rollouts kommen von einer Phase zur nächsten automatisch voran, ohne dass Sie bei jedem Schritt zur Konsole zurückkehren müssen. Siehe [Automatisiertes Rollout-Konzept](automated-rollout-concept.md) für einen Überblick.

Automatisierte Rollouts werden für Feature Flags, Feature Groups und Team-übergreifende Feature Groups unterstützt.

## Schritt 1: Automatisierten Rollout aktivieren {#enable-automated-rollout}

Öffnen Sie beim Erstellen einer neuen Feature Flag, Feature Group oder Cross-Team Feature Group die Registerkarte **Grundlegende Details** und suchen Sie die Option **Typ des Rollouts auswählen**. Standardwert ist **Manuell**. Um einen automatisierten Rollout-Plan zu aktivieren, wählen Sie **Automatisierter Rollout**.

>[!NOTE]
>
>Bei Auswahl des automatisierten Rollouts wird das Feld „Prozentsatz“ im Abschnitt „Grundlegende Details“ automatisch auf 100 % festgelegt und kann nicht mehr bearbeitet werden. Sie steuern den Prozentsatz für jede Phase einzeln auf der Registerkarte Zielgruppe .

## Schritt 2: Rollout-Plan erstellen {#build-rollout-plan}

Öffnen Sie die Registerkarte **Audience** und aktivieren Sie den Umschalter **Phasen**. Dadurch werden die Steuerelemente **Phasenblock hinzufügen** und **Warteblock hinzufügen** aktiviert.

Um Ihren Rollout-Plan zu erstellen, fügen Sie Phase und Warteblöcke in der Reihenfolge hinzu, in der sie ausgeführt werden sollen:

### Phasenblock hinzufügen {#add-phase-block}

Ein Phasenblock definiert die Zielgruppenkriterien für eine Phase des Rollouts. Der Block der ersten Phase wird mit den Zielgruppenkriterien konfiguriert, die sich bereits auf der Seite befinden. Für jeden nachfolgenden Phasenblock wird die Zielgruppe der vorherigen Phase als Ausgangspunkt vorab ausgefüllt.

Konfigurieren Sie die Zielgruppe für jeden Phasenblock:

* **Percentage** - Legen Sie fest, wie viel Prozent der definierten Zielgruppe die Funktion in dieser Phase erhält.
* **Zielgruppenregeln** - Fügen Sie Profil-, Kontext- oder segmentbasierte Regeln hinzu, um bestimmte Benutzer anzusprechen.

>[!IMPORTANT]
>
>Jede nachfolgende Phase sollte die Audience der vorherigen Phase erweitern, nicht ersetzen. Entfernen Sie beim Konfigurieren späterer Phasen keine Zielgruppenregeln aus früheren Phasen, da dadurch versehentlich Benutzende ausgeschlossen werden können, die die Funktion bereits erhalten haben.

### Warteblock hinzufügen {#add-wait-block}

Ein Warteblock definiert die Pause zwischen zwei Phasenblöcken. Wählen Sie nach dem Hinzufügen eines Warteblocks eine der folgenden Optionen aus:

| Option | Beschreibung |
|---|---|
| **Warten** | Eine relative Dauer - z. B. 2 Tage, 4 Stunden warten. Erlebnis-Rollouts gelangen nach Ablauf dieser Dauer zur nächsten Phase. |
| **Warten** | Ein festes Datum und eine feste Uhrzeit Erlebnis-Rollouts gelangt zum nächsten Phasenblock im festgelegten Zeitpunkt. |

### Hinzufügen nachfolgender Phasenblöcke {#add-subsequent-phases}

Wiederholen Sie den Vorgang, um weitere Phasenblöcke und Warteblöcke hinzuzufügen, bis Ihr vollständiger Rollout-Plan konfiguriert ist.

## Schritt 3: Rollout planen oder veröffentlichen {#schedule-or-publish}

Wählen Sie nach Abschluss des Rollout-Plans aus, wie er aktiviert werden soll:

* **Zeitplan** - Legen Sie ein Datum und eine Uhrzeit für den automatischen Start des Rollouts fest. Weitere Informationen [&#x200B; Sie unter &#x200B;](../feature-flags/schedule.md).
* **Manuell veröffentlichen** - Schalten Sie das Feature Flag ein oder verschieben Sie die Feature Group in den Status **Veröffentlichen**, um sofort zu beginnen.

Der Plan beginnt mit der Ausführung ab dem Block der ersten Phase. Sie können den aktiven Plan jederzeit überwachen und bearbeiten. Siehe [Überwachen und Bearbeiten eines Rollout-](monitor-edit-rollout-plan.md).

## Siehe auch {#see-also}

* [Automatisiertes Rollout-Konzept](automated-rollout-concept.md)
* [Überwachen und Bearbeiten eines Rollout-Plans](monitor-edit-rollout-plan.md)
* [Festlegen einer Funktion für das schrittweise Rollout](../feature-flags/set-feature-gradual-rollout.md)
* [Zielgruppenkriterien](../audience/audience-in-feature-flags-and-feature-groups.md)
