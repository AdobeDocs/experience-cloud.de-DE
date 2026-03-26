---
title: Fehlerbehebung
description: Verwenden Sie die Experience Rollouts Workbench, um Probleme bei der Bewertung von Feature Flag für bestimmte Benutzer zu diagnostizieren, einschließlich der Überprüfung, welche Funktionen für eine bestimmte Benutzeridentität aktiviert, deaktiviert oder nicht zugeordnet sind.
exl-id: d64e9573-8e18-46a1-a75a-5ae5bfc7c82d
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 1%

---

# Fehlerbehebung {#troubleshooting}

Erlebnis-Rollouts beinhalten ein integriertes Diagnose-Tool namens **Features Workbench** mit dem Sie genau verstehen können, welche Feature Flags ein bestimmter Benutzer erhält und warum. Sie können damit Berichte über unerwartetes Verhalten von Funktionen untersuchen, ohne Probleme im Code reproduzieren zu müssen.

## Zugriff auf Workbench-Funktionen {#access-workbench}

Gehen Sie wie folgt vor, um Feature Workbench zu öffnen:

1. Melden Sie sich bei der Konsole „Experience Rollouts“ an.
2. Navigieren Sie **oberen Menü zu** Workbench > Endbenutzer“.
3. Wählen Sie die **Funktionen** aus.

## Benutzeridentität eingeben {#input-identity}

Um Feature Flag-Auswertungen für einen bestimmten Benutzer anzuzeigen, geben Sie die folgenden Informationen in das Workbench-Formular ein:

* **ID-Typ** - Wählen Sie den Kennungstyp aus, den Sie verwenden. Zu den unterstützten Typen gehören E-Mail, GUID und Besucher-ID. Sie können auch direkt ein **Release-Flag** eingeben, um anhand des Flag-Werts nachzuschlagen, welche Versionen für einen Benutzer aktiviert waren.
* **ID-Wert** - Geben Sie die Benutzerkennung ein. Wenn Sie E-Mail als ID-Typ auswählen, beachten Sie, dass mehrere GUIDs mit derselben E-Mail-Adresse verknüpft werden können. Ein Dropdown-Menü GUID wird bereitgestellt, über das Sie zwischen den zugehörigen GUIDs wechseln können.
* **Auth-Quelltyp** - Wählen Sie, falls für Ihre Integration zutreffend.
* **Kontextvariablen** - Geben Sie optional Schlüssel-Wert-Paare für den Kontext an, die die Auswertung von Zielgruppenregeln beeinflussen (z. B. Land, Gerätetyp).
* **Team und Anwendung** - Wählen Sie das Team und die Anwendung aus, für die Sie Feature Flags abrufen möchten. Ihr aktuelles Team und eine seiner Anwendungen sind standardmäßig vorausgewählt.

Wählen Sie nach dem Ausfüllen des Formulars **Funktionen abrufen**.

## Interpretieren der Ergebnisse {#interpret-results}

Die Ergebnisse hängen vom eingegebenen ID-Typ ab.

### E-Mail- oder GUID-Suche {#email-guid-lookup}

Wenn Sie einen Benutzer per E-Mail oder GUID nachschlagen, werden in den Ergebnissen zwei Abschnitte angezeigt:

**Release-Flags**

In diesem Abschnitt werden drei Listen für das ausgewählte Team und die ausgewählte Anwendung angezeigt:

* **Aktiviert** - Versionen, die derzeit für diesen Benutzer aktiv sind.
* **Deaktiviert** - Versionen, die zwar vorhanden, aber für diesen Benutzer nicht aktiviert sind.
* **Unused** - Lösebits, an die keine Freigabe angehängt ist.

Versionen, die mit dem aktuell ausgewählten Team und der aktuell ausgewählten Anwendung verknüpft sind, werden oben in jeder Liste angezeigt.

**Feature Flags und Gruppen**

In diesem Abschnitt werden alle Feature Flags des ausgewählten Teams und der ausgewählten Anwendung aufgelistet, die derzeit für den Benutzer aktiviert sind. Jeder Eintrag zeigt:

* Schlüssel und Name der Feature Flag
* Funktionsgruppe (wenn das Flag zu einer gehört)
* Variante (wenn A/B-Tests konfiguriert sind)
* Ob die Markierung zielgruppenverknüpft ist

Sie können auch auf **Anfrage/Antwort anzeigen** klicken, um die genaue API-Anfrage und -Antwort zu überprüfen, die zu den Ergebnissen geführt hat.

### Nicht-selbst-E-Mail oder Nicht-GUID {#non-self-lookup}

Wenn die eingegebene E-Mail nicht Ihre eigene ist oder ein Nicht-GUID-Typ verwendet wird, wird nur der Abschnitt **Feature Flags und**) angezeigt.

### Suche nach Release-Flag {#release-flag-lookup}

Wenn Sie als ID **Typ ein** Versionsflag“ eingeben, wird nur der Abschnitt **Versionsflags** angezeigt, in dem aufgeführt wird, welche Versionen für den mit diesem Flag verknüpften Benutzer aktiviert und deaktiviert wurden.

## Häufige Probleme {#common-issues}

In der folgenden Tabelle werden häufige Probleme und deren Untersuchung mithilfe von Workbench beschrieben.

| Symptom | Was zu überprüfen ist |
|---|---|
| Benutzer erhält kein Feature Flag, das er erhalten sollte | Überprüfen Sie die Auswahl von Team und Anwendung. Überprüfen Sie, ob die ID des Benutzers mit dem Zielgruppen-Regeltyp (E-Mail, GUID usw.) übereinstimmt. Vergewissern Sie sich, dass sich die Funktion im Status **Veröffentlichen** oder **Vollständiger Rollout** befindet. |
| Die Funktion ist für alle Benutzer unerwartet aktiviert | Bestätigen Sie, dass auf die Funktion keine Zielgruppenregeln angewendet wurden oder dass der Prozentsatz auf 100 % eingestellt ist. Überprüfen Sie, ob sich die Funktion **Status „Vollständiger Rollout** befindet. |
| Zielgruppenregel stimmt nicht überein | Verwenden Sie Workbench mit Kontextvariablen, um zu bestätigen, dass die zur Laufzeit übergebenen Werte mit den in der Zielgruppenregel konfigurierten Werten übereinstimmen. |
| Feature Flag-Status ist korrekt, aber der Benutzer sieht immer noch altes Verhalten | Überprüfen Sie die für die Anwendung konfigurierte TTL. SDK speichert Funktionsdaten zwischen und aktualisiert diese nur im konfigurierten Abrufintervall. |

## Siehe auch {#see-also}

* [Support erhalten](get-support.md)
* [Support kontaktieren](contact-support.md)
