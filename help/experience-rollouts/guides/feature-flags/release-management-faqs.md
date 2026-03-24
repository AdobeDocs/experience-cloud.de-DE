---
title: Häufig gestellte Fragen zur Versionsverwaltung
description: Hier finden Sie Antworten auf häufig gestellte Fragen zur Versionsverwaltung bei Adobe Experience Rollouts.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---


# Häufig gestellte Fragen zur Versionsverwaltung {#release-management-faqs}

## Wie fordere ich eine Version an? {#request-release}

Unter [Veröffentlichung anfordern](request-a-release.md) finden Sie den vollständigen Prozess und die Informationen, die Sie bereitstellen müssen.

## Welche Zielgruppenkriterien werden für Versionen unterstützt? {#audience-criteria}

Versionen unterstützen die folgenden Zielgruppenregeln:

* ID-Typ (Kontotyp)
* Land
* Benutzer-ID (GUID)
* E-Mail-Adresse (Einzel- oder Massenliste)
* Email domain
* Client-IP
* Prozentsatz (alle Benutzer)
* Prozentsatz (nur authentifizierte Benutzer)

Sie können mehrere Regeln mithilfe der AND/OR-Logik kombinieren, einschließlich verschachtelter Bedingungen. Eine [ Anleitung zur Konfiguration finden ](update-release-audience-rules.md) unter „Versions-Zielgruppenregeln aktualisieren .

## Wie füge ich eine Anwendung zu einer Version hinzu? {#onboard-application}

Nachdem die Version erstellt wurde, öffnen Sie sie in der Konsole und fügen Sie Ihre Anwendung zur Versionskonfiguration hinzu. Der Produktversionsinhaber für jedes Programm kann dann die entsprechenden Feature Flags hinzufügen. Siehe [End-to-End-Workflow von Version](release-workflow-end-to-end.md) für die vollständige Sequenz.

## Eine Funktion wird nicht für einen Benutzer zurückgegeben, der sich qualifizieren sollte. Wie kann ich Fehler beheben? {#troubleshoot}

Führen Sie zum Debugging die folgenden Schritte aus:

1. **Überprüfen Sie den Status der Version.** Die Version muss den Status **Veröffentlicht** oder **Vollständiger Rollout** aufweisen, um Funktionen bereitzustellen. Siehe [Versionsstatus](release-states.md).
2. **Überprüfen Sie das Anwendungs- und Feature Flag.** Stellen Sie sicher, dass das Feature Flag für das richtige Programm erstellt wurde und dass das Programm mit der richtigen Version verknüpft ist.
3. **Vergewissern Sie sich, dass das Feature Flag aktiviert ist.** Eine deaktivierte Markierung wird auch dann nicht bereitgestellt, wenn die Freigabe aktiv ist.
4. **Überprüfen Sie die Zielgruppenkriterien.** Vergewissern Sie sich, dass der Benutzer alle in den Zielgruppenregeln definierten Bedingungen erfüllt. Überprüfen Sie die Kriterien für die spezifische Version, mit der die Funktion verknüpft ist.

## Siehe auch {#see-also}

* [Release anfordern](request-a-release.md)
* [Aktualisieren der Regeln für Veröffentlichungszielgruppen](update-release-audience-rules.md)
* [Versionsstatus](release-states.md)
* [End-to-End-Workflow für die Veröffentlichung](release-workflow-end-to-end.md)
