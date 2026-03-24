---
title: Erstellen des ersten Feature Flags
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts ein Feature Flag erstellen, eine Zielgruppe festlegen und testen, bevor Sie sie für Benutzende bereitstellen.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Erstellen des ersten Feature Flags {#create-feature-flag}

## Voraussetzungen {#prerequisites}

Bevor Sie ein Feature Flag erstellen, führen Sie Folgendes aus:

* Sie haben Zugriff auf die Konsole „Experience Rollouts“ — siehe [Bei Konsole anmelden](../console/log-in-to-the-console.md)
* Sie gehören einem Team an - siehe [Verwalten von Teams](../teams/manage-teams.md)
* Ihr Programm wurde integriert - siehe [Onboarding Ihres Programms](../applications/onboard-your-application.md)
* Sie haben die Rolle **Entwickler** oder **Produktversionsinhaber** (siehe [Benutzerrollen](../teams/user-roles.md)

## Schritt 1: Feature Flag erstellen {#create}

Gehen Sie wie folgt vor, um ein neues Feature Flag in der Konsole zu erstellen:

1. Melden Sie sich bei der Konsole „Experience Rollouts“ an und navigieren Sie zu **Funktionen und Versionen > Feature Flags**.
2. Wählen Sie Ihr Programm aus der Dropdown **Liste** Programm“ aus.
3. Wählen Sie **Neue Funktion** aus.
4. Geben Sie einen Titel, einen Schlüssel, eine Beschreibung und optional ein Tag an.
5. Fügen Sie optional Zielgruppenkriterien hinzu (siehe Schritt 2).
6. Speichern Sie Ihre Feature Flag-Einstellungen.

## Schritt 2: Audience-Kriterien hinzufügen {#audience}

Zielgruppenkriterien steuern, welche Benutzer die Funktion sehen. Sie können Kriterien hinzufügen, die auf folgenden Kriterien basieren:

* Profilattribute (wie Land, E-Mail-Domain, Benutzer-ID)
* Kontextvariablen
* Vordefinierte Zielgruppensegmente

Um Zielgruppenkriterien hinzuzufügen, wechseln Sie zur Registerkarte **Zielgruppe** , wenn Sie ein Feature Flag erstellen oder bearbeiten.

>[!NOTE]
>
>Die **Entwickler**-Rolle ist Sandbox. Entwickler können eine Funktion nur für sich selbst bereitstellen, indem sie ihre eigene Benutzer-ID unter **Zielgruppe > Profil > Benutzer-ID** hinzufügen. Um eine Funktion für externe Benutzer verfügbar zu machen, benötigen Sie die Rolle **Produktversionsinhaber** .

## Schritt 3: Audience-Größe berechnen {#audience-size}

Nachdem Sie Zielgruppenkriterien hinzugefügt haben, wählen **in der** Leiste die Option „Berechnen“ aus, um eine geschätzte Anzahl der Benutzer zu erhalten, die sich für die Funktion qualifizieren. Auf diese Weise können Sie Ihre Zielgruppenbestimmung vor der Live-Schaltung validieren.

## Schritt 4: Zeitplan (optional) {#schedule}

Sie können festlegen, dass eine Feature Flag zu einem späteren Zeitpunkt aktiviert wird. Weitere Informationen [&#x200B; Sie unter &#x200B;](schedule.md).

## FAQ: Ich kann kein Feature Flag als Entwickler hinzufügen {#faq}

Die **Entwickler**-Rolle ist Sandbox. Entwickler können Funktionen privat testen, indem sie ihre Benutzer-ID zur Zielgruppe hinzufügen. Sie können Funktionen nicht für externe Benutzer verfügbar machen. Verwenden Sie die Rolle **Produktversionsinhaber**, um Funktionen für externe Benutzer freizugeben. Wenden Sie sich an Ihren Team-Administrator, um Ihre Rolle zu aktualisieren.

## Siehe auch {#see-also}

* [Festlegen einer Funktion für das schrittweise Rollout](set-feature-gradual-rollout.md)
* [Erstellen einer Funktionsgruppe](create-a-feature-group.md)
* [Benutzerrollen](../teams/user-roles.md)
