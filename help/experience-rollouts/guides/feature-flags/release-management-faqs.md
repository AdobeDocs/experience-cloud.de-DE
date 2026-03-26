---
title: Häufig gestellte Fragen zur Versionsverwaltung
description: Hier finden Sie Antworten auf häufig gestellte Fragen zur Versionsverwaltung bei Adobe Experience Rollouts.
exl-id: 802b99bd-85ee-4f4d-afca-88d1297f8782
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# Häufig gestellte Fragen zur Versionsverwaltung {#release-management-faqs}

## Wie fordere ich eine Version an? {#request-release}

Wenden Sie sich an den Experience Rollouts-Support , um eine Version anzufordern. Geben Sie Ihren Team-Namen, die Anwendungsdetails, die Zielgruppe und die gewünschte Rollout-Zeitleiste an.

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

Sie können mehrere Regeln mithilfe der AND/OR-Logik kombinieren, einschließlich verschachtelter Bedingungen.

## Wie füge ich eine Anwendung zu einer Version hinzu? {#onboard-application}

Nachdem die Version erstellt wurde, öffnen Sie sie in der Konsole und fügen Sie Ihre Anwendung zur Versionskonfiguration hinzu. Der Produktversionsinhaber für jedes Programm kann dann die entsprechenden Feature Flags hinzufügen.

## Eine Funktion wird nicht für einen Benutzer zurückgegeben, der sich qualifizieren sollte. Wie kann ich Fehler beheben? {#troubleshoot}

Führen Sie zum Debugging die folgenden Schritte aus:

1. **Überprüfen Sie den Status der Version.** Die Version muss den Status **Veröffentlicht** oder **Vollständiger Rollout** aufweisen, um Funktionen bereitzustellen.
2. **Überprüfen Sie das Anwendungs- und Feature Flag.** Stellen Sie sicher, dass das Feature Flag für das richtige Programm erstellt wurde und dass das Programm mit der richtigen Version verknüpft ist.
3. **Vergewissern Sie sich, dass das Feature Flag aktiviert ist.** Eine deaktivierte Markierung wird auch dann nicht bereitgestellt, wenn die Freigabe aktiv ist.
4. **Überprüfen Sie die Zielgruppenkriterien.** Vergewissern Sie sich, dass der Benutzer alle in den Zielgruppenregeln definierten Bedingungen erfüllt. Überprüfen Sie die Kriterien für die spezifische Version, mit der die Funktion verknüpft ist.

## Siehe auch {#see-also}

* [Support kontaktieren](../support/contact-support.md)
