---
title: Erstellen einer Team-übergreifenden Funktionsgruppe
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts eine Team-übergreifende Funktionsgruppe erstellen, um Feature Flags über Anwendungen hinweg zu koordinieren, die verschiedenen Teams gehören.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 2%

---


# Erstellen einer Team-übergreifenden Funktionsgruppe {#create-cross-team-feature-group}

## Voraussetzungen {#prerequisites}

Bevor Sie eine Team-übergreifende Funktionsgruppe erstellen, bestätigen Sie Folgendes:

* Sie haben Zugriff auf die Konsole — siehe [Bei Konsole anmelden](../console/log-in-to-the-console.md)
* Sie gehören einem Team an und Ihr Programm wird integriert
* Sie verfügen über die **Funktionsadministrator**-Rolle — siehe [Benutzerrollen](../teams/user-roles.md)
* Sie haben die Feature Flags erstellt, die einbezogen werden sollen - siehe [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)

Eine Team-übergreifende Funktionsgruppe ermöglicht es, Feature Flags aus Programmen über mehrere Teams mit umfassender Zielgruppen-Zielgruppenbestimmung zu bündeln. Im Gegensatz zu Versionen ist es vollständig selbstbedienend und hat keine Begrenzung für die Anzahl, die Sie erstellen können. Siehe [Versionen und teamübergreifende Funktionsgruppen](releases-and-cross-team-feature-groups.md) für einen Vergleich.

## Schritt 1: Erstellen der Team-übergreifenden Feldergruppe {#create}

Starten Sie den Erstellungsprozess über den Abschnitt Versionen der Konsole:

1. Navigieren Sie **der Konsole zu** Funktionen und Versionen > Versionen“.
2. Wählen Sie **Neue Funktionsgruppe (Team-übergreifend)** aus.

## Schritt 2: Grundlegende Details {#basic-details}

Geben Sie einen Titel, einen Schlüssel, eine Beschreibung und optional ein Tag an. Konfigurieren Sie die folgenden Optionen:

* **Rollout in Prozent** - Legen Sie fest, wie viel von der Zielgruppe die Funktion erhält.
* **Rollout-Typ** - Auf „Manuell“ einstellen. Der Prozentsatz wird im Laufe des Rollouts Schritt für Schritt verwaltet.

>[!NOTE]
>
>A/B-Tests werden für Team-übergreifende Funktionsgruppen nicht unterstützt. Verwenden Sie zum Ausführen von A/B[Tests eine Standardfunktionsgruppe ](create-a-feature-group.md)Anwendungen müssen sich im selben Team befinden).

## Schritt 3: Zielgruppe {#audience}

Aktivieren Sie auf **Registerkarte** Zielgruppe **die Option Zielgruppenregeln** und konfigurieren Sie:

* **Segmente** - Wählen Sie ein vordefiniertes Zielgruppensegment aus.
* **Zusätzliche Filter** - Fügen Sie direkt profilbasierte oder kontextbasierte Kriterien hinzu.
* **Anwendungen** - Wählen Sie eine oder mehrere Anwendungen aus Ihrem Team oder anderen Teams aus.

>[!IMPORTANT]
>
>Durch das Hinzufügen einer Anwendung von einem anderen Team erhalten die Feature Admins dieses Teams das Recht, dieser teamübergreifenden Funktionsgruppe Feature Flags für ihre Anwendung hinzuzufügen. Sie können ihre Feature Flags nicht selbst hinzufügen.

## Schritt 4: Funktionen {#features}

Auf der Registerkarte **Funktionen** wird ein Feld für jede enthaltene Anwendung angezeigt:

* Für Programme in Ihrem eigenen Team können Sie Feature Flags direkt hinzufügen.
* Für Bewerbungen von anderen Teams sind diese Felder ausgegraut - die Feature Admins des jeweiligen Teams müssen ihre Flags hinzufügen.

>[!IMPORTANT]
>
>Ein Feature Flag kann jeweils nur über eine Methode bereitgestellt werden. Wenn Sie einer Team-übergreifenden Funktionsgruppe eine Markierung hinzufügen, werden alle Zielgruppen- oder prozentualen Rollout-Sets im Flag direkt entfernt. Flags, die bereits in einer anderen Version oder Funktionsgruppe enthalten sind, werden nicht angezeigt.

## Schritt 5: Zeitplan (optional) {#schedule}

Sie können die Aktivierung der Team-übergreifenden Funktionsgruppe zu einem späteren Zeitpunkt planen. Weitere Informationen [ Sie unter ](schedule.md).

## Verwalten von Status {#states}

Das Team, das die Team-übergreifende Funktionsgruppe erstellt, ist dafür verantwortlich und kann ihren Status verwalten. Funktions-Admin-Mitglieder des Eigentümerteams können über das Dropdown-Menü Status zwischen Status wechseln:

| Land | Beschreibung |
|---|---|
| **Speichern** | Gespeichert und nicht live. Alle Änderungen sind zulässig. |
| **Veröffentlichen** | Live für die konfigurierte Zielgruppe. Funktionsadministratoren können mit der Aktualisierung von Zielgruppenkriterien und Rollout-Prozentsatz fortfahren. |
| **Vollständiger Rollout** | Verfügbar für alle Benutzer. Nach diesem Punkt kann die Zielgruppe nicht mehr weiter eingeschränkt werden. |
| **Baseline** | Funktionen sind jetzt der Standard. Die Team-übergreifende Funktionsgruppe ist geschlossen. |
| **abbrechen** | Der Rollout wird angehalten. Von dieser Gruppe erhalten keine Benutzer Funktionen. |

## Häufig gestellte Fragen (FAQ) {#faqs}

**Gibt es eine Begrenzung für die Anzahl teamübergreifender Funktionsgruppen?**
Nein. Im Gegensatz zu -Versionen gibt es keine Beschränkung. Archivieren oder deaktivieren Sie jedoch Gruppen, wenn sie nicht mehr benötigt werden.

**Was ist der Unterschied zwischen einer Version und einer teamübergreifenden Funktionsgruppe?**
Siehe [Versionen und teamübergreifende Funktionsgruppen](releases-and-cross-team-feature-groups.md) für einen detaillierten Vergleich.

## Siehe auch {#see-also}

* [Versionen und teamübergreifende Funktionsgruppen](releases-and-cross-team-feature-groups.md)
* [Erstellen einer Funktionsgruppe](create-a-feature-group.md)
