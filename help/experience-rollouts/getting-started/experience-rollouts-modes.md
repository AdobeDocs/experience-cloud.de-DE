---
title: Erlebnis-Rollout-Modi
description: Erfahren Sie mehr über die beiden Funktions-Targeting-Modi in Adobe Experience Rollouts - Zielgruppenbestimmung auf Benutzerebene und Zielgruppenbestimmung auf Organisationsebene - und wann jeder dieser Modi verwendet werden sollte.
source-git-commit: bb4541dd7a77edadded2edbc9c71905cf70f2e24
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 3%

---


# Erlebnis-Rollout-Modi {#modes}

Erlebnis-Rollouts bietet zwei unterschiedliche Targeting-Modi für Funktionen. Jede Version erfüllt einen anderen Zweck der Versionskontrolle und ist für einen bestimmten Anwendungstyp oder Anwendungsfall konzipiert.

>[!TIP]
>
>Wählen Sie den Modus basierend auf dem, was Sie steuern: einzelne Benutzersitzungen oder Organisations- und Umgebungsbereiche.

## Zielgruppenbestimmung auf Benutzerebene {#user-level}

### Überblick {#user-level-overview}

Die Zielgruppenbestimmung auf Benutzerebene ermöglicht den Rollout von Funktionen auf Benutzerebene. Es unterstützt die präzise Zielgruppenbestimmung bestimmter Benutzender, interner Tester, kanarischer Benutzender und prozentuale schrittweise Rollouts.

Dieser Modus eignet sich am besten für Anwendungen, bei denen das Erlebnis je nach angemeldetem Benutzer unterschiedlich aussehen muss.

### Verwendungszeitpunkt {#user-level-when}

Verwenden Sie Targeting auf Benutzerebene, wenn Sie Folgendes tun möchten:

* Aktivieren einer Funktion für bestimmte Benutzer
* Durchführen von A/B-Experimenten
* Canary-Tests mit einer kleinen Gruppe vor einem größeren Rollout durchführen
* Schrittweises Rollout einer Funktion nach Prozentsatz der Benutzer
* Optimieren Sie das Erlebnis basierend auf einzelnen Benutzerattributen (z. B. E-Mail-Domain oder Profildaten)

### Einschränkungen {#user-level-limitations}

Das Targeting auf Benutzerebene ist nicht für die folgenden Szenarien konzipiert:

* Steuert keine Funktionen auf Organisations-, Umgebungs- oder Regionsebene
* Nicht für die mandantenweite Aktivierung von Funktionen oder Berechtigungs-Gating vorgesehen

## Zielgruppenbestimmung auf Organisations- und Umgebungsebene {#org-level}

### Überblick {#org-level-overview}

Die Zielgruppenbestimmung auf Organisationsebene ermöglicht den Rollout von Funktionen im Umfang von Organisation, Umgebung und Region. Es steuert die Verfügbarkeit von Funktionen für gesamte Unternehmen oder bestimmte Bereitstellungsumgebungen und nicht für einzelne Benutzer.

Dieser Modus ist für Funktionen auf Unternehmensebene und umgebungsspezifische Rollouts konzipiert.

### Verwendungszeitpunkt {#org-level-when}

Verwenden Sie Targeting auf Organisationsebene, wenn Sie Folgendes tun möchten:

* Aktivieren einer Funktion für eine gesamte Organisation
* Kontrollieren der Funktionsverfügbarkeit nach Umgebung (z. B. Staging oder Produktion)
* Durchführen eines regionalen Rollouts
* Gate-Funktionen basierend auf der Berechtigungs- oder Abonnementebene

### Einschränkungen {#org-level-limitations}

Das Targeting auf Org- und Umgebungsebene ist nicht für die folgenden Szenarien konzipiert:

* Unterstützt kein Rich-User-Profil-basiertes Targeting
* Unterstützt keinen prozentualen Rollout auf der Ebene einzelner Benutzer
* Nicht für Experimente oder A/B-Tests vorgesehen

## Vergleich {#comparison}

| Dimension | Zielgruppenbestimmung auf Benutzerebene | Zielgruppenbestimmung auf Organisations- und Umgebungsebene |
|---|---|---|
| Kontrollbereich | Individueller Benutzer | Organisation, Umgebung, Region |
| Zielgruppenbestimmungsgrundlage | Benutzerprofil und Attribute | Organisations- und Umgebungskontext |
| Rollout in Prozent | Ja | Nein |
| A/B-Tests | Ja | Nein |
| Enterprise-Gating | Nein | Ja |

## Den richtigen Modus wählen {#choosing}

* Wenn Ihre Frage *lautet: „Welche Benutzer sollten diese Funktion sehen?“* → Verwenden **Targeting auf Benutzerebene**
* Wenn Ihre Frage lautet *„Welche Organisationen oder Umgebungen sollten diese Funktion nutzen?“* → Verwenden Sie **org- und Targeting auf Umgebungsebene**
