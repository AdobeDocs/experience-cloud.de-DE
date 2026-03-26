---
title: Zeitplan
description: Erfahren Sie, wie Sie eine Feature Flag, eine Feature Group oder eine Team-übergreifende Feature Group planen, die zu einem späteren Zeitpunkt in Adobe Experience Rollouts automatisch aktiviert werden soll.
exl-id: f8309daa-428b-41a0-8817-89c8f603bec8
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# Zeitplan {#schedule}

Die Planung ist eine optionale Funktion, mit der Sie ein Datum und eine Uhrzeit für die Aktivierung einer Feature Flag oder Feature Group in der Zukunft festlegen können. Das manuelle Ein-/Ausschalten bleibt verfügbar und muss nicht durch einen Zeitplan ersetzt werden.

Planung wird unterstützt für:

* Feature Flags
* Funktionsgruppen

## Schritt 1: Zeitplan festlegen {#set-schedule}

1. Öffnen Sie das Feature Flag oder die Feature Group in der Konsole.
2. Klicken Sie **auf** Schaltfläche „Zeitplan“ auf der rechten Bildschirmseite.
3. Legen Sie im Popup-Fenster das **Startdatum und die Uhrzeit** fest und wählen Sie die **Zeitzone** aus.

## Schritt 2: Speichern {#save}

Wählen **Zeitplan festlegen** und speichern Sie dann die Einstellungen. Der Zeitplan wird erst wirksam, wenn Sie speichern.

## Nachdem ein Zeitplan festgelegt wurde {#after-schedule-set}

Nach dem Speichern werden das geplante Datum und die geplante Uhrzeit in der Feature Flag- oder Feature Group-Ansicht angezeigt.

Wenn Sie versuchen, den Ein-/Aus-Status manuell umzuschalten, während ein Zeitplan aktiv ist, wird eine Warnung angezeigt, in der Sie gefragt werden, ob Sie den Zeitplan überschreiben oder die Aktion abbrechen möchten.

## Am geplanten Datum und zur geplanten Uhrzeit {#on-schedule}

Zum geplanten Zeitpunkt wird das Feature Flag oder die Feature Group automatisch aktiviert (wechselt in den Status EIN).

Nachdem der Zeitplan ausgelöst wird, ist **Schaltfläche** Zeitplan“ deaktiviert. Zeitpläne können nur festgelegt werden, wenn das Feature Flag oder die Feature Group den Status „Aus“ aufweist.

## Siehe auch {#see-also}

* [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)
* [Erstellen einer Funktionsgruppe](create-a-feature-group.md)
