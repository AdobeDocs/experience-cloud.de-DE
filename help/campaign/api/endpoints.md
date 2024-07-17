---
title: Endpunkte
description: Erfahren Sie mehr über die API-Endpunkte.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: 9f6d3da6-374d-47f5-bc8f-b31b19cbb5ca
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 95%

---

# Endpunkte {#endpoints}

Die verfügbaren Endpunkte für die Adobe Campaign REST-API:

* **/profileAndServices**: zur Interaktion mit vordefinierten Feldern. Erweiterte Felder können bei diesem Endpunkt nicht aufgerufen werden.
* **/profileAndServicesExt**: zur Interaktion mit benutzerdefinierten Feldern, die bei der benutzerdefinierten Ressourcenerweiterung von Profil oder Dienste hinzugefügt werden. Weiterführende Informationen zu benutzerdefinierten Ressourcen finden Sie in [diesem Abschnitt](custom-resources.md).
* **/&lt;transactionalAPI>**: zur Interaktion mit der API für Transaktionsnachrichten (der Name des API-Endpunkts für Transaktionsnachrichten hängt von der Konfiguration Ihrer Instanz ab). Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](managing-transactional-messages.md).
* **/workflow/execute**: zur Interaktion mit Workflows. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](controlling-a-workflow.md).

Standardmäßig stehen für die APIs **profileAndServices** und **profileAndServicesExt** folgende Hauptressourcen zur Verfügung:

* **/profile**: zur Interaktion mit Profilen aus der Campaign-Datenbank. Um einem Dienst Profile hinzuzufügen, verwenden Sie den Endpunkt **/service**. Weitere Informationen zu Profilen in Campaign finden Sie in der [Campaign-Dokumentation](https://helpx.adobe.com/de/campaign/standard/audiences/using/about-profiles.html).
* **/service**: zum Verwalten von Anmeldediensten. Weitere Informationen zu Diensten in Campaign finden Sie in der [Campaign-Dokumentation](https://helpx.adobe.com/de/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>Alle anderen Ressourcen, die erweitert oder erstellt wurden, stehen nur über die API **ProfileAndServicesExt** zur Verfügung. Sie müssen mit der **Profil**-Ressource verknüpft sein, um aufgerufen werden zu können.
