---
title: Onboarding Ihres Programms
description: Erfahren Sie, wie Sie eine neue Anwendung in Adobe Experience Rollouts integrieren, damit Ihr Team Feature Flags erstellen und verwalten kann.
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 2%

---

# Onboarding Ihres Programms {#onboard-your-application}

Sie müssen über die Rolle **Admin** verfügen, um eine neue Anwendung hinzuzufügen. Wenden Sie sich an Ihren Team-Administrator, wenn Sie Ihre Rolle überprüfen oder aktualisieren müssen.

## Neue Anwendung hinzufügen {#add-application}

1. Melden Sie sich bei der Konsole „Experience Rollouts“ an und navigieren Sie zu **Admin > Anwendungen**.

   >[!NOTE]
   >
   >Wenn die Schaltfläche **Neue Anwendung** nicht sichtbar ist, stellen Sie sicher, dass Sie sich im richtigen Team befinden und die Rolle **Admin** haben.

2. Wählen Sie **Neue Anwendung** aus.

3. Wählen Sie den **Kanal** aus, der Ihrem Anwendungstyp (Web, Mobile, Desktop oder Service) entspricht.

4. Geben Sie die folgenden Informationen an:

   | Feld | Beschreibung |
   |---|---|
   | **Anwendungs-ID** | Eine eindeutige Kennung, die beim Aufrufen von Erlebnis-Rollouts aus Ihrem Code verwendet wird. Verwenden Sie die Client-ID Ihrer Anwendung. |
   | **TTL** | Das Abrufintervall (in Sekunden) für die Aktualisierung des Anwendungscache. Gilt nur für Server-seitige SDKs. |
   | **Team** | Das Team, das für diese Anwendung verantwortlich ist und sie verwaltet. Nur Mitglieder dieses Teams können dafür Feature Flags erstellen und bearbeiten. |

5. Bestätigen Sie die Angaben mithilfe der Schaltfläche **Hinzufügen**. Ihre Anwendung ist jetzt registriert und bereit für die Konfiguration des Feature Flags.

## Wie geht es weiter? {#next-steps}

Sobald Ihre Anwendung integriert ist, kann Ihr Team mit der Erstellung von Feature Flags beginnen:

* [Erstellen des ersten Feature Flags](../feature-flags/create-your-first-feature-flag.md)
* [Integrieren von Erlebnis-Rollouts in Ihre App](../integrate/integrating-in-your-app.md)

## Siehe auch {#see-also}

* [Anwendungen verwalten](manage-applications.md)
* [Melden Sie sich bei der Konsole an](../console/log-in-to-the-console.md)
