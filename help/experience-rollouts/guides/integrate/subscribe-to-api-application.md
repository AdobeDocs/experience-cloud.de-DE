---
title: Abonnieren der API-Anwendung in Adobe Developer Console
description: Erfahren Sie, wie Sie Ihre Anwendung über Adobe Developer Console für die Experience Rollouts-API abonnieren, damit Sie die Feature Flag-Endpunkte aufrufen können.
source-git-commit: 120a2ea34682c878aaf6f6cb75504a8704d10e3d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 3%

---


# Abonnieren der API-Anwendung in Adobe Developer Console {#subscribe-to-api}

Um die Experience Rollouts-API über Ihr Programm aufzurufen, müssen Sie sie über die [Adobe Developer Console](https://developer.adobe.com/console) abonnieren. Dadurch erhält die Anwendung eine Client-ID, mit der Experience Rollouts die Aufrufenden identifiziert.

## Voraussetzungen {#prerequisites}

Bevor Sie sich anmelden, bestätigen Sie Folgendes:

* Das Onboarding Ihres Programms erfolgt über die Konsole „Experience Rollouts“ (siehe &quot;[&#x200B; Ihres Programms](../applications/onboard-your-application.md)
* Sie haben Zugriff auf die Adobe Developer Console für Ihr Unternehmen

## Abonnieren der Experience Rollouts-API {#subscribe}

Gehen Sie wie folgt vor, um Ihre Anwendung für die Experience Rollouts-API zu abonnieren:

1. Wechseln Sie zu [Adobe Developer Console](https://developer.adobe.com/console) und melden Sie sich mit Ihren Unternehmensanmeldeinformationen an.
2. Wählen Sie Ihr Projekt aus oder erstellen Sie ein neues.
3. Wählen Sie **API hinzufügen** aus.
4. Suchen Sie nach **Experience Rollouts API** und wählen Sie sie aus.
5. Befolgen Sie die Anweisungen, um die API zu konfigurieren und Anmeldeinformationen zu generieren.
6. Beachten Sie die **Client-ID**, die für Ihr Projekt generiert wurde. Diese Kennung verwenden Sie, wenn Sie die Experience Rollouts-API aufrufen und Ihre Anwendung in der Experience Rollouts-Konsole einbinden.

## Server-seitige SDK-Integrationen {#server-sdk}

Bei der Integration mit der Java-SDK oder der Node.js-SDK benötigen Sie **API-Schlüssel eine Client** ID mit Service-Token. Mit dem Service-Token kann SDK Experience Rollouts-APIs im Hintergrund aufrufen.

>[!NOTE]
>
>Server-seitige SDK-Client-IDs müssen durch Experience Rollouts unterstützt werden, bevor sie API-Aufrufe durchführen können. Wenden Sie sich nach Abschluss der Developer Console-Einrichtung an den Support.

## Siehe auch {#see-also}

* [Starthandbuch](startup-guide.md)
* [SDKs](sdks.md)
* [Onboarding Ihres Programms](../applications/onboard-your-application.md)
* [Integrationsschritte](integration-steps.md)
