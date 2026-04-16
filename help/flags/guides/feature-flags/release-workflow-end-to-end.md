---
title: End-to-End-Workflow für die Veröffentlichung
description: Lernen Sie den kompletten Workflow zur Verwaltung einer koordinierten Version in Flags kennen, von der Definition von Feature Flags bis zur Live-Schaltung.
hide: true
exl-id: 086e3192-c22b-4de8-a15a-89edb09ac230
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---

# End-to-End-Workflow für die Veröffentlichung {#release-workflow}

Auf dieser Seite wird die vollständige Abfolge der Aktivitäten einer koordinierten Version beschrieben, die von einem Release Manager verwaltet wird.

## &#x200B;1. Feature Flags pro Anwendung definieren {#define-flags}

Jedes Produkt-Team weist einen **Produktversionsinhaber** zu, der sich bei der Flags -Konsole anmeldet und Feature Flags für die Anwendungen erstellt, deren Inhaber er ist. Das Produkt-Team implementiert dann die bedingte Logik in seinem Code und platziert Funktionen hinter diesen Flags.

## &#x200B;2. Erstellen der Version {#create-release}

Für die Erstellung einer neuen Version ist eine Support-Anfrage erforderlich - sie erfolgt nicht vollständig selbst. Kontaktieren Sie den Flags-Support, damit die Version erstellt wird. Geben Sie den Versionsnamen, das Eigentümer-Team, die Zielumgebung, das Ziel, die teilnehmenden Anwendungen und die erwartete Dauer an.

Sobald die Veröffentlichung bestätigt wurde, öffnet der Release Manager die Konsole und schließt die Konfiguration der Version ab.

## &#x200B;3. Hinzufügen von Feature Flags zur Version {#add-flags}

Für jedes Programm, das der Version hinzugefügt wird, meldet sich der Produktversionsinhaber des Programms an und fügt die entsprechenden Feature Flags zur Version hinzu. Diese Flags stellen die Funktionen dar, die mit der Version live geschaltet werden.

## &#x200B;4. Konfigurieren der Audience {#configure-audience}

Der Release Manager wählt die Zielgruppe für die Veröffentlichung aus, z. B. 1 % der Benutzer in einem bestimmten Land, alle Benutzer mit einer bestimmten E-Mail-Domain oder eine Liste bestimmter Benutzer-IDs. Nach der Konfiguration speichert und veröffentlicht der Release Manager die Version, wodurch sie für die angegebene Zielgruppe live geschaltet wird.

## &#x200B;5. Erweitern und Verwalten des Rollouts {#expand}

Nach der Live-Schaltung kann der Release-Manager die Zielgruppenregeln anpassen, um den Rollout schrittweise zu erweitern, Probleme zu überwachen und den Lebenszyklus mithilfe der Steuerelemente für den Versionsstatus zu verwalten. Weitere Informationen [ Sie unter ](release-states.md)Versionsstatus“.

## Wichtigste Punkte {#key-points}

* Alle teilnehmenden Anwendungen stellen ihren Code unabhängig hinter Feature Flags für die Produktion bereit. Es ist kein koordinierter Bereitstellungszeitpunkt erforderlich.
* Die Version ist der zentrale Kontrollpunkt, der alle Flags über alle Teams hinweg gleichzeitig aktiviert.
* Das Audience-Targeting für -Versionen basiert auf Authentifizierungs-Token-Attributen (Land, E-Mail, Benutzer-ID, Prozentsatz).

## Siehe auch {#see-also}

* [Release anfordern](request-a-release.md)
* [Aktualisieren der Regeln für Veröffentlichungszielgruppen](update-release-audience-rules.md)
* [Versionsstatus](release-states.md)

<!-- -->
