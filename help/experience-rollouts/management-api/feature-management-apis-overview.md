---
title: Übersicht über Feature Management-APIs
description: Überblick über die Experience Rollouts-Management-APIs, mit denen Sie Feature Flags, Feature Groups und Releases programmgesteuert erstellen, lesen, aktualisieren und löschen können.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Übersicht über Feature Management-APIs {#feature-management-apis-overview}

Mit Experience Rollouts-Management-APIs können Sie Feature Flags, Feature Groups und Releases programmgesteuert verwalten. Teams, die Workflows automatisieren oder Erlebnis-Rollouts in vorhandene Bereitstellungs-Pipelines integrieren müssen, können diese APIs anstelle der Konsole verwenden.

>[!NOTE]
>
>Der Zugriff auf die Verwaltungs-APIs mit einem Service-Token wird auf Anfrage gewährt. Wenden Sie sich an den Experience Rollouts-Support und geben Sie eine geschäftliche Begründung für die Zugriffsanfrage an.

## Verfügbare Verwaltungs-APIs {#available-apis}

Die folgenden Management-APIs sind verfügbar:

* [Feature Flags Management API](feature-flags-management-api.md) - Erstellen, Lesen, Aktualisieren und Löschen von Feature Flags für eine Anwendung.
* [Feature Group Management API](feature-group-management-api.md) - Erstellen, Lesen, Aktualisieren und Löschen von Feature Groups.
* [Versionsverwaltungs-APIs](release-management-apis.md) - Erstellen und bearbeiten Sie Team-übergreifende Funktionsgruppen und Versionen.

## Gemeinsame Anforderungen {#common-requirements}

Alle Management-API-Aufrufe erfordern Folgendes:

* Ein **API-Schlüssel** aus der Adobe Developer Console - siehe [Abonnieren der API-Anwendung](../guides/integrate/subscribe-to-api-application.md).
* Ein **IMS-Benutzerzugriffstoken** oder **Service-Token**, das als `Bearer <token>` in der `Authorization`-Kopfzeile übergeben wird.
* Ein `Content-Type: application/json`.

API-Schlüssel und Token müssen für Staging- und Produktionsumgebungen separat bereitgestellt werden.

## Hilfsleitfäden {#helper-guides}

Die folgenden Handbücher helfen beim Erstellen der richtigen API-Payloads:

* [Client-ID für ein Programm abrufen](get-client-id.md) - Suchen Sie die numerische Client-ID, die für Feature Flags und Feature Group Management-APIs erforderlich ist.
* [Abrufen der gewünschten Zielgruppenkriterien](get-audience-criteria.md) - Verwenden Sie die Konsole und die GET-API, um die richtige JSON-Struktur für Zielgruppenkriterien zu generieren.
* [Management Patch-API](management-patch-api.md) - Aktualisieren Sie einzelne Felder eines Feature Flags, einer Feature Group oder einer Team-übergreifenden Feature Group, ohne das vollständige Objekt zu übergeben.

## Siehe auch {#see-also}

* **GET Feature API V3** und **GET Feature API V2** - im Abschnitt Funktions-API dieses Handbuchs finden Sie die vollständigen Verweise.
* [Abonnieren des API-Programms](../guides/integrate/subscribe-to-api-application.md)
