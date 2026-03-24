---
title: Versionsstatus
description: Erfahren Sie mehr über die Lebenszyklusstatus einer Version in Adobe Experience Rollouts, einschließlich der Bedeutung der einzelnen Status und der zulässigen Transitionen.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 3%

---


# Versionsstatus {#release-states}

Versionsverwalter können den Status von Versionen direkt über die Navigationsleiste der Konsole aktualisieren. Der Status steuert, ob die Version live, auf Tests beschränkt, vollständig ausgerollt oder geschlossen ist.

## Verfügbare Status {#states}

| # | Land | Beschreibung | Zulässige Änderungen |
|---|---|---|---|
| 1 | **Entwurf** | Die Version wird im System gespeichert, ist aber noch nicht aktiv. Es werden keine Zielgruppenregeln angewendet. | Alle zulässigen Änderungen (Version, Funktionen, Zielgruppe). |
| 2 | **Gespeichert** | Die Freigabe wird registriert und ihr wird ein Slot zugewiesen. Die Version ist für Benutzer noch nicht sichtbar. | Alle Änderungen zulässig. |
| 3 | **Veröffentlicht** | Die Version ist für die angegebene Zielgruppe live. Benutzer, die die Zielgruppenkriterien erfüllen, erhalten die Funktionen. | Alle Änderungen zulässig. |
| 4 | **Vollständiger Rollout** | Die Version steht allen Benutzern unabhängig von den Zielgruppenregeln zur Verfügung. Alle Zielgruppenregeln werden entfernt. | Funktionsänderungen zulässig. Zielgruppe kann nicht geändert werden. |
| 5 | **Baseline** | Alle Benutzer verfügen jetzt über die Funktionen dieser Version als Standardverhalten. Der bedingte Code kann entfernt werden. Der Freigabeschlitz ist freigegeben. | Keine Änderungen zulässig. |
| 6 | **abgebrochen** | Die Veröffentlichung wurde gestoppt. Keine Benutzer erhalten Funktionen aus dieser Version. Der Freigabeschlitz ist freigegeben. | Keine Änderungen zulässig. |

## Zulässige Übergänge {#transitions}

Nicht alle Statusübergänge sind zulässig. Wenn Sie die zulässigen Pfade verstehen, können Sie den Rollout planen und Fehler beim Verwalten von Statusänderungen vermeiden:

* Eine Version kann durch die Status Entwurf → Gespeichert → Veröffentlicht → Vollständiger Rollout → Grundlinie weitergeleitet werden
* Eine Version kann im Entwurfsmodus, im gespeicherten Modus, im Veröffentlichungsmodus oder im vollständigen Rollout abgebrochen werden
* Nach Baseline oder Abbruch sind keine weiteren Änderungen zulässig

## Freigabekapazität {#capacity}

Die Anzahl der aktiven (gespeicherten oder veröffentlichten) Versionen ist jederzeit begrenzt. So geben Sie Kapazitäten frei:

* Verschieben abgeschlossener Versionen nach **Baseline** sobald alle teilnehmenden Anwendungen ihren bedingten Code entfernt haben.
* **Abbruch** Versionen, die nicht erfolgreich waren und nicht fortgesetzt werden.

Planen Sie die Veröffentlichung oder brechen Sie die Veröffentlichung innerhalb von drei Monaten ab.

## Siehe auch {#see-also}

* [Release anfordern](request-a-release.md)
* [End-to-End-Workflow für die Veröffentlichung](release-workflow-end-to-end.md)
* [Aktualisieren der Regeln für Veröffentlichungszielgruppen](update-release-audience-rules.md)
