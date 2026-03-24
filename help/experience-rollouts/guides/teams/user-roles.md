---
title: Benutzerrollen
description: Erfahren Sie mehr über die fünf Benutzerrollen, die in Adobe Experience Rollouts verfügbar sind, und wie Sie für jedes Teammitglied die richtige Rolle auswählen.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---


# Benutzerrollen {#user-roles}

Erlebnis-Rollouts bietet fünf Rollen. Jede Rolle ist auf eine bestimmte Reihe von Zuständigkeiten zugeschnitten. Rollen schließen sich standardmäßig gegenseitig aus - Mitglieder mit der Administratorrolle haben nicht automatisch die Berechtigung „Produktversionsinhaber“. Weisen Sie einem Mitglied mehrere Rollen zu, wenn ein umfassenderer Zugriff erforderlich ist.

## Verfügbare Rollen {#roles}

| Rolle | Zuständigkeiten |
|---|---|
| **Admin** | integriert Anwendungen in die Konsole, verwaltet Team-Mitglieder und genehmigt oder lehnt Zugriffsanfragen ab. Erforderlich, bevor das Team Feature Flags verwenden kann. |
| **Produktversionsinhaber** | Erstellt und aktualisiert Feature Flags und Feature Groups für ihre Anwendung. Kann Zielgruppen mit Feature Flags verknüpfen, um Funktionen für externe Benutzer verfügbar zu machen. |
| **Entwicklerin/Entwickler** | Funktioniert in einem Sandbox-Kontext, um Funktionen hinter Feature Flags zu testen, ohne andere Benutzer zu beeinflussen. Kann eine Feature Flag für eine private Zielgruppe (z. B. eine bestimmte Benutzer-ID oder E-Mail-Adresse) in der Staging- oder Produktionsumgebung bereitstellen. |
| **Feature Admin** | Erstellt und verwaltet Team-übergreifende Funktionsgruppen. Verwenden Sie diese Rolle bei der Koordinierung von Flags in Programmen, die verschiedenen Teams gehören. |
| **Versionsmanager** | Verwaltet Versionen mit mehreren Teams und Anwendungen und aktualisiert die Zielgruppenregeln, die definieren, wer eine Version erhält. |

## Auswählen der richtigen Rolle {#choosing}

Verwenden Sie die folgende Anleitung, um Rollen zuzuweisen:

* **Hinzufügen oder Aktualisieren von Feature Flags für Ihr Programm** → **Product Release Owner**
* **Testen von Funktionen privat, ohne andere zu**→ **Developer**
* **Team-übergreifende Funktionsgruppen verwalten** → **Funktionsadministrator**
* **Verwalten von Versionen über mehrere Teams und Anwendungen hinweg** → **Release Manager**
* **Onboarding von Programmen und Verwalten der Team-**→ **Admin**

>[!NOTE]
>
>Ein Mitglied kann mehr als eine Funktion innehaben. Beispielsweise sollte ein Ingenieur, der Funktionen testet und die Anwendungen des Teams verwaltet, sowohl über die Rollen **Entwickler** als auch **Administrator** verfügen.

## Berechtigungsfehler {#permissions-error}

Wenn beim Aktualisieren einer Funktion oder Gruppe der Fehler „Nicht genügend Berechtigungen“ auftritt, benötigen Mitglieder die Rolle **Produktversionsinhaber** . Wenden Sie sich an Ihren Team-Administrator, damit diese Rolle hinzugefügt wird.

## Siehe auch {#see-also}

* [Mitglieder zu Ihrem Team hinzufügen](add-team-members.md)
* [Teams verwalten](manage-teams.md)
