---
title: Starthandbuch
description: Führen Sie diese Schritte aus, um Ihre Anwendung in Adobe Experience Rollouts zu integrieren, von der Zugriffsanfrage bis zur Erstellung Ihres ersten Feature Flags.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 1%

---


# Starthandbuch {#startup-guide}

Führen Sie diese Schritte aus, um Erlebnis-Rollouts in Ihr Programm zu integrieren.

## Schritt 1: Zugriff anfordern {#step-1-access}

Fordern Sie Zugriff auf die Konsole „Experience Rollouts“ an und schließen Sie sich Ihrem Team an. Eine [&#x200B; Anleitung finden &#x200B;](../console/request-access.md) unter „Zugriff anfordern“.

## Schritt 2: Onboarding der Anwendung {#step-2-onboard}

Nachdem Sie Zugriff erhalten haben, melden Sie sich bei der Konsole Erlebnis-Rollouts an und stellen Sie sicher, dass Ihr Programm unter Ihrem Team aufgeführt ist. Ist dies nicht der Fall, bitten Sie Ihren Team-Administrator, es hinzuzufügen. Siehe [Onboarden des Programms](../applications/onboard-your-application.md).

Bereiten Sie vor dem Onboarding Folgendes vor:

| Anforderung | Details |
|---|---|
| **Anwendungs-ID** | Eine eindeutige Client-Kennung, die beim Aufrufen der Experience Rollouts-APIs verwendet wird. Verwenden Sie die vorhandene Client-ID Ihrer Anwendung, sofern verfügbar. |
| **Server-seitige Clients** | Bei der Integration mit einer serverseitigen SDK benötigen Sie eine Admin-Client-ID mit entsprechenden Berechtigungen. |
| **Desktop-Clients** | Anstelle einer Client-ID können ein Produkt-Code und eine Produktversion verwendet werden. |

## Schritt 3: Experience Rollouts-API abonnieren {#step-3-subscribe}

Abonnieren Sie die Experience Rollouts-API über die Adobe Developer Console, damit Ihre Anwendung die Feature Flag-Endpunkte aufrufen kann. Siehe [Abonnieren der API-Anwendung in Adobe Developer Console](subscribe-to-api-application.md).

>[!NOTE]
>
>Wenn Sie die Integration über eine Server-seitige SDK durchführen, benötigen Sie eine Service-Token-Client-ID. Wenden Sie sich an den Experience Rollouts-Support , um Ihre Client-ID zu ändern.

## Schritt 4: Integrieren mit einer SDK oder der API {#step-4-integrate}

Befolgen Sie die [Integrationsschritte](integration-steps.md) für Ihren Anwendungstyp. Wählen Sie den Pfad aus, der zu Ihrem Stack passt:

* **Webservices** → Java SDK oder Node.js SDK
* **Web und Mobile Apps** → Feature API v3
* **Desktop-Programme** → Feature API v2

## Schritt 5: Erstellen und Testen des ersten Feature Flag {#step-5-feature-flag}

Erstellen Sie nach Abschluss der Integration Ihr erstes Feature Flag in der Konsole und testen Sie es:

* [Erstellen des ersten Feature Flags](../feature-flags/create-your-first-feature-flag.md)

## Siehe auch {#see-also}

* [Integrieren von Erlebnis-Rollouts in Ihre App](integrating-in-your-app.md)
* [Integrationsschritte](integration-steps.md)
* [SDKs](sdks.md)
