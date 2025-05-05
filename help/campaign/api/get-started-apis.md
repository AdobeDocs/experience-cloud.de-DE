---
title: Erste Schritte mit Campaign REST-APIs
description: Erstellen Sie Integrationen und bauen Sie Ihr eigenes Ökosystem auf, indem Sie Campaign mit einer Reihe von Technologien verknüpfen.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierter Benutzer beschränkt"
exl-id: c6968252-a012-4029-bbb8-66f4f693e99b
source-git-commit: ea8b978d8f71942c8d034804ca269957a09a52db
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 48%

---

# Erste Schritte mit Campaign REST-APIs {#get-started-apis}

>[!CAUTION]
>
>Diese Dokumentation richtet sich an Adobe Campaign Standard-Kunden, die zu Campaign v8 migrieren.
>
>Bevor Sie API-Aufrufe ausführen, überprüfen Sie bitte die Volumenbeschränkungen in Ihrer Lizenzvereinbarung. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://helpx.adobe.com/de/legal/product-descriptions/campaign-standard.html#ITInfrastructureResourcesbyActiveProfilesTiers).

Mit den Campaign REST-APIs können Sie **Integrationen erstellen** für Adobe Campaign erstellen und **Ihr eigenes Ökosystem**, indem Sie Adobe Campaign mit dem von Ihnen verwendeten Technologiebereich verbinden.

Mit den Adobe Campaign REST-APIs erhalten Sie Zugriff auf die folgenden Funktionen:

<table><tr>
 <td valign="top"><a href="retrieving-profiles.md"><img width="60px" alt="Bedingungen" src="assets/icon_profile.svg"/></a><p><a href="retrieving-profiles.md">Profile</a></p></td>
<td valign="top"><a href="creating-a-service.md"><img width="60px" alt="Bedingungen" src="assets/icon_services.svg"/></a><p><a href="creating-a-service.md">Dienste und Abonnements</a></p></td>
<td valign="top"><a href="interacting-with-custom-resources.md"><img width="60px" alt="Bedingungen" src="assets/icon_customresources.svg"/></a><p><a href="interacting-with-custom-resources.md">Benutzerdefinierte Ressourcen</a></p></td>
<td valign="top"><a href="controlling-a-workflow.md"><img width="60px" alt="Bedingungen" src="assets/icon_workflows.svg"/></a><p><a href="controlling-a-workflow.md">Workflows</a></p></td>
<td valign="top"><a href="managing-transactional-messages.md"><img width="60px" alt="Bedingungen" src="assets/icon_transactionalmessage.svg"/></a><p><a href="managing-transactional-messages.md">Transaktionsnachrichten</a></p></td>
</tr></table>

Um die Campaign REST-APIs verwenden zu können, benötigen Sie ein Adobe I/O-Konto. Dies ist ein notwendiger erster Schritt zum Kennenlernen der API-Funktionen.
Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](setting-up-api-access.md).

Die APIs, die wir bereitstellen, basieren auf **Standardkonzepten** mit einer REST-Schnittstelle und JSON-Payloads.

Alle Endpunkte werden in dieser Dokumentation ausführlich mit den allgemeinen Begriffen beschrieben, die Sie für die Bearbeitung der API kennen sollten, sowie mit der vollständigen API-Referenz, Code-Beispielen und Schnellstartanleitungen. Alle Beispiele arbeiten mit Postman; Sie können aber auch Ihren bevorzugten REST-Client nutzen.

Wenn etwas fehlt oder fehlerhaft erscheint, fragen Sie bitte die [Community](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-standard/ct-p/adobe-campaign-standard-community?profile.language=de).
