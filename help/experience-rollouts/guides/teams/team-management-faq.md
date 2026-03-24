---
title: Häufig gestellte Fragen zur Team-Verwaltung
description: Hier finden Sie Antworten auf häufig gestellte Fragen zur Verwaltung von Teams, Mitgliedern und Rollen bei den Rollouts zu Adobe Experience Platform.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---


# Häufig gestellte Fragen zur Team-Verwaltung {#team-management-faq}

## Ich versuche, einen Benutzer hinzuzufügen, aber die Suche gibt keine Ergebnisse zurück {#user-not-found}

Dies kann in der Staging-Umgebung auftreten, wenn sich der Benutzer noch nie bei der Staging-Umgebung angemeldet hat. Um dies zu beheben, bitten Sie den Benutzer, sich mindestens einmal bei der Staging-Konsole anzumelden, um sein Konto im Staging-Identitätssystem zu erstellen. Nachdem sie sich angemeldet haben, versuchen Sie erneut, nach ihnen zu suchen.

## Ich bin Administrator, kann jedoch keine Feature Flags erstellen oder bearbeiten {#admin-cannot-edit-flags}

Rollen in Experience Rollouts schließen sich gegenseitig aus. Die Rolle **Admin** gewährt Team-Management-Berechtigungen, umfasst jedoch nicht die Berechtigungen eines **Produktversionsinhabers**. Um Feature Flags zu erstellen und zu bearbeiten, benötigt ein Mitglied neben der Rolle **Admin** die Rolle **Produktversionsinhaber**.

Wenden Sie sich an Ihren Team-Administrator, um zusätzliche Rollen zuweisen zu lassen. Unter [Benutzerrollen](user-roles.md) finden Sie eine vollständige Aufschlüsselung der Möglichkeiten, die die einzelnen Rollen haben.

## Haben Administratoren eine Hierarchie? Kann ein Administrator einen anderen überschreiben? {#admin-hierarchy}

Nein. Teams in Erlebnis-Rollouts haben eine flache Struktur. Alle Mitglieder mit der **Admin**-Rolle haben dieselben Berechtigungen und können die Konfigurationen der anderen Mitglieder verwalten. Es gibt keinen hierarchischen Genehmigungs-Workflow zwischen Administratoren.

## Wie entferne ich ein Mitglied aus meinem Team? {#remove-member}

Mitglieder werden über das Zugriffsverwaltungssystem entfernt. Suchen Sie als Administrator den Zugriffsdatensatz des Mitglieds für Ihr Team und widerrufen Sie dessen Rolle. Wenn Sie sich nicht sicher sind, wie Sie dies tun sollen, wenden Sie sich an das Zugriffsverwaltungs-Team Ihres Unternehmens.

## Kann ein Mitglied mehr als eine Funktion haben? {#multiple-roles}

Ja. Weisen Sie einem Mitglied mehrere Rollen zu, wenn seine Verantwortlichkeiten mehr als eine Funktion umfassen. Beispielsweise sollte ein Teammitglied, das sowohl das Team verwaltet als auch Feature Flags erstellt, sowohl über die Rollen **Admin** als auch **Product Release Owner** verfügen.

## Siehe auch {#see-also}

* [Benutzerrollen](user-roles.md)
* [Mitglieder zu Ihrem Team hinzufügen](add-team-members.md)
* [Teams verwalten](manage-teams.md)
