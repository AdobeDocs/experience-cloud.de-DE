---
title: Versionen und teamübergreifende Funktionsgruppen
description: Machen Sie sich mit dem Unterschied zwischen Versionen und teamübergreifenden Funktionsgruppen in den Adobe Experience Rollouts vertraut und erfahren Sie, wann welche für koordinierte Rollouts für mehrere Teams verwendet werden sollten.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 2%

---


# Versionen und teamübergreifende Funktionsgruppen {#releases-and-cross-team}

Sowohl Versionen als auch Team-übergreifende Funktionsgruppen unterstützen koordinierte Rollouts über mehrere Teams und Anwendungen hinweg. Die richtige Auswahl hängt von Ihren Caching-Anforderungen, den Zielgruppen-Targeting-Anforderungen und der gewünschten Kontrolle über den Prozess ab.

## Team-übergreifende Funktionsgruppen {#cross-team-feature-groups}

Eine Team-übergreifende Funktionsgruppe ermöglicht es Ihnen, Feature Flags aus Programmen verschiedener Teams zu bündeln und mit umfangreichen Zielgruppenkriterien zu verwalten.

Hauptmerkmale:

* **Self-Service** - Keine Support-Anfrage erforderlich, um eine zu erstellen
* **Rich-Audience** - Unterstützt alle Audience-Kriterien (Profilattribute, Kontextvariablen, prozentualer Rollout)
* **Keine Begrenzung** für die Zahl, die Sie erstellen können
* **Keine Zwischenspeicherung** - Für Auswertungen von Feature-Flags ist ein API-Aufruf erforderlich. Zwischenspeicherung auf SDK-Ebene wird nicht unterstützt

Eine schrittweise Anleitung zur Erstellung finden Sie unter [Erstellen einer teamübergreifenden Funktionsgruppe](create-cross-team-feature-group.md).

## Versionen {#releases}

Eine Version ist für große, koordinierte Launches konzipiert, bei denen eine Zwischenspeicherung auf SDK-Ebene erforderlich ist. Versionen verwenden das Token-basierte Audience-Targeting.

Hauptmerkmale:

* **Erfordert eine Support** - Versionen werden nicht vollständig selbst bereitgestellt. Wenden Sie sich an den Experience Rollouts-Support, um eine Version zu erstellen
* **SDK-Caching** - Alle Versionsdaten werden lokal im SDK-Server zwischengespeichert, wodurch API-Aufrufe reduziert werden
* **Kriterien für eingeschränkte Zielgruppe** - Zielgruppenregeln basieren auf Authentifizierungs-Token (Land, E-Mail, Benutzer-ID, Prozentsatz usw.)
* **Eingeschränkte aktive Versionen** - Eine endliche Anzahl aktiver Versionen kann gleichzeitig vorhanden sein. Planen Sie den Abschluss oder die Baseline-Veröffentlichung innerhalb von drei Monaten.

## Vergleich {#comparison}

| | Team-übergreifende Funktionsgruppe | -Version |
|---|---|---|
| Self-Service | ✓ | Erfordert Support-Anfrage |
| Kriterien für umfangreiche Zielgruppen | ✓ | Limited |
| A/B-Tests | ✗ | ✗ |
| SDK-Caching | ✗ | ✓ |
| Aktives Limit | Keine Beschränkung | Limited |

## Empfehlung {#recommendation}

Wenn Ihr Anwendungsfall umfangreiches Audience-Targeting und Self-Service-Management umfasst, verwenden Sie eine **teamübergreifende Funktionsgruppe**. Wenn Ihre Backend-Services das Caching auf SDK-Ebene erfordern und die einfacheren Zielgruppenkriterien von Versionen ausreichend sind, verwenden Sie eine **Version**.

## Siehe auch {#see-also}

* [Funktionen, Funktionsgruppen und Versionen](features-feature-groups-releases.md)
* [Erstellen einer Team-übergreifenden Funktionsgruppe](create-cross-team-feature-group.md)
* [Release anfordern](request-a-release.md)
