---
title: Anwendungen verwalten
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts Programme verwalten, neue Programme hinzufügen und die Verantwortung für das Team verstehen.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---


# Anwendungen verwalten {#manage-applications}

Ein **Programm** in Experience Rollouts stellt den Service oder das Produkt dar, den bzw. das Sie mit Feature Flags steuern möchten. Bevor Ihr Team Feature Flags erstellen kann, müssen Sie mindestens eine Anwendung in die Konsole integrieren.

## Wer kann Anwendungen verwalten? {#permissions}

Nur Mitglieder mit der Rolle **Admin** können Programme hinzufügen oder ändern. Wenn Sie diese Rolle nicht haben, wenden Sie sich an Ihren Team-Administrator.

## Hinzufügen einer Anwendung {#add-application}

Eine schrittweise Anleitung zum Hinzufügen einer Anwendung zu Ihrem Team [&#x200B; Sie unter &#x200B;](onboard-your-application.md) Ihrer Anwendung .

## Teameigentum {#team-ownership}

Jede Anwendung gehört genau einem Team. Nur Mitglieder dieses Teams können die Feature Flags der Anwendung verwalten.

Dieses Eigentümermodell wirkt sich auch darauf aus, wie Sie Elementgruppen strukturieren:

* **In Ihrem Team** - Ein Produktversionsinhaber kann Feature Flags über Anwendungen hinweg gruppieren, die demselben Team gehören. Siehe [Funktionsgruppen zur Steuerung mehrerer Funktionen](../../concepts/feature-groups-to-control-multiple-features.md).
* **Team-übergreifend** - Wenn Sie Feature Flags aus Programmen gruppieren müssen, die sich im Besitz verschiedener Teams befinden, verwenden Sie eine Team-übergreifende Feature Group, für die die Rolle **Feature Admin** erforderlich ist.

## Siehe auch {#see-also}

* [Onboarding Ihres Programms](onboard-your-application.md)
* [Funktionsgruppen zur Steuerung mehrerer Funktionen](../../concepts/feature-groups-to-control-multiple-features.md)
* [Benutzerrollen](../teams/user-roles.md)
