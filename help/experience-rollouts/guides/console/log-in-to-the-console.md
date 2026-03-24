---
title: Melden Sie sich bei der Konsole „Experience Rollouts“ an
description: Erfahren Sie, wie Sie mit Adobe Experience Rollouts beginnen, indem Sie Ihr Team finden, Zugriff anfordern und sich bei der Konsole anmelden.
source-git-commit: a7ff5bf33bd8e8c5ff89848955bf6af33b0d6c21
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 2%

---


# Melden Sie sich bei der Konsole „Experience Rollouts“ an {#log-in}

Die ersten Schritte mit dem Rollout von Erlebnissen umfassen drei Schritte: Suchen oder Erstellen eines Teams, Anfordern von Zugriff und Anmelden bei der Konsole.

## Voraussetzungen {#before-you-begin}

Erlebnis-Rollouts sind um **Teams** organisiert. Jedes Team besitzt ein oder mehrere Programme und verwaltet Feature Flags für diese Programme. Bevor Sie sich anmelden können, müssen Sie einem Team angehören.

Erkundigen Sie sich bei Ihrem Produkt oder Engineering-Lead, ob für Ihr Projekt bereits ein Team existiert. Bitten Sie in diesem Fall den Team-Administrator, Sie mit der richtigen [Benutzerrolle“ &#x200B;](../teams/user-roles.md). Wenn noch kein Team vorhanden ist, führen Sie die Schritte unter [Neues Team erstellen“ &#x200B;](create-a-new-team.md).

## Zugriff anfordern {#request-access}

Sobald Sie wissen, welchem Team Sie beitreten sollen, fordern Sie über das Zugriffsverwaltungssystem Ihres Unternehmens Zugriff an. Eine [&#x200B; Anleitung finden &#x200B;](request-access.md) unter „Zugriff anfordern“.

Nachdem Ihre Anfrage genehmigt wurde, erhalten Sie die Berechtigungen, die mit der Rolle verknüpft sind, die Ihnen von Ihrem Team-Administrator gewährt wurde.

## Melden Sie sich bei der Konsole an {#log-in-steps}

Nachdem der Zugriff gewährt wurde:

1. Wechseln Sie zu [https://experience.adobe.com/](https://experience.adobe.com/) und melden Sie sich mit Ihren Unternehmensanmeldeinformationen an.
2. Wählen Sie **Programmumschalter** Erlebnis-Rollouts“ aus.
3. Wählen Sie die entsprechende Umgebung aus (**Staging** für Tests, **Produktion** für Live-Rollouts. Detaillierte Informationen finden [&#x200B; unter &#x200B;](environments-overview.md)Umgebungen - Übersicht“.

## Erste Schritte nach der Anmeldung {#first-steps}

Überprüfen Sie nach der Anmeldung, ob Ihre Anwendung in der Konsole aufgeführt ist. Programme werden von Team-Administratoren verwaltet. Wenn Ihr Programm nicht aufgeführt ist, wenden Sie sich an Ihren Team-Administrator, damit es hinzugefügt wird. Weitere Informationen finden [&#x200B; unter &#x200B;](../applications/manage-applications.md) von Programmen .

## Wichtige Terminologie {#terminology}

| Begriff | Definition |
|---|---|
| **Team** | Eine selbstverwaltete Gruppe, die im Besitz von Programmen ist und Feature Flags verwaltet. Teams haben eine flache Struktur mit verschiedenen Benutzerrollen und Berechtigungsebenen. |
| **Anwendung** | Die Anwendung, die Sie mit Feature Flags steuern möchten. Jede Anwendung gehört einem Team. |
| **Feature Flag / Feature Group / Release** | Die in Experience Rollouts für Funktionstests und Versionsverwaltung erstellten Artefakte. |
