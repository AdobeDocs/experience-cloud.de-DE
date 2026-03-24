---
title: Integrationsschritte
description: Befolgen Sie die Integrationsschritte für Ihren Anwendungstyp, um Adobe Experience Rollouts mit Ihrem Webservice, Web- oder Mobile App oder Desktop-Programm zu verbinden.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# Integrationsschritte {#integration-steps}

Wählen Sie den Integrationspfad aus, der Ihrem Anwendungstyp entspricht.

## Web-Dienste {#web-services}

Backend-Services werden über eine Server-seitige SDK integriert. Wählen Sie die SDK für Ihren Technologie-Stack.

**Java**

Befolgen Sie das [Handbuch zur Java SDK-Integration](../sdk-releases/java/java-sdk-integration-guide.md) für Einrichtung, Abhängigkeitskonfiguration und Initialisierung.

**Node.js**

Befolgen Sie [Node.js-SDK-Integrationshandbuch](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md) für die Einrichtung und Initialisierung.

**Andere Sprachen**

Wenn Ihr Stack oben nicht aufgeführt ist, integrieren Sie ihn direkt in **Feature API V3** (siehe den Abschnitt zur Feature API dieses Handbuchs). Wenden Sie sich an den Support bei Experience Rollouts , wenn Sie Anleitung benötigen.

## Web und mobile Anwendungen {#web-mobile}

Web- und mobile Anwendungen rufen die **Feature API V3** auf, um Feature Flags für den aktuellen Benutzer abzurufen und bedingte Logik in der Anwendung anzuwenden.

Siehe **GET Feature API V3** im Abschnitt Funktions-API dieses Handbuchs für die vollständige API-Referenz.

## Desktop-Programme {#desktop}

Desktop-Programme rufen die **Feature API V2** auf, um Feature Flags abzurufen.

Siehe **GET Feature API V2** im Abschnitt Funktions-API dieses Handbuchs für die vollständige API-Referenz.

>[!IMPORTANT]
>
>Desktop-Clients müssen den TTL-Wert in der API-Antwort berücksichtigen und eine elegante Fehlerbehandlung für die Nichtverfügbarkeit der API implementieren. Siehe [Desktop-Programme](desktop-applications.md) für die Anforderungen.

## Siehe auch {#see-also}

* [Starthandbuch](startup-guide.md)
* [SDKs](sdks.md)
* [Web-Dienste](web-services.md)
* [Desktop-Programme](desktop-applications.md)
