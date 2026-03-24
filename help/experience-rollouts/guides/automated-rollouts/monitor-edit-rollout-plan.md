---
title: Überwachen und Bearbeiten eines Rollout-Plans
description: Erfahren Sie, wie Sie den Fortschritt eines automatisierten Rollout-Plans in den Rollouts von Adobe Experience Platform verfolgen und wie Sie einen laufenden Plan anhalten, fortsetzen oder abbrechen können.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Überwachen und Bearbeiten eines Rollout-Plans {#monitor-edit-rollout-plan}

Sobald ein automatisierter Rollout live ist, können Sie dessen Fortschritt verfolgen und bei Bedarf eingreifen. Auf dieser Seite wird beschrieben, wie Sie die Fortschrittsanzeige lesen, einen Plan anhalten und fortsetzen und bei Bedarf abbrechen können.

Auf dieser Seite wird davon ausgegangen, dass Sie bereits einen Rollout-Plan erstellt und veröffentlicht haben. Siehe [Erstellen eines automatisierten Rollouts](create-automated-rollout.md) falls Sie noch keinen eingerichtet haben.

## Rollout-Fortschritt anzeigen {#view-progress}

Nachdem die Ausführung des Rollout-Plans begonnen hat, öffnen Sie die Registerkarte **Audience** der Funktion, um den aktuellen Status des Plans anzuzeigen. Der Plan zeigt eine Fortschrittsanzeige an, die anzeigt, welcher Phasenblock derzeit aktiv ist.

Verwenden Sie die Fortschrittsanzeige, um Folgendes zu verstehen:

* **Abgeschlossene Blöcke** - Alle Phasen- und Warteblöcke über dem Indikator wurden ausgeführt. Diese Blöcke sind gesperrt und können nicht bearbeitet werden.
* **Aktueller Block** - Der aktuell markierte Block ist die aktive Phase oder Wartezeit.
* **Kommende Blöcke** - Alle Phasen- und Warteblöcke unter dem Indikator wurden noch nicht ausgeführt. Diese können weiterhin bearbeitet werden.

## Aussetzen eines Rollout-Plans {#pause}

Um den Rollout während der Ausführung jederzeit anzuhalten, wählen Sie in der Konsole **Rollout anhalten** aus.

Wenn der Plan angehalten wurde:

* Die Zielgruppe aus dem zuletzt abgeschlossenen Phasenblock bleibt aktiv. Benutzende in dieser Zielgruppe erhalten die Funktion weiterhin.
* Die Feature Flag, Feature Group oder Cross-Team Feature Group verbleibt in ihrem aktuellen Status „Ein“ oder „Veröffentlicht“. Die Funktion wird weiterhin für die aktuelle aktive Zielgruppe bereitgestellt.
* Anstehende Phase und Warteblöcke bleiben bearbeitbar.

Um einen pausierten Plan fortzusetzen, wählen Sie **Rollout fortsetzen** aus. Der Plan geht dort weiter, wo er aufgehört hat.

## Abbrechen eines Rollout-Plans {#abort}

Um den Rollout-Plan dauerhaft zu stoppen, wählen Sie **Rollout abbrechen** in der Konsole aus.

Wenn der Plan abgebrochen wird:

* Die Zielgruppe aus dem zuletzt abgeschlossenen Phasenblock bleibt aktiv und die Funktion wird weiterhin für diese Zielgruppe bereitgestellt.
* Die Funktion selbst ist nicht deaktiviert. Wenn Sie die Bereitstellung der Funktion vollständig beenden möchten, müssen Sie die Veröffentlichung separat abbrechen oder das Feature Flag oder die Gruppe deaktivieren.
* Anstehende Phasen- und Warteblöcke können nicht mehr bearbeitet werden.
* Ein abgebrochener Plan kann nicht fortgesetzt werden.

>[!IMPORTANT]
>
>Durch Abbrechen eines Rollout-Plans wird die Funktion nicht automatisch deaktiviert. Führen Sie eine separate Aktion für den Funktionsstatus durch, wenn Sie die Bereitstellung für Benutzer beenden möchten.

## Bearbeiten bevorstehender Phasenblöcke {#edit-upcoming}

Während der Plan in Bearbeitung (oder angehalten) ist, können Sie weiterhin jede Phase oder jeden Warteblock bearbeiten, die noch nicht ausgeführt wurde:

* Passen Sie die Zielgruppenregeln oder den Prozentsatz für einen bevorstehenden Phasenblock an.
* Ändern der Dauer oder des festen Datums eines bevorstehenden Warteblocks.

Abgeschlossene Blöcke sind gesperrt und können nicht geändert werden.

## Siehe auch {#see-also}

* [Erstellen eines automatisierten Rollouts](create-automated-rollout.md)
* [Automatisiertes Rollout-Konzept](automated-rollout-concept.md)
* [Versionsstatus](../feature-flags/release-states.md)
